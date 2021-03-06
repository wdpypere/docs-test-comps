###########
types\::aii
###########

Types
-----

 - **structure_aii_module**
    - *structure_aii_module/dummy*
        - Optional
        - Type: string
 - **structure_aii_hook**
    - *structure_aii_hook/module*
        - Required
        - Type: string
 - **structure_aii_hooklist**
    - *structure_aii_hooklist/pre_install*
        - Optional
        - Type: structure_aii_hook
    - *structure_aii_hooklist/post_install*
        - Optional
        - Type: structure_aii_hook
    - *structure_aii_hooklist/post_reboot*
        - Optional
        - Type: structure_aii_hook
    - *structure_aii_hooklist/anaconda*
        - Optional
        - Type: structure_aii_hook
    - *structure_aii_hooklist/boot*
        - Optional
        - Type: structure_aii_hook
    - *structure_aii_hooklist/configure*
        - Optional
        - Type: structure_aii_hook
    - *structure_aii_hooklist/firmware*
        - Optional
        - Type: structure_aii_hook
    - *structure_aii_hooklist/install*
        - Optional
        - Type: structure_aii_hook
    - *structure_aii_hooklist/livecd*
        - Optional
        - Type: structure_aii_hook
    - *structure_aii_hooklist/remove*
        - Optional
        - Type: structure_aii_hook
    - *structure_aii_hooklist/rescue*
        - Optional
        - Type: structure_aii_hook
    - *structure_aii_hooklist/status*
        - Optional
        - Type: structure_aii_hook
 - **structure_aii**
    - Description: AII structure which defines the osinstall, nbp, dhcp config and hooks.
    - *structure_aii/osinstall*
        - Optional
        - Type: structure_aii_module
    - *structure_aii/nbp*
        - Optional
        - Type: structure_aii_module
    - *structure_aii/dhcp*
        - Optional
        - Type: structure_aii_module
    - *structure_aii/hooks*
        - Optional
        - Type: structure_aii_hooklist
    - *structure_aii/protected*
        - Description: The "protected" value can be used to protect the install and removal. By setting this value (eg. to the latest buildid), you will be asked to confirm this string as verification when trying to do install, configure or removal actions. This is done with the --confirm option of aii-shellfe
        - Optional
        - Type: string
