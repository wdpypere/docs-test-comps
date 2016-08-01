### NAME

ncm-gip2:  NCM component for generic LCG information provider

### DESCRIPTION

The ncm-gip2 component manages configuration of Generic Information Provider (GIP), used to collect data on available resources. It
allows to manage both LCG and gLite flavor of GIP.

### Resources

#### `/software/components/gip2/basedir` : string (required)

Base directory for gip components (must contain directories plugin/, provider/...)

Default : none.

#### `/software/components/gip2/group` : string (required)

Group GIP account belongs to. Used to define group ownership of GIP directories and files.

Default : root.

#### `/software/components/gip2/flavor` : string (required)

Define GIP flavor used. Can be 'lcg' org 'glite'.

Default : glite.

#### `/software/components/gip2/ldif` : nlist (optional)

Named list of LDIF files used by GIP plugins. Key is an arbitrary name, value is a nlist defiining a set of LDIF
entries to be added to a specific LDIF file. The LDIF entries can be either defined directly (no staticInfoCmd defined)
or as a configuration file processed by staticInfoCmd. This nlist properties are defined below.

Default : none.

##### LDIF confFile : string (optional)

Name of the file to create with 'entries', used as the input file for staticInfoCmd. Ignored when
staticInfoCmd is ommitted.

Default : key of the `/software/components/gip2/ldif` nlist.

##### LDIF template : string (deprecated)

Kept for backward compatibility. Ignored if specified.

Default : none.

##### LDIF ldifFile : string (required)

Name of the LDIF file to produce. It can be either a name or an absolute path. When using a name without a path,
the file will be created in the LDIF directory (basedir/ldif).

Default : none.

##### LDIF entries : nlist (optional)

nlist of LDIF entries (key is the DN, value is a nlist of attribute/value pairs) to put in the resulting file 
if staticInfoCmd is not specified or sets of key value/pairs (key is the set name and and value is a nlist of key/value pairs).

Key is interpreted as an escaped value.

If ommitted and confFile is defined, must be defined in `/software/components/gip2/ldifConfEntries` 
key matching confFile.

Default : none.

##### LDIF staticInfoCmd : string (optional)

Path of the command to execute to transform entries into a LDIF file. If absent, the global
staticInfoCmd is used.

Default : none.

#### `/software/components/gip2/ldifConfEntries` : nlist (optional)

It is a nlist of 'entries' (as defined under `/software/components/gip2/ldif`). The key must match a file name as
specified with confFile under `/software/components/gip2/ldif.` This property allows to have a global definition
of a configuration file, used to generate LDIF files, that is common to several LDIF sets/files (this is for example the
case for GLUE2 with the CREAM CE). When such a shared configuration file is used to generate several LDIF files,
'entries' under `/software/components/gip2/ldif` must be left undefined and the configuration file contents must
be defined here.

Default: none.

#### `/software/components/gip2/plugin` : nlist (optional)

Named list of GIP plugins (plugins are associated with a static LDIF file). Key the plugin name, value is the plugin script.

Default : none.

#### `/software/components/gip2/provider` : nlist (optional)

Named list of GIP providers. Key the provider name, value is the provider script.

Default : none.

#### `/software/components/gip2/staticInfoCmd` : string (optional)

Path of the command to execute to transform entries into a LDIF file if none is defined in the 
`/software/components/gip2/ldif` entry. It is here for backward compatibility but it is recommended
to define it as part of the ldif entries. If undefined in both locations, the configuration file
is read directly without any processing.

Default : none.

#### `/software/components/gip2/scripts` : nlist (optional)

Named list of GIP scripts (usually used to launch lcg/glite-info-generic with the appropriate configuration.
Key the script name, value is the script.

Default : none.

#### `/software/components/gip2/stubs` : nlist (optional)

Named list of static LDIF files produced without a Glue template. Mainly used to add intermediate LDIF entries
required for subtree search to work. Key is LDIF the file name (without directory), value is a list of LDIF entries
to put in the LDIF file.

If stubs are defined, BDII will be restarted if running on the current node.

Default : none.

#### `/software/components/gip2/external` : list of strings (optional)

List of files/scripts that will be trusted as if managed by the component.

Default : none.

#### `/software/components/gip2/user` : string (required)

Account GIP runs under. Used to define user ownership of GIP directories and files.

Default : none.

#### `/software/components/gip2/workDirs` : list of strings (optional)

List of working directories used by GIP that must be configured to be owned and writable by GIP user.

Default : none.

#### `/software/components/gip2/etcDir` : string (optional)

Location of the "etc" directory.

Default : basedir/etc (LCG) or basedir/etc/gip (gLite)

#### `/software/components/gip2/ldifDir` : string (optional)

Location of the "ldif" directory.

Default : basedir/ldif (LCG) or basedir/etc/ldif (gLite)

#### `/software/components/gip2/pluginDir` : string (optional)

Location of the "plugin" directory.

Default : basedir/plugin (LCG) or basedir/etc/plugin (gLite)

#### `/software/components/gip2/providerDir` : string (optional)

Location of the "provider" directory.

Default : basedir/provider (LCG) or basedir/etc/provider (gLite)

### DEPENDENCIES

None.

### BUGS

None known.

Charles Loomis <charles.loomis@cern.ch>

Charles Loomis <charles.loomis@cern.ch>,Michel Jouvin <>

### VERSION

2.7.2

### SEE ALSO

ncm-ncd(1)
