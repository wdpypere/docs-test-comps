### Types

- `/software/filecopy/structure_filecopy`
    - `/software/filecopy/structure_filecopy/config`
        - optional
        - type: string
    - `/software/filecopy/structure_filecopy/source`
        - optional
        - type: string
    - `/software/filecopy/structure_filecopy/restart`
        - optional
        - type: string
    - `/software/filecopy/structure_filecopy/perms`
        - optional
        - type: string
    - `/software/filecopy/structure_filecopy/owner`
        - optional
        - type: string
    - `/software/filecopy/structure_filecopy/group`
        - optional
        - type: string
    - `/software/filecopy/structure_filecopy/no_utf8`
        - optional
        - type: boolean
    - `/software/filecopy/structure_filecopy/forceRestart`
        - required
        - type: boolean
    - `/software/filecopy/structure_filecopy/backup`
        - required
        - type: boolean
- `/software/filecopy/component_filecopy`
    - `/software/filecopy/component_filecopy/services`
        - optional
        - type: structure_filecopy
    - `/software/filecopy/component_filecopy/forceRestart`
        - required
        - type: boolean

### Functions

  - component_filecopy_valid
