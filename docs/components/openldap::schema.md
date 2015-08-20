### Types

- `/software/openldap/long_pow2`
    - decription: 
    power of 2 (up to 64k)

- `/software/openldap/ldap_hash`
    - decription: 
     Possible acceptable values

- `/software/openldap/ldap_sizelimit`
    - `/software/openldap/ldap_sizelimit/soft`
        - optional
        - type: long

    - `/software/openldap/ldap_sizelimit/hard`
        - optional
        - type: long

- `/software/openldap/ldap_buffer_size`
    - `/software/openldap/ldap_buffer_size/listener`
        - optional
        - type: type_absoluteURI

    - `/software/openldap/ldap_buffer_size/read`
        - optional
        - type: long

    - `/software/openldap/ldap_buffer_size/write`
        - optional
        - type: long

- `/software/openldap/ldap_access_item`
    - `/software/openldap/ldap_access_item/who`
        - optional
        - type: string

    - `/software/openldap/ldap_access_item/access`
        - optional
        - type: string

    - `/software/openldap/ldap_access_item/control`
        - optional
        - type: string

- `/software/openldap/ldap_access`
    - `/software/openldap/ldap_access/what`
        - optional
        - type: string

    - `/software/openldap/ldap_access/attrs`
        - optional
        - type: string

    - `/software/openldap/ldap_access/by`
        - required
        - type: string

- `/software/openldap/auth_regexp`
    - `/software/openldap/auth_regexp/match`
        - required
        - type: string

    - `/software/openldap/auth_regexp/replace`
        - required
        - type: string

- `/software/openldap/ldap_syntax`
- `/software/openldap/tls_options`
    - `/software/openldap/tls_options/CipherSuite`
        - required
        - type: string

    - `/software/openldap/tls_options/CACertificateFile`
        - optional
        - type: string

    - `/software/openldap/tls_options/CACertificatePath`
        - optional
        - type: string

    - `/software/openldap/tls_options/CertificateFile`
        - optional
        - type: string

    - `/software/openldap/tls_options/CertificateKeyFile`
        - optional
        - type: string

    - `/software/openldap/tls_options/DHParamFile`
        - optional
        - type: string

    - `/software/openldap/tls_options/RandFile`
        - optional
        - type: string

    - `/software/openldap/tls_options/VerifyClient`
        - optional
        - type: string

    - `/software/openldap/tls_options/CRLCheck`
        - optional
        - type: string

    - `/software/openldap/tls_options/CRLFile`
        - optional
        - type: string

- `/software/openldap/ldap_checkpoint`
    - `/software/openldap/ldap_checkpoint/size`
        - required
        - type: long
        - range: 0..

    - `/software/openldap/ldap_checkpoint/minutes`
        - required
        - type: long
        - range: 0..

- `/software/openldap/ldap_global`
    - `/software/openldap/ldap_global/access`
        - required
        - type: ldap_access

    - `/software/openldap/ldap_global/allow`
        - optional
        - type: string

    - `/software/openldap/ldap_global/argsfile`
        - optional
        - type: string

    - `/software/openldap/ldap_global/attributeoptions`
        - optional
        - type: string

    - `/software/openldap/ldap_global/attributetype`
        - optional
        - type: ldap_syntax

    - `/software/openldap/ldap_global/authid`-rewrite
        - optional
        - type: string

    - `/software/openldap/ldap_global/authz`-policy
        - optional
        - type: string

    - `/software/openldap/ldap_global/authz`-regexp
        - required
        - type: auth_regexp

    - `/software/openldap/ldap_global/concurrency`
        - optional
        - type: long

    - `/software/openldap/ldap_global/conn_max_pending_auth`
        - optional
        - type: long

    - `/software/openldap/ldap_global/defaultsearchbase`
        - optional
        - type: string

    - `/software/openldap/ldap_global/disallow`
        - optional
        - type: string

    - `/software/openldap/ldap_global/ditcontentrule`
        - optional
        - type: ldap_syntax

    - `/software/openldap/ldap_global/gentlehup`
        - required
        - type: boolean

    - `/software/openldap/ldap_global/idletimeout`
        - optional
        - type: long

    - `/software/openldap/ldap_global/include`
        - optional
        - type: string

    - `/software/openldap/ldap_global/ldapsyntax`
        - optional
        - type: ldap_syntax

    - `/software/openldap/ldap_global/listener`-threads
        - optional
        - type: long_pow2

    - `/software/openldap/ldap_global/localSSF`
        - required
        - type: long

    - `/software/openldap/ldap_global/logfile`
        - optional
        - type: string

    - `/software/openldap/ldap_global/loglevel`
        - optional
        - type: long

    - `/software/openldap/ldap_global/moduleload`
        - optional
        - type: string

    - `/software/openldap/ldap_global/modulepath`
        - optional
        - type: string

    - `/software/openldap/ldap_global/objectclass`
        - optional
        - type: ldap_syntax

    - `/software/openldap/ldap_global/password`-hash
        - required
        - type: ldap_hash

    - `/software/openldap/ldap_global/password`-crypt-salt-format
        - optional
        - type: string

    - `/software/openldap/ldap_global/pidfile`
        - optional
        - type: string

    - `/software/openldap/ldap_global/referral`
        - optional
        - type: type_URI

    - `/software/openldap/ldap_global/require`
        - optional
        - type: string

    - `/software/openldap/ldap_global/reverse`-lookup
        - required
        - type: boolean

    - `/software/openldap/ldap_global/rootDSE`
        - optional
        - type: string

    - `/software/openldap/ldap_global/sasl`-auxprops
        - optional
        - type: string

    - `/software/openldap/ldap_global/sasl`-host
        - optional
        - type: type_fqdn

    - `/software/openldap/ldap_global/sasl`-ream
        - optional
        - type: string

    - `/software/openldap/ldap_global/sasl`-secprops
        - optional
        - type: string

    - `/software/openldap/ldap_global/schemadn`
        - optional
        - type: string

    - `/software/openldap/ldap_global/security`
        - optional
        - type: string

    - `/software/openldap/ldap_global/serverID`
        - optional
        - type: long
        - range: 0..4095

    - `/software/openldap/ldap_global/sizelimit`
        - optional
        - type: ldap_sizelimit

    - `/software/openldap/ldap_global/sockbuf_max_incoming`
        - optional
        - type: long

    - `/software/openldap/ldap_global/sockbuf_max_incoming_auth`
        - optional
        - type: long

    - `/software/openldap/ldap_global/sortvals`
        - optional
        - type: string

    - `/software/openldap/ldap_global/tcp`-buffer
        - optional
        - type: ldap_buffer_size

    - `/software/openldap/ldap_global/threads`
        - required
        - type: long
        - range: 2..

    - `/software/openldap/ldap_global/tls`
        - optional
        - type: tls_options

    - `/software/openldap/ldap_global/timelimit`
        - optional
        - type: long

    - `/software/openldap/ldap_global/tool`-threads
        - required
        - type: long

    - `/software/openldap/ldap_global/writetimeout`
        - optional
        - type: long

- `/software/openldap/ldap_database_string`
- `/software/openldap/ldap_ops`
- `/software/openldap/ldap_replica_retries`
    - `/software/openldap/ldap_replica_retries/interval`
        - required
        - type: string

    - `/software/openldap/ldap_replica_retries/retries`
        - required
        - type: long

- `/software/openldap/ldap_replica_cfg`
    - `/software/openldap/ldap_replica_cfg/rid`
        - required
        - type: long
        - range: 0..999

    - `/software/openldap/ldap_replica_cfg/provider`
        - required
        - type: type_absoluteURI

    - `/software/openldap/ldap_replica_cfg/searchbase`
        - required
        - type: string

    - `/software/openldap/ldap_replica_cfg/type`
        - optional
        - type: string

    - `/software/openldap/ldap_replica_cfg/interval`
        - optional
        - type: string

    - `/software/openldap/ldap_replica_cfg/retry`
        - optional
        - type: ldap_replica_retries

    - `/software/openldap/ldap_replica_cfg/scope`
        - optional
        - type: string

    - `/software/openldap/ldap_replica_cfg/attrs`
        - optional
        - type: string

    - `/software/openldap/ldap_replica_cfg/attrsonly`
        - optional
        - type: boolean

    - `/software/openldap/ldap_replica_cfg/sizelimit`
        - optional
        - type: long

    - `/software/openldap/ldap_replica_cfg/timelimit`
        - optional
        - type: long

    - `/software/openldap/ldap_replica_cfg/schemachecking`
        - required
        - type: boolean

    - `/software/openldap/ldap_replica_cfg/network`-timeout
        - optional
        - type: long

    - `/software/openldap/ldap_replica_cfg/timeout`
        - optional
        - type: long

    - `/software/openldap/ldap_replica_cfg/bindmethod`
        - optional
        - type: string

    - `/software/openldap/ldap_replica_cfg/binddn`
        - optional
        - type: string

    - `/software/openldap/ldap_replica_cfg/saslmech`
        - optional
        - type: string

    - `/software/openldap/ldap_replica_cfg/authcid`
        - optional
        - type: string

    - `/software/openldap/ldap_replica_cfg/authzid`
        - optional
        - type: string

    - `/software/openldap/ldap_replica_cfg/credentials`
        - optional
        - type: string

    - `/software/openldap/ldap_replica_cfg/realm`
        - optional
        - type: string

    - `/software/openldap/ldap_replica_cfg/secprops`
        - optional
        - type: string

    - `/software/openldap/ldap_replica_cfg/keepalive`
        - optional
        - type: string

    - `/software/openldap/ldap_replica_cfg/starttls`
        - optional
        - type: string

    - `/software/openldap/ldap_replica_cfg/tls_cert`
        - optional
        - type: string

    - `/software/openldap/ldap_replica_cfg/tls_key`
        - optional
        - type: string

    - `/software/openldap/ldap_replica_cfg/tls_cacert`
        - optional
        - type: string

    - `/software/openldap/ldap_replica_cfg/tls_cacertdir`
        - optional
        - type: string

    - `/software/openldap/ldap_replica_cfg/tls_reqcert`
        - optional
        - type: string

    - `/software/openldap/ldap_replica_cfg/tls_ciphersuite`
        - optional
        - type: string

    - `/software/openldap/ldap_replica_cfg/tls_crlcheck`
        - optional
        - type: string

    - `/software/openldap/ldap_replica_cfg/suffixmassage`
        - optional
        - type: string

    - `/software/openldap/ldap_replica_cfg/logbase`
        - optional
        - type: string

    - `/software/openldap/ldap_replica_cfg/logfilter`
        - optional
        - type: string

    - `/software/openldap/ldap_replica_cfg/syncdata`
        - optional
        - type: string

    - `/software/openldap/ldap_replica_cfg/filter`
        - optional
        - type: string

- `/software/openldap/ldap_overlay_syncprov`
    - `/software/openldap/ldap_overlay_syncprov/checkpoint`
        - optional
        - type: long

    - `/software/openldap/ldap_overlay_syncprov/sessionlog`
        - optional
        - type: long

    - `/software/openldap/ldap_overlay_syncprov/nopresent`
        - optional
        - type: boolean

    - `/software/openldap/ldap_overlay_syncprov/reloadhint`
        - optional
        - type: boolean

- `/software/openldap/type_ldap_overlay`
    - `/software/openldap/type_ldap_overlay/syncprov`
        - optional
        - type: ldap_overlay_syncprov

- `/software/openldap/type_db_config`
    - `/software/openldap/type_db_config/cachesize`
        - optional
        - type: long

    - `/software/openldap/type_db_config/lg_regionmax`
        - optional
        - type: long

    - `/software/openldap/type_db_config/lg_bsize`
        - optional
        - type: long

    - `/software/openldap/type_db_config/lg_max`
        - optional
        - type: long

- `/software/openldap/ldap_database_limits`
    - `/software/openldap/ldap_database_limits/size`
        - optional
        - type: ldap_sizelimit

    - `/software/openldap/ldap_database_limits/time`
        - optional
        - type: ldap_sizelimit

- `/software/openldap/ldap_monitoring`
    - `/software/openldap/ldap_monitoring/default`
        - optional
        - type: boolean

- `/software/openldap/ldap_database`
    - `/software/openldap/ldap_database/class`
        - required
        - type: ldap_database_string

    - `/software/openldap/ldap_database/add_content_acl`
        - required
        - type: boolean

    - `/software/openldap/ldap_database/checkpoint`
        - optional
        - type: ldap_checkpoint

    - `/software/openldap/ldap_database/db_config`
        - optional
        - type: type_db_config

    - `/software/openldap/ldap_database/directory`
        - optional
        - type: string

    - `/software/openldap/ldap_database/extra_attrs`
        - optional
        - type: string

    - `/software/openldap/ldap_database/index`
        - optional
        - type: string

    - `/software/openldap/ldap_database/hidden`
        - required
        - type: boolean

    - `/software/openldap/ldap_database/lastmod`
        - required
        - type: boolean

    - `/software/openldap/ldap_database/limits`
        - optional
        - type: ldap_database_limits

    - `/software/openldap/ldap_database/maxderefdepth`
        - required
        - type: long

    - `/software/openldap/ldap_database/mirrormode`
        - optional
        - type: boolean

    - `/software/openldap/ldap_database/monitoring`
        - optional
        - type: boolean

    - `/software/openldap/ldap_database/overlay`
        - optional
        - type: type_ldap_overlay

    - `/software/openldap/ldap_database/readonly`
        - optional
        - type: boolean

    - `/software/openldap/ldap_database/restrict`
        - optional
        - type: ldap_ops

    - `/software/openldap/ldap_database/rootdn`
        - optional
        - type: string

    - `/software/openldap/ldap_database/rootpw`
        - optional
        - type: string

    - `/software/openldap/ldap_database/suffix`
        - optional
        - type: string

    - `/software/openldap/ldap_database/subordinate`
        - optional
        - type: boolean

    - `/software/openldap/ldap_database/sync_use_subentry`
        - optional
        - type: boolean

    - `/software/openldap/ldap_database/syncrepl`
        - optional
        - type: ldap_replica_cfg

    - `/software/openldap/ldap_database/updatedn`
        - optional
        - type: string

    - `/software/openldap/ldap_database/updateref`
        - optional
        - type: type_absoluteURI

    - `/software/openldap/ldap_database/backend_specific`
        - optional
        - type: string

- `/software/openldap/component_openldap`
    - `/software/openldap/component_openldap/conf_file`
        - required
        - type: string

    - `/software/openldap/component_openldap/include_schema`
        - required
        - type: string

    - `/software/openldap/component_openldap/loglevel`
        - optional
        - type: long
        - range: 0..

    - `/software/openldap/component_openldap/pidfile`
        - optional
        - type: string

    - `/software/openldap/component_openldap/argsfile`
        - optional
        - type: string

    - `/software/openldap/component_openldap/database`
        - required
        - type: string

    - `/software/openldap/component_openldap/suffix`
        - required
        - type: string

    - `/software/openldap/component_openldap/rootdn`
        - required
        - type: string

    - `/software/openldap/component_openldap/rootpw`
        - required
        - type: string

    - `/software/openldap/component_openldap/directory`
        - required
        - type: string

    - `/software/openldap/component_openldap/index`
        - optional
        - type: string

    - `/software/openldap/component_openldap/global`
        - optional
        - type: ldap_global

    - `/software/openldap/component_openldap/backends`
        - optional
        - type: ldap_database

    - `/software/openldap/component_openldap/databases`
        - optional
        - type: ldap_database

    - `/software/openldap/component_openldap/monitoring`
        - optional
        - type: ldap_monitoring

    - `/software/openldap/component_openldap/move_slapdd`
        - optional
        - type: boolean
### Functions
  - %s
   description: 
    converts a list of named loglevels to its numeric value
    returns undef in case of unknown entry
    returns (whichever comes first in list)
      0 if one of the values is 'nologging'
      -1 if one of the values is 'any'
 
