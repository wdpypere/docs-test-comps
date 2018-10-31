#############
nss :: schema
#############

Types
-----

 - **/software/nss/component_nss_build**
    - */software/nss/component_nss_build/script*
        - Optional
        - Type: string
    - */software/nss/component_nss_build/depends*
        - Optional
        - Type: string
    - */software/nss/component_nss_build/active*
        - Optional
        - Type: boolean
 - **/software/nss/component_nss_build_dbs**
    - */software/nss/component_nss_build_dbs/db*
        - Optional
        - Type: component_nss_build
    - */software/nss/component_nss_build_dbs/nis*
        - Optional
        - Type: component_nss_build
    - */software/nss/component_nss_build_dbs/compat*
        - Optional
        - Type: component_nss_build
    - */software/nss/component_nss_build_dbs/dns*
        - Optional
        - Type: component_nss_build
    - */software/nss/component_nss_build_dbs/files*
        - Optional
        - Type: component_nss_build
    - */software/nss/component_nss_build_dbs/ldap*
        - Optional
        - Type: component_nss_build
 - **/software/nss/component_nss_db**
 - **/software/nss/component_nss_type**
    - */software/nss/component_nss_type/build*
        - Optional
        - Type: component_nss_build_dbs
    - */software/nss/component_nss_type/databases*
        - Optional
        - Type: component_nss_db
