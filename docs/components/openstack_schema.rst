
Types
-----

 - `/software/openstack/openstack_identity_config`
    - Description: 
Type to define OpenStack identity services

    - `/software/openstack/openstack_identity_config/keystone`
        - Optional
        - Type: openstack_keystone_config
 - `/software/openstack/openstack_storage_config`
    - Description: 
Type to define OpenStack storage services

    - `/software/openstack/openstack_storage_config/glance`
        - Optional
        - Type: openstack_glance_config
 - `/software/openstack/openstack_compute_config`
    - Description: 
Type to define OpenStack compute services

    - `/software/openstack/openstack_compute_config/nova`
        - Optional
        - Type: openstack_nova_config
 - `/software/openstack/openstack_network_config`
    - Description: 
Type to define OpenStack network services

    - `/software/openstack/openstack_network_config/neutron`
        - Optional
        - Type: openstack_neutron_config
 - `/software/openstack/openstack_dashboard_config`
    - Description: 
Type to define OpenStack dashboard services

    - `/software/openstack/openstack_dashboard_config/horizon`
        - Optional
        - Type: openstack_horizon_config
 - `/software/openstack/openstack_messaging_config`
    - Description: 
Type to define OpenStack messaging services

    - `/software/openstack/openstack_messaging_config/rabbitmq`
        - Optional
        - Type: openstack_rabbitmq_config
 - `/software/openstack/openstack_hypervisor_config`
    - Description: 
Hyperviosr configuration.

 - `/software/openstack/openstack_component`
    - Description: 
Type to define OpenStack services
Keystone, Nova, Neutron, etc

    - `/software/openstack/openstack_component/identity`
        - Optional
        - Type: openstack_identity_config
    - `/software/openstack/openstack_component/compute`
        - Optional
        - Type: openstack_compute_config
    - `/software/openstack/openstack_component/storage`
        - Optional
        - Type: openstack_storage_config
    - `/software/openstack/openstack_component/network`
        - Optional
        - Type: openstack_network_config
    - `/software/openstack/openstack_component/dashboard`
        - Optional
        - Type: openstack_dashboard_config
    - `/software/openstack/openstack_component/messaging`
        - Optional
        - Type: openstack_messaging_config
    - `/software/openstack/openstack_component/openrc`
        - Optional
        - Type: openstack_openrc_config
    - `/software/openstack/openstack_component/hypervisor`
        - Description: Hypervisor configuration. Host is a hypervisor when this attribute exists
        - Optional
        - Type: openstack_hypervisor_config
