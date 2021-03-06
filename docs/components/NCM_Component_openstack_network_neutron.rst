###############################################
NCM\::Component\::openstack\::network - neutron
###############################################

Types
-----

 - **/software/components/openstack/openstack_neutron_ml2**
    - Description: The Neutron configuration options in ml2_conf.ini "ml2" Section.
    - */software/components/openstack/openstack_neutron_ml2/type_drivers*
        - Description: WARNING: After you configure the ML2 plug-in, removing values in the type_drivers option can lead to database inconsistency
        - Required
        - Type: openstack_neutrondriver
    - */software/components/openstack/openstack_neutron_ml2/tenant_network_types*
        - Description: Ordered list of network_types to allocate as tenant networks. The default value "local" is useful for single-box testing but provides no connectivity between hosts
        - Required
        - Type: openstack_neutrondriver
    - */software/components/openstack/openstack_neutron_ml2/mechanism_drivers*
        - Description: An ordered list of networking mechanism driver entrypoints to be loaded from the neutron.ml2.mechanism_drivers namespace
        - Required
        - Type: openstack_neutron_mechanism_drivers
    - */software/components/openstack/openstack_neutron_ml2/extension_drivers*
        - Description: An ordered list of extension driver entrypoints to be loaded from the neutron.ml2.extension_drivers namespace
        - Required
        - Type: openstack_neutronextension
 - **/software/components/openstack/openstack_neutron_ml2_type_flat**
    - Description: The Neutron configuration options in ml2_conf.ini "ml2_type_flat" Section.
    - */software/components/openstack/openstack_neutron_ml2_type_flat/flat_networks*
        - Description: List of physical_network names with which flat networks can be created. Use default "*" to allow flat networks with arbitrary physical_network names. Use an empty list to disable flat networks
        - Required
        - Type: string
 - **/software/components/openstack/openstack_neutron_ml2_type_vxlan**
    - Description: The Neutron configuration options in ml2_conf.ini "ml2_type_vxlan" Section.
    - */software/components/openstack/openstack_neutron_ml2_type_vxlan/vni_ranges*
        - Description: Configure the VXLAN network identifier range for self-service networks
        - Required
        - Type: string
        - Default value: 1:1000
 - **/software/components/openstack/openstack_neutron_ml2_type_vlan**
    - Description: The Neutron configuration options in ml2_conf.ini "ml2_type_vlan" Section.
    - */software/components/openstack/openstack_neutron_ml2_type_vlan/network_vlan_ranges*
        - Description: List of <physical_network>:<vlan_min>:<vlan_max> or <physical_network> specifying physical_network names usable for VLAN provider and tenant networks, as well as ranges of VLAN tags on each available for allocation to tenant networks
        - Required
        - Type: string
 - **/software/components/openstack/openstack_neutron_securitygroup**
    - Description: The Neutron configuration options in ml2_conf.ini "securitygroup" Section.
    - */software/components/openstack/openstack_neutron_securitygroup/enable_ipset*
        - Description: Use ipset to speed-up the iptables based security groups. Enabling ipset support requires that ipset is installed on L2 agent node
        - Optional
        - Type: boolean
        - Default value: true
    - */software/components/openstack/openstack_neutron_securitygroup/enable_security_group*
        - Description: Controls whether the neutron security group API is enabled in the server. It should be false when using no security groups or using the nova security group API
        - Optional
        - Type: boolean
        - Default value: true
    - */software/components/openstack/openstack_neutron_securitygroup/firewall_driver*
        - Description: Driver for security groups
        - Optional
        - Type: openstack_neutron_firewall_driver
        - Default value: neutron.agent.linux.iptables_firewall.IptablesFirewallDriver
 - **/software/components/openstack/openstack_neutron_vxlan**
    - Description: The Neutron configuration options in linuxbridge_agent.ini "vxlan" Section.
    - */software/components/openstack/openstack_neutron_vxlan/enable_vxlan*
        - Description: Enable VXLAN on the agent. Can be enabled when agent is managed by ml2 plugin using linuxbridge mechanism driver
        - Optional
        - Type: boolean
        - Default value: true
    - */software/components/openstack/openstack_neutron_vxlan/local_ip*
        - Description: IP address of local overlay (tunnel) network endpoint. Use either an IPv4 or IPv6 address that resides on one of the host network interfaces. The IP version of this value must match the value of the 'overlay_ip_version' option in the ML2 plug-in configuration file on the neutron server node(s)
        - Required
        - Type: type_ip
    - */software/components/openstack/openstack_neutron_vxlan/l2_population*
        - Description: Extension to use alongside ml2 plugins l2population mechanism driver. It enables the plugin to populate VXLAN forwarding table
        - Optional
        - Type: boolean
        - Default value: true
 - **/software/components/openstack/openstack_neutron_linux_bridge**
    - Description: The Neutron configuration options in linuxbridge_agent.ini "linux_bridge" Section.
    - */software/components/openstack/openstack_neutron_linux_bridge/physical_interface_mappings*
        - Description: Comma-separated list of <physical_network>:<physical_interface> tuples mapping physical network names to the agents node-specific physical network interfaces to be used for flat and VLAN networks. All physical networks listed in network_vlan_ranges on the server should have mappings to appropriate interfaces on each agent. https://docs.openstack.org/ocata/install-guide-rdo/environment-networking.html
        - Required
        - Type: string
 - **/software/components/openstack/openstack_neutron_ovs**
    - Description: The Neutron configuration options in openvswitch_agent.ini "ovs" Section.
    - */software/components/openstack/openstack_neutron_ovs/bridge_mappings*
        - Description: Comma-separated list of <physical_network>:<bridge> tuples mapping physical network names to the agents node-specific Open vSwitch bridge names to be used for flat and VLAN networks. The length of bridge names should be no more than 11. Each bridge must exist, and should have a physical network interface configured as a port. All physical networks configured on the server should have mappings to appropriate bridges on each agent. Note: If you remove a bridge from this mapping, make sure to disconnect it from the integration bridge as it wont be managed by the agent anymore
        - Required
        - Type: string
 - **/software/components/openstack/openstack_neutron_agent**
    - Description: The Neutron configuration options in openvswitch_agent.ini "agent" Section.
    - */software/components/openstack/openstack_neutron_agent/l2_population*
        - Description: Extension to use alongside ml2 plugins l2population mechanism driver. It enables the plugin to populate VXLAN forwarding table
        - Required
        - Type: boolean
        - Default value: true
    - */software/components/openstack/openstack_neutron_agent/tunnel_types*
        - Description: Network types supported by the agent (gre and/or vxlan)
        - Required
        - Type: openstack_tunnel_types
 - **/software/components/openstack/openstack_neutron_common**
    - Description: list of Neutron common configuration sections
    - */software/components/openstack/openstack_neutron_common/DEFAULT*
        - Required
        - Type: openstack_DEFAULTS
    - */software/components/openstack/openstack_neutron_common/keystone_authtoken*
        - Required
        - Type: openstack_keystone_authtoken
    - */software/components/openstack/openstack_neutron_common/oslo_concurrency*
        - Required
        - Type: openstack_oslo_concurrency
 - **/software/components/openstack/openstack_neutron_ml2_config**
    - */software/components/openstack/openstack_neutron_ml2_config/ml2*
        - Required
        - Type: openstack_neutron_ml2
    - */software/components/openstack/openstack_neutron_ml2_config/ml2_type_flat*
        - Optional
        - Type: openstack_neutron_ml2_type_flat
    - */software/components/openstack/openstack_neutron_ml2_config/ml2_type_vxlan*
        - Optional
        - Type: openstack_neutron_ml2_type_vxlan
    - */software/components/openstack/openstack_neutron_ml2_config/ml2_type_vlan*
        - Optional
        - Type: openstack_neutron_ml2_type_vlan
    - */software/components/openstack/openstack_neutron_ml2_config/securitygroup*
        - Optional
        - Type: openstack_neutron_securitygroup
 - **/software/components/openstack/openstack_neutron_linuxbridge_config**
    - */software/components/openstack/openstack_neutron_linuxbridge_config/linux_bridge*
        - Required
        - Type: openstack_neutron_linux_bridge
    - */software/components/openstack/openstack_neutron_linuxbridge_config/vxlan*
        - Optional
        - Type: openstack_neutron_vxlan
    - */software/components/openstack/openstack_neutron_linuxbridge_config/securitygroup*
        - Optional
        - Type: openstack_neutron_securitygroup
 - **/software/components/openstack/openstack_neutron_openvswitch_config**
    - */software/components/openstack/openstack_neutron_openvswitch_config/ovs*
        - Required
        - Type: openstack_neutron_ovs
    - */software/components/openstack/openstack_neutron_openvswitch_config/securitygroup*
        - Optional
        - Type: openstack_neutron_securitygroup
    - */software/components/openstack/openstack_neutron_openvswitch_config/agent*
        - Optional
        - Type: openstack_neutron_agent
 - **/software/components/openstack/openstack_neutron_l3_config**
    - */software/components/openstack/openstack_neutron_l3_config/DEFAULT*
        - Required
        - Type: openstack_DEFAULTS
 - **/software/components/openstack/openstack_neutron_dhcp_config**
    - */software/components/openstack/openstack_neutron_dhcp_config/DEFAULT*
        - Required
        - Type: openstack_DEFAULTS
 - **/software/components/openstack/openstack_neutron_metadata_config**
    - */software/components/openstack/openstack_neutron_metadata_config/DEFAULT*
        - Required
        - Type: openstack_DEFAULTS
 - **/software/components/openstack/openstack_neutron_nova**
    - Description: Neutron nova section
    - */software/components/openstack/openstack_neutron_nova/endpoint_type*
        - Description: Type of the nova endpoint to use. This endpoint will be looked up in the keystone catalog and should be one of public, internal or admin
        - Required
        - Type: choice
        - Default value: internal
 - **/software/components/openstack/openstack_neutron_service_config**
    - Description: list of Neutron service configuration sections
    - */software/components/openstack/openstack_neutron_service_config/database*
        - Optional
        - Type: openstack_database
    - */software/components/openstack/openstack_neutron_service_config/nova*
        - Description: nova section has the same options than "keystone_authtoken" but with the nova user and passwod
        - Optional
        - Type: openstack_neutron_nova
 - **/software/components/openstack/openstack_quattor_neutron**
 - **/software/components/openstack/openstack_neutron_config**
    - Description: list of Neutron service configuration sections
    - */software/components/openstack/openstack_neutron_config/service*
        - Optional
        - Type: openstack_neutron_service_config
    - */software/components/openstack/openstack_neutron_config/ml2*
        - Optional
        - Type: openstack_neutron_ml2_config
    - */software/components/openstack/openstack_neutron_config/linuxbridge*
        - Optional
        - Type: openstack_neutron_linuxbridge_config
    - */software/components/openstack/openstack_neutron_config/openvswitch*
        - Optional
        - Type: openstack_neutron_openvswitch_config
    - */software/components/openstack/openstack_neutron_config/l3*
        - Optional
        - Type: openstack_neutron_l3_config
    - */software/components/openstack/openstack_neutron_config/dhcp*
        - Optional
        - Type: openstack_neutron_dhcp_config
    - */software/components/openstack/openstack_neutron_config/metadata*
        - Optional
        - Type: openstack_neutron_metadata_config
    - */software/components/openstack/openstack_neutron_config/quattor*
        - Required
        - Type: openstack_quattor_neutron
