### Types

- `/software/useraccess/useraccess_pointer`
- `/software/useraccess/structure_kerberos`
    - `/software/useraccess/structure_kerberos/realm`
        - required
        - type: type_hostname

    - `/software/useraccess/structure_kerberos/principal`
        - required
        - type: string

    - `/software/useraccess/structure_kerberos/instance`
        - optional
        - type: string

    - `/software/useraccess/structure_kerberos/host`
        - optional
        - type: type_hostname

- `/software/useraccess/credentialfilestring`
- `/software/useraccess/structure_useraccess_auth`
    - `/software/useraccess/structure_useraccess_auth/ssh_keys_urls`
        - optional
        - type: type_absoluteURI

    - `/software/useraccess/structure_useraccess_auth/kerberos4`
        - optional
        - type: structure_kerberos

    - `/software/useraccess/structure_useraccess_auth/kerberos5`
        - optional
        - type: structure_kerberos

    - `/software/useraccess/structure_useraccess_auth/acls`
        - optional
        - type: string

    - `/software/useraccess/structure_useraccess_auth/roles`
        - optional
        - type: useraccess_pointer

    - `/software/useraccess/structure_useraccess_auth/ssh_keys`
        - optional
        - type: string

    - `/software/useraccess/structure_useraccess_auth/managed_credentials`
        - required
        - type: credentialfilestring

- `/software/useraccess/structure_component_useraccess`
    - `/software/useraccess/structure_component_useraccess/configSerial`
        - optional
        - type: string

    - `/software/useraccess/structure_component_useraccess/users`
        - required
        - type: structure_useraccess_auth

    - `/software/useraccess/structure_component_useraccess/roles`
        - optional
        - type: structure_useraccess_auth

    - `/software/useraccess/structure_component_useraccess/acl_services`
        - optional
        - type: string
### Functions
