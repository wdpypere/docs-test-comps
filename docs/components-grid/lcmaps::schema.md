
### Types

 - `/software/lcmaps/lcmaps_modulespec_type`
    - `/software/lcmaps/lcmaps_modulespec_type/path`
        - Optional
        - Type: string
    - `/software/lcmaps/lcmaps_modulespec_type/args`
        - Optional
        - Type: string
 - `/software/lcmaps/lcmaps_policy_type`
    - `/software/lcmaps/lcmaps_policy_type/name`
        - Optional
        - Type: string
    - `/software/lcmaps/lcmaps_policy_type/ruleset`
        - Optional
        - Type: string
 - `/software/lcmaps/lcmaps_file_type`
    - `/software/lcmaps/lcmaps_file_type/dbpath`
        - Optional
        - Type: string
    - `/software/lcmaps/lcmaps_file_type/modulepath`
        - Optional
        - Type: string
    - `/software/lcmaps/lcmaps_file_type/module`
        - Optional
        - Type: lcmaps_modulespec_type
    - `/software/lcmaps/lcmaps_file_type/policies`
        - Optional
        - Type: lcmaps_policy_type
 - `/software/lcmaps/lcmaps_component`
    - `/software/lcmaps/lcmaps_component/flavor`
        - Optional
        - Type: string
    - `/software/lcmaps/lcmaps_component/dbpath`
        - Optional
        - Type: string
    - `/software/lcmaps/lcmaps_component/modulepath`
        - Optional
        - Type: string
    - `/software/lcmaps/lcmaps_component/multifile`
        - Optional
        - Type: boolean
    - `/software/lcmaps/lcmaps_component/module`
        - Optional
        - Type: lcmaps_modulespec_type
    - `/software/lcmaps/lcmaps_component/policies`
        - Optional
        - Type: lcmaps_policy_type
    - `/software/lcmaps/lcmaps_component/config`
        - Optional
        - Type: lcmaps_file_type
    - `/software/lcmaps/lcmaps_component/multifile`
        - Optional
        - Type: boolean

### Functions

 - component_lcmaps_valid
