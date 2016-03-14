### Types

- `/software/dirperm/structure_dirperm_entry`
    - decription: ensure that a directory is within a mountpoint configured in the profile
    - decription: ensure that a directory is within a mountpoint
    - `/software/dirperm/structure_dirperm_entry/path`
        - required
        - type: string
    - `/software/dirperm/structure_dirperm_entry/perm`
        - required
        - type: string
    - `/software/dirperm/structure_dirperm_entry/owner`
        - required
        - type: string
    - `/software/dirperm/structure_dirperm_entry/type`
        - required
        - type: string
    - `/software/dirperm/structure_dirperm_entry/initdir`
        - optional
        - type: string
    - `/software/dirperm/structure_dirperm_entry/checkmount`
        - required
        - type: boolean
    - `/software/dirperm/structure_dirperm_entry/within_mount`
        - required
        - type: boolean
- `/software/dirperm/component_dirperm`
    - `/software/dirperm/component_dirperm/paths`
        - optional
        - type: structure_dirperm_entry

### Functions

  - dirperm_permissions_valid
