### NAME

ncm-dpmlfc : NCM component to manage DPM and LFC configuration.

### DESCRIPTION

This component allows to manage configuration of DPM and LFC services, with the exception of DPM xrootd protocol which is managed by 
the ncm-xrootd configuration module.

Configuration module **ncm-dpmlfc** requires that the DPM and/or LFC configuration describes all nodes participating to the service and their respective 
role (in term of daemon running on each node). Each daemon/host combination is called a daemon instance in this documentation.

Using the whole DPM and/or LFC description, **ncm-dpmlfc** takes care of action needed on every node to configure it as requested 
(you MUST use the same configuration description on every node participating to DPM and/or LFC). This includes restarting 
a service after configuration changes if needed.

There are 2 sets of configuration options:

- Global options

    There is one separate set for DPM and LFC, `/software/components/dpmlfc/options/dpm` and `/software/components/dpmlfc/options/lfc` respectively. In each set,
    there is a subset, `db`, describing the database and database connection options.

- Protocol options

    For each access or management protocol, there is one set of global options under `/software/components/dpmlfc/protocols`. Each option defined in these sets
    can be superseded in the node-specific options for the given protocol.

Following sections describe each option by group of related options.

### GLOBAL OPTIONS (DPM and LFC)

DPM and LFC accept the same global options but there is a separate set for each one. Replace `PRODUCT` by `dpm` or `lfc`.

- `/software/components/dpmlfc/options/PRODUCT/accessProtocols` : list (optional, DPM only)

    List of access protocols supported on disk servers. Supported protocols are : https, gsiftp, rfio, xroot.
    Note that xrootd configuration itself, including the DPM/Xrootd plug-in, must be configured with
    ncm-xrootd.

    Default: None (default configuration provided by RPM will be used)

- `/software/components/dpmlfc/options/PRODUCT/controlProtocols` : list (optional, DPM only)

    List of control protocols supported. Supported protocols are : srmv1, srmv2, srmv2.2.

    Default: None (default configuration provided by RPM will be used)

- `/software/components/dpmlfc/options/PRODUCT/gridmapfile`

    This option defines the local gridmap file used by products daemons. 

    Default: None (default configuration provided by RPM will be used)

- `/software/components/dpmlfc/options/PRODUCT/gridmapdir`

    This option defines the gridmap dir used by products daemons. 

    Default: None (default configuration provided by RPM will be used)

- `/software/components/dpmlfc/options/PRODUCT/group`

    This option defines the userid used by product daemons. 

    Default: None (default configuration provided by RPM will be used)

- `/software/components/dpmlfc/options/PRODUCT/user`

    This option defines the userid used by product daemons. 

    Default: dpmmgr for DPM, lfcmgr for LFC

### DATABASE CONNECTION OPTIONS (DPM and LFC)

DPM and LFC accepts the same set of options to describe the database connection. In the following option names, 
replace `PRODUCT` by either `dpm` or `lfc`. Both sets can coexist.

- `/software/components/dpmlfc/options/PRODUCT/db/configfile`

    This option defines the file used to keep track of database connection information. This file will be owned by the userid used to run daemons and only this user will have access to this file.

    Default : `/etc/DPMCONFIG` for DPM, `/etc/NSCONFIG` for LFC

- `/software/components/dpmlfc/options/PRODUCT/db/infoFile` (string, optional)

    Name (without path) of the file containing connection information to DPM DB to be used by GIP to collect information about DPM.
    This file will be owned and accessible only by GIP user.

    This file will not be created if `infoUser` is not defined.

    Default : DPMINFO for DPM, LFCINFO for LFC.

- `/software/components/dpmlfc/options/PRODUCT/db/infoPwd` (string, optional)

    Password for database connection account used by GIP to collect information about DPM

    Default : generated password. It is recommended to use this default value (password changed at each run).

- `/software/components/dpmlfc/options/PRODUCT/db/infoUser` (string, optional)

    Username for database connection account used by GIP to collect information about DPM. If this option
    is not defined, the infoFile is not updated by **ncm-dpmlfc**.

    Default : None

- `/software/components/dpmlfc/options/PRODUCT/db/password` (string, required)

    This option defines the password used to connect to the database.

    Default : none

- `/software/components/dpmlfc/options/PRODUCT/db/server` (string, optional)

    This option defines the server running the database. This component checks that
    DPM and LFC database server run on different node (DPNS and LFC use the same database name). 
    `localhost` is considered different as DPNS and LFC are not allowed to run on the same node. 

    Default : localhost.

- `/software/components/dpmlfc/options/PRODUCT/db/user`

    This option defines the userid used to connect to the database.

    Default : userid used to run daemons

### PROTOCOL OPTIONS (DPM and LFC)

Each access or management protocol has its specific set of global options under `/software/components/dpmlfc/protocols` (e.g. `dpm`, `dpns`, `srmv22`, `dav`...).
Each of these options can be redefined in the node-specific options for the corresponding protocol. Node specific options are specified as a nlist attached to
the node name. This allows configuration options to be different for each host running an instance of the service but it is
generally not sensible to use a different value for each host.

See the schema, for the complete list of supported options for each protocols. Main options are described here.

#### WebDav options

All WebDav options are optional and thus have no default value. To see the value used when the
option is undefined, look at `/etc/httpd/conf.d/zlcgdm-dav.conf`

- DiskAnonUser : string (optional)

    User to use for anonymous access on file contents. Typically, must match NSAnonUser.

- DiskFlags : list of string (optional)

    Flags controlling access to file contents. Possible values are : Write, RemoteCopy, NoAuthn.

- NSAnonUser : string (optional)

    User to use for anonymous access to namespace. Typically, must match DiskAnonUser.

- NSFlags : list of string (optional)

    Flags controlling namespace access. Possible values are : Write, RemoteCopy, NoAuthn.

- NSMaxReplicas : long (optional, LFC only)

    Maximum number of replica to return.

- NSRedirectPort : list of long (optional, 2 list elements required)

    Ports to use when redirecting to disk servers. First element is the port to use for http access,
    second element is the port for https access.

- NSSecureRedirect : string (optional)

    Enable/disable secure redirect (https) to disk servers. Value must be `on` or `off`.

- NSServer : list of string (optional, 2 list elements required)

    Name (first element) and port (second element) of the host serving the namespace, both specified as string. This is
    mainly useful to allow access to the namespace from localhost on any DPM nodes, if direct access to namespace has been
    configured on disk servers (via `TrustedDNs`).

- NSTrustedDNs : list of string (optional)

    DNs of DPM nodes allowed a direct access to the namespace.

- NSType : string (optional)

    Indicates whether the namespace is attached to DPM or LFC. Valid values are `DPM` and `LFC`.

- SSLCertFile : string

    Certificate (public key) file name to use for https.

- SSLCertKey : string (optional)

    Private key file name to use for https.

- SSLCACertPath : string (optional)

    Directory path containing the CA certificates

- SSLCARevocationPath : string (optional)

    Directory path containing the CA revocation lists.

- SSLCipherSuite : list of string (optional)

    List of enabled ciphers in SSL configuration.

- SSLHonorCipherOrder : string (optional)

    Order of ciphers.

- SSLOptions : list of string (optional)

    SSL options to use (namespace and file access).

- SSLProtocol : list of string (optional)

    List of enabled/disabled of SSL protocols.

- SSLSessionCache : string (optional)

    SSLSessionCache parameter (see Apache documentation)

- SSLSessionCacheTimeout : long (optional)

    SSLSessionCacheTiemout parameter (see Apache documentation)

- SSLVerifyClient : string (optional)

    Level of client certificate verifications (see Apache documentation). Valid values are `require`, `optional` and `none`.

- SSLVerifyDepth : long (optional)

    Verification depth of certificate chain (see Apache documentation).

#### xrootd options

xrootd options are ignored. Use ncm-xrootd instead.

#### Options for other (legacy) protocols

Legacy (non dmlite-based) protocols share several options. Some protocolas also have specific options:
in this case, the option description states it explicitly.

- allowCoreDump: boolean (optional)

    `allowCoreDump` allows to explicitly enable/disable creation of a core dump in the event of a daemon crash.

    Default: use daemon default (see documentation)

- logfile: string (optional)

    `logfile` option is the name of the logfile used by the daemon instance. Generally, each daemon has a dedicated directory under `/var/log`, where the actual log file is rotated. This option is accepted by every type of daemon.

    Default : use daemon default (see documentation).

- port: long (optional)

    `port` allows to specify a non standard port for the daemon.

    Default : default service port (see documentation or 'man service\_name').

- threads : long (optional)

    Number of threads to use.

    Default : default service port (see documentation or 'man service\_name').

- maxOpenFiles : long (optional)

    Maximum number of open files (used as input to ulimit).

    Default : default service port (see documentation or 'man service\_name').

- requestMaxAge: string (optional, `dpm` daemon only)

    `requestMaxAge` allows to configure automatic purging of DPM request database, based on request age. It defines
    the maximum lifetime allowed for a request before it is removed from the request database. This must be a number
    optionally followed by `y` (year), `m` (month), `d` (day), `h` (hour). If no unit is specified, the number is
    interpreted as seconds.

    Default: by default automatic purging is disabled

- fastThreads : long (optional, `dpm` daemon only)

    Number of threads to use for short operations

    Default : default service configuration (see documentation or 'man service\_name').

- slowThreads : long (optional, `dpm` daemon only)

    Number of threads to use for long operations

    Default : default service configuration (see documentation or 'man service\_name').

- useSyncGet : boolean (optional, `dpm` daemon only)

    Use synchronous get operation when querying the namespace.

    Default : default service configuration (see documentation or 'man service\_name').

- readonly : boolean (optional, dpns and lfc only)

    Configure a readonly DPNS

    Default : default service configuration (see documentation or 'man service\_name').

- portRange : string (optional, rfio or gsiftp)

    TCP port range to use for transfers.

    Default : default service configuration (see documentation or 'man service\_name').

- startupOptions : string (optional, rfio or gsiftp)

    Daemon options to use at startup.

    Default : default service configuration (see documentation or 'man service\_name').

- disableAutoVirtualIDs : boolean (optional, lfc only)

    Disable automatic creation of virtual IDs.

    Default : default service configuration (see documentation or 'man service\_name').

### VO OPTIONS (DPM and LFC) : `/software/components/dpmlfc/vos`

VO-related options described each VO that must be configured to get access to DPM or LFC namespace. This includes creating VO home directory and setting correct permissions.

VO-related options are stored under `/software/components/dpmlfc/vos`, which is a nlist with one entry per VO. nlist key is the VO name. Value is a nlist describing VO properties.

- `/software/components/dpmlfc/vos/VONAME/gid`

    This property specifies virtual GID to associate with the VO. Default is normally appropriate

    Default : auto-generated virtual GID.

### POOL OPTIONS (DPM)

- `/software/components/dpmlfc/pool`

    Not implemented yet.

### DEPENDENCIES

None.

### BUGS

None known.

Michel Jouvin <>

Michel Jouvin <>

### SEE ALSO

ncm-ncd(1)
