####################
vomsclient :: schema
####################

Types
-----

 - **/software/components/vomsclient/structure_vomsclient_voms_info**
    - */software/components/vomsclient/structure_vomsclient_voms_info/name*
        - Optional
        - Type: string
    - */software/components/vomsclient/structure_vomsclient_voms_info/host*
        - Required
        - Type: type_fqdn
    - */software/components/vomsclient/structure_vomsclient_voms_info/port*
        - Required
        - Type: type_port
    - */software/components/vomsclient/structure_vomsclient_voms_info/cert*
        - Required
        - Type: string
    - */software/components/vomsclient/structure_vomsclient_voms_info/oldcert*
        - Optional
        - Type: string
    - */software/components/vomsclient/structure_vomsclient_voms_info/DN*
        - Optional
        - Type: string
    - */software/components/vomsclient/structure_vomsclient_voms_info/issuer*
        - Optional
        - Type: string
 - **/software/components/vomsclient/vomsclient_component**
    - */software/components/vomsclient/vomsclient_component/lscfile*
        - Optional
        - Type: boolean
    - */software/components/vomsclient/vomsclient_component/vomsCertsDir*
        - Optional
        - Type: string
    - */software/components/vomsclient/vomsclient_component/vomsServersDir*
        - Optional
        - Type: string
    - */software/components/vomsclient/vomsclient_component/vos*
        - Optional
        - Type: structure_vomsclient_voms_info
