############################################
NCM\::Component\::openstack\::share - manila
############################################

Types
-----

 - **/software/components/openstack/openstack_manila_share_driver**
 - **/software/components/openstack/openstack_manila_common**
    - Description: Common Manila storage backends options
    - */software/components/openstack/openstack_manila_common/share_backend_name*
        - Description: The backend name for a given driver implementation
        - Required
        - Type: string
    - */software/components/openstack/openstack_manila_common/share_driver*
        - Description: Driver to use for share creation
        - Required
        - Type: openstack_manila_share_driver
    - */software/components/openstack/openstack_manila_common/driver_handles_share_servers*
        - Description: There are two possible approaches for share drivers in Manila. First is when share driver is able to handle share-servers and second when not. Drivers can support either both or only one of these approaches. So, set this opt to True if share driver is able to handle share servers and it is desired mode else set False. It is set to None by default to make this choice intentional
        - Required
        - Type: boolean
        - Default value: false
 - **/software/components/openstack/openstack_manila_lvm**
    - Description: The Manila configuration options in the "lvm" Section.
    - */software/components/openstack/openstack_manila_lvm/lvm_share_volume_group*
        - Description: Name for the VG that will contain exported shares
        - Required
        - Type: string
        - Default value: manila-volumes
    - */software/components/openstack/openstack_manila_lvm/lvm_share_export_ip*
        - Description: List of IPs to export shares
        - Optional
        - Type: type_ip
 - **/software/components/openstack/openstack_manila_ceph**
    - Description: The Manila configuration options in the "ceph" Section.
    - */software/components/openstack/openstack_manila_ceph/cephfs_conf_path*
        - Description: Fully qualified path to the ceph.conf file
        - Required
        - Type: absolute_file_path
        - Default value: /etc/ceph/ceph.conf
    - */software/components/openstack/openstack_manila_ceph/cephfs_protocol_helper_type*
        - Description: The type of protocol helper to use. Default is CEPHFS
        - Required
        - Type: choice
        - Default value: CEPHFS
    - */software/components/openstack/openstack_manila_ceph/cephfs_auth_id*
        - Description: The name of the ceph auth identity to use
        - Required
        - Type: string
        - Default value: manila
    - */software/components/openstack/openstack_manila_ceph/cephfs_cluster_name*
        - Description: The name of the cluster in use, if it is not the default ('ceph')
        - Required
        - Type: string
        - Default value: ceph
    - */software/components/openstack/openstack_manila_ceph/cephfs_enable_snapshots*
        - Description: Whether to enable snapshots in this driver. Note that the snapshot support for the CephFS driver is experimental and is known to have several caveats for use. Only enable this and the equivalent manila.conf option if you understand these risks. See (http://docs.ceph.com/docs/master/cephfs/experimental-features/) for more details
        - Required
        - Type: boolean
        - Default value: false
    - */software/components/openstack/openstack_manila_ceph/cephfs_ganesha_server_is_remote*
        - Description: Whether the NFS-Ganesha server is remote to the driver
        - Optional
        - Type: boolean
        - Default value: false
    - */software/components/openstack/openstack_manila_ceph/cephfs_ganesha_server_ip*
        - Description: The IP address of the NFS-Ganesha server
        - Optional
        - Type: type_ip
    - */software/components/openstack/openstack_manila_ceph/cephfs_ganesha_server_username*
        - Description: sets the username (NFSGADMIN) that the File Share Service should use to manage the NFS-Ganesha service
        - Optional
        - Type: string
    - */software/components/openstack/openstack_manila_ceph/cephfs_ganesha_server_password*
        - Description: sets the corresponding password (NFSGPW) of the username defined in cephfs_ganesha_server_username
        - Optional
        - Type: string
    - */software/components/openstack/openstack_manila_ceph/cephfs_ganesha_path_to_private_key*
        - Description: sets the SSH private key path used by cephfs_ganesha_server_username to get access to the NFS-Ganesha service
        - Optional
        - Type: absolute_file_path
    - */software/components/openstack/openstack_manila_ceph/ganesha_rados_store_enable*
        - Description: Persist Ganesha exports and export counter in Ceph RADOS objects, highly available storage
        - Optional
        - Type: boolean
        - Default value: true
    - */software/components/openstack/openstack_manila_ceph/ganesha_rados_store_pool_name*
        - Description: Name of the Ceph RADOS pool to store Ganesha exports and export counter
        - Optional
        - Type: string
        - Default value: cephfs_data
 - **/software/components/openstack/openstack_manila_generic**
    - Description: The Manila configuration options in the "generic" Section.
    - */software/components/openstack/openstack_manila_generic/service_instance_flavor_id*
        - Description: ID of flavor, that will be used for service instance creation. Only used if driver_handles_share_servers=True
        - Required
        - Type: long
        - Range: 1..
        - Default value: 100
    - */software/components/openstack/openstack_manila_generic/service_image_name*
        - Description: Name of image in Glance, that will be used for service instance creation. Only used if driver_handles_share_servers=True
        - Required
        - Type: string
        - Default value: manila-service-image
    - */software/components/openstack/openstack_manila_generic/service_instance_user*
        - Description: User in service instance that will be used for authentication
        - Required
        - Type: string
        - Default value: manila
    - */software/components/openstack/openstack_manila_generic/service_instance_password*
        - Description: Password for service instance user
        - Required
        - Type: string
    - */software/components/openstack/openstack_manila_generic/interface_driver*
        - Description: Vif driver. Used only with Neutron and if driver_handles_share_servers=True
        - Required
        - Type: string
        - Default value: manila.network.linux.interface.BridgeInterfaceDriver
 - **/software/components/openstack/openstack_manila_neutron**
    - Description: The manila configuration options in the "neutron" section.
    - */software/components/openstack/openstack_manila_neutron/url*
        - Description: Any valid URL that points to the Neutron API service is appropriate here. This typically matches the URL returned for the 'network' service type from the Keystone service catalog
        - Required
        - Type: type_absoluteURI
 - **/software/components/openstack/openstack_quattor_manila**
 - **/software/components/openstack/openstack_manila_config**
    - Description: list of Manila configuration sections
    - */software/components/openstack/openstack_manila_config/DEFAULT*
        - Required
        - Type: openstack_DEFAULTS
    - */software/components/openstack/openstack_manila_config/database*
        - Required
        - Type: openstack_database
    - */software/components/openstack/openstack_manila_config/keystone_authtoken*
        - Required
        - Type: openstack_keystone_authtoken
    - */software/components/openstack/openstack_manila_config/oslo_concurrency*
        - Required
        - Type: openstack_oslo_concurrency
    - */software/components/openstack/openstack_manila_config/cephfsnative*
        - Optional
        - Type: openstack_manila_ceph
    - */software/components/openstack/openstack_manila_config/cephfsnfs*
        - Optional
        - Type: openstack_manila_ceph
    - */software/components/openstack/openstack_manila_config/lvm*
        - Optional
        - Type: openstack_manila_lvm
    - */software/components/openstack/openstack_manila_config/generic*
        - Optional
        - Type: openstack_manila_generic
    - */software/components/openstack/openstack_manila_config/neutron*
        - Optional
        - Type: openstack_manila_neutron
    - */software/components/openstack/openstack_manila_config/nova*
        - Optional
        - Type: openstack_keystone_authtoken
    - */software/components/openstack/openstack_manila_config/cinder*
        - Optional
        - Type: openstack_keystone_authtoken
    - */software/components/openstack/openstack_manila_config/quattor*
        - Required
        - Type: openstack_quattor_manila
