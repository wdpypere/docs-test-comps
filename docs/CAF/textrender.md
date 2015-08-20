### NAME

CAF::TextRender - Class for rendering structured text

### SYNOPSIS

    use CAF::TextRender;

    my $module = 'tiny';
    my $trd = CAF::TextRender->new($module, $contents, log => $self);
    print "$trd"; ### stringification

    $module = "general";
    $trd = CAF::TextRender->new($module, $contents, log => $self);
    ### return CAF::FileWriter instance (rendered text already added)
    my $fh = $trd->filewriter('/some/path');
    die "Problem rendering the text" if (!defined($fh));
    $fh->close();

### DESCRIPTION

This class simplyfies the generation of structured text like config files.
(It is based on 14.8.0 ncm-metaconfig).

#### Private methods

- `_initialize`

    Initialize the process object. Arguments:

    - `module`

        The rendering module to use: either one of the following reserved values

        - json

            JSON format (using `JSON::XS`) (JSON true and false have to be resp. `\1` and c<\\0>)

        - yaml

            YAML (using `YAML::XS`) (YAML true and false, either resp. `$YAML_BOOL-`{yes}> and
            `$YAML_BOOL-`{no}>; or the strings `$YAML_BOOL_PREFIX."true"` and
            `$YAML_BOOL_PREFIX."false"` (There are known problems with creating hashrefs using the
            `$YAML_BOOL-`{yes}> value for true; Perl seems to mess up the structure when creating
            the hashrefs))

        - properties

            Java properties format (using `Config::Properties`),

        - tiny

            .INI format (using `Config::Tiny`)

        - general

            (using `Config::General`)

        Or, for any other value, `Template::Toolkit` is used, and the `module` then indicates
        the relative path of the template to use.

    - `contents`

        `contents` is a hash reference holding the contents to pass to the rendering module.

    It takes some extra optional arguments:

    - `log`

        A `CAF::Reporter` object to log to.

    - `includepath`

        The basedirectory for TT template files, and the INCLUDE\_PATH
        for the Template instance. The `includepath` is either a string
        (i.e. ':'-separated list of paths), an arrayref (of multiple include paths)
        or undef (the default '/usr/share/templates/quattor' is used).

    - `relpath`

        The relative path w.r.t. the includepath to look for TT template files.
        This relative path should not be part of the module name, however it
        is not the INCLUDE\_PATH. (In particular, any TT `INCLUDE` statement has
        to use it as the relative basepath).
        If `relpath` is undefined, the default 'metaconfig' is used. If you do not
        have a subdirectory in the includepath, use an empty string.

    - `eol`

        If `eol` is true, the rendered text will be verified that it ends with
        an end-of-line, and if missing, a newline character will be added.
        By default, `eol` is true (this is text rendering afterall).

        `eol` set to false will not strip trailing newlines (use `chomp`
        or something similar for that).

    - `usecache`

        If `usecache` is false, the text is always re-rendered.
        Default is to cache the rendered text (`usecache` is true).

    - `ttoptions`

        A hash-reference `ttoptions` with Template Toolkit options,
        except for INCLUDE\_PATH which is forced via `includepath` option.
        By default, STRICT (default 0) and RECURSION (default 1) are set.

#### `get_text`

`get_text` renders and returns the text.

In case of a rendering error, `get_text` returns `undef`
(and an error is logged if log instance is present).
This is the main difference from the auto-stringification that
returns an empty string in case of a rendering error.

By default, the rendered result is cached. To force re-rendering the text,
clear the current cache by passing `1` as first argument
(or disable caching completely with the option `usecache`
set to false during the <CAF::TextRender> initialisation).

#### `filewriter`

Create and return an open `CAF::FileWriter` instance with
first argument as the filename. If the rendering fails,
`undef` is returned.

The rendered text is added to the filehandle.
It's up to the consumer to cancel
and/or close the instance

All `CAF::FileWriter` initialisation options are supported
and passed on. (If no `log` option is provided,
 the one from the `CAF::TextRender` instance is passed).

Two new options `header` and `footer` are supported
 to resp. prepend and append to the rendered text.

If `eol` was set during initialisation, the header and footer
will also be checked for EOL.
(EOL is still added to the rendered text if
`eol` is set during initialisation, even if there is a footer
defined.)
