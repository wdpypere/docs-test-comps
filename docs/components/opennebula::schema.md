### Types

- `/software/opennebula/directory`
- `/software/opennebula/opennebula_mysql_db`
    - `/software/opennebula/opennebula_mysql_db/server`
        - optional
        - type: string
    - `/software/opennebula/opennebula_mysql_db/port`
        - optional
        - type: type_port
    - `/software/opennebula/opennebula_mysql_db/user`
        - optional
        - type: string
    - `/software/opennebula/opennebula_mysql_db/passwd`
        - optional
        - type: string
    - `/software/opennebula/opennebula_mysql_db/db_name`
        - optional
        - type: string
- `/software/opennebula/opennebula_db`
    - `/software/opennebula/opennebula_db/backend`
        - required
        - type: string
- `/software/opennebula/opennebula_log`
    - `/software/opennebula/opennebula_log/system`
        - required
        - type: string
    - `/software/opennebula/opennebula_log/debug_level`
        - required
        - type: long
        - range: 0..3
- `/software/opennebula/opennebula_federation`
    - `/software/opennebula/opennebula_federation/mode`
        - required
        - type: string
    - `/software/opennebula/opennebula_federation/zone_id`
        - required
        - type: long
    - `/software/opennebula/opennebula_federation/master_oned`
        - required
        - type: string
- `/software/opennebula/opennebula_im`
    - `/software/opennebula/opennebula_im/executable`
        - required
        - type: string
    - `/software/opennebula/opennebula_im/arguments`
        - required
        - type: string
    - `/software/opennebula/opennebula_im/sunstone_name`
        - optional
        - type: string
- `/software/opennebula/opennebula_im_mad_collectd`
- `/software/opennebula/opennebula_im_mad_kvm`
- `/software/opennebula/opennebula_im_mad_xen`
- `/software/opennebula/opennebula_im_mad`
    - `/software/opennebula/opennebula_im_mad/collectd`
        - required
        - type: opennebula_im_mad_collectd
    - `/software/opennebula/opennebula_im_mad/kvm`
        - required
        - type: opennebula_im_mad_kvm
    - `/software/opennebula/opennebula_im_mad/xen`
        - optional
        - type: opennebula_im_mad_xen
- `/software/opennebula/opennebula_vm`
    - `/software/opennebula/opennebula_vm/executable`
        - required
        - type: string
    - `/software/opennebula/opennebula_vm/arguments`
        - required
        - type: string
    - `/software/opennebula/opennebula_vm/default`
        - required
        - type: string
    - `/software/opennebula/opennebula_vm/sunstone_name`
        - required
        - type: string
    - `/software/opennebula/opennebula_vm/imported_vms_actions`
        - required
        - type: string
    - `/software/opennebula/opennebula_vm/keep_snapshots`
        - required
        - type: boolean
- `/software/opennebula/opennebula_vm_mad_kvm`
- `/software/opennebula/opennebula_vm_mad_xen`
- `/software/opennebula/opennebula_vm_mad`
    - `/software/opennebula/opennebula_vm_mad/kvm`
        - required
        - type: opennebula_vm_mad_kvm
    - `/software/opennebula/opennebula_vm_mad/xen`
        - optional
        - type: opennebula_vm_mad_xen
- `/software/opennebula/opennebula_tm_mad`
    - `/software/opennebula/opennebula_tm_mad/executable`
        - required
        - type: string
    - `/software/opennebula/opennebula_tm_mad/arguments`
        - required
        - type: string
- `/software/opennebula/opennebula_datastore_mad`
    - `/software/opennebula/opennebula_datastore_mad/executable`
        - required
        - type: string
    - `/software/opennebula/opennebula_datastore_mad/arguments`
        - required
        - type: string
- `/software/opennebula/opennebula_hm_mad`
    - `/software/opennebula/opennebula_hm_mad/executable`
        - required
        - type: string
- `/software/opennebula/opennebula_auth_mad`
    - `/software/opennebula/opennebula_auth_mad/executable`
        - required
        - type: string
    - `/software/opennebula/opennebula_auth_mad/authn`
        - required
        - type: string
- `/software/opennebula/opennebula_tm_mad_conf`
    - `/software/opennebula/opennebula_tm_mad_conf/name`
        - required
        - type: string
    - `/software/opennebula/opennebula_tm_mad_conf/ln_target`
        - required
        - type: string
    - `/software/opennebula/opennebula_tm_mad_conf/clone_target`
        - required
        - type: string
    - `/software/opennebula/opennebula_tm_mad_conf/shared`
        - required
        - type: boolean
    - `/software/opennebula/opennebula_tm_mad_conf/ds_migrate`
        - optional
        - type: boolean
- `/software/opennebula/opennebula_ds_mad_conf`
    - decription: 
The  configuration for each driver is defined in DS_MAD_CONF.
These values are used when creating a new datastore and should not be modified
since they defined the datastore behavior.

    - `/software/opennebula/opennebula_ds_mad_conf/name`
        - description: name of the transfer driver, listed in the -d option of the DS_MAD section
        - required
        - type: string
    - `/software/opennebula/opennebula_ds_mad_conf/required_attrs`
        - description: comma separated list of required attributes in the DS template
        - required
        - type: string
    - `/software/opennebula/opennebula_ds_mad_conf/persistent_only`
        - description: specifies whether the datastore can only manage persistent images
        - required
        - type: boolean
    - `/software/opennebula/opennebula_ds_mad_conf/marketplace_actions`
        - optional
        - type: string
- `/software/opennebula/opennebula_market_mad_conf`
    - decription: 
The  configuration for each driver is defined in MARKET_MAD_CONF.
These values are used when creating a new marketplace and should not be modified
since they define the marketplace behavior.
A public marketplace can be removed even if it has registered apps.

    - `/software/opennebula/opennebula_market_mad_conf/name`
        - description: name of the market driver
        - required
        - type: string
    - `/software/opennebula/opennebula_market_mad_conf/required_attrs`
        - description: comma separated list of required attributes in the Market template
        - required
        - type: string
    - `/software/opennebula/opennebula_market_mad_conf/app_actions`
        - description: list of actions allowed for a MarketPlaceApp.
        monitor: the apps of the marketplace will be monitored.
        create: the app in the marketplace.
        delete: the app from the marketplace.
    
        - required
        - type: string
    - `/software/opennebula/opennebula_market_mad_conf/public`
        - description: set to TRUE for external marketplaces
        - optional
        - type: boolean
- `/software/opennebula/opennebula_default_cost`
    - decription:  
The following attributes define the default cost for Virtual Machines that don't have 
a CPU, MEMORY or DISK cost.
This is used by the oneshowback calculate method.

    - `/software/opennebula/opennebula_default_cost/cpu_cost`
        - required
        - type: long
    - `/software/opennebula/opennebula_default_cost/memory_cost`
        - required
        - type: long
    - `/software/opennebula/opennebula_default_cost/disk_cost`
        - required
        - type: long
- `/software/opennebula/opennebula_vnc_ports`
    - decription: 
VNC_BASE_PORT is deprecated since OpenNebula 5.0
OpenNebula will automatically assign start + vmid,
allowing to generate different ports for VMs so they do not collide.

    - `/software/opennebula/opennebula_vnc_ports/start`
        - description: VNC port pool for automatic VNC port assignment,
    if possible the port will be set to START + VMID
        - required
        - type: long
        - range: 5900..65535
    - `/software/opennebula/opennebula_vnc_ports/reserved`
        - optional
        - type: long
- `/software/opennebula/opennebula_vlan_ids`
    - decription: 
LAN ID pool for the automatic VLAN_ID assignment.
This pool is for 802.1Q networks (Open vSwitch and 802.1Q drivers).
The driver will try first to allocate VLAN_IDS[START] + VNET_ID

    - `/software/opennebula/opennebula_vlan_ids/start`
        - description: first VLAN_ID to use
        - required
        - type: long
    - `/software/opennebula/opennebula_vlan_ids/reserved`
        - optional
        - type: long
- `/software/opennebula/opennebula_vxlan_ids`
    - decription: 
Automatic VXLAN Network ID (VNI) assignment. 
This is used or vxlan networks.
NOTE: reserved is not supported by this pool

    - `/software/opennebula/opennebula_vxlan_ids/start`
        - description: first VNI (Virtual Network ID) to use
        - required
        - type: long
- `/software/opennebula/opennebula_market_mad`
    - decription: 
Drivers to manage different marketplaces, specialized for the storage backend.

    - `/software/opennebula/opennebula_market_mad/executable`
        - description: path of the transfer driver executable, can be an absolute path or
    relative to $ONE_LOCATION/lib/mads (or `/usr/lib/one/mads`/ if OpenNebula was 
    installed in /)
    
        - required
        - type: string
    - `/software/opennebula/opennebula_market_mad/arguments`
        - description: arguments for the driver executable:
        -t number of threads, i.e. number of repo operations at the same time
        -m marketplace mads separated by commas
    
        - required
        - type: string
- `/software/opennebula/opennebula_ceph_datastore`
    - decription:  
type for ceph datastore specific attributes. 
ceph_host, ceph_secret, ceph_user, ceph_user_key and pool_name are mandatory

    - `/software/opennebula/opennebula_ceph_datastore/ceph_host`
        - optional
        - type: string
    - `/software/opennebula/opennebula_ceph_datastore/ceph_secret`
        - optional
        - type: type_uuid
    - `/software/opennebula/opennebula_ceph_datastore/ceph_user`
        - optional
        - type: string
    - `/software/opennebula/opennebula_ceph_datastore/ceph_user_key`
        - optional
        - type: string
    - `/software/opennebula/opennebula_ceph_datastore/pool_name`
        - optional
        - type: string
    - `/software/opennebula/opennebula_ceph_datastore/rbd_format`
        - optional
        - type: long
        - range: 1..2
- `/software/opennebula/opennebula_ar`
    - decription:  
type for vnet ars specific attributes. 
type and size are mandatory 

    - `/software/opennebula/opennebula_ar/type`
        - required
        - type: string
    - `/software/opennebula/opennebula_ar/ip`
        - optional
        - type: type_ipv4
    - `/software/opennebula/opennebula_ar/size`
        - required
        - type: long
        - range: 1..
    - `/software/opennebula/opennebula_ar/mac`
        - optional
        - type: type_hwaddr
    - `/software/opennebula/opennebula_ar/global_prefix`
        - optional
        - type: string
    - `/software/opennebula/opennebula_ar/ula_prefix`
        - optional
        - type: string
- `/software/opennebula/opennebula_datastore`
    - decription:  
type for an opennebula datastore. Defaults to a ceph datastore (ds_mad is ceph).
shared DS is also supported

    - `/software/opennebula/opennebula_datastore/bridge_list`
        - optional
        - type: string
    - `/software/opennebula/opennebula_datastore/datastore_capacity_check`
        - required
        - type: boolean
    - `/software/opennebula/opennebula_datastore/disk_type`
        - required
        - type: string
    - `/software/opennebula/opennebula_datastore/ds_mad`
        - required
        - type: string
    - `/software/opennebula/opennebula_datastore/tm_mad`
        - required
        - type: string
    - `/software/opennebula/opennebula_datastore/type`
        - required
        - type: string
    - `/software/opennebula/opennebula_datastore/labels`
        - description: datastore labels is a list of strings to group the datastores under a given name and filter them 
    in the admin and cloud views. It is also possible to include in the list 
    sub-labels using a common slash: list("Name", "Name/SubName")
        - optional
        - type: string
- `/software/opennebula/opennebula_vnet`
    - `/software/opennebula/opennebula_vnet/bridge`
        - required
        - type: string
    - `/software/opennebula/opennebula_vnet/vn_mad`
        - required
        - type: string
    - `/software/opennebula/opennebula_vnet/gateway`
        - optional
        - type: type_ipv4
    - `/software/opennebula/opennebula_vnet/gateway6`
        - optional
        - type: type_network_name
    - `/software/opennebula/opennebula_vnet/dns`
        - optional
        - type: type_ipv4
    - `/software/opennebula/opennebula_vnet/network_mask`
        - optional
        - type: type_ipv4
    - `/software/opennebula/opennebula_vnet/network_address`
        - optional
        - type: type_ipv4
    - `/software/opennebula/opennebula_vnet/guest_mtu`
        - optional
        - type: long
    - `/software/opennebula/opennebula_vnet/context_force_ipv4`
        - optional
        - type: boolean
    - `/software/opennebula/opennebula_vnet/search_domain`
        - optional
        - type: string
    - `/software/opennebula/opennebula_vnet/bridge_ovs`
        - optional
        - type: string
    - `/software/opennebula/opennebula_vnet/vlan`
        - optional
        - type: boolean
    - `/software/opennebula/opennebula_vnet/vlan_id`
        - optional
        - type: long
        - range: 0..4095
    - `/software/opennebula/opennebula_vnet/ar`
        - optional
        - type: opennebula_ar
    - `/software/opennebula/opennebula_vnet/labels`
        - description: vnet labels is a list of strings to group the vnets under a given name and filter them 
    in the admin and cloud views. It is also possible to include in the list 
    sub-labels using a common slash: list("Name", "Name/SubName")
        - optional
        - type: string
- `/software/opennebula/opennebula_user`
    - decription: 
Set OpenNebula regular users and their primary groups.
By default new users are assigned to the users group.

    - `/software/opennebula/opennebula_user/ssh_public_key`
        - optional
        - type: string
    - `/software/opennebula/opennebula_user/password`
        - optional
        - type: string
    - `/software/opennebula/opennebula_user/group`
        - optional
        - type: string
    - `/software/opennebula/opennebula_user/labels`
        - description: user labels is a list of strings to group the users under a given name and filter them 
    in the admin and cloud views. It is also possible to include in the list 
    sub-labels using a common slash: list("Name", "Name/SubName")
        - optional
        - type: string
- `/software/opennebula/opennebula_group`
    - decription: 
Set a group name and an optional decription

    - `/software/opennebula/opennebula_group/description`
        - optional
        - type: string
    - `/software/opennebula/opennebula_group/labels`
        - optional
        - type: string
- `/software/opennebula/opennebula_remoteconf_ceph`
    - `/software/opennebula/opennebula_remoteconf_ceph/pool_name`
        - required
        - type: string
    - `/software/opennebula/opennebula_remoteconf_ceph/host`
        - required
        - type: string
    - `/software/opennebula/opennebula_remoteconf_ceph/ceph_user`
        - optional
        - type: string
    - `/software/opennebula/opennebula_remoteconf_ceph/staging_dir`
        - optional
        - type: directory
    - `/software/opennebula/opennebula_remoteconf_ceph/rbd_format`
        - optional
        - type: long
        - range: 1..2
    - `/software/opennebula/opennebula_remoteconf_ceph/qemu_img_convert_args`
        - optional
        - type: string
- `/software/opennebula/opennebula_oned`
    - decription: 
Type that sets the OpenNebula
oned.conf file

    - `/software/opennebula/opennebula_oned/db`
        - required
        - type: opennebula_db
    - `/software/opennebula/opennebula_oned/default_device_prefix`
        - optional
        - type: string
    - `/software/opennebula/opennebula_oned/onegate_endpoint`
        - optional
        - type: string
    - `/software/opennebula/opennebula_oned/manager_timer`
        - optional
        - type: long
    - `/software/opennebula/opennebula_oned/monitoring_interval`
        - required
        - type: long
    - `/software/opennebula/opennebula_oned/monitoring_threads`
        - required
        - type: long
    - `/software/opennebula/opennebula_oned/host_per_interval`
        - optional
        - type: long
    - `/software/opennebula/opennebula_oned/host_monitoring_expiration_time`
        - optional
        - type: long
    - `/software/opennebula/opennebula_oned/vm_individual_monitoring`
        - optional
        - type: boolean
    - `/software/opennebula/opennebula_oned/vm_per_interval`
        - optional
        - type: long
    - `/software/opennebula/opennebula_oned/vm_monitoring_expiration_time`
        - optional
        - type: long
    - `/software/opennebula/opennebula_oned/vm_submit_on_hold`
        - optional
        - type: boolean
    - `/software/opennebula/opennebula_oned/max_conn`
        - optional
        - type: long
    - `/software/opennebula/opennebula_oned/max_conn_backlog`
        - optional
        - type: long
    - `/software/opennebula/opennebula_oned/keepalive_timeout`
        - optional
        - type: long
    - `/software/opennebula/opennebula_oned/keepalive_max_conn`
        - optional
        - type: long
    - `/software/opennebula/opennebula_oned/timeout`
        - optional
        - type: long
    - `/software/opennebula/opennebula_oned/rpc_log`
        - optional
        - type: boolean
    - `/software/opennebula/opennebula_oned/message_size`
        - optional
        - type: long
    - `/software/opennebula/opennebula_oned/log_call_format`
        - optional
        - type: string
    - `/software/opennebula/opennebula_oned/scripts_remote_dir`
        - required
        - type: directory
    - `/software/opennebula/opennebula_oned/log`
        - required
        - type: opennebula_log
    - `/software/opennebula/opennebula_oned/federation`
        - required
        - type: opennebula_federation
    - `/software/opennebula/opennebula_oned/port`
        - required
        - type: type_port
    - `/software/opennebula/opennebula_oned/vnc_base_port`
        - required
        - type: long
    - `/software/opennebula/opennebula_oned/network_size`
        - required
        - type: long
    - `/software/opennebula/opennebula_oned/mac_prefix`
        - required
        - type: string
    - `/software/opennebula/opennebula_oned/datastore_location`
        - optional
        - type: directory
    - `/software/opennebula/opennebula_oned/datastore_base_path`
        - optional
        - type: directory
    - `/software/opennebula/opennebula_oned/datastore_capacity_check`
        - required
        - type: boolean
    - `/software/opennebula/opennebula_oned/default_image_type`
        - required
        - type: string
    - `/software/opennebula/opennebula_oned/default_cdrom_device_prefix`
        - required
        - type: string
    - `/software/opennebula/opennebula_oned/session_expiration_time`
        - required
        - type: long
    - `/software/opennebula/opennebula_oned/default_umask`
        - required
        - type: long
    - `/software/opennebula/opennebula_oned/im_mad`
        - required
        - type: opennebula_im_mad
    - `/software/opennebula/opennebula_oned/vm_mad`
        - required
        - type: opennebula_vm_mad
    - `/software/opennebula/opennebula_oned/tm_mad`
        - required
        - type: opennebula_tm_mad
    - `/software/opennebula/opennebula_oned/datastore_mad`
        - required
        - type: opennebula_datastore_mad
    - `/software/opennebula/opennebula_oned/hm_mad`
        - required
        - type: opennebula_hm_mad
    - `/software/opennebula/opennebula_oned/auth_mad`
        - required
        - type: opennebula_auth_mad
    - `/software/opennebula/opennebula_oned/market_mad`
        - required
        - type: opennebula_market_mad
    - `/software/opennebula/opennebula_oned/default_cost`
        - required
        - type: opennebula_default_cost
    - `/software/opennebula/opennebula_oned/listen_address`
        - required
        - type: type_ipv4
    - `/software/opennebula/opennebula_oned/vnc_ports`
        - required
        - type: opennebula_vnc_ports
    - `/software/opennebula/opennebula_oned/vlan_ids`
        - required
        - type: opennebula_vlan_ids
    - `/software/opennebula/opennebula_oned/vxlan_ids`
        - required
        - type: opennebula_vxlan_ids
    - `/software/opennebula/opennebula_oned/tm_mad_conf`
        - required
        - type: opennebula_tm_mad_conf
    - `/software/opennebula/opennebula_oned/ds_mad_conf`
        - required
        - type: opennebula_ds_mad_conf
    - `/software/opennebula/opennebula_oned/market_mad_conf`
        - required
        - type: opennebula_market_mad_conf
    - `/software/opennebula/opennebula_oned/vm_restricted_attr`
        - required
        - type: string
    - `/software/opennebula/opennebula_oned/image_restricted_attr`
        - required
        - type: string
    - `/software/opennebula/opennebula_oned/vnet_restricted_attr`
        - required
        - type: string
    - `/software/opennebula/opennebula_oned/inherit_datastore_attr`
        - required
        - type: string
    - `/software/opennebula/opennebula_oned/inherit_image_attr`
        - required
        - type: string
    - `/software/opennebula/opennebula_oned/inherit_vnet_attr`
        - required
        - type: string
- `/software/opennebula/opennebula_instance_types`
    - `/software/opennebula/opennebula_instance_types/name`
        - required
        - type: string
    - `/software/opennebula/opennebula_instance_types/cpu`
        - required
        - type: long
        - range: 1..
    - `/software/opennebula/opennebula_instance_types/vcpu`
        - required
        - type: long
        - range: 1..
    - `/software/opennebula/opennebula_instance_types/memory`
        - required
        - type: long
    - `/software/opennebula/opennebula_instance_types/description`
        - optional
        - type: string
- `/software/opennebula/opennebula_rpc_service`
    - decription:  
type for opennebula service common RPC attributes. 

    - `/software/opennebula/opennebula_rpc_service/one_xmlrpc`
        - description: OpenNebula daemon RPC contact information
        - required
        - type: type_absoluteURI
    - `/software/opennebula/opennebula_rpc_service/core_auth`
        - description: authentication driver to communicate with OpenNebula core
        - required
        - type: string
- `/software/opennebula/opennebula_sunstone`
    - decription: 
Type that sets the OpenNebula
sunstone_server.conf file

    - `/software/opennebula/opennebula_sunstone/env`
        - required
        - type: string
    - `/software/opennebula/opennebula_sunstone/tmpdir`
        - required
        - type: directory
    - `/software/opennebula/opennebula_sunstone/host`
        - required
        - type: type_ipv4
    - `/software/opennebula/opennebula_sunstone/port`
        - required
        - type: type_port
    - `/software/opennebula/opennebula_sunstone/sessions`
        - required
        - type: string
    - `/software/opennebula/opennebula_sunstone/memcache_host`
        - required
        - type: string
    - `/software/opennebula/opennebula_sunstone/memcache_port`
        - required
        - type: type_port
    - `/software/opennebula/opennebula_sunstone/memcache_namespace`
        - required
        - type: string
    - `/software/opennebula/opennebula_sunstone/debug_level`
        - required
        - type: long
        - range: 0..3
    - `/software/opennebula/opennebula_sunstone/auth`
        - required
        - type: string
    - `/software/opennebula/opennebula_sunstone/encode_user_password`
        - optional
        - type: boolean
    - `/software/opennebula/opennebula_sunstone/vnc_proxy_port`
        - required
        - type: type_port
    - `/software/opennebula/opennebula_sunstone/vnc_proxy_support_wss`
        - required
        - type: string
    - `/software/opennebula/opennebula_sunstone/vnc_proxy_cert`
        - required
        - type: string
    - `/software/opennebula/opennebula_sunstone/vnc_proxy_key`
        - required
        - type: string
    - `/software/opennebula/opennebula_sunstone/vnc_proxy_ipv6`
        - required
        - type: boolean
    - `/software/opennebula/opennebula_sunstone/lang`
        - required
        - type: string
    - `/software/opennebula/opennebula_sunstone/table_order`
        - required
        - type: string
    - `/software/opennebula/opennebula_sunstone/marketplace_username`
        - optional
        - type: string
    - `/software/opennebula/opennebula_sunstone/marketplace_password`
        - optional
        - type: string
    - `/software/opennebula/opennebula_sunstone/marketplace_url`
        - required
        - type: type_absoluteURI
    - `/software/opennebula/opennebula_sunstone/oneflow_server`
        - required
        - type: type_absoluteURI
    - `/software/opennebula/opennebula_sunstone/instance_types`
        - required
        - type: opennebula_instance_types
    - `/software/opennebula/opennebula_sunstone/routes`
        - required
        - type: string
- `/software/opennebula/opennebula_oneflow`
    - decription: 
Type that sets the OpenNebula
oneflow-server.conf file

    - `/software/opennebula/opennebula_oneflow/host`
        - description: host where OneFlow server will run
        - required
        - type: type_ipv4
    - `/software/opennebula/opennebula_oneflow/port`
        - description: port where OneFlow server will run
        - required
        - type: type_port
    - `/software/opennebula/opennebula_oneflow/lcm_interval`
        - description: time in seconds between Life Cycle Manager steps
        - required
        - type: long
    - `/software/opennebula/opennebula_oneflow/default_cooldown`
        - description: default cooldown period after a scale operation, in seconds
        - required
        - type: long
    - `/software/opennebula/opennebula_oneflow/shutdown_action`
        - description: default shutdown action
    terminate : OpenNebula >= 5.0.0
    shutdown  : OpenNebula < 5.0.0
    
        - required
        - type: string
    - `/software/opennebula/opennebula_oneflow/action_number`
        - description: default numner of virtual machines that will receive the given call in each interval
    defined by action_period, when an action is performed on a role
        - required
        - type: long
        - range: 1..
    - `/software/opennebula/opennebula_oneflow/action_period`
        - required
        - type: long
        - range: 1..
    - `/software/opennebula/opennebula_oneflow/vm_name_template`
        - description: default name for the Virtual Machines created by OneFlow.
    You can use any of the following placeholders:
        $SERVICE_ID
        $SERVICE_NAME
        $ROLE_NAME
        $VM_NUMBER
    
        - required
        - type: string
    - `/software/opennebula/opennebula_oneflow/debug_level`
        - description: log debug level
        0 = ERROR
        1 = WARNING
        2 = INFO 
        3 = DEBUG
    
        - required
        - type: long
        - range: 0..3
- `/software/opennebula/opennebula_kvmrc`
    - decription: 
Type that sets the OpenNebula
VMM kvmrc conf files

    - `/software/opennebula/opennebula_kvmrc/lang`
        - required
        - type: string
    - `/software/opennebula/opennebula_kvmrc/libvirt_uri`
        - required
        - type: string
    - `/software/opennebula/opennebula_kvmrc/qemu_protocol`
        - required
        - type: string
    - `/software/opennebula/opennebula_kvmrc/libvirt_keytab`
        - optional
        - type: string
    - `/software/opennebula/opennebula_kvmrc/shutdown_timeout`
        - required
        - type: long
    - `/software/opennebula/opennebula_kvmrc/force_destroy`
        - optional
        - type: boolean
    - `/software/opennebula/opennebula_kvmrc/cancel_no_acpi`
        - optional
        - type: boolean
    - `/software/opennebula/opennebula_kvmrc/default_attach_cache`
        - optional
        - type: string
    - `/software/opennebula/opennebula_kvmrc/migrate_options`
        - optional
        - type: string
    - `/software/opennebula/opennebula_kvmrc/default_attach_discard`
        - optional
        - type: string
- `/software/opennebula/opennebula_rpc`
    - decription:  
Type that sets the OpenNebula conf
to contact to ONE RPC server

    - `/software/opennebula/opennebula_rpc/port`
        - required
        - type: type_port
    - `/software/opennebula/opennebula_rpc/host`
        - required
        - type: string
    - `/software/opennebula/opennebula_rpc/user`
        - required
        - type: string
    - `/software/opennebula/opennebula_rpc/password`
        - required
        - type: string
- `/software/opennebula/opennebula_untouchables`
    - decription: 
Type that sets the OpenNebula
untouchable resources

    - `/software/opennebula/opennebula_untouchables/datastores`
        - optional
        - type: string
    - `/software/opennebula/opennebula_untouchables/vnets`
        - optional
        - type: string
    - `/software/opennebula/opennebula_untouchables/users`
        - optional
        - type: string
    - `/software/opennebula/opennebula_untouchables/groups`
        - optional
        - type: string
    - `/software/opennebula/opennebula_untouchables/hosts`
        - optional
        - type: string
- `/software/opennebula/component_opennebula`
    - decription: 
Type to define ONE basic resources
datastores, vnets, hosts names, etc

    - `/software/opennebula/component_opennebula/datastores`
        - optional
        - type: opennebula_datastore
    - `/software/opennebula/component_opennebula/groups`
        - optional
        - type: opennebula_group
    - `/software/opennebula/component_opennebula/users`
        - optional
        - type: opennebula_user
    - `/software/opennebula/component_opennebula/vnets`
        - optional
        - type: opennebula_vnet
    - `/software/opennebula/component_opennebula/hosts`
        - optional
        - type: string
    - `/software/opennebula/component_opennebula/rpc`
        - optional
        - type: opennebula_rpc
    - `/software/opennebula/component_opennebula/untouchables`
        - optional
        - type: opennebula_untouchables
    - `/software/opennebula/component_opennebula/oned`
        - optional
        - type: opennebula_oned
    - `/software/opennebula/component_opennebula/sunstone`
        - optional
        - type: opennebula_sunstone
    - `/software/opennebula/component_opennebula/oneflow`
        - optional
        - type: opennebula_oneflow
    - `/software/opennebula/component_opennebula/kvmrc`
        - optional
        - type: opennebula_kvmrc
    - `/software/opennebula/component_opennebula/ssh_multiplex`
        - required
        - type: boolean
    - `/software/opennebula/component_opennebula/cfg_group`
        - optional
        - type: string
    - `/software/opennebula/component_opennebula/host_ovs`
        - optional
        - type: boolean
    - `/software/opennebula/component_opennebula/host_hyp`
        - required
        - type: string
    - `/software/opennebula/component_opennebula/tm_system_ds`
        - optional
        - type: string

### Functions

- is_consistent_database
    - description:  
check if a specific type of database has the right attributes
 
- is_consistent_datastore
    - description:  
check if a specific type of datastore has the right attributes
 