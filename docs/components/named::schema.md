### Types

- `/software/named/component_named`
    - `/software/named/component_named/serverConfig`
        - optional
        - type: string
    - `/software/named/component_named/configfile`
        - optional
        - type: string
    - `/software/named/component_named/use_localhost`
        - required
        - type: boolean
    - `/software/named/component_named/start`
        - optional
        - type: boolean
    - `/software/named/component_named/servers`
        - optional
        - type: type_ip
    - `/software/named/component_named/options`
        - optional
        - type: string
    - `/software/named/component_named/search`
        - optional
        - type: type_fqdn

### Functions

  - component_named_valid
