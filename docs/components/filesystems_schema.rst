#####################
filesystems :: schema
#####################

Types
-----

 - **/software/filesystems/structure_component_filesystems**
    - Description: when manage_blockdevs is false, filesystems does same as fstabNo other resources here: this component takes its configurationfrom fstab component, "/system/filesystems" and "/system/blockdevices"
    - */software/filesystems/structure_component_filesystems/manage_blockdevs*
        - Optional
        - Type: boolean
