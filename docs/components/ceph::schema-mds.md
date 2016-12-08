### Types

- `/software/ceph/ceph_mds_config`
    - decription:  configuration options for a ceph mds daemon 
    - `/software/ceph/ceph_mds_config/mds_cache_size`
        - optional
        - type: long
    - `/software/ceph/ceph_mds_config/mds_max_purge_files`
        - optional
        - type: long
    - `/software/ceph/ceph_mds_config/mds_max_purge_ops`
        - optional
        - type: long
    - `/software/ceph/ceph_mds_config/mds_max_purge_ops_per_pg`
        - optional
        - type: double
- `/software/ceph/ceph_mds`
    - decription:  ceph mds-specific type 
    - `/software/ceph/ceph_mds/fqdn`
        - required
        - type: type_fqdn
    - `/software/ceph/ceph_mds/config`
        - optional
        - type: ceph_mds_config

