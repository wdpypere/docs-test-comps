### Types

- `/software/systemd/systemd_skip`
    - `/software/systemd/systemd_skip/service`
        - required
        - type: boolean

- `/software/systemd/systemd_target`
- `/software/systemd/systemd_unit_type`
    - `/software/systemd/systemd_unit_type/name`
        - optional
        - type: string

    - `/software/systemd/systemd_unit_type/targets`
        - required
        - type: systemd_target

    - `/software/systemd/systemd_unit_type/type`
        - required
        - type: string

    - `/software/systemd/systemd_unit_type/startstop`
        - required
        - type: boolean

    - `/software/systemd/systemd_unit_type/state`
        - required
        - type: string

- `/software/systemd/component_systemd`
    - `/software/systemd/component_systemd/skip`
        - required
        - type: systemd_skip

    - `/software/systemd/component_systemd/unconfigured`
        - required
        - type: string

    - `/software/systemd/component_systemd/unit`
        - optional
        - type: systemd_unit_type
### Functions
