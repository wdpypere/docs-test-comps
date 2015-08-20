### Types

- `/software/nrpe/component_nrpe_options`
    - `/software/nrpe/component_nrpe_options/log_facility`
        - required
        - type: string

    - `/software/nrpe/component_nrpe_options/pid_file`
        - required
        - type: string

    - `/software/nrpe/component_nrpe_options/server_port`
        - required
        - type: type_port

    - `/software/nrpe/component_nrpe_options/server_address`
        - optional
        - type: string

    - `/software/nrpe/component_nrpe_options/nrpe_user`
        - required
        - type: string

    - `/software/nrpe/component_nrpe_options/nrpe_group`
        - required
        - type: string

    - `/software/nrpe/component_nrpe_options/allowed_hosts`
        - required
        - type: type_hostname

    - `/software/nrpe/component_nrpe_options/dont_blame_nrpe`
        - required
        - type: boolean

    - `/software/nrpe/component_nrpe_options/command_prefix`
        - optional
        - type: string

    - `/software/nrpe/component_nrpe_options/debug`
        - required
        - type: boolean

    - `/software/nrpe/component_nrpe_options/command_timeout`
        - required
        - type: long

    - `/software/nrpe/component_nrpe_options/connection_timeout`
        - required
        - type: long

    - `/software/nrpe/component_nrpe_options/allow_weak_random_seed`
        - optional
        - type: boolean

    - `/software/nrpe/component_nrpe_options/command`
        - required
        - type: string

    - `/software/nrpe/component_nrpe_options/include`
        - optional
        - type: string

    - `/software/nrpe/component_nrpe_options/include_dir`
        - optional
        - type: string

- `/software/nrpe/structure_component_nrpe`
    - `/software/nrpe/structure_component_nrpe/mode`
        - required
        - type: long

    - `/software/nrpe/structure_component_nrpe/options`
        - required
        - type: component_nrpe_options
### Functions
