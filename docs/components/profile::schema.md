### Types

- `/software/profile/structure_profile_path`
    - `/software/profile/structure_profile_path/prepend`
        - optional
        - type: string
    - `/software/profile/structure_profile_path/append`
        - optional
        - type: string
    - `/software/profile/structure_profile_path/value`
        - optional
        - type: string
- `/software/profile/structure_profile_script`
    - `/software/profile/structure_profile_script/flavors`
        - required
        - type: string
    - `/software/profile/structure_profile_script/env`
        - optional
        - type: string
    - `/software/profile/structure_profile_script/path`
        - optional
        - type: structure_profile_path
    - `/software/profile/structure_profile_script/flavorSuffix`
        - required
        - type: boolean
- `/software/profile/component_profile`
    - `/software/profile/component_profile/configDir`
        - optional
        - type: string
    - `/software/profile/component_profile/configName`
        - optional
        - type: string
    - `/software/profile/component_profile/scripts`
        - optional
        - type: structure_profile_script

### Functions

- component_profile_script_valid