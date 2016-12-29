
### Types

 - `/software/chkconfig/service_type`
    - `/software/chkconfig/service_type/name`
        - Optional
        - Type: string
    - `/software/chkconfig/service_type/add`
        - Optional
        - Type: boolean
    - `/software/chkconfig/service_type/del`
        - Optional
        - Type: boolean
    - `/software/chkconfig/service_type/on`
        - Optional
        - Type: string
    - `/software/chkconfig/service_type/off`
        - Optional
        - Type: string
    - `/software/chkconfig/service_type/reset`
        - Optional
        - Type: string
    - `/software/chkconfig/service_type/startstop`
        - Optional
        - Type: boolean
 - `/software/chkconfig/component_chkconfig_type`
    - `/software/chkconfig/component_chkconfig_type/service`
        - Optional
        - Type: service_type
    - `/software/chkconfig/component_chkconfig_type/default`
        - Optional
        - Type: string

### Functions

 - chkconfig_allow_combinations
    - Arguments:
