### Types

- `/software/ccm/component_ccm`
    - `/software/ccm/component_ccm/configFile`
        - required
        - type: string

    - `/software/ccm/component_ccm/profile`
        - required
        - type: type_hostURI

    - `/software/ccm/component_ccm/profile_failover`
        - optional
        - type: type_hostURI

    - `/software/ccm/component_ccm/context`
        - optional
        - type: type_hostURI

    - `/software/ccm/component_ccm/debug`
        - required
        - type: long
        - range: 0..1

    - `/software/ccm/component_ccm/force`
        - required
        - type: long
        - range: 0..1

    - `/software/ccm/component_ccm/preprocessor`
        - optional
        - type: string

    - `/software/ccm/component_ccm/cache_root`
        - required
        - type: string

    - `/software/ccm/component_ccm/get_timeout`
        - required
        - type: long
        - range: 0..

    - `/software/ccm/component_ccm/lock_retries`
        - required
        - type: long
        - range: 0..

    - `/software/ccm/component_ccm/lock_wait`
        - required
        - type: long
        - range: 0..

    - `/software/ccm/component_ccm/retrieve_retries`
        - required
        - type: long
        - range: 0..

    - `/software/ccm/component_ccm/retrieve_wait`
        - required
        - type: long
        - range: 0..

    - `/software/ccm/component_ccm/cert_file`
        - optional
        - type: string

    - `/software/ccm/component_ccm/key_file`
        - optional
        - type: string

    - `/software/ccm/component_ccm/ca_file`
        - optional
        - type: string

    - `/software/ccm/component_ccm/ca_dir`
        - optional
        - type: string

    - `/software/ccm/component_ccm/world_readable`
        - required
        - type: long
        - range: 0..1

    - `/software/ccm/component_ccm/base_url`
        - optional
        - type: type_absoluteURI

    - `/software/ccm/component_ccm/dbformat`
        - optional
        - type: string

    - `/software/ccm/component_ccm/json_typed`
        - optional
        - type: boolean
### Functions
