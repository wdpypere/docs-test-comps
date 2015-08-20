### Types

- `/software/pam/component_pam_options`
- `/software/pam/component_listfile_acl`
    - `/software/pam/component_listfile_acl/filename`
        - required
        - type: string

    - `/software/pam/component_listfile_acl/items`
        - required
        - type: string

- `/software/pam/component_pam_module_stack`
    - `/software/pam/component_pam_module_stack/control`
        - required
        - type: string

    - `/software/pam/component_pam_module_stack/module`
        - required
        - type: string

    - `/software/pam/component_pam_module_stack/options`
        - optional
        - type: component_pam_options

    - `/software/pam/component_pam_module_stack/allow`
        - optional
        - type: component_listfile_acl

    - `/software/pam/component_pam_module_stack/deny`
        - optional
        - type: component_listfile_acl

- `/software/pam/component_pam_service_type`
    - `/software/pam/component_pam_service_type/auth`
        - optional
        - type: component_pam_module_stack

    - `/software/pam/component_pam_service_type/account`
        - optional
        - type: component_pam_module_stack

    - `/software/pam/component_pam_service_type/password`
        - optional
        - type: component_pam_module_stack

    - `/software/pam/component_pam_service_type/session`
        - optional
        - type: component_pam_module_stack

    - `/software/pam/component_pam_service_type/mode`
        - optional
        - type: string

- `/software/pam/component_pam_module`
    - `/software/pam/component_pam_module/path`
        - optional
        - type: string

- `/software/pam/component_pam_access_entry`
    - `/software/pam/component_pam_access_entry/permission`
        - required
        - type: string

    - `/software/pam/component_pam_access_entry/users`
        - required
        - type: string

    - `/software/pam/component_pam_access_entry/origins`
        - required
        - type: string

- `/software/pam/component_pam_access`
    - `/software/pam/component_pam_access/filename`
        - required
        - type: string

    - `/software/pam/component_pam_access/acl`
        - required
        - type: component_pam_access_entry

    - `/software/pam/component_pam_access/lastacl`
        - required
        - type: component_pam_access_entry

    - `/software/pam/component_pam_access/allowpos`
        - required
        - type: boolean

    - `/software/pam/component_pam_access/allowneg`
        - required
        - type: boolean

- `/software/pam/component_pam_entry`
    - `/software/pam/component_pam_entry/modules`
        - optional
        - type: component_pam_module

    - `/software/pam/component_pam_entry/services`
        - optional
        - type: component_pam_service_type

    - `/software/pam/component_pam_entry/directory`
        - optional
        - type: string

    - `/software/pam/component_pam_entry/acldir`
        - optional
        - type: string

    - `/software/pam/component_pam_entry/access`
        - optional
        - type: component_pam_access
### Functions
