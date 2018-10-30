
Types
-----

 - `/software/openstack/openstack_neutron_ml2`
    - Description: 
    The Neutron configuration options in ml2_conf.ini "ml2" Section.

    - `/software/openstack/openstack_neutron_ml2/type_drivers`
        - Description: WARNING: After you configure the ML2 plug-in,
    removing values in the type_drivers option can lead to database inconsistency
        - Optional
        - Type: type_neutrondriver
    - `/software/openstack/openstack_neutron_ml2/tenant_network_types`
        - Description: Ordered list of network_types to allocate as tenant networks. The default
    value "local" is useful for single-box testing but provides no connectivity
    between hosts
        - Optional
        - Type: type_neutrondriver
    - `/software/openstack/openstack_neutron_ml2/mechanism_drivers`
        - Description: An ordered list of networking mechanism driver entrypoints to be loaded from
    the neutron.ml2.mechanism_drivers namespace
        - Optional
        - Type: string
    - `/software/openstack/openstack_neutron_ml2/extension_drivers`
        - Description: An ordered list of extension driver entrypoints to be loaded from the
    neutron.ml2.extension_drivers namespace
        - Optional
        - Type: type_neutronextension
 - `/software/openstack/openstack_neutron_ml2_type_flat`
    - Description: 
    The Neutron configuration options in ml2_conf.ini "ml2_type_flat" Section.

    - `/software/openstack/openstack_neutron_ml2_type_flat/flat_networks`
        - Description: List of physical_network names with which flat networks can be created. Use
    default "*" to allow flat networks with arbitrary physical_network names. Use
    an empty list to disable flat networks
        - Optional
        - Type: string
 - `/software/openstack/openstack_neutron_ml2_type_vxlan`
    - Description: 
    The Neutron configuration options in ml2_conf.ini "ml2_type_vxlan" Section.

    - `/software/openstack/openstack_neutron_ml2_type_vxlan/vni_ranges`
        - Description: Configure the VXLAN network identifier range for self-service networks
        - Optional
        - Type: string
 - `/software/openstack/openstack_neutron_securitygroup`
    - Description: 
    The Neutron configuration options in ml2_conf.ini "securitygroup" Section.

    - `/software/openstack/openstack_neutron_securitygroup/enable_ipset`
        - Description: Use ipset to speed-up the iptables based security groups. Enabling ipset
    support requires that ipset is installed on L2 agent node
        - Optional
        - Type: boolean
    - `/software/openstack/openstack_neutron_securitygroup/enable_security_group`
        - Description: Controls whether the neutron security group API is enabled in the server. It
    should be false when using no security groups or using the nova security
    group API
        - Optional
        - Type: boolean
    - `/software/openstack/openstack_neutron_securitygroup/firewall_driver`
        - Description: Driver for security groups
        - Optional
        - Type: string
 - `/software/openstack/openstack_neutron_vxlan`
    - Description: 
    The Neutron configuration options in linuxbridge_agent.ini "vxlan" Section.

    - `/software/openstack/openstack_neutron_vxlan/enable_vxlan`
        - Description: Enable VXLAN on the agent. Can be enabled when agent is managed by ml2 plugin
    using linuxbridge mechanism driver
        - Optional
        - Type: boolean
    - `/software/openstack/openstack_neutron_vxlan/local_ip`
        - Description: IP address of local overlay (tunnel) network endpoint. Use either an IPv4 or
    IPv6 address that resides on one of the host network interfaces. The IP
    version of this value must match the value of the 'overlay_ip_version' option
    in the ML2 plug-in configuration file on the neutron server node(s)
        - Optional
        - Type: type_ip
    - `/software/openstack/openstack_neutron_vxlan/l2_population`
        - Description: Extension to use alongside ml2 plugins l2population mechanism driver. It
    enables the plugin to populate VXLAN forwarding table
        - Optional
        - Type: boolean
 - `/software/openstack/openstack_neutron_linux_bridge`
    - Description: 
    The Neutron configuration options in linuxbridge_agent.ini "linux_bridge" Section.

    - `/software/openstack/openstack_neutron_linux_bridge/physical_interface_mappings`
        - Description: Comma-separated list of <physical_network>:<physical_interface> tuples
    mapping physical network names to the agents node-specific physical network
    interfaces to be used for flat and VLAN networks. All physical networks
    listed in network_vlan_ranges on the server should have mappings to
    appropriate interfaces on each agent.
    https://docs.openstack.org/ocata/install-guide-rdo/environment-networking.html
        - Optional
        - Type: string
 - `/software/openstack/openstack_neutron_common`
    - Description: 
    list of Neutron common configuration sections

    - `/software/openstack/openstack_neutron_common/DEFAULT`
        - Optional
        - Type: openstack_DEFAULTS
    - `/software/openstack/openstack_neutron_common/keystone_authtoken`
        - Optional
        - Type: openstack_keystone_authtoken
    - `/software/openstack/openstack_neutron_common/oslo_concurrency`
        - Optional
        - Type: openstack_oslo_concurrency
 - `/software/openstack/openstack_neutron_ml2_config`
    - `/software/openstack/openstack_neutron_ml2_config/ml2`
        - Optional
        - Type: openstack_neutron_ml2
    - `/software/openstack/openstack_neutron_ml2_config/ml2_type_flat`
        - Optional
        - Type: openstack_neutron_ml2_type_flat
    - `/software/openstack/openstack_neutron_ml2_config/ml2_type_vxlan`
        - Optional
        - Type: openstack_neutron_ml2_type_vxlan
    - `/software/openstack/openstack_neutron_ml2_config/securitygroup`
        - Optional
        - Type: openstack_neutron_securitygroup
 - `/software/openstack/openstack_neutron_linuxbridge_config`
    - `/software/openstack/openstack_neutron_linuxbridge_config/linux_bridge`
        - Optional
        - Type: openstack_neutron_linux_bridge
    - `/software/openstack/openstack_neutron_linuxbridge_config/vxlan`
        - Optional
        - Type: openstack_neutron_vxlan
    - `/software/openstack/openstack_neutron_linuxbridge_config/securitygroup`
        - Optional
        - Type: openstack_neutron_securitygroup
 - `/software/openstack/openstack_neutron_l3_config`
    - `/software/openstack/openstack_neutron_l3_config/DEFAULT`
        - Optional
        - Type: openstack_DEFAULTS
 - `/software/openstack/openstack_neutron_dhcp_config`
    - `/software/openstack/openstack_neutron_dhcp_config/DEFAULT`
        - Optional
        - Type: openstack_DEFAULTS
 - `/software/openstack/openstack_neutron_metadata_config`
    - `/software/openstack/openstack_neutron_metadata_config/DEFAULT`
        - Optional
        - Type: openstack_DEFAULTS
 - `/software/openstack/openstack_neutron_service_config`
    - Description: 
    list of Neutron service configuration sections

    - `/software/openstack/openstack_neutron_service_config/database`
        - Optional
        - Type: openstack_database
    - `/software/openstack/openstack_neutron_service_config/nova`
        - Description: nova section has the same options than "keystone_authtoken" but with the nova user and passwod
        - Optional
        - Type: openstack_domains_common
 - `/software/openstack/openstack_neutron_config`
    - Description: 
    list of Neutron service configuration sections

    - `/software/openstack/openstack_neutron_config/service`
        - Optional
        - Type: openstack_neutron_service_config
    - `/software/openstack/openstack_neutron_config/ml2`
        - Optional
        - Type: openstack_neutron_ml2_config
    - `/software/openstack/openstack_neutron_config/linuxbridge`
        - Optional
        - Type: openstack_neutron_linuxbridge_config
    - `/software/openstack/openstack_neutron_config/l3`
        - Optional
        - Type: openstack_neutron_l3_config
    - `/software/openstack/openstack_neutron_config/dhcp`
        - Optional
        - Type: openstack_neutron_dhcp_config
    - `/software/openstack/openstack_neutron_config/metadata`
        - Optional
        - Type: openstack_neutron_metadata_config
