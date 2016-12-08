### Types

- `/software/ceph/ceph_mon_config`
    - decription:  configuration options for a ceph monitor daemon 
- `/software/ceph/ceph_monitor`
    - decription:  ceph monitor-specific type 
    - `/software/ceph/ceph_monitor/fqdn`
        - required
        - type: type_fqdn
    - `/software/ceph/ceph_monitor/config`
        - optional
        - type: ceph_mon_config

