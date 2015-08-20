### Types

- `/software/ipmi/structure_users`
    - `/software/ipmi/structure_users/login`
        - required
        - type: string

    - `/software/ipmi/structure_users/password`
        - required
        - type: string

    - `/software/ipmi/structure_users/priv`
        - optional
        - type: string

    - `/software/ipmi/structure_users/userid`
        - optional
        - type: long

- `/software/ipmi/component_ipmi_type`
    - `/software/ipmi/component_ipmi_type/channel`
        - required
        - type: long

    - `/software/ipmi/component_ipmi_type/users`
        - required
        - type: structure_users

    - `/software/ipmi/component_ipmi_type/net_interface`
        - required
        - type: string
### Functions
