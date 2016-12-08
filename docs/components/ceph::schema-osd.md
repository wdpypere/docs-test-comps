### Types

- `/software/ceph/ceph_osd_config`
    - decription:  configuration options for a ceph osd daemon 
    - `/software/ceph/ceph_osd_config/osd_deep_scrub_interval`
        - optional
        - type: double
    - `/software/ceph/ceph_osd_config/osd_journal_size`
        - optional
        - type: long
        - range: 0..
    - `/software/ceph/ceph_osd_config/osd_max_scrubs`
        - optional
        - type: long
        - range: 0..
    - `/software/ceph/ceph_osd_config/osd_objectstore`
        - optional
        - type: string
    - `/software/ceph/ceph_osd_config/osd_op_threads`
        - optional
        - type: long
        - range: 0..
    - `/software/ceph/ceph_osd_config/osd_scrub_begin_hour`
        - optional
        - type: long
        - range: 0..24
    - `/software/ceph/ceph_osd_config/osd_scrub_end_hour`
        - optional
        - type: long
        - range: 0..24
    - `/software/ceph/ceph_osd_config/osd_scrub_load_threshold`
        - optional
        - type: double
    - `/software/ceph/ceph_osd_config/osd_scrub_min_interval`
        - optional
        - type: double
    - `/software/ceph/ceph_osd_config/osd_scrub_max_interval`
        - optional
        - type: double
- `/software/ceph/ceph_osd`
    - decription:  
ceph osd-specific type 
The key of the ceph_osd should be the path to the mounted disk. 
This can be an absolute path or a relative one to `/var/lib/ceph/osd`/
journal_path should be the path to a journal file
This can be an absolute path or a relative one to `/var/lib/ceph/log`/
With labels osds can be grouped. This should also be defined in root. 

    - `/software/ceph/ceph_osd/config`
        - optional
        - type: ceph_osd_config
    - `/software/ceph/ceph_osd/in`
        - optional
        - type: boolean
    - `/software/ceph/ceph_osd/journal_path`
        - optional
        - type: string
    - `/software/ceph/ceph_osd/crush_weight`
        - required
        - type: double
    - `/software/ceph/ceph_osd/labels`
        - optional
        - type: string
- `/software/ceph/ceph_osd_host`
    - decription:  ceph osdhost-specific type, defining all osds on a host 
    - `/software/ceph/ceph_osd_host/fqdn`
        - required
        - type: type_fqdn
    - `/software/ceph/ceph_osd_host/osds`
        - required
        - type: ceph_osd

