########################
ceph :: v2 :: schema-mds
########################

Types
-----

 - **/software/ceph/ceph_mds_config**
    - Description: configuration options for a ceph mds daemon
    - */software/ceph/ceph_mds_config/mds_cache_size*
        - Optional
        - Type: long
        - Default value: 100000
    - */software/ceph/ceph_mds_config/mds_cache_memory_limit*
        - Optional
        - Type: long
    - */software/ceph/ceph_mds_config/mds_max_purge_files*
        - Optional
        - Type: long
        - Default value: 64
    - */software/ceph/ceph_mds_config/mds_max_purge_ops*
        - Optional
        - Type: long
        - Default value: 8192
    - */software/ceph/ceph_mds_config/mds_max_purge_ops_per_pg*
        - Optional
        - Type: double
        - Default value: 0.5
    - */software/ceph/ceph_mds_config/mds_log_max_expiring*
        - Optional
        - Type: long
        - Default value: 20
    - */software/ceph/ceph_mds_config/mds_log_max_segments*
        - Optional
        - Type: long
        - Default value: 30
 - **/software/ceph/ceph_mds**
    - Description: ceph mds-specific type
    - */software/ceph/ceph_mds/fqdn*
        - Optional
        - Type: type_fqdn
