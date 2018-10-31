########################
ceph :: v2 :: schema-rgw
########################

Types
-----

 - **/software/ceph/type_quoted_string**
 - **/software/ceph/ceph_rgw_config**
    - Description: configuration options for a ceph rados gateway instance
    - */software/ceph/ceph_rgw_config/host*
        - Optional
        - Type: string
    - */software/ceph/ceph_rgw_config/keyring*
        - Optional
        - Type: string
    - */software/ceph/ceph_rgw_config/rgw_socket_path*
        - Optional
        - Type: string
    - */software/ceph/ceph_rgw_config/log_file*
        - Optional
        - Type: absolute_file_path
        - Default value: /var/log/radosgw/client.radosgw.gateway.log
    - */software/ceph/ceph_rgw_config/rgw_frontends*
        - Optional
        - Type: type_quoted_string
        - Default value: "civetweb port=8000"
    - */software/ceph/ceph_rgw_config/rgw_print_continue*
        - Optional
        - Type: boolean
        - Default value: false
    - */software/ceph/ceph_rgw_config/rgw_dns_name*
        - Optional
        - Type: type_fqdn
    - */software/ceph/ceph_rgw_config/rgw_enable_ops_log*
        - Optional
        - Type: boolean
        - Default value: true
    - */software/ceph/ceph_rgw_config/rgw_enable_usage_log*
        - Optional
        - Type: boolean
        - Default value: true
    - */software/ceph/ceph_rgw_config/user*
        - Optional
        - Type: string
 - **/software/ceph/ceph_radosgw**
    - Description: ceph rados gateway typehttp://ceph.com/docs/master/radosgw/
    - */software/ceph/ceph_radosgw/config*
        - Optional
        - Type: ceph_rgw_config
