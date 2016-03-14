### NAME

NCM::afsclt - NCM AFS client configuration component

### SYNOPSIS

- Configure()

    Sets ThisCell and enables AFS authentication (via authconfig) and a
    few options in `/etc/sysconfig/afs.` Configures `/etc/sysconfig/iptables`
    for the AFS client callback port.

- Unconfigure()

    `/etc/sysconfig/afs`: reset to defaults
    iptables: remove the AFS ports
    authconfig: no action
    CellServDB: no action

### RESOURCES

- `/software/components/afsclt/active` : boolean

    activates/deactivates the component.

- `/software/components/afsclt/thiscell` : string

    local AFS cell for this machine

- `/software/components/afsclt/settime` : boolean

    make AFS client set the system time or not.

- `/software/components/afsclt/options` : nlist

    various command-line options for the afsd daemon

- `/software/components/afsclt/cachesize` : int

    desired AFS cache size on disk, in 1K blocks. The running AFS cache
    will get adjusted online, and $afs\_cacheinfo will be changed if
    required. Please note that an available (mounted) AFS cache partition
    has precedence over this value, i.e. you cannot force a lower usage of
    the cache partition. For Linux machines, a cache partition will use
    CACHESIZE=AUTOMATIC, for other OSes, a hardcoded fill rate of 85% is
    used.

- `/software/components/afsclt/cellservdb` : string

    A regularly-updated AFS CellServDB URL or filename (e.g. from AFS)
    that this component will copy to local disk. The local AFS client will
    get notified of any additions or changes within a cell.

### DEPENDENCIES

#### Components to be run before:

none.

#### Components to be run after:

none.

Jaroslaw Polok <>

### SEE ALSO

authconfig(1), `fs help`, iptables documentation

\-head1 BUGS

Previous versions insisted on configuring a PAM `account` entry, 
this didn't really work for local accounts such as _root_...
