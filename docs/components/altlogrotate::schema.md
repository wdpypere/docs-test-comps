### Types

- `/software/altlogrotate/structure_altlogrotate_scripts`
    - `/software/altlogrotate/structure_altlogrotate_scripts/prerotate`
        - optional
        - type: string

    - `/software/altlogrotate/structure_altlogrotate_scripts/postrotate`
        - optional
        - type: string

    - `/software/altlogrotate/structure_altlogrotate_scripts/firstaction`
        - optional
        - type: string

    - `/software/altlogrotate/structure_altlogrotate_scripts/lastaction`
        - optional
        - type: string

- `/software/altlogrotate/structure_altlogrotate_create_params`
    - `/software/altlogrotate/structure_altlogrotate_create_params/mode`
        - required
        - type: string

    - `/software/altlogrotate/structure_altlogrotate_create_params/owner`
        - required
        - type: string

    - `/software/altlogrotate/structure_altlogrotate_create_params/group`
        - required
        - type: string

- `/software/altlogrotate/structure_altlogrotate_logrot`
    - `/software/altlogrotate/structure_altlogrotate_logrot/pattern`
        - optional
        - type: string

    - `/software/altlogrotate/structure_altlogrotate_logrot/global`
        - optional
        - type: boolean

    - `/software/altlogrotate/structure_altlogrotate_logrot/overwrite`
        - optional
        - type: boolean

    - `/software/altlogrotate/structure_altlogrotate_logrot/include`
        - optional
        - type: string

    - `/software/altlogrotate/structure_altlogrotate_logrot/compress`
        - optional
        - type: boolean

    - `/software/altlogrotate/structure_altlogrotate_logrot/copy`
        - optional
        - type: boolean

    - `/software/altlogrotate/structure_altlogrotate_logrot/copytruncate`
        - optional
        - type: boolean

    - `/software/altlogrotate/structure_altlogrotate_logrot/delaycompress`
        - optional
        - type: boolean

    - `/software/altlogrotate/structure_altlogrotate_logrot/ifempty`
        - optional
        - type: boolean

    - `/software/altlogrotate/structure_altlogrotate_logrot/missingok`
        - optional
        - type: boolean

    - `/software/altlogrotate/structure_altlogrotate_logrot/sharedscripts`
        - optional
        - type: boolean

    - `/software/altlogrotate/structure_altlogrotate_logrot/dateext`
        - optional
        - type: boolean

    - `/software/altlogrotate/structure_altlogrotate_logrot/compresscmd`
        - optional
        - type: string

    - `/software/altlogrotate/structure_altlogrotate_logrot/uncompresscmd`
        - optional
        - type: string

    - `/software/altlogrotate/structure_altlogrotate_logrot/compressext`
        - optional
        - type: string

    - `/software/altlogrotate/structure_altlogrotate_logrot/compressoptions`
        - optional
        - type: string

    - `/software/altlogrotate/structure_altlogrotate_logrot/create`
        - optional
        - type: boolean

    - `/software/altlogrotate/structure_altlogrotate_logrot/createparams`
        - optional
        - type: structure_altlogrotate_create_params

    - `/software/altlogrotate/structure_altlogrotate_logrot/extension`
        - optional
        - type: string

    - `/software/altlogrotate/structure_altlogrotate_logrot/mail`
        - optional
        - type: type_email

    - `/software/altlogrotate/structure_altlogrotate_logrot/nomail`
        - optional
        - type: boolean

    - `/software/altlogrotate/structure_altlogrotate_logrot/mailselect`
        - optional
        - type: string

    - `/software/altlogrotate/structure_altlogrotate_logrot/olddir`
        - optional
        - type: string

    - `/software/altlogrotate/structure_altlogrotate_logrot/noolddir`
        - optional
        - type: boolean

    - `/software/altlogrotate/structure_altlogrotate_logrot/rotate`
        - optional
        - type: long
        - range: 0..

    - `/software/altlogrotate/structure_altlogrotate_logrot/start`
        - optional
        - type: long
        - range: 0..

    - `/software/altlogrotate/structure_altlogrotate_logrot/size`
        - optional
        - type: string

    - `/software/altlogrotate/structure_altlogrotate_logrot/taboo_replace`
        - optional
        - type: boolean

    - `/software/altlogrotate/structure_altlogrotate_logrot/tabooext`
        - optional
        - type: string

    - `/software/altlogrotate/structure_altlogrotate_logrot/frequency`
        - optional
        - type: string

    - `/software/altlogrotate/structure_altlogrotate_logrot/scripts`
        - optional
        - type: structure_altlogrotate_scripts

- `/software/altlogrotate/component_altlogrotate`
    - `/software/altlogrotate/component_altlogrotate/configFile`
        - required
        - type: string

    - `/software/altlogrotate/component_altlogrotate/configDir`
        - required
        - type: string

    - `/software/altlogrotate/component_altlogrotate/entries`
        - optional
        - type: structure_altlogrotate_logrot
### Functions
