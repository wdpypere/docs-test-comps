############################################
pan\::quattor\::aii\::opennebula\::functions
############################################

Functions
---------

 - opennebula_ipv42mac
    - Description: This function generates OpenNebula MAC addresses from MAC_PREFIX + IPv4Based on OpenNebula opennebula_ipv42mac function:https://github.com/OpenNebula/one/blob/master/share/router/vmcontext.rbSyntax:mac_prefix:string ipv4:stringmac_prefix hex:hex value used also by oned.conf (02:00 by default)ipv4 IP used by the VM
 - opennebula_replace_vm_mac
    - Description: This function replaces nic hwaddr using OpenNebula MAC functionUse the same MAC_PREFIX for OpenNebula component (oned.conf) and AIISyntax:mac_prefix:stringmac_prefix hex:hex value used by oned.confExample:"/hardware/cards/nic" = opennebula_replace_vm_mac(MAC_PREFIX);
