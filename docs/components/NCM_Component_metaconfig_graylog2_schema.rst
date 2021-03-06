################################################
NCM\::Component\::metaconfig\::graylog2 - schema
################################################

Types
-----

 - **/software/components/metaconfig/syslogprot_string**
 - **/software/components/metaconfig/graylog2**
    - */software/components/metaconfig/graylog2/syslog_listen_port*
        - Required
        - Type: long
        - Default value: 514
    - */software/components/metaconfig/graylog2/syslog_protocol*
        - Required
        - Type: syslogprot_string
        - Default value: udp
    - */software/components/metaconfig/graylog2/elasticsearch_url*
        - Required
        - Type: type_absoluteURI
        - Default value: http://localhost:9200/
    - */software/components/metaconfig/graylog2/elasticsearch_index_name*
        - Required
        - Type: string
        - Default value: graylog2
    - */software/components/metaconfig/graylog2/force_syslog_rdns*
        - Required
        - Type: boolean
        - Default value: false
    - */software/components/metaconfig/graylog2/mongodb_useauth*
        - Required
        - Type: boolean
        - Default value: false
    - */software/components/metaconfig/graylog2/mongodb_user*
        - Optional
        - Type: string
    - */software/components/metaconfig/graylog2/mongodb_password*
        - Optional
        - Type: string
    - */software/components/metaconfig/graylog2/mongodb_host*
        - Required
        - Type: type_fqdn
        - Default value: localhost.localdomain
    - */software/components/metaconfig/graylog2/mongodb_replica_set*
        - Optional
        - Type: string
    - */software/components/metaconfig/graylog2/mongodb_database*
        - Required
        - Type: string
        - Default value: graylog2
    - */software/components/metaconfig/graylog2/mongodb_port*
        - Required
        - Type: long
        - Default value: 27017
    - */software/components/metaconfig/graylog2/mq_batch_size*
        - Required
        - Type: long
        - Default value: 4000
    - */software/components/metaconfig/graylog2/mq_poll_freq*
        - Required
        - Type: long
        - Default value: 1
    - */software/components/metaconfig/graylog2/mq_max_size*
        - Required
        - Type: long
        - Default value: 0
    - */software/components/metaconfig/graylog2/mongodb_max_connections*
        - Required
        - Type: long
        - Default value: 100
    - */software/components/metaconfig/graylog2/mongodb_threads_allowed_to_block_multiplier*
        - Required
        - Type: long
        - Default value: 5
    - */software/components/metaconfig/graylog2/use_gelf*
        - Required
        - Type: boolean
        - Default value: true
    - */software/components/metaconfig/graylog2/gelf_listen_address*
        - Required
        - Type: type_ip
        - Default value: 0.0.0.0
    - */software/components/metaconfig/graylog2/gelf_listen_port*
        - Required
        - Type: type_port
        - Default value: 12201
    - */software/components/metaconfig/graylog2/rules_file*
        - Optional
        - Type: string
    - */software/components/metaconfig/graylog2/amqp_enabled*
        - Required
        - Type: boolean
        - Default value: false
    - */software/components/metaconfig/graylog2/amqp_subscribed_queues*
        - Optional
        - Type: string
    - */software/components/metaconfig/graylog2/amqp_host*
        - Required
        - Type: string
        - Default value: localhost
    - */software/components/metaconfig/graylog2/amqp_port*
        - Required
        - Type: long
        - Default value: 5672
    - */software/components/metaconfig/graylog2/amqp_username*
        - Required
        - Type: string
        - Default value: guest
    - */software/components/metaconfig/graylog2/amqp_password*
        - Required
        - Type: string
        - Default value: guest
    - */software/components/metaconfig/graylog2/amqp_virtualhost*
        - Required
        - Type: string
        - Default value: /
    - */software/components/metaconfig/graylog2/forwarder_loggly_timeout*
        - Required
        - Type: long
        - Default value: 3
