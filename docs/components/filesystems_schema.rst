#####################
filesystems :: schema
#####################

Types
-----

 - **/software/components/filesystems/structure_component_filesystems**
    - Description: when manage_blockdevs is false, filesystems does same as fstabNo other resources here: this component takes its configurationfrom fstab component, "/system/filesystems" and "/system/blockdevices"
    - */software/components/filesystems/structure_component_filesystems/manage_blockdevs*
        - Required
        - Type: boolean
        - Default value: true
