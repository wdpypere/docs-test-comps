
### NAME

ncm-metaconfig: Configure services whose config format can be
rendered via [TextRender](../CAF/TextRender.md).

### DESCRIPTION

metaconfig

### RESOURCES

#### `/software/components/metaconfig`

The configuration information for the component.  It is an nlist of
`services`, indexed by absolute path. Each service contains:

- `mode` : long

    File permissions. Defaults to 0644.

- `owner` : string

    File owner. Defaults to root.

- `group` : string

    File group. Defaults to root.

- `backup` ? string

    Extension for the file's backup.

- `module` : string

    Module to render the configuration file. See ["CONFIGURATION MODULES"](#configuration-modules)
    below.

- `daemons` ? `caf_service_action{}`

    An nlist with foreach daemon the [Service](../CAF/Service.md) action to take
    if the file changes.

    Even if multiple `services` are associated to the same daemon, each action
    for the daemon will be taken at most once.

    If multiple actions are to be taken for the same daemon, all actions
    will be taken (no attempt to optimize is made).

- `preamble` ? string

    Text to place at start of file.

    It can be useful to include context in a configuration file, in the form of
    a comment, such as how it was generated. Most of the formats that can be
    output by this component support "comment" lines, but none of the modules that
    it uses will generate them. The preamble attribute will be written out
    verbatim, before the contents is generated. No comment character is added,
    the user must specify this as part of the preamble string.

- `contents`

    A free-form structure describing the valid entries for the
    configuration file. It is recommended to define another type for each
    config file, and bind it to these contents, to get the best
    validation.

- `element`

    Predefined conversions from `EDG::WP4::CCM::TextRender`:

    - `yesno` ? boolean

        Convert boolean to (lowercase) 'yes' and 'no'.

    - `YESNO` ? boolean

        Convert boolean to (uppercase) 'YES' and 'NO'.

    - `truefalse` ? boolean

        Convert boolean to (lowercase) 'true' and 'false'.

    - `TRUEFALSE` ? boolean

        Convert boolean to (uppercase) 'TRUE' and 'FALSE'.

    - `doublequote` ? boolean

        Convert string to doublequoted string.

    - `singlequote` ? boolean

        Convert string to singlequoted string.

### CONFIGURATION MODULES

The following formats can be rendered via `CAF::TextRender`:

- general

    Uses Perl's [Config::General](https://metacpan.org/pod/Config::General). This leads to configuration files
    similar to this one:

        <nlist>
          <another nlist>
            scalar value
            another scalar value
          </another nlist>
        </nlist>
        list_element 0
        list_element 1
        list_element 2

- tiny

    Uses Perl's [Config::Tiny](https://metacpan.org/pod/Config::Tiny), typically for `key = value` files or
    INI-like files with sections separated by `[section]` headers.

- yaml

    Uses Perl's [YAML::XS](https://metacpan.org/pod/YAML::XS) for rendering YAML configuration files.

- json

    Uses [JSON::XS](https://metacpan.org/pod/JSON::XS) for rendering JSON configuration files.

- properties

    Uses [Config::Properties](https://metacpan.org/pod/Config::Properties) for rendering Java-style configuration
    files.

- Any other string

    Uses [Template::Toolkit](https://metacpan.org/pod/Template::Toolkit) for rendering configuration files in formats
    supplied by the user.

    The name of the template is given by this field. It **must** be a path
    relative to `metaconfig/`, and the component actively sanitizes this
    field.

### EXAMPLES

#### Configuring `/etc/ccm.conf`

The well-known `/etc/ccm.conf` can be defined like this:

### Define a valid structure for the file

    type ccm_conf_file = {
        "profile" : type_absoluteURI
        "debug" : long(0..5)
        "force" : boolean = false
        ...
    };

    bind "/software/components/metaconfig/services/{/etc/ccm.conf}/contents" = ccm_conf_file;

### Fill in the contents

    prefix "/software/components/metaconfig/services/{/etc/ccm.conf}"

    "contents/profile" = "http://www.google.com";
    "module" = "general";

### And that's it

Now, just compile and deploy. You should get the same results as with
old good [ccm](../components/ccm.md).

#### Generating an INI-like file

We can generate simple INI-like files with the `Config::Tiny` module.

### Example schema

Let's imagine the file has two sections with one key each:

    # This is the first section, labeled "s1"
    type section_1 = {
       "a" : long
    };

    # This is the second section, labeled "s2"
    type section_2 = {
       "b" : string
    };

    # This is the full file structure
    type my_ini_file = {
       "s1" : section_1
       "s2" : section_2
    };

    bind "/software/components/metaconfig/services/{/etc/foo.ini}/contents" = my_ini_file;

### Describing the file

We'll define the permissions, who renders it and which daemons are associated to it.

    prefix "/software/components/metaconfig/services/{/etc/foo.ini}";

    "mode" = 0600;
    "owner" = "root";
    "group" = "root";
    "module" = "tiny";
    "daemons/foo" = "restart";
    "daemons/bar" = "reload";

And we'll ensure the module that renders it is installed (Yum-based
syntax here):

    "/software/packages/{perl-Config-Tiny}" = nlist();

### Describing the file's contents

And now, we only have to specify the contents:

    prefix "/software/components/metaconfig/services/{/etc/foo.ini}/contents";
    "s1/a" = 42;
    "s2/b" = "hitchicker";

### And that's it

That's it!  When you deploy your configuration you should see your
`/etc/foo.ini` in the correct location.
