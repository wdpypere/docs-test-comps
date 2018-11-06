########################################
NCM\::Component\::aii\::freeipa - schema
########################################

Types
-----

 - **/software/components/freeipa/aii_freeipa**
    - */software/components/freeipa/aii_freeipa/module*
        - Required
        - Type: string
    - */software/components/freeipa/aii_freeipa/remove*
        - Description: remove the host on AII removal (precedes disable)
        - Required
        - Type: boolean
        - Default value: false
    - */software/components/freeipa/aii_freeipa/disable*
        - Description: disable the host on AII removal
        - Required
        - Type: boolean
        - Default value: true

Functions
---------

 - validate_aii_freeipa_hooks
    - Description: a function to validate all freeipa hooksexample usage: bind "/system/aii/hooks" = dict with validate_aii_freeipa_hooks('post_reboot')
