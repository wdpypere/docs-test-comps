### Types

- `/software/network/structure_route`
    - decription: 
    Route

    - `/software/network/structure_route/address`
        - optional
        - type: type_ip
    - `/software/network/structure_route/netmask`
        - optional
        - type: type_ip
    - `/software/network/structure_route/gateway`
        - optional
        - type: type_ip
- `/software/network/structure_interface_alias`
    - decription: 
    Interface alias

    - `/software/network/structure_interface_alias/ip`
        - optional
        - type: type_ip
    - `/software/network/structure_interface_alias/netmask`
        - required
        - type: type_ip
    - `/software/network/structure_interface_alias/broadcast`
        - optional
        - type: type_ip
    - `/software/network/structure_interface_alias/fqdn`
        - optional
        - type: type_fqdn
- `/software/network/structure_bonding_options`
    - decription: 
    Describes the bonding options for configuring channel bonding on EL5 and similar.

    - `/software/network/structure_bonding_options/mode`
        - required
        - type: long
        - range: 0..6
    - `/software/network/structure_bonding_options/miimon`
        - required
        - type: long
    - `/software/network/structure_bonding_options/updelay`
        - optional
        - type: long
    - `/software/network/structure_bonding_options/downdelay`
        - optional
        - type: long
    - `/software/network/structure_bonding_options/primary`
        - optional
        - type: valid_interface
    - `/software/network/structure_bonding_options/lacp_rate`
        - optional
        - type: long
        - range: 0..1
    - `/software/network/structure_bonding_options/xmit_hash_policy`
        - optional
        - type: string
- `/software/network/structure_bridging_options`
    - decription: 
    describes the bridging options
    (the parameters for `/sys/class/net`/<br>/brport)

    - `/software/network/structure_bridging_options/bpdu_guard`
        - optional
        - type: long
    - `/software/network/structure_bridging_options/flush`
        - optional
        - type: long
    - `/software/network/structure_bridging_options/hairpin_mode`
        - optional
        - type: long
    - `/software/network/structure_bridging_options/multicast_fast_leave`
        - optional
        - type: long
    - `/software/network/structure_bridging_options/multicast_router`
        - optional
        - type: long
    - `/software/network/structure_bridging_options/path_cost`
        - optional
        - type: long
    - `/software/network/structure_bridging_options/priority`
        - optional
        - type: long
    - `/software/network/structure_bridging_options/root_block`
        - optional
        - type: long
- `/software/network/structure_ethtool_offload`
    - decription: 
    interface ethtool offload

    - `/software/network/structure_ethtool_offload/rx`
        - optional
        - type: string
    - `/software/network/structure_ethtool_offload/tx`
        - optional
        - type: string
    - `/software/network/structure_ethtool_offload/tso`
        - optional
        - type: string
    - `/software/network/structure_ethtool_offload/gro`
        - optional
        - type: string
- `/software/network/structure_ethtool_ring`
    - decription: 
    interface ethtool ring

    - `/software/network/structure_ethtool_ring/rx`
        - optional
        - type: long
    - `/software/network/structure_ethtool_ring/tx`
        - optional
        - type: long
    - `/software/network/structure_ethtool_ring/rx`-mini
        - optional
        - type: long
    - `/software/network/structure_ethtool_ring/rx`-jumbo
        - optional
        - type: long
- `/software/network/structure_ethtool_wol`
    - decription: 
    ethtool wol p|u|m|b|a|g|s|d...
    from the man page
        Sets Wake-on-LAN options.  Not all devices support this.  The argument to this option is  a  string
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
    - decription: 
    ethtool

    - `/software/network/structure_ethtool/wol`
        - optional
        - type: structure_ethtool_wol
    - `/software/network/structure_ethtool/autoneg`
        - optional
        - type: string
    - `/software/network/structure_ethtool/duplex`
        - optional
        - type: string
    - `/software/network/structure_ethtool/speed`
        - optional
        - type: long
- `/software/network/structure_interface`
    - decription: 
    interface

    - `/software/network/structure_interface/ip`
        - optional
        - type: type_ip
    - `/software/network/structure_interface/gateway`
        - optional
        - type: type_ip
    - `/software/network/structure_interface/netmask`
        - optional
        - type: type_ip
    - `/software/network/structure_interface/broadcast`
        - optional
        - type: type_ip
    - `/software/network/structure_interface/driver`
        - optional
        - type: string
    - `/software/network/structure_interface/bootproto`
        - optional
        - type: string
    - `/software/network/structure_interface/onboot`
        - optional
        - type: string
    - `/software/network/structure_interface/type`
        - optional
        - type: string
    - `/software/network/structure_interface/device`
        - optional
        - type: string
    - `/software/network/structure_interface/master`
        - optional
        - type: string
    - `/software/network/structure_interface/mtu`
        - optional
        - type: long
    - `/software/network/structure_interface/route`
        - optional
        - type: structure_route
    - `/software/network/structure_interface/aliases`
        - optional
        - type: structure_interface_alias
    - `/software/network/structure_interface/set_hwaddr`
        - optional
        - type: boolean
    - `/software/network/structure_interface/bridge`
        - optional
        - type: valid_interface
    - `/software/network/structure_interface/bonding_opts`
        - optional
        - type: structure_bonding_options
    - `/software/network/structure_interface/offload`
        - optional
        - type: structure_ethtool_offload
    - `/software/network/structure_interface/ring`
        - optional
        - type: structure_ethtool_ring
    - `/software/network/structure_interface/ethtool`
        - optional
        - type: structure_ethtool
    - `/software/network/structure_interface/vlan`
        - optional
        - type: boolean
    - `/software/network/structure_interface/physdev`
        - optional
        - type: valid_interface
    - `/software/network/structure_interface/fqdn`
        - optional
        - type: string
    - `/software/network/structure_interface/network_environment`
        - optional
        - type: string
    - `/software/network/structure_interface/network_type`
        - optional
        - type: string
    - `/software/network/structure_interface/nmcontrolled`
        - optional
        - type: boolean
    - `/software/network/structure_interface/linkdelay`
        - optional
        - type: long
    - `/software/network/structure_interface/stp`
        - optional
        - type: boolean
    - `/software/network/structure_interface/delay`
        - optional
        - type: long
    - `/software/network/structure_interface/bridging_opts`
        - optional
        - type: structure_bridging_options
    - `/software/network/structure_interface/bond_ifaces`
        - optional
        - type: string
    - `/software/network/structure_interface/ovs_bridge`
        - optional
        - type: valid_interface
    - `/software/network/structure_interface/ovs_extra`
        - optional
        - type: string
    - `/software/network/structure_interface/ovs_opts`
        - optional
        - type: string
    - `/software/network/structure_interface/ovs_patch_peer`
        - optional
        - type: string
    - `/software/network/structure_interface/ovs_tunnel_opts`
        - optional
        - type: string
    - `/software/network/structure_interface/ovs_tunnel_type`
        - optional
        - type: string
    - `/software/network/structure_interface/ipv4_failure_fatal`
        - optional
        - type: boolean
    - `/software/network/structure_interface/ipv6_autoconf`
        - optional
        - type: boolean
    - `/software/network/structure_interface/ipv6_failure_fatal`
        - optional
        - type: boolean
    - `/software/network/structure_interface/ipv6_mtu`
        - optional
        - type: long
        - range: 1280..65536
    - `/software/network/structure_interface/ipv6_privacy`
        - optional
        - type: string
    - `/software/network/structure_interface/ipv6_rtr`
        - optional
        - type: boolean
    - `/software/network/structure_interface/ipv6addr`
        - optional
        - type: type_network_name
    - `/software/network/structure_interface/ipv6addr_secondaries`
        - optional
        - type: type_network_name
    - `/software/network/structure_interface/ipv6init`
        - optional
        - type: boolean
- `/software/network/structure_router`
    - decription: 
    router

- `/software/network/structure_ipv6`
    - decription: 
    IPv6 global settings

    - `/software/network/structure_ipv6/enabled`
        - optional
        - type: boolean
    - `/software/network/structure_ipv6/default_gateway`
        - optional
        - type: type_ip
    - `/software/network/structure_ipv6/gatewaydev`
        - optional
        - type: valid_interface
- `/software/network/structure_network`
    - decription: 
    network

    - `/software/network/structure_network/domainname`
        - required
        - type: type_fqdn
    - `/software/network/structure_network/hostname`
        - required
        - type: type_shorthostname
    - `/software/network/structure_network/realhostname`
        - optional
        - type: type_fqdn
    - `/software/network/structure_network/default_gateway`
        - optional
        - type: type_ip
    - `/software/network/structure_network/gatewaydev`
        - optional
        - type: valid_interface
    - `/software/network/structure_network/interfaces`
        - required
        - type: structure_interface
    - `/software/network/structure_network/nameserver`
        - optional
        - type: type_ip
    - `/software/network/structure_network/nisdomain`
        - optional
        - type: string
    - `/software/network/structure_network/nozeroconf`
        - optional
        - type: boolean
    - `/software/network/structure_network/set_hwaddr`
        - optional
        - type: boolean
    - `/software/network/structure_network/nmcontrolled`
        - optional
        - type: boolean
    - `/software/network/structure_network/allow_nm`
        - optional
        - type: boolean
    - `/software/network/structure_network/primary_ip`
        - optional
        - type: string
    - `/software/network/structure_network/routers`
        - optional
        - type: structure_router
    - `/software/network/structure_network/ipv6`
        - optional
        - type: structure_ipv6

