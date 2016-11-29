### Types

- `/software/chkconfig/service_type`
    - `/software/chkconfig/service_type/name`
        - optional
        - type: string
    - `/software/chkconfig/service_type/add`
        - optional
        - type: boolean
    - `/software/chkconfig/service_type/del`
        - optional
        - type: boolean
    - `/software/chkconfig/service_type/on`
        - optional
        - type: string
    - `/software/chkconfig/service_type/off`
        - optional
        - type: string
    - `/software/chkconfig/service_type/reset`
        - optional
        - type: string
    - `/software/chkconfig/service_type/startstop`
        - optional
        - type: boolean
- `/software/chkconfig/component_chkconfig_type`
    - `/software/chkconfig/component_chkconfig_type/service`
        - required
        - type: service_type
    - `/software/chkconfig/component_chkconfig_type/default`
        - optional
        - type: string

### Functions

- chkconfig_allow_combinations