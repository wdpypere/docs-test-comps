### NAME

yaim: NCM component for configuring gLite middleware via YAIM (version 3.1 and higher).

Note that this version of the component is not backwards compatible with version 
1.1 and earlier. See section **CHANGES SINCE VERSION 1.1** for more details.

### DESCRIPTION

The _yaim_ component generates the yaim configuration file and runs
the corresponding configuration script for the kind of node.
By default, the configuration file (SITE\_INFO\_DEF\_FILE) is generated under
`/etc/lcg`-quattor-site-info.def.

An example configuration template (yaim\_example.tpl) is shipped with
this component.

Important: Please read the BUGS section of this man page!!

### RESOURCES

#### `/software/components/yaim/configure` (boolean)

If defined and and set to true, the YAIM configuration phase is
triggered. If not, the component will only print what it would do

#### `/software/components/yaim/force` (boolean)

If true, Yaim is always executed. Normally Yaim will only be executed if
either the contents of the generated configuration files have changed, 
or if the previous run of Yaim ended with an error.
The default for this option is false.

#### `/software/components/yaim/nodetype` (list of strings)

specifies which node types are configured on that machine and the order
in which they are configured. 
A single machine may belong to one or more node types.
The list of supported node types is automatically determined at run time by
parsing the information in the files in directory node-info.d. These files are
provided by the gLite middleware installation.

Note: the values for <X> are case sensitive, but do not depend on
the prefix _glite-_!
Note as well that not all of these node types are fully tested.
Please check yourself at least once if you are happy with the result.
(The ncm-yaim component is just responsible for generating the yaim
config file and running yaim, but it cannot guarantee the correct
functioning of yaim).

Please refer to the YAIM documentation for the precise meaning of
these configuration keys.

Example:

     "/software/components/yaim/nodetype"    = list("WN");
     "/software/components/yaim/configure"   = true;

This will configure the WN services.

#### `/software/components/yaim/conf`/<X> (string)

Sets a specific Yaim configuration setting <X>. Valid config keys are:

        LCG_REPOSITORY CA_REPOSITORY REPOSITORY_TYPE
        CE_HOST CLASSIC_HOST RB_HOST PX_HOST BDII_HOST MON_HOST REG_HOST 
        GRID_TRUSTED_BROKERS GRID_ACCEPTED_CREDENTIALS 
        GRID_AUTHORIZED_RENEWERS GRID_DEFAULT_RENEWERS 
        GRID_AUTHORIZED_RETRIEVERS GRID_DEFAULT_RETRIEVERS
        GRID_AUTHORIZED_KEY_RETRIEVERS GRID_DEFAULT_KEY_RETRIEVERS
        GRID_TRUSTED_RETRIEVERS GRID_DEFAULT_TRUSTED_RETRIEVERS
        WN_LIST USERS_CONF
        FUNCTIONS_DIR
        MYSQL_PASSWORD GRIDICE_SERVER_HOST SITE_EMAIL SITE_SUPPORT_EMAIL
        SITE_NAME SITE_VERSION SITE_HTTP_PROXY INSTALL_DATE INSTALL_ROOT OUTPUT_STORAGE
        BDII_HTTP_URL BDII_REGIONS BDII_CE_URL BDII_SE_URL
        BDII_RB_URL BDII_PX_URL
        DCACHE_ADMIN DCACHE_POOLS DCACHE_PORT_RANGE RESET_DCACHE_CONFIGURATION
        MY_DOMAIN
        DPMCONFIG DPMDATA DPMDB_PWD DPMFSIZE DPM_HOST DPMLOGS
        DPMPOOL DPM_POOLS DPM_PORT_RANGE DPMUSER_PWD DPMMGR
        GLOBUS_TCP_PORT_RANGE GRIDMAP_AUTH JAVA_LOCATION JOB_MANAGER
        LFC_HOST QUEUES SE_TYPE LFC_DB_PASSWORD LFC_DB LFC_DB_HOST
        CRON_DIR
        SITE_LOC SITE_LAT SITE_LONG SITE_WEB SITE_TIER SITE_SUPPORT_SITE
        APEL_DB_PASSWORD
        VOBOX_HOST VOBOX_PORT
        GSSKLOG GSSKLOG_SERVER
        LFC_TYPE LFC_HOST_ALIAS TORQUE_SERVER BATCH_SERVER EDG_WL_SCRATCH
        BATCH_LOG_DIR BDII_FCR CE_DATADIR CLASSIC_STORAGE_DIR DPMPOOL_NODES
        GROUPS_CONF RB_RLS SE_ARCH
        YAIM_VERSION
        DPM_DB_HOST
        BATCH_BIN_DIR BATCH_VERSION BATCH_CONF_DIR 
        RFIO_PORT_RANGE VO_SW_DIR WMS_HOST ORACLE_LOCATION LB_HOST
        GRIDVIEW_WSDL USERS_DN_WMS
        SITE_DESC SITE_SECURITY_EMAIL
        SITE_OTHER_GRID SITE_OTHER_EGEE_ROC SITE_OTHER_EGEE_SERVICE
        SITE_OTHER_WLCG_TIER
        MYSQL_ADMIN
        NAGIOS_ADMIN_DNS
        NAGIOS_CGI_ENABLE_CONFIG
        NAGIOS_HOST
        NAGIOS_HTTPD_ENABLE_CONFIG
        NAGIOS_NAGIOS_ENABLE_CONFIG
        NAGIOS_NCG_ENABLE_CONFIG
        NAGIOS_NSCA_PASS
        NAGIOS_ROLE
        NCG_VO
        NAGIOS_MYPROXY_NAME
        NCG_GOCDB_COUNTRY_NAME
        NCG_GOCDB_ROC_NAME
        NCG_LDAP_FILTER
        NCG_NRPE_UI
        NCG_PROBES_TYPE
        CEMON_HOST ACCESS_BY_DOMAIN CREAM_DB_USER BLPARSER_HOST BLP_PORT CREAM_PORT BLAH_JOBID_PREFIX 
        CREAM_CE_STATE

Note: the values for <X> have to be upper case!

Please refer to the YAIM documentation for the precise meaning of
these configuration keys.

Example:

      "/software/components/yaim/conf/CE_HOST"="myce01.mydomain.org";

The values are automatically put in quotes in the resulting
configuration file under `/etc/lcg`-quattor-site-info.def :

      CE_HOST="myce01.mydomain.org"

You can provide a script in `/usr/libexec`/ called create-YAIM-users\_conf, which is
executed if it exists with the full name of the users.conf file as an argument. Here
you can add your own script to create the users.conf file. The same is true for the
groups.conf file, it is called create-YAIM-groups\_conf.

If no users.conf resp. groups.conf exists, this YAIM component will copy over the
expample ones, otherwise a configuration of gLite 3.0 will fail.

#### `/software/components/yaim/vo`/&lt;list>/services/<X>

(Note: for backwards compatibility, VO info may be found also under
       `/system/vo` if `/software/components/yaim/vo` is not defined)

Sets a number of VO related parameters. <X> can be:

    SW_DIR DEFAULT_SE SE SGM USERS STORAGE_DIR QUEUES VOMS_SERVERS VOMS_EXTRA_MAPS VOMS_POOL_PATH VOMSES

Note: the values for <X> have to be upper case!

Please refer to the YAIM documentation for the precise meaning of
these configuration keys.

The VO output is by default written to the generated configuration file. However, if the
value USE\_VO\_D is defined and true, the configuration per VO is written to a file vo.d/VO\_NAME
under the directory containing the SITE\_INFO file.

Example (assuming that `/software/components/yaim/vo/0` is ATLAS):

     "/software/components/yaim/vo/0/services/SW_DIR"="/pool/atlas";

This will generate in the yaim config file `/etc/lcg`-quattor-site-info.def :

     VO_ATLAS_SW_DIR="/pool/atlas"

#### `/software/components/yaim/conf/FTA`/<X>

Sets a specific FTA specific configuration setting <X>. Because the number of possible keys is almost unlimited
Any entry for <X> will be taken.

Please refer to the YAIM documentation for the precise meaning of
these configuration keys.

Example:

      "/software/components/yaim/conf/FTA/MACHINES"="castor pollox pia";

results in:

      FTA_MACHINES="castor pollox pia"

#### `/software/components/yaim/conf/FTS`/<X>

Sets a specific FTS specific configuration setting <X>. Valid config keys are:

    HOST_ALIAS DBURL STATS_GENERATION_INTERVAL SUBMIT_VOMS_ATTRIBUTES
    ADMIN_VOMS_ATTRIBUTES DB_SQLPLUS_CONNECTSTRING DB_USER DB_PASSWORD

Note: the values for <X> have to be upper case!

Please refer to the YAIM documentation for the precise meaning of
these configuration keys.

Example:

      "/software/components/yaim/conf/FTS/HOST_ALIAS"="prod-fts";

results in:

      FTS_HOST_ALIAS="prod-fts"

#### `/software/components/yaim/conf/CE`/<X>

Sets a specific CE specific configuration setting <X>. Valid config keys are:

    BATCH_SYS CPU_MODEL CPU_VENDOR
    CPU_SPEED OS OS_RELEASE OS_VERSION MINPHYSMEM
    MINVIRTMEM SMPSIZE SI00 SF00 OUTBOUNDIP
    INBOUNDIP RUNTIMEENV

Note: the values for <X> have to be upper case!

Please refer to the YAIM documentation for the precise meaning of
these configuration keys.

Example:

      "/software/components/yaim/conf/CE/CPU_MODEL"="PIII";

results in:

      CE_CPU_MODEL="PIII"

#### `/software/components/yaim/conf/CE/closeSE`/<SE>/<X>

Sets a number of CE / close SE related parameters. <X> can be:

    HOST, ACCESS_POINT

Note: the values for <X> have to be upper case!

Please refer to the YAIM documentation for the precise meaning of
these configuration keys.

Example:

    "/software/components/yaim/conf/CE/closeSE/se01/HOST"=value("/software/components/yaim/conf/se_host");
    "/software/components/yaim/conf/CE/closeSE/se01/ACCESS_POINT"="/storage";

    "/software/components/yaim/conf/CE/closeSE/se02/HOST"="anotherse.mydomain.org";
    "/software/components/yaim/conf/CE/closeSE/se02/ACCESS_POINT"="/somewhere";

Assuming that `/software/components/yaim/conf/CLASSIC`\_HOST is "se.mydomain.org" this settings results in:

    SE_LIST="SE01 SE02"
    CE_CLOSE_SE01_HOST="se.mydomain.org"
    CE_CLOSE_SE01_ACCESS_POINT="/storage"
    CE_CLOSE_SE2_HOST="anotherse.cern.ch"
    CE_CLOSE_SE2_ACCESS_POINT="/somewhere"

#### `/software/components/yaim/SCAS`/<X>

Sets configuration specific for the SCAS server. Valid configuration keys:
  SCAS\_HOST
  SCAS\_PORT
  SCAS\_CONFIG
  SCAS\_DEBUG\_LEVEL
  SCAS\_GROUP
  SCAS\_HOST\_CERT
  SCAS\_HOST\_KEY
  SCAS\_LCMAPS\_CONFIG
  SCAS\_LCMAPS\_DEBUG\_LEVEL
  SCAS\_LCMAPS\_DIR
  SCAS\_LCMAPS\_LOG\_LEVEL
  SCAS\_LCAS\_CONFIG
  SCAS\_LCAS\_DEBUG\_LEVEL
  SCAS\_LCAS\_DIR
  SCAS\_LCAS\_LOG\_LEVEL
  SCAS\_LOG\_DIR
  SCAS\_LOG\_FILE
  SCAS\_LOG\_LEVEL
  SCAS\_USER

#### `/software/components/yaim/GLEXEC`/<X>

Sets configuration specific for GLEXEC at the worker node. Valid configuration keys:
  GLEXEC\_WN\_OPMODE
  GLEXEC\_WN\_SCAS\_ENABLED
  GLEXEC\_WN\_LCASLCMAPS\_LOG
  GLEXEC\_WN\_LCAS\_DEBUG\_LEVEL
  GLEXEC\_WN\_LCAS\_DIR
  GLEXEC\_WN\_LCAS\_CONFIG
  GLEXEC\_WN\_LCAS\_LOG\_LEVEL
  GLEXEC\_WN\_LCMAPS\_DEBUG\_LEVEL
  GLEXEC\_WN\_LCMAPS\_DIR
  GLEXEC\_WN\_LCMAPS\_CONFIG
  GLEXEC\_WN\_LCMAPS\_LOG\_LEVEL
  GLEXEC\_WN\_LOG\_DIR
  GLEXEC\_WN\_LOG\_FILE
  GLEXEC\_WN\_LOG\_LEVEL
  GLEXEC\_WN\_LOG\_DESTINATION
  PILOT\_JOB\_FLAG
  GLEXEC\_EXTRA\_WHITELIST
  SCAS\_HOST
  SCAS\_PORT
  SCAS\_ENDPOINTS

#### `/software/components/yaim/vo`

If this (ordered) list exists, only these VOs are taken into account, in the given order. This was implemented
as required to set up the LCF services with this YAIM component. If this branch of the schema does not
exist, no changes apply. With this list you can also restrict the list of VOs.

#### Further configuration

It is possible to add arbitrary information to the YAIM input file by putting it into the global schema 
under:

      "/software/components/yaim/extra/"

Example:

      "/software/components/yaim/extra/FUTURE_GLITE_CONF_VAR" = "Glite 5.0";

This will result in:

      FUTURE_GLITE_CONF_VAR" = "Glite 5.0"

As the example shows, this tree can also be used to add missing or new variables, until they have made 
it into a new realease of this component

#### Secure information

To avoid putting security relevant information, like database passwords into CDB, this component is now adding the
file `/etc/yaim.secretpasswords` to the end of the info.def file. You can use other methods to put this file (in mode 600)
onto the node. The file name is configurable with the value 

    "/software/components/yaim/SECRET_PASSWORDS" = "/etc/.myinvisiblesecret";

#### further configurations

The info.def file itself is configurable:

    "/software/components/yaim/SITE_INFO_DEF_FILE" = "/etc/glite-quattor-site-info.def"; 

And it defaults to `/etc/lcg`-quattor-site-info.def.

The path to YAIM is configurable, which allows to use this component for LCG as well as for gLite:

    "/software/components/yaim/conf/YAIM_HOME" = "/opt/glite/yaim";

All other paths are derived from it.

The location of the Yaim script itself is configurable via:

    "/software/components/yaim/YAIM_SCRIPT" = "/path/to/my/yaim/script";

This allows to use wrappers for Yaim. By default, \<YAIM\_SCRIPT\> is undefined
and the script to be executed is \<YAIM\_HOME\>/bin/yaim.

### DEPENDENCIES

#### Components to be run before:

none.

#### Components to be run after:

none.

### Important: BUGS

The Pan 'global schema' path locations for the resources described
above have not been agreed yet - thus they end up under
`/software/components/yaim`/\*.

In previous ncm-yaim versions, `/system/vo` was used for VO
information. This has been moved now to `/software/components/yaim/vo` -
for backwards compatibility, the old path is used if that one is
undefined.

There are a number of underlying Yaim bugs (see above, and also in
Savannah under https://savannah.cern.ch/bugs/?group=lcgoperation,
category 'yaim').

The Yaim functions used for any particular node type are defined in
\<YAIM\_HOME\>/node-info.d/\*. These files are provided as part of the gLite release
and cannot be edited by ncm-yaim in order to add/remove/change functions.

### CHANGES SINCE VERSION 1.1

\* Support for Yaim versions prior to 3.1 has been dropped.

\* It is no longer possible to install middleware via Yaim.

\* If writing the configuration file(s) or execution of the Yaim command fails,
the generated configuration file is renamed with suffix _.failed_. 
When Yaim completes without errors, the configuration directory will not contain
any more configuration file with this suffix.

\* The schema has changed: the attribute node type is now a list of strings, to
enable configuration of an ordered list of node types.

Thorsten Kleinwort <Thorsten.Kleinwort@yahoo.de>
German Cancio <German.Cancio@cern.ch>
James Casey <James.Casey@cern.ch>
Ulrich Schwickerath <Ulrich.Schwickerath@cern.ch>
Veronique Lefebure <Veronique.Lefebure@cern.ch>
Ronald Starink <>

### SEE ALSO

ncm-ncd(1), http://cern.ch/quattor
http://cern.ch/grid-deployment

An example configuration template (yaim\_example.tpl) is shipped with
this component.
