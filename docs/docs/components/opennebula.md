### NAME

ncm-opennebula: Configuration module for OpenNebula

### DESCRIPTION

Configuration module for OpenNebula. 

### IMPLEMENTED FEATURES

Features that are implemented at this moment:

- Adding/removing VNETs
- Adding/removing datastores (only CEPH datastores for the moment)
- Adding/removing hypervirsors 
- Adding/removing OpenNebula regular users

OpenNebula installation is 100% automated. Therefore:

- All the new OpenNebula templates created by the component will include a QUATTOR flag
- The component only will modify/remove resources with the QUATTOR flag set, otherwise the resource is ignored
- If the component finds any issue during hypervisor host configuration then the node is included within OpenNebula infrastructure but as disabled host
- ONE component does not generate `/etc/one/oned.conf` file (yet). https://github.com/quattor/configuration-modules-core/issues/365
- The OpenNebula tt files required by the quattor component are shipped by config-templates-metaconfig package

### INITIAL CREATION

\- The schema details are annotated in the schema file.

\- Example pan files are included in the examples folder and also in the test folders.

To set up the initial cluster, some steps should be taken:

- 1. First install the required gems as root in your OpenNebula server: `/usr/share/one/install`\_gems
- 2. The OpenNebula server(s) should have passwordless ssh access as oneadmin user to all the hypervisor hosts of the cluster e.g. by distributing the public key(s) of the OpenNebula host over the cluster
- 3. Start OpenNebula services: ### for i in '' -econe -gate -novnc -occi -sunstone; do service opennebula$i stop; done
- 4. Run the component a first time
- 5. The new oneadmin password will be available from `/var/lib/one`/.one/one\_auth.new file

### RESOURCES

#### `/software/components/opennebula`

The configuration information for the component.  Each field should
be described in this section. 

### DEPENDENCIES

The component was tested with OpenNebula version 4.8 and 4.10

Following package dependencies should be installed to run the component:

- perl-Config-Tiny 
- perl-LC
- perl-Net-OpenNebula >= 0.2.2 !
