##########################################
NCM\::Component\::authconfig\::sssd - ldap
##########################################

Types
-----

 - **/software/components/authconfig/ldap_schema**
 - **/software/components/authconfig/ldap_authok**
 - **/software/components/authconfig/ldap_deref**
 - **/software/components/authconfig/ldap_order**
 - **/software/components/authconfig/sssd_chpass**
    - Description: LDAP chpass fields
    - */software/components/authconfig/sssd_chpass/uri*
        - Optional
        - Type: type_absoluteURI
    - */software/components/authconfig/sssd_chpass/backup_uri*
        - Optional
        - Type: type_absoluteURI
    - */software/components/authconfig/sssd_chpass/dns_service_name*
        - Optional
        - Type: string
    - */software/components/authconfig/sssd_chpass/update_last_change*
        - Required
        - Type: boolean
        - Default value: false
 - **/software/components/authconfig/sssd_ldap_defaults**
    - */software/components/authconfig/sssd_ldap_defaults/bind_dn*
        - Optional
        - Type: string
    - */software/components/authconfig/sssd_ldap_defaults/authtok_type*
        - Required
        - Type: ldap_authok
        - Default value: password
    - */software/components/authconfig/sssd_ldap_defaults/authtok*
        - Optional
        - Type: string
 - **/software/components/authconfig/sssd_netgroup**
    - Description: LDAP netgroup fields
    - */software/components/authconfig/sssd_netgroup/object_class*
        - Required
        - Type: string
        - Default value: nisNetgroup
    - */software/components/authconfig/sssd_netgroup/name*
        - Required
        - Type: string
        - Default value: cn
    - */software/components/authconfig/sssd_netgroup/member*
        - Required
        - Type: string
        - Default value: memberNisNetgroup
    - */software/components/authconfig/sssd_netgroup/triple*
        - Required
        - Type: string
        - Default value: nisNetgroupTriple
    - */software/components/authconfig/sssd_netgroup/uuid*
        - Required
        - Type: string
        - Default value: nsUniqueId
    - */software/components/authconfig/sssd_netgroup/modify_timestamp*
        - Required
        - Type: string
        - Default value: modifyTimestamp
    - */software/components/authconfig/sssd_netgroup/search_base*
        - Optional
        - Type: string
 - **/software/components/authconfig/sssd_autofs**
    - Description: LDAP autofs fields
    - */software/components/authconfig/sssd_autofs/map_object_class*
        - Required
        - Type: string
        - Default value: automountMap
    - */software/components/authconfig/sssd_autofs/map_name*
        - Required
        - Type: string
        - Default value: ou
    - */software/components/authconfig/sssd_autofs/entry_object_class*
        - Required
        - Type: string
        - Default value: automount
    - */software/components/authconfig/sssd_autofs/entry_key*
        - Required
        - Type: string
        - Default value: cn
    - */software/components/authconfig/sssd_autofs/entry_value*
        - Required
        - Type: string
        - Default value: automountInformation
    - */software/components/authconfig/sssd_autofs/search_base*
        - Optional
        - Type: string
 - **/software/components/authconfig/sssd_ldap_service**
    - Description: LDAP IP service fields
    - */software/components/authconfig/sssd_ldap_service/object_class*
        - Required
        - Type: string
        - Default value: ipService
    - */software/components/authconfig/sssd_ldap_service/name*
        - Required
        - Type: string
        - Default value: cn
    - */software/components/authconfig/sssd_ldap_service/port*
        - Required
        - Type: string
        - Default value: ipServicePort
    - */software/components/authconfig/sssd_ldap_service/proto*
        - Required
        - Type: string
        - Default value: ipServiceProtocol
    - */software/components/authconfig/sssd_ldap_service/search_base*
        - Optional
        - Type: string
 - **/software/components/authconfig/authconfig_sssd_ldap**
    - Description: LDAP access provider for SSSD. See the sssd-ldap man page. Timeouts are expressed in seconds.
    - */software/components/authconfig/authconfig_sssd_ldap/user*
        - Required
        - Type: sssd_user
    - */software/components/authconfig/authconfig_sssd_ldap/group*
        - Required
        - Type: sssd_group
    - */software/components/authconfig/authconfig_sssd_ldap/chpass*
        - Optional
        - Type: sssd_chpass
    - */software/components/authconfig/authconfig_sssd_ldap/default*
        - Required
        - Type: sssd_ldap_defaults
    - */software/components/authconfig/authconfig_sssd_ldap/sasl*
        - Optional
        - Type: sssd_sasl
    - */software/components/authconfig/authconfig_sssd_ldap/krb5*
        - Optional
        - Type: sssd_krb5
    - */software/components/authconfig/authconfig_sssd_ldap/sudo*
        - Optional
        - Type: sssd_sudo
    - */software/components/authconfig/authconfig_sssd_ldap/sudorule*
        - Optional
        - Type: sssd_sudorule
    - */software/components/authconfig/authconfig_sssd_ldap/tls*
        - Optional
        - Type: sssd_tls
    - */software/components/authconfig/authconfig_sssd_ldap/netgroup*
        - Optional
        - Type: sssd_netgroup
    - */software/components/authconfig/authconfig_sssd_ldap/autofs*
        - Optional
        - Type: sssd_autofs
    - */software/components/authconfig/authconfig_sssd_ldap/uri*
        - Optional
        - Type: type_absoluteURI
    - */software/components/authconfig/authconfig_sssd_ldap/backup_uri*
        - Optional
        - Type: type_absoluteURI
    - */software/components/authconfig/authconfig_sssd_ldap/search_base*
        - Optional
        - Type: string
    - */software/components/authconfig/authconfig_sssd_ldap/schema*
        - Required
        - Type: ldap_schema
        - Default value: rfc2307
    - */software/components/authconfig/authconfig_sssd_ldap/service*
        - Optional
        - Type: sssd_ldap_service
    - */software/components/authconfig/authconfig_sssd_ldap/krb5_backup_server*
        - Optional
        - Type: string
    - */software/components/authconfig/authconfig_sssd_ldap/krb5_canonicalize*
        - Optional
        - Type: boolean
    - */software/components/authconfig/authconfig_sssd_ldap/krb5_realm*
        - Optional
        - Type: string
    - */software/components/authconfig/authconfig_sssd_ldap/krb5_server*
        - Optional
        - Type: string
    - */software/components/authconfig/authconfig_sssd_ldap/access_filter*
        - Optional
        - Type: string
    - */software/components/authconfig/authconfig_sssd_ldap/access_order*
        - Required
        - Type: ldap_order
        - Default value: filter
    - */software/components/authconfig/authconfig_sssd_ldap/connection_expire_timeout*
        - Required
        - Type: long
        - Default value: 900
    - */software/components/authconfig/authconfig_sssd_ldap/deref*
        - Optional
        - Type: string
    - */software/components/authconfig/authconfig_sssd_ldap/deref_threshold*
        - Optional
        - Type: long
    - */software/components/authconfig/authconfig_sssd_ldap/disable_paging*
        - Required
        - Type: boolean
        - Default value: false
    - */software/components/authconfig/authconfig_sssd_ldap/dns_service_name*
        - Optional
        - Type: string
    - */software/components/authconfig/authconfig_sssd_ldap/entry_usn*
        - Optional
        - Type: string
    - */software/components/authconfig/authconfig_sssd_ldap/enumeration_refresh_timeout*
        - Required
        - Type: long
        - Default value: 300
    - */software/components/authconfig/authconfig_sssd_ldap/enumeration_search_timeout*
        - Required
        - Type: long
        - Default value: 60
    - */software/components/authconfig/authconfig_sssd_ldap/force_upper_case_realm*
        - Required
        - Type: boolean
        - Default value: false
    - */software/components/authconfig/authconfig_sssd_ldap/groups_use_matching_rule_in_chain*
        - Optional
        - Type: boolean
    - */software/components/authconfig/authconfig_sssd_ldap/id_use_start_tls*
        - Optional
        - Type: boolean
    - */software/components/authconfig/authconfig_sssd_ldap/id_mapping*
        - Optional
        - Type: boolean
        - Default value: false
    - */software/components/authconfig/authconfig_sssd_ldap/network_timeout*
        - Required
        - Type: long
        - Default value: 6
    - */software/components/authconfig/authconfig_sssd_ldap/ns_account_lock*
        - Optional
        - Type: string
    - */software/components/authconfig/authconfig_sssd_ldap/offline_timeout*
        - Optional
        - Type: long
    - */software/components/authconfig/authconfig_sssd_ldap/opt_timeout*
        - Required
        - Type: long
        - Default value: 6
    - */software/components/authconfig/authconfig_sssd_ldap/page_size*
        - Required
        - Type: long
        - Default value: 1000
    - */software/components/authconfig/authconfig_sssd_ldap/purge_cache_timeout*
        - Required
        - Type: long
        - Default value: 10800
    - */software/components/authconfig/authconfig_sssd_ldap/pwd_policy*
        - Required
        - Type: string
        - Default value: none
    - */software/components/authconfig/authconfig_sssd_ldap/referrals*
        - Optional
        - Type: boolean
    - */software/components/authconfig/authconfig_sssd_ldap/rootdse_last_usn*
        - Optional
        - Type: string
    - */software/components/authconfig/authconfig_sssd_ldap/search_timeout*
        - Required
        - Type: long
        - Default value: 6
    - */software/components/authconfig/authconfig_sssd_ldap/account_expire_policy*
        - Optional
        - Type: string
