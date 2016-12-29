
### NAME

lcmaps: NCM component to manage LCMAPS configuration file(s)

### DESCRIPTION

The _lcmaps_ component writes the LCMAPS configuration file(s). The
primary file is the LCMAPS database, listing the plugin modules
to be defines and the policies to describe (in the specific order 
as specified in the list in the CDB).

### RESOURCES

#### `/software/components/lcmaps/dbpath`

Location of the main LCMAPS database (list of plugin modules).
Default: `/opt/edg/etc/lcmaps/lcmaps.db`

#### `/software/components/lcmaps/modulepath`

The LCMAPS module search path.

#### `/software/components/lcmaps/module`

Named list (nlist) of modules to be used in the LCMAPS policies.
The names here are the module symbolic references that
are used to define the policies

#### `/software/components/lcmaps/module/{}/path`

Path of the module to load.

#### `/software/components/lcmaps/module/{}/args`

Arguments to the module (these are concatenated to the module
path itself and quoted.

#### `/software/components/lcmaps/policies`

List (ordered) of LCMAPS policies

#### `/software/components/lcmaps/policies`/\[\]/name

Name of the policy.

#### `/software/components/lcmaps/policies`/\[\]/ruleset

List (ordered) of rulesets for this policy.

### EXAMPLE

    "/software/components/lcmaps/dbpath" = "/opt/edg/etc/lcmaps/policy.conf";
    "/software/components/lcmaps/modulepath" = "/opt/edg/lib/lcmaps/modules";
    "/software/components/lcmaps/module/localaccount/path" = 
           "lcmaps_localaccount.mod";
    "/software/components/lcmaps/module/localaccount/args" = 
           "-gridmapfile `/etc/grid`-security/grid-mapfile";

    "/software/components/lcmaps/module/poolaccount/path" = "lcmaps_poolaccount.mod";
    "/software/components/lcmaps/module/poolaccount/args" =
           " -override_inconsistency" +
           " -gridmapfile `/etc/grid`-security/grid-mapfile" +
           " -gridmapdir `/etc/grid`-security/gridmapdir";

    "/software/components/lcmaps/module/posixenf/path" = "lcmaps_posix_enf.mod";
    "/software/components/lcmaps/module/posixenf/args" =
           " -maxuid 1 -maxpgid 1 -maxsgid 32";
    "/software/components/lcmaps/policies" = list (
         nlist(
                 "name", "standard",
                 "ruleset", list (
                         "localaccount -> posixenf | poolaccount",
                         "poolaccount -> posixenf"
                         )
                 ),
         nlist(
                 "name", "GridFTPacquisition",
                 "ruleset", list (
                         "vomsextract -> vomslocalgroup",
                         "vomslocalgroup -> vomspoolgroup",
                         "vomspoolgroup -> vomspoolaccount",
                         "vomspoolaccount -> ldap_enf"
                         )
                 )
    );

### Multi-file mode

If "/software/components/lcmaps/multifile" is set to True, the LCMAPS
component will work in the experimental "multi-file" mode. The regular
resources like "/software/components/lcmaps/dbpath" are ignored, and
relocated, but similarly named ones in the array
"/software/components/lcmaps/config\[\]" are used. Thus, multiple
LCMAPS policy files can be written to support for example separate
services (gatekeeper, gridftp) on the same host. 
For example, the ".../dbpath" resource becomes:

    "/software/components/lcmaps/config/0/dbpath" = "/opt/edg/etc/lcmaps/policy.gridftp";
    "/software/components/lcmaps/config/0/modulepath" = "/opt/edg/lib/lcmaps/modules";
    ...

    "/software/components/lcmaps/config/1/dbpath" = "/opt/edg/etc/lcmaps/policy.gatekeeper";
    ...
