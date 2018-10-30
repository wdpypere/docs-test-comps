
Types
-----

 - `/software/openstack/openstack_keystone_token`
    - Description: 
    The Keystone "token" configuration section

    - `/software/openstack/openstack_keystone_token/provider`
        - Description: Entry point for the token provider in the "keystone.token.provider"
    namespace. The token provider controls the token construction, validation,
    and revocation operations. Keystone includes "fernet" and "uuid" token
    providers. "uuid" tokens must be persisted (using the backend specified in
    the "[token] driver" option), but do not require any extra configuration or
    setup. "fernet" tokens do not need to be persisted at all, but require that
    you run "keystone-manage fernet_setup" (also see the "keystone-manage
    fernet_rotate" command)
        - Optional
        - Type: string
    - `/software/openstack/openstack_keystone_token/driver`
        - Description: Entry point for the token persistence backend driver in the
    "keystone.token.persistence" namespace. Keystone provides "kvs" and "sql"
    drivers. The "kvs" backend depends on the configuration in the "[kvs]"
    section. The "sql" option (default) depends on the options in your
    "[database]" section. If you are using the "fernet" "[token] provider", this
    backend will not be utilized to persist tokens at all. (string value)
        - Optional
        - Type: string
 - `/software/openstack/openstack_keystone_authtoken`
    - Description: 
    The Keystone configuration options in the "authtoken" Section

    - `/software/openstack/openstack_keystone_authtoken/auth_uri`
        - Description: Complete "public" Identity API endpoint. This endpoint should not be an
    "admin" endpoint, as it should be accessible by all end users. Unauthenticated
    clients are redirected to this endpoint to authenticate. Although this
    endpoint should  ideally be unversioned, client support in the wild varies.
    If you are using a versioned v2 endpoint here, then this  should *not* be the
    same endpoint the service user utilizes  for validating tokens, because normal
    end users may not be  able to reach that endpoint. http(s)://host:port
        - Optional
        - Type: type_absoluteURI
    - `/software/openstack/openstack_keystone_authtoken/memcached_servers`
        - Description: Optionally specify a list of memcached server(s) to use for caching. If left
    undefined, tokens will instead be cached in-process ("host:port" list)
        - Optional
        - Type: type_hostport
 - `/software/openstack/openstack_keystone_paste_deploy`
    - Description: 
    The Keystone configuration options in the "paste_deploy" Section.

    - `/software/openstack/openstack_keystone_paste_deploy/flavor`
        - Description: Deployment flavor to use in the server application pipeline.
    Provide a string value representing the appropriate deployment
    flavor used in the server application pipleline. This is typically
    the partial name of a pipeline in the paste configuration file with
    the service name removed.

    For example, if your paste section name in the paste configuration
    file is [pipeline:glance-api-keystone], set "flavor" to
    "keystone"
        - Optional
        - Type: string
 - `/software/openstack/openstack_openrc_config`
    - Description: 
Type that sets the OpenStack OpenRC script configuration

    - `/software/openstack/openstack_openrc_config/os_username`
        - Optional
        - Type: string
    - `/software/openstack/openstack_openrc_config/os_password`
        - Optional
        - Type: string
    - `/software/openstack/openstack_openrc_config/os_project_name`
        - Optional
        - Type: string
    - `/software/openstack/openstack_openrc_config/os_user_domain_name`
        - Optional
        - Type: string
    - `/software/openstack/openstack_openrc_config/os_project_domain_name`
        - Optional
        - Type: string
    - `/software/openstack/openstack_openrc_config/os_region_name`
        - Optional
        - Type: string
    - `/software/openstack/openstack_openrc_config/os_auth_url`
        - Optional
        - Type: type_absoluteURI
    - `/software/openstack/openstack_openrc_config/os_identity_api_version`
        - Optional
        - Type: long
        - Range: 1..
    - `/software/openstack/openstack_openrc_config/os_image_api_version`
        - Optional
        - Type: long
        - Range: 1..
 - `/software/openstack/openstack_keystone_config`
    - Description: 
    The Keystone configuration sections

    - `/software/openstack/openstack_keystone_config/DEFAULT`
        - Optional
        - Type: openstack_DEFAULTS
    - `/software/openstack/openstack_keystone_config/database`
        - Optional
        - Type: openstack_database
    - `/software/openstack/openstack_keystone_config/token`
        - Optional
        - Type: openstack_keystone_token
