### Types

- `/software/gsissh/structure_gsissh_server`
    - `/software/gsissh/structure_gsissh_server/port`
        - required
        - type: type_port
    - `/software/gsissh/structure_gsissh_server/options`
        - optional
        - type: string
- `/software/gsissh/structure_gsissh_client`
    - `/software/gsissh/structure_gsissh_client/options`
        - optional
        - type: string
- `/software/gsissh/gsissh_component`
    - `/software/gsissh/gsissh_component/globus_location`
        - optional
        - type: string
    - `/software/gsissh/gsissh_component/gpt_location`
        - optional
        - type: string
    - `/software/gsissh/gsissh_component/server`
        - optional
        - type: structure_gsissh_server
    - `/software/gsissh/gsissh_component/client`
        - optional
        - type: structure_gsissh_client

