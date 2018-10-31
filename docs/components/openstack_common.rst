
Types
-----

 - `/software/openstack/type_storagebackend`
 - `/software/openstack/type_neutrondriver`
 - `/software/openstack/type_neutronextension`
 - `/software/openstack/openstack_domains_common`
    - Description: OpenStack common domains section
    - `/software/openstack/openstack_domains_common/project_domain_name`
        - Description: Domain name containing project
        - Optional
        - Type: string
    - `/software/openstack/openstack_domains_common/project_name`
        - Description: Project name to scope to
        - Optional
        - Type: string
    - `/software/openstack/openstack_domains_common/auth_type`
        - Description: The type of authentication credential to create.
    Required if no context is passed to the credential factory
        - Optional
        - Type: string
    - `/software/openstack/openstack_domains_common/user_domain_name`
        - Description: Users domain name
        - Optional
        - Type: string
    - `/software/openstack/openstack_domains_common/auth_url`
        - Description: Keystone authentication URL http(s)://host:port
        - Optional
        - Type: type_absoluteURI
    - `/software/openstack/openstack_domains_common/username`
        - Description: OpenStack service username
        - Optional
        - Type: string
    - `/software/openstack/openstack_domains_common/password`
        - Description: OpenStack service user password
        - Optional
        - Type: string
 - `/software/openstack/openstack_database`
    - Description: The configuration options in the database Section
    - `/software/openstack/openstack_database/connection`
        - Description: The SQLAlchemy connection string to use to connect to the database
        - Optional
        - Type: string
 - `/software/openstack/openstack_oslo_concurrency`
    - Description: The configuration options in 'oslo_concurrency' Section.
    - `/software/openstack/openstack_oslo_concurrency/lock_path`
        - Description: Directory to use for lock files.  For security, the specified directory should
    only be writable by the user running the processes that need locking. Defaults
    to environment variable OSLO_LOCK_PATH. If external locks are used, a lock
    path must be set
        - Optional
        - Type: absolute_file_path
 - `/software/openstack/openstack_DEFAULTS`
    - Description: The configuration options in the DEFAULTS Section
    - `/software/openstack/openstack_DEFAULTS/admin_token`
        - Description: Using this feature is *NOT* recommended. Instead, use the "keystone-manage
    bootstrap" command. The value of this option is treated as a "shared secret"
    that can be used to bootstrap Keystone through the API. This "token" does not
    represent a user (it has no identity), and carries no explicit authorization
    (it effectively bypasses most authorization checks). If set to "None", the
    value is ignored and the "admin_token" middleware is effectively disabled.
    However, to completely disable "admin_token" in production (highly
    recommended, as it presents a security risk), remove
    AdminTokenAuthMiddleware (the "admin_token_auth" filter) from your paste
    application pipelines (for example, in "keystone-paste.ini")
        - Optional
        - Type: string
    - `/software/openstack/openstack_DEFAULTS/notifications`
        - Optional
        - Type: string
    - `/software/openstack/openstack_DEFAULTS/debug`
        - Description: From oslo.log
    If set to true, the logging level will be set to DEBUG instead of the default
    INFO level.
    Note: This option can be changed without restarting
        - Optional
        - Type: boolean
    - `/software/openstack/openstack_DEFAULTS/use_syslog`
        - Description: Use syslog for logging. Existing syslog format is DEPRECATED and will be
    changed later to honor RFC5424. This option is ignored if log_config_append
    is set
        - Optional
        - Type: boolean
    - `/software/openstack/openstack_DEFAULTS/syslog_log_facility`
        - Description: Syslog facility to receive log lines. This option is ignored if
    log_config_append is set
        - Optional
        - Type: string
    - `/software/openstack/openstack_DEFAULTS/auth_strategy`
        - Description: From nova.conf
    This determines the strategy to use for authentication: keystone or noauth2.
    "noauth2" is designed for testing only, as it does no actual credential
    checking. "noauth2" provides administrative credentials only if "admin" is
    specified as the username
        - Optional
        - Type: string
    - `/software/openstack/openstack_DEFAULTS/my_ip`
        - Description: From nova.conf
    The IP address which the host is using to connect to the management network.
    Default is IPv4 address of this host
        - Optional
        - Type: type_ip
    - `/software/openstack/openstack_DEFAULTS/enabled_apis`
        - Description: From nova.conf
    List of APIs to be enabled by default
        - Optional
        - Type: string
    - `/software/openstack/openstack_DEFAULTS/transport_url`
        - Description: From nova.conf
    An URL representing the messaging driver to use and its full configuration.
    Example: rabbit://openstack:<rabbit_password>@<fqdn>
        - Optional
        - Type: string
    - `/software/openstack/openstack_DEFAULTS/rootwrap_config`
        - Description: Path to the rootwrap configuration file.

    Goal of the root wrapper is to allow a service-specific unprivileged user to
    run a number of actions as the root user in the safest manner possible.
    The configuration file used here must match the one defined in the sudoers
    entry.

    Be sure to include into sudoers these lines:
        nova ALL = (root) NOPASSWD: /usr/bin/nova-rootwrap /etc/nova/rootwrap.conf *
    more info https://wiki.openstack.org/wiki/Rootwrap
        - Optional
        - Type: absolute_file_path
    - `/software/openstack/openstack_DEFAULTS/core_plugin`
        - Description: From neutron.conf
    The core plugin Neutron will use
        - Optional
        - Type: string
    - `/software/openstack/openstack_DEFAULTS/service_plugins`
        - Description: From neutron.conf
    The service plugins Neutron will use
        - Optional
        - Type: string
    - `/software/openstack/openstack_DEFAULTS/allow_overlapping_ips`
        - Description: From neutron.conf
    Allow overlapping IP support in Neutron. Attention: the following parameter
    MUST be set to False if Neutron is being used in conjunction with Nova
    security groups
        - Optional
        - Type: boolean
    - `/software/openstack/openstack_DEFAULTS/notify_nova_on_port_status_changes`
        - Description: From neutron.conf
    Send notification to nova when port status changes
        - Optional
        - Type: boolean
    - `/software/openstack/openstack_DEFAULTS/notify_nova_on_port_data_changes`
        - Description: From neutron.conf
    Send notification to nova when port data (fixed_ips/floatingip) changes so
    nova can update its cache
        - Optional
        - Type: boolean
    - `/software/openstack/openstack_DEFAULTS/interface_driver`
        - Description: From Neutron l3_agent.ini and dhcp_agent.ini
    The driver used to manage the virtual interface
        - Optional
        - Type: string
    - `/software/openstack/openstack_DEFAULTS/dhcp_driver`
        - Description: From Neutron dhcp_agent.ini
    The driver used to manage the DHCP server
        - Optional
        - Type: string
    - `/software/openstack/openstack_DEFAULTS/enable_isolated_metadata`
        - Description: From Neutron dhcp_agent.ini
    The DHCP server can assist with providing metadata support on isolated
    networks. Setting this value to True will cause the DHCP server to append
    specific host routes to the DHCP request. The metadata service will only be
    activated when the subnet does not contain any router port. The guest
    instance must be configured to request host routes via DHCP (Option 121).
    This option does not have any effect when force_metadata is set to True
        - Optional
        - Type: boolean
    - `/software/openstack/openstack_DEFAULTS/nova_metadata_ip`
        - Description: From Neutron metadata_agent.ini
    IP address or hostname used by Nova metadata server
        - Optional
        - Type: string
    - `/software/openstack/openstack_DEFAULTS/metadata_proxy_shared_secret`
        - Description: From Neutron metadata_agent.ini
    When proxying metadata requests, Neutron signs the Instance-ID header with a
    shared secret to prevent spoofing. You may select any string for a secret,
    but it must match here and in the configuration used by the Nova Metadata
    Server. NOTE: Nova uses the same config key, but in [neutron] section.
        - Optional
        - Type: string
    - `/software/openstack/openstack_DEFAULTS/firewall_driver`
        - Description: Driver for security groups
        - Optional
        - Type: string
    - `/software/openstack/openstack_DEFAULTS/use_neutron`
        - Description: Use neutron and disable the default firewall setup
        - Optional
        - Type: boolean
 - `/software/openstack/openstack_rabbitmq_config`
    - Description: Type to enable RabbitMQ and the message system for OpenStack.
    - `/software/openstack/openstack_rabbitmq_config/user`
        - Description: RabbitMQ user to get access to the queue
        - Optional
        - Type: string
    - `/software/openstack/openstack_rabbitmq_config/password`
        - Optional
        - Type: string
    - `/software/openstack/openstack_rabbitmq_config/permissions`
        - Description: Set config/write/read permissions for RabbitMQ service.
    A regular expression matching resource names for
    which the user is granted configure permissions
        - Optional
        - Type: string
