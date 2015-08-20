### Types

- `/software/accounts/structure_userinfo`
    - `/software/accounts/structure_userinfo/comment`
        - optional
        - type: string

    - `/software/accounts/structure_userinfo/homeDir`
        - optional
        - type: string

    - `/software/accounts/structure_userinfo/createHome`
        - optional
        - type: boolean

    - `/software/accounts/structure_userinfo/createKeys`
        - optional
        - type: boolean

    - `/software/accounts/structure_userinfo/groups`
        - required
        - type: string

    - `/software/accounts/structure_userinfo/password`
        - optional
        - type: string

    - `/software/accounts/structure_userinfo/shell`
        - required
        - type: string

    - `/software/accounts/structure_userinfo/uid`
        - required
        - type: long
        - range: 0..

    - `/software/accounts/structure_userinfo/poolStart`
        - optional
        - type: long
        - range: 0..

    - `/software/accounts/structure_userinfo/poolDigits`
        - optional
        - type: long
        - range: 1..

    - `/software/accounts/structure_userinfo/poolSize`
        - optional
        - type: long
        - range: 0..

    - `/software/accounts/structure_userinfo/info`
        - optional
        - type: string

    - `/software/accounts/structure_userinfo/ldap`
        - optional
        - type: boolean

- `/software/accounts/structure_groupinfo`
    - `/software/accounts/structure_groupinfo/comment`
        - optional
        - type: string

    - `/software/accounts/structure_groupinfo/gid`
        - required
        - type: long
        - range: 1..

- `/software/accounts/structure_login_defs`
    - `/software/accounts/structure_login_defs/uid_min`
        - optional
        - type: long
        - range: 1..

    - `/software/accounts/structure_login_defs/uid_max`
        - optional
        - type: long
        - range: 1..

    - `/software/accounts/structure_login_defs/gid_min`
        - optional
        - type: long
        - range: 1..

    - `/software/accounts/structure_login_defs/gid_max`
        - optional
        - type: long
        - range: 1..

    - `/software/accounts/structure_login_defs/pass_max_days`
        - optional
        - type: long
        - range: 1..

    - `/software/accounts/structure_login_defs/pass_min_days`
        - optional
        - type: long
        - range: 1..

    - `/software/accounts/structure_login_defs/pass_min_len`
        - optional
        - type: long
        - range: 1..

    - `/software/accounts/structure_login_defs/pass_warn_age`
        - optional
        - type: long
        - range: 1..

    - `/software/accounts/structure_login_defs/create_home`
        - optional
        - type: string

    - `/software/accounts/structure_login_defs/mail_dir`
        - optional
        - type: string

    - `/software/accounts/structure_login_defs/umask`
        - optional
        - type: string

    - `/software/accounts/structure_login_defs/userdel_cmd`
        - optional
        - type: string

    - `/software/accounts/structure_login_defs/usergroups_enab`
        - optional
        - type: boolean

- `/software/accounts/component_accounts`
    - `/software/accounts/component_accounts/rootpwd`
        - optional
        - type: string

    - `/software/accounts/component_accounts/rootshell`
        - optional
        - type: string

    - `/software/accounts/component_accounts/shadowpwd`
        - optional
        - type: boolean

    - `/software/accounts/component_accounts/users`
        - optional
        - type: structure_userinfo

    - `/software/accounts/component_accounts/groups`
        - optional
        - type: structure_groupinfo

    - `/software/accounts/component_accounts/login_defs`
        - optional
        - type: structure_login_defs

    - `/software/accounts/component_accounts/remove_unknown`
        - required
        - type: boolean

    - `/software/accounts/component_accounts/preserved_accounts`
        - required
        - type: string

    - `/software/accounts/component_accounts/kept_users`
        - required
        - type: string

    - `/software/accounts/component_accounts/kept_groups`
        - required
        - type: string

    - `/software/accounts/component_accounts/ldap`
        - optional
        - type: boolean
### Functions
  - %s
