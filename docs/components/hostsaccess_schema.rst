#####################
hostsaccess :: schema
#####################

Types
-----

 - **/software/hostsaccess/structure_hostsaccess_entry**
    - */software/hostsaccess/structure_hostsaccess_entry/daemon*
        - Optional
        - Type: string
    - */software/hostsaccess/structure_hostsaccess_entry/host*
        - Optional
        - Type: string
 - **/software/hostsaccess/component_hostsaccess**
    - */software/hostsaccess/component_hostsaccess/allow*
        - Optional
        - Type: structure_hostsaccess_entry
    - */software/hostsaccess/component_hostsaccess/deny*
        - Optional
        - Type: structure_hostsaccess_entry
