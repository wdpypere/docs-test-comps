### Types

- `/software/gmetad/structure_component_gmetad_data_source_host`
    - `/software/gmetad/structure_component_gmetad_data_source_host/address`
        - required
        - type: type_hostname

    - `/software/gmetad/structure_component_gmetad_data_source_host/port`
        - optional
        - type: type_port

- `/software/gmetad/structure_component_gmetad_data_source`
    - `/software/gmetad/structure_component_gmetad_data_source/name`
        - required
        - type: string

    - `/software/gmetad/structure_component_gmetad_data_source/polling_interval`
        - optional
        - type: long
        - range: 1..

    - `/software/gmetad/structure_component_gmetad_data_source/host`
        - optional
        - type: structure_component_gmetad_data_source_host

- `/software/gmetad/structure_component_gmetad`
    - `/software/gmetad/structure_component_gmetad/debug_level`
        - optional
        - type: long
        - range: 0..

    - `/software/gmetad/structure_component_gmetad/data_source`
        - required
        - type: structure_component_gmetad_data_source

    - `/software/gmetad/structure_component_gmetad/scalability`
        - optional
        - type: string

    - `/software/gmetad/structure_component_gmetad/gridname`
        - optional
        - type: string

    - `/software/gmetad/structure_component_gmetad/authorithy`
        - optional
        - type: type_absoluteURI

    - `/software/gmetad/structure_component_gmetad/trusted_hosts`
        - optional
        - type: type_hostname

    - `/software/gmetad/structure_component_gmetad/all_trusted`
        - optional
        - type: string

    - `/software/gmetad/structure_component_gmetad/setuid`
        - optional
        - type: string

    - `/software/gmetad/structure_component_gmetad/setuid_username`
        - optional
        - type: string

    - `/software/gmetad/structure_component_gmetad/xml_port`
        - optional
        - type: type_port

    - `/software/gmetad/structure_component_gmetad/interactive_port`
        - optional
        - type: type_port

    - `/software/gmetad/structure_component_gmetad/server_threads`
        - optional
        - type: long
        - range: 1..

    - `/software/gmetad/structure_component_gmetad/rrd_rootdir`
        - optional
        - type: string

    - `/software/gmetad/structure_component_gmetad/file`
        - required
        - type: string
### Functions
