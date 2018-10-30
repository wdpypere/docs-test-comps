
Types
-----

 - `/software/openstack/openstack_nova_api_database`
    - Description: 
    The Nova configuration options in "api_database" Section.

    - `/software/openstack/openstack_nova_api_database/connection`
        - Description: The SQLAlchemy connection string to use to connect to the database.
    Example (mysql): mysql+pymysql://nova:<NOVA_DBPASS>@<nova_fqdn>/nova_api
    
        - Optional
        - Type: string
 - `/software/openstack/openstack_nova_vnc`
    - Description: 
    The Nova configuration options in the "vnc" Section.

    - `/software/openstack/openstack_nova_vnc/vncserver_listen`
        - Description: The IP address or hostname on which an instance should listen to for
    incoming VNC connection requests on this node
        - Optional
        - Type: type_ip
    - `/software/openstack/openstack_nova_vnc/vncserver_proxyclient_address`
        - Description: Private, internal IP address or hostname of VNC console proxy.
    The VNC proxy is an OpenStack component that enables compute service
    users to access their instances through VNC clients.
    This option sets the private address to which proxy clients, such as
    "nova-xvpvncproxy", should connect to.
        - Optional
        - Type: type_ip
    - `/software/openstack/openstack_nova_vnc/enabled`
        - Description: Enable VNC related features.
    Guests will get created with graphical devices to support this. Clients
    (for example Horizon) can then establish a VNC connection to the guest
        - Optional
        - Type: boolean
    - `/software/openstack/openstack_nova_vnc/novncproxy_base_url`
        - Description: Public address of noVNC VNC console proxy.
    The VNC proxy is an OpenStack component that enables compute service
    users to access their instances through VNC clients. noVNC provides
    VNC support through a websocket-based client.

    This option sets the public base URL to which client systems will
    connect. noVNC clients can use this address to connect to the noVNC
    instance and, by extension, the VNC sessions
        - Optional
        - Type: type_absoluteURI
 - `/software/openstack/openstack_nova_glance`
    - Description: 
    The Nova configuration options in the "glance" Section.

    - `/software/openstack/openstack_nova_glance/api_servers`
        - Description: List of glance api servers endpoints available to nova.
    https is used for ssl-based glance api servers.

    Possible values:
        * A list of any fully qualified url of the form
        "scheme://hostname:port[/path]"
        (i.e. "http://10.0.1.0:9292" or "https://my.glance.server/image")
        - Optional
        - Type: type_absoluteURI
 - `/software/openstack/openstack_nova_placement`
    - Description: 
    The Nova configuration options in "placement" Section.

    - `/software/openstack/openstack_nova_placement/os_region_name`
        - Description: Region name of this node. This is used when picking the URL in the service
    catalog
        - Optional
        - Type: string
 - `/software/openstack/openstack_nova_libvirt`
    - Description: 
    The Nova hypervisor configuration options in "libvirt" Section.

    - `/software/openstack/openstack_nova_libvirt/virt_type`
        - Description: Describes the virtualization type (or so called domain type) libvirt should
    use.

    The choice of this type must match the underlying virtualization strategy
    you have chosen for the host
        - Optional
        - Type: string
    - `/software/openstack/openstack_nova_libvirt/images_rbd_pool`
        - Description: The RADOS pool in which rbd volumes are stored
        - Optional
        - Type: string
    - `/software/openstack/openstack_nova_libvirt/images_type`
        - Description: VM Images format. If default is specified, then use_cow_images flag is used
    instead of this one. Related options: * virt.use_cow_images * images_volume_group
        - Optional
        - Type: string
    - `/software/openstack/openstack_nova_libvirt/rbd_secret_uuid`
        - Description: The libvirt UUID of the secret for the rbd_user volumes
        - Optional
        - Type: type_uuid
    - `/software/openstack/openstack_nova_libvirt/rbd_user`
        - Description: The RADOS client name for accessing rbd(RADOS Block Devices) volumes.
    Libvirt will refer to this user when connecting and authenticating with the Ceph RBD server
        - Optional
        - Type: string
 - `/software/openstack/openstack_nova_neutron`
    - Description: 
    The Nova hypervisor configuration options in "neutron" Section.

    - `/software/openstack/openstack_nova_neutron/url`
        - Description: Any valid URL that points to the Neutron API service is appropriate here.
    This typically matches the URL returned for the 'network' service type
    from the Keystone service catalog
        - Optional
        - Type: type_absoluteURI
    - `/software/openstack/openstack_nova_neutron/region_name`
        - Description: Region name for connecting to Neutron in admin context.
    This option is used in multi-region setups. If there are two Neutron
    servers running in two regions in two different machines, then two
    services need to be created in Keystone with two different regions and
    associate corresponding endpoints to those services. When requests are made
    to Keystone, the Keystone service uses the region_name to determine the
    region the request is coming from
        - Optional
        - Type: string
    - `/software/openstack/openstack_nova_neutron/metadata_proxy_shared_secret`
        - Description: This option holds the shared secret string used to validate proxy requests to
    Neutron metadata requests. In order to be used, the
    "X-Metadata-Provider-Signature" header must be supplied in the request
        - Optional
        - Type: string
    - `/software/openstack/openstack_nova_neutron/service_metadata_proxy`
        - Description: When set to True, this option indicates that Neutron will be used to proxy
    metadata requests and resolve instance ids. Otherwise, the instance ID must be
    passed to the metadata request in the 'X-Instance-ID' header
        - Optional
        - Type: boolean
 - `/software/openstack/openstack_nova_scheduler`
    - Description: 
    The Nova configuration options in the "scheduler" Section.

    - `/software/openstack/openstack_nova_scheduler/discover_hosts_in_cells_interval`
        - Description: This value controls how often (in seconds) the scheduler should attempt
    to discover new hosts that have been added to cells. If negative (the
    default), no automatic discovery will occur.
    Deployments where compute nodes come and go frequently may want this
    enabled, where others may prefer to manually discover hosts when one
    is added to avoid any overhead from constantly checking. If enabled,
    every time this runs, we will select any unmapped hosts out of each
    cell database on every run.
        - Optional
        - Type: long
        - Range: -1..
 - `/software/openstack/openstack_nova_common`
    - Description: 
    list of Nova common configuration sections

    - `/software/openstack/openstack_nova_common/DEFAULT`
        - Optional
        - Type: openstack_DEFAULTS
    - `/software/openstack/openstack_nova_common/keystone_authtoken`
        - Optional
        - Type: openstack_keystone_authtoken
    - `/software/openstack/openstack_nova_common/vnc`
        - Optional
        - Type: openstack_nova_vnc
    - `/software/openstack/openstack_nova_common/glance`
        - Optional
        - Type: openstack_nova_glance
    - `/software/openstack/openstack_nova_common/oslo_concurrency`
        - Optional
        - Type: openstack_oslo_concurrency
    - `/software/openstack/openstack_nova_common/placement`
        - Description: placement service is mandatory since Ocata release
        - Optional
        - Type: openstack_nova_placement
    - `/software/openstack/openstack_nova_common/neutron`
        - Optional
        - Type: openstack_nova_neutron
 - `/software/openstack/openstack_nova_config`
    - Description: 
    list of Nova configuration sections

    - `/software/openstack/openstack_nova_config/database`
        - Optional
        - Type: openstack_database
    - `/software/openstack/openstack_nova_config/api_database`
        - Optional
        - Type: openstack_nova_api_database
    - `/software/openstack/openstack_nova_config/libvirt`
        - Optional
        - Type: openstack_nova_libvirt
    - `/software/openstack/openstack_nova_config/scheduler`
        - Optional
        - Type: openstack_nova_scheduler
