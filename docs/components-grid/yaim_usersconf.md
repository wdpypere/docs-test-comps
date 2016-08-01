### NAME

yaim\_usersconf: NCM component to write users.conf and groups.conf files used by YAIM 
to generate grid-mapfiles.

### DESCRIPTION

The _yaim\_usersconf_ component writes the users.conf and groups.conf
files used by YAIM. The exact locations should be specified in the CDB
structure at "/software/components/yaim\_usersconf/users\_conf\_file" and  
"/software/components/yaim\_usersconf/groups\_conf\_file".

### RESOURCES

#### `/system/vo`/<VO-name>/gridusers (list)

A list of nlists, where each element specifies a username and an (optional)
flag to describe the role of the user.

The component will iterate over this list, writing an entry in users.conf
for each element that has a corresponding user on the system.

#### `/system/vo`/<VO-name>/gridgroups (list)

A list of nlists, where each element specifies a VOMS path and an (optional)
flag to describe the role.

The component will iterate over this list, writing an entry in groups.conf
for each element that has a corresponding group on the system.

### SEE ALSO

ncm-ncd(1), http://cern.ch/quattor
http://cern.ch/grid-deployment
