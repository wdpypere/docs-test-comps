##############################################
NCM\::Component\::metaconfig\::bacula - schema
##############################################

Types
-----

 - **/software/components/metaconfig/bacula_autochanger**
    - */software/components/metaconfig/bacula_autochanger/Name*
        - Required
        - Type: string
    - */software/components/metaconfig/bacula_autochanger/Device*
        - Required
        - Type: string
    - */software/components/metaconfig/bacula_autochanger/Changer_Command*
        - Required
        - Type: string
    - */software/components/metaconfig/bacula_autochanger/Changer_Device*
        - Required
        - Type: string
 - **/software/components/metaconfig/bacula_device**
    - */software/components/metaconfig/bacula_device/Name*
        - Required
        - Type: string
    - */software/components/metaconfig/bacula_device/Media_Type*
        - Required
        - Type: string
    - */software/components/metaconfig/bacula_device/Device_Type*
        - Required
        - Type: string
    - */software/components/metaconfig/bacula_device/Random_Access*
        - Required
        - Type: boolean
    - */software/components/metaconfig/bacula_device/Archive_Device*
        - Required
        - Type: string
    - */software/components/metaconfig/bacula_device/Label_Media*
        - Required
        - Type: boolean
    - */software/components/metaconfig/bacula_device/Drive_Index*
        - Optional
        - Type: long
    - */software/components/metaconfig/bacula_device/Autoselect*
        - Optional
        - Type: boolean
    - */software/components/metaconfig/bacula_device/Autochanger*
        - Optional
        - Type: boolean
    - */software/components/metaconfig/bacula_device/AutomaticMount*
        - Optional
        - Type: boolean
    - */software/components/metaconfig/bacula_device/RemovableMedia*
        - Optional
        - Type: boolean
    - */software/components/metaconfig/bacula_device/AlwaysOpen*
        - Optional
        - Type: boolean
    - */software/components/metaconfig/bacula_device/MaximumOpenWait*
        - Optional
        - Type: long
    - */software/components/metaconfig/bacula_device/Maximum_Network_Buffer_Size*
        - Optional
        - Type: long
    - */software/components/metaconfig/bacula_device/Maximum_Block_Size*
        - Optional
        - Type: long
 - **/software/components/metaconfig/bacula_filedaemon**
    - */software/components/metaconfig/bacula_filedaemon/Name*
        - Required
        - Type: string
    - */software/components/metaconfig/bacula_filedaemon/FDport*
        - Required
        - Type: long
        - Default value: 9102
    - */software/components/metaconfig/bacula_filedaemon/WorkingDirectory*
        - Required
        - Type: string
        - Default value: /var/spool/bacula
    - */software/components/metaconfig/bacula_filedaemon/Pid_Directory*
        - Required
        - Type: string
        - Default value: /var/run
    - */software/components/metaconfig/bacula_filedaemon/Maximum_Concurrent_Jobs*
        - Required
        - Type: long
        - Default value: 20
    - */software/components/metaconfig/bacula_filedaemon/Maximum_Network_Buffer_Size*
        - Optional
        - Type: long
 - **/software/components/metaconfig/bacula_message_destinations**
    - */software/components/metaconfig/bacula_message_destinations/destination*
        - Required
        - Type: string
    - */software/components/metaconfig/bacula_message_destinations/address*
        - Optional
        - Type: string
    - */software/components/metaconfig/bacula_message_destinations/types*
        - Required
        - Type: string
 - **/software/components/metaconfig/bacula_director**
    - */software/components/metaconfig/bacula_director/Name*
        - Required
        - Type: string
    - */software/components/metaconfig/bacula_director/Password*
        - Required
        - Type: string
    - */software/components/metaconfig/bacula_director/Monitor*
        - Optional
        - Type: boolean
 - **/software/components/metaconfig/bacula_messages**
    - */software/components/metaconfig/bacula_messages/Name*
        - Required
        - Type: string
    - */software/components/metaconfig/bacula_messages/MailCommand*
        - Optional
        - Type: string
    - */software/components/metaconfig/bacula_messages/messagedestinations*
        - Required
        - Type: bacula_message_destinations
 - **/software/components/metaconfig/bacula_storage**
    - */software/components/metaconfig/bacula_storage/Name*
        - Required
        - Type: string
    - */software/components/metaconfig/bacula_storage/SDAddress*
        - Required
        - Type: string
    - */software/components/metaconfig/bacula_storage/SDPort*
        - Required
        - Type: long
        - Default value: 9103
    - */software/components/metaconfig/bacula_storage/WorkingDirectory*
        - Required
        - Type: string
        - Default value: /var/spool/bacula
    - */software/components/metaconfig/bacula_storage/Pid_Directory*
        - Required
        - Type: string
        - Default value: /var/run
    - */software/components/metaconfig/bacula_storage/Maximum_Concurrent_Jobs*
        - Required
        - Type: long
        - Default value: 20
 - **/software/components/metaconfig/bacula_main_config**
    - */software/components/metaconfig/bacula_main_config/FileDaemon*
        - Optional
        - Type: bacula_filedaemon
    - */software/components/metaconfig/bacula_main_config/Director*
        - Optional
        - Type: bacula_director
    - */software/components/metaconfig/bacula_main_config/Messages*
        - Optional
        - Type: bacula_messages
    - */software/components/metaconfig/bacula_main_config/Storage*
        - Optional
        - Type: bacula_storage
    - */software/components/metaconfig/bacula_main_config/Device*
        - Optional
        - Type: bacula_device
    - */software/components/metaconfig/bacula_main_config/Autochanger*
        - Optional
        - Type: bacula_autochanger
 - **/software/components/metaconfig/bacula_config**
    - */software/components/metaconfig/bacula_config/preincludes*
        - Optional
        - Type: string
    - */software/components/metaconfig/bacula_config/includes*
        - Optional
        - Type: string
    - */software/components/metaconfig/bacula_config/main*
        - Optional
        - Type: bacula_main_config
