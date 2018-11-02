##################
filecopy :: schema
##################

Types
-----

 - **/software/components/filecopy/structure_filecopy**
    - */software/components/filecopy/structure_filecopy/config*
        - Optional
        - Type: string
    - */software/components/filecopy/structure_filecopy/source*
        - Optional
        - Type: string
    - */software/components/filecopy/structure_filecopy/restart*
        - Optional
        - Type: string
    - */software/components/filecopy/structure_filecopy/perms*
        - Optional
        - Type: string
    - */software/components/filecopy/structure_filecopy/owner*
        - Optional
        - Type: string
    - */software/components/filecopy/structure_filecopy/group*
        - Optional
        - Type: string
    - */software/components/filecopy/structure_filecopy/no_utf8*
        - Optional
        - Type: boolean
    - */software/components/filecopy/structure_filecopy/forceRestart*
        - Required
        - Type: boolean
        - Default value: false
    - */software/components/filecopy/structure_filecopy/backup*
        - Required
        - Type: boolean
        - Default value: true
 - **/software/components/filecopy/component_filecopy**
    - */software/components/filecopy/component_filecopy/services*
        - Optional
        - Type: structure_filecopy
    - */software/components/filecopy/component_filecopy/forceRestart*
        - Required
        - Type: boolean
        - Default value: false

Functions
---------

 - component_filecopy_valid
