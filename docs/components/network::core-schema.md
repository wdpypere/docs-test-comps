
### Types

 - `/software/network/structure_route`
    - Description: 
    Add route (IPv4 of IPv6)
    Presence of ':' in any of the values indicates this is IPv6 related.

    - `/software/network/structure_route/address`
        - Description: The ADDRESS in ADDRESS/PREFIX via GATEWAY
        - Optional
        - Type: type_ip
    - `/software/network/structure_route/prefix`
        - Description: The PREFIX in ADDRESS/PREFIX via GATEWAY
        - Optional
        - Type: long
    - `/software/network/structure_route/gateway`
        - Description: The GATEWAY in ADDRESS/PREFIX via GATEWAY
        - Optional
        - Type: type_ip
    - `/software/network/structure_route/netmask`
        - Description: alternative notation for prefix (cannot be combined with prefix)
        - Optional
        - Type: type_ip
    - `/software/network/structure_route/command`
        - Description: route add command options to use (cannot be combined with other options)
        - Optional
        - Type: string
 - `/software/network/structure_rule`
    - Description: 
    Add rule (IPv4 of IPv6)
    Presence of ':' in any of the values indicates this is IPv6 related.

    - `/software/network/structure_rule/command`
        - Description: rule add options to use (cannot be combined with other options)
        - Optional
        - Type: string
 - `/software/network/structure_interface_alias`
    - Description: 
    Interface alias

    - `/software/network/structure_interface_alias/ip`
        - Optional
        - Type: type_ip
    - `/software/network/structure_interface_alias/netmask`
        - Optional
        - Type: type_ip
    - `/software/network/structure_interface_alias/broadcast`
        - Optional
        - Type: type_ip
    - `/software/network/structure_interface_alias/fqdn`
        - Optional
        - Type: type_fqdn
 - `/software/network/structure_bonding_options`
    - Description: 
    Describes the bonding options for configuring channel bonding on EL5 and similar.

    - `/software/network/structure_bonding_options/mode`
        - Optional
        - Type: long
        - Range: 0..6
    - `/software/network/structure_bonding_options/miimon`
        - Optional
        - Type: long
    - `/software/network/structure_bonding_options/updelay`
        - Optional
        - Type: long
    - `/software/network/structure_bonding_options/downdelay`
        - Optional
        - Type: long
    - `/software/network/structure_bonding_options/primary`
        - Optional
        - Type: valid_interface
    - `/software/network/structure_bonding_options/lacp_rate`
        - Optional
        - Type: long
        - Range: 0..1
    - `/software/network/structure_bonding_options/xmit_hash_policy`
        - Optional
        - Type: string
 - `/software/network/structure_bridging_options`
    - Description: 
    describes the bridging options
    (the parameters for /sys/class/net/<br>/brport)

    - `/software/network/structure_bridging_options/bpdu_guard`
        - Optional
        - Type: long
    - `/software/network/structure_bridging_options/flush`
        - Optional
        - Type: long
    - `/software/network/structure_bridging_options/hairpin_mode`
        - Optional
        - Type: long
    - `/software/network/structure_bridging_options/multicast_fast_leave`
        - Optional
        - Type: long
    - `/software/network/structure_bridging_options/multicast_router`
        - Optional
        - Type: long
    - `/software/network/structure_bridging_options/path_cost`
        - Optional
        - Type: long
    - `/software/network/structure_bridging_options/priority`
        - Optional
        - Type: long
    - `/software/network/structure_bridging_options/root_block`
        - Optional
        - Type: long
 - `/software/network/structure_ethtool_offload`
    - Description: 
    interface ethtool offload

    - `/software/network/structure_ethtool_offload/rx`
        - Optional
        - Type: string
    - `/software/network/structure_ethtool_offload/tx`
        - Optional
        - Type: string
    - `/software/network/structure_ethtool_offload/tso`
        - Description: Set the TCP segment offload parameter to "off" or "on"
        - Optional
        - Type: string
    - `/software/network/structure_ethtool_offload/gro`
        - Optional
        - Type: string
 - `/software/network/structure_ethtool_ring`
    - Description: 
    Set the ethernet transmit or receive buffer ring counts.
    See ethtool --show-ring for the values.

    - `/software/network/structure_ethtool_ring/rx`
        - Optional
        - Type: long
    - `/software/network/structure_ethtool_ring/tx`
        - Optional
        - Type: long
    - `/software/network/structure_ethtool_ring/rx-mini`
        - Optional
        - Type: long
    - `/software/network/structure_ethtool_ring/rx-jumbo`
        - Optional
        - Type: long
 - `/software/network/structure_ethtool_wol`
    - Description: 
    ethtool wol p|u|m|b|a|g|s|d...
    from the man page
        Sets Wake-on-LAN options.  Not all devices support this.  The argument to this option is a string
        of characters specifying which options to enable.
            p  Wake on phy activity
            u  Wake on unicast messages
            m  Wake on multicast messages
            b  Wake on broadcast messages
            a  Wake on ARP
            g  Wake on MagicPacket(tm)
            s  Enable SecureOn(tm) password for MagicPacket(tm)
            d  Disable (wake on nothing).  This option clears all previous option

 - `/software/network/structure_ethtool`
    - Description: 
    ethtool

    - `/software/network/structure_ethtool/wol`
        - Optional
        - Type: structure_ethtool_wol
    - `/software/network/structure_ethtool/autoneg`
        - Optional
        - Type: string
    - `/software/network/structure_ethtool/duplex`
        - Optional
        - Type: string
    - `/software/network/structure_ethtool/speed`
        - Optional
        - Type: long
 - `/software/network/structure_interface_plugin_vxlan`
    - Description: 
    interface plugin for vxlan support via initscripts-vxlan

    - `/software/network/structure_interface_plugin_vxlan/vni`
        - Description: VXLAN Network Identifier (or VXLAN Segment ID); derived from devicename vxlan[0-9] if not defined
        - Optional
        - Type: long
        - Range: 0..16777216
    - `/software/network/structure_interface_plugin_vxlan/group`
        - Description: multicast ip to join
        - Optional
        - Type: type_ip
    - `/software/network/structure_interface_plugin_vxlan/remote`
        - Description: destination IP address to use in outgoing packets
        - Optional
        - Type: type_ip
    - `/software/network/structure_interface_plugin_vxlan/local`
        - Description: source IP address to use in outgoing packets
        - Optional
        - Type: type_ip
    - `/software/network/structure_interface_plugin_vxlan/dstport`
        - Description: UDP destination port
        - Optional
        - Type: long
        - Range: 2..65535
    - `/software/network/structure_interface_plugin_vxlan/gbp`
        - Description: Group Policy extension
        - Optional
        - Type: boolean
 - `/software/network/structure_interface_plugin`
    - Description: 
    interface plugin via custom ifup/down[-pre]-local hooks

    - `/software/network/structure_interface_plugin/vxlan`
        - Description: VXLAN support via initscripts-vxlan
        - Optional
        - Type: structure_interface_plugin_vxlan
 - `/software/network/structure_interface`
    - Description: 
    interface

    - `/software/network/structure_interface/ip`
        - Optional
        - Type: type_ip
    - `/software/network/structure_interface/gateway`
        - Optional
        - Type: type_ip
    - `/software/network/structure_interface/netmask`
        - Optional
        - Type: type_ip
    - `/software/network/structure_interface/broadcast`
        - Optional
        - Type: type_ip
    - `/software/network/structure_interface/driver`
        - Optional
        - Type: string
    - `/software/network/structure_interface/bootproto`
        - Optional
        - Type: string
    - `/software/network/structure_interface/onboot`
        - Optional
        - Type: boolean
    - `/software/network/structure_interface/type`
        - Optional
        - Type: string
    - `/software/network/structure_interface/device`
        - Optional
        - Type: string
    - `/software/network/structure_interface/master`
        - Optional
        - Type: string
    - `/software/network/structure_interface/mtu`
        - Optional
        - Type: long
    - `/software/network/structure_interface/route`
        - Description: Routes for this interface.
      These values are used to generate the /etc/sysconfig/network-scripts/route[6]-<interface> files
      as used by ifup-routes when using ncm-network.
      This allows for mixed IPv4 and IPv6 configuration
        - Optional
        - Type: structure_route
    - `/software/network/structure_interface/rule`
        - Description: Rules for this interface.
      These values are used to generate the /etc/sysconfig/network-scripts/rule[6]-<interface> files
      as used by ifup-routes when using ncm-network.
      This allows for mixed IPv4 and IPv6 configuration
        - Optional
        - Type: structure_rule
    - `/software/network/structure_interface/aliases`
        - Description: Aliases for this interface.
      These values are used to generate the /etc/sysconfig/network-scripts/ifcfg-<interface>:<key> files
      as used by ifup-aliases when using ncm-network.
        - Optional
        - Type: structure_interface_alias
    - `/software/network/structure_interface/set_hwaddr`
        - Description: Explicitly set the MAC address. The MAC address is taken from /hardware/cards/nic/<interface>/hwaddr.
        - Optional
        - Type: boolean
    - `/software/network/structure_interface/bridge`
        - Optional
        - Type: valid_interface
    - `/software/network/structure_interface/bonding_opts`
        - Optional
        - Type: structure_bonding_options
    - `/software/network/structure_interface/offload`
        - Optional
        - Type: structure_ethtool_offload
    - `/software/network/structure_interface/ring`
        - Optional
        - Type: structure_ethtool_ring
    - `/software/network/structure_interface/ethtool`
        - Optional
        - Type: structure_ethtool
    - `/software/network/structure_interface/vlan`
        - Description: Is a VLAN device. If the device name starts with vlan, this is always true.
        - Optional
        - Type: boolean
    - `/software/network/structure_interface/physdev`
        - Description: If the device name starts with vlan, this has to be set.
      It is set (but ignored by ifup) if it the device is not named vlan
        - Optional
        - Type: valid_interface
    - `/software/network/structure_interface/fqdn`
        - Optional
        - Type: string
    - `/software/network/structure_interface/network_environment`
        - Optional
        - Type: string
    - `/software/network/structure_interface/network_type`
        - Optional
        - Type: string
    - `/software/network/structure_interface/nmcontrolled`
        - Optional
        - Type: boolean
    - `/software/network/structure_interface/defroute`
        - Description: Set DEFROUTE, is the default for ipv6_defroute
        - Optional
        - Type: boolean
    - `/software/network/structure_interface/linkdelay`
        - Optional
        - Type: long
    - `/software/network/structure_interface/stp`
        - Optional
        - Type: boolean
    - `/software/network/structure_interface/delay`
        - Optional
        - Type: long
    - `/software/network/structure_interface/bridging_opts`
        - Optional
        - Type: structure_bridging_options
    - `/software/network/structure_interface/bond_ifaces`
        - Optional
        - Type: string
    - `/software/network/structure_interface/ovs_bridge`
        - Optional
        - Type: valid_interface
    - `/software/network/structure_interface/ovs_extra`
        - Optional
        - Type: string
    - `/software/network/structure_interface/ovs_opts`
        - Optional
        - Type: string
    - `/software/network/structure_interface/ovs_patch_peer`
        - Optional
        - Type: string
    - `/software/network/structure_interface/ovs_tunnel_opts`
        - Optional
        - Type: string
    - `/software/network/structure_interface/ovs_tunnel_type`
        - Optional
        - Type: string
    - `/software/network/structure_interface/ipv4_failure_fatal`
        - Optional
        - Type: boolean
    - `/software/network/structure_interface/ipv6_autoconf`
        - Optional
        - Type: boolean
    - `/software/network/structure_interface/ipv6_failure_fatal`
        - Optional
        - Type: boolean
    - `/software/network/structure_interface/ipv6_mtu`
        - Optional
        - Type: long
        - Range: 1280..65536
    - `/software/network/structure_interface/ipv6_privacy`
        - Optional
        - Type: string
    - `/software/network/structure_interface/ipv6_rtr`
        - Optional
        - Type: boolean
    - `/software/network/structure_interface/ipv6_defroute`
        - Description: Set IPV6_DEFROUTE, defaults to defroute value
        - Optional
        - Type: boolean
    - `/software/network/structure_interface/ipv6addr`
        - Optional
        - Type: type_network_name
    - `/software/network/structure_interface/ipv6addr_secondaries`
        - Optional
        - Type: type_network_name
    - `/software/network/structure_interface/ipv6init`
        - Optional
        - Type: boolean
    - `/software/network/structure_interface/plugin`
        - Optional
        - Type: structure_interface_plugin
 - `/software/network/structure_router`
    - Description: 
    router

 - `/software/network/structure_ipv6`
    - Description: 
    IPv6 global settings

    - `/software/network/structure_ipv6/enabled`
        - Optional
        - Type: boolean
    - `/software/network/structure_ipv6/default_gateway`
        - Optional
        - Type: type_ip
    - `/software/network/structure_ipv6/gatewaydev`
        - Optional
        - Type: valid_interface
 - `/software/network/structure_network`
    - Description: 
    Host network configuration

    These values are used to generate /etc/sysconfig/network
    when using ncm-network (unless specified otherwise).

    - `/software/network/structure_network/domainname`
        - Optional
        - Type: type_fqdn
    - `/software/network/structure_network/hostname`
        - Optional
        - Type: type_shorthostname
    - `/software/network/structure_network/realhostname`
        - Optional
        - Type: type_fqdn
    - `/software/network/structure_network/default_gateway`
        - Optional
        - Type: type_ip
    - `/software/network/structure_network/guess_default_gateway`
        - Description: When default_gateway is not set, the component will try to guess the default
      gateway using the first configured gateway set on an interface.
      The default is true for backward compatible behaviour.
        - Optional
        - Type: boolean
    - `/software/network/structure_network/gatewaydev`
        - Optional
        - Type: valid_interface
    - `/software/network/structure_network/interfaces`
        - Description: Per interface network settings.
      These values are used to generate the /etc/sysconfig/network-scripts/ifcfg-<interface> files
      when using ncm-network.
        - Optional
        - Type: structure_interface
    - `/software/network/structure_network/nameserver`
        - Optional
        - Type: type_ip
    - `/software/network/structure_network/nisdomain`
        - Optional
        - Type: string
    - `/software/network/structure_network/nozeroconf`
        - Description: Setting nozeroconf to true stops an interface from being assigned an automatic address in the 169.254.0.0 subnet.
        - Optional
        - Type: boolean
    - `/software/network/structure_network/set_hwaddr`
        - Description: The default behaviour for all interfaces wrt setting the MAC address (see interface set_hwaddr attribute).
      The component default is false.
        - Optional
        - Type: boolean
    - `/software/network/structure_network/nmcontrolled`
        - Optional
        - Type: boolean
    - `/software/network/structure_network/allow_nm`
        - Optional
        - Type: boolean
    - `/software/network/structure_network/primary_ip`
        - Optional
        - Type: string
    - `/software/network/structure_network/routers`
        - Optional
        - Type: structure_router
    - `/software/network/structure_network/ipv6`
        - Optional
        - Type: structure_ipv6
