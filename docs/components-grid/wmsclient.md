### NAME

wmsclient: NCM component to configure gLite WMS and EDG RB clients

### DESCRIPTION

The ncm-wmsclient component manages the configuration file of gLite WMS (both LB/NB and WMProxy interfaces) and EDG RB clients
command line interface. It creates both the site default variables and per VO configuration files.

Part of the configuration information used by this component comes from `/system/vo/VONAME/services.` EDG RB
information (legacy) is directly under this configuration path, gLite WMS configuration is under `/system/vo/VONAME/services/wms.`
Both share the same structure too.

### RESOURCES

wmsclient supports both gLite WMS with NS/LB interface or WMProxy interface and EDG RB. Information resources to describe all have the same structure.
There must be one for each variant to configure. Supported MW variants are 'edg', 'glite' and 'wmproxy'.

#### `/software/components/wmsclient/MW`\_VARIANT/active

Set to true to configure this WMS/RB variant.

Default : true (for a present variant).

#### `/software/components/wmsclient/MW`\_VARIANT/basedir

The base directory to use for generating VO-specific configuration
file.  It defaults to EDG\_LOCATION/etc (or `/opt/edg/etc` if EDG\_LOCATION
is not defined) for EDG RB, and to GLITE\_LOCATION/etc (or `/opt/glite/etc` if GLITE\_LOCATION
is not defined) for gLite WMS. 

#### `/software/components/wmsclient/MW`\_VARIANT/defaultAttrs

Set of properties and resources allowing to override default values for WMS/RB default ClassAds files. To know the
exact set of supported properties, look at ncm-wmsclient schema. To be taken into account, a property must be listed
in the template file for default ClassAds.

Default values should be appropriate.

#### VO specific configuration

VO specific configuration is under `/system/vo` configuration path. There is one entry per VO. In the resource for
each VO, this component uses the items described below. Except for VO full name, information is under 'services'
for EDG RB and under 'services/wms' for gLite WMS. 

##### `/system/vo`/\*/name

The official name of the VO.

Default : none.

##### services/lbhosts (required)

The list of logging and bookkeeping servers for this VO.  (Usually the
same as the resource broker list). If not present, configuration of WMS/RB client for this VO is ignored.

Default : none.

##### services/nshosts

The list of network server hosts (i.e. resource brokers) for this VO. It is a required property for EDG RB and for
gLite WMS with NS/LB interface ('glite' variant). They are ignored for 'wmproxy'.

Default : none.

##### services/wmproxies ('wmproxy' only, required)

The list of gLite WMS proxy endpoints for this VO. It is a required property for gLite WMS and it is not supported
for EDG RB.

Default : none.

##### services/myproxy (optional)

The myproxy server to use for this VO.

Default : none.

##### services/hlr (optional)

The HLR (accounting) server to use for this VO.

Default : none.

### DEPENDENCIES

None.

### BUGS

None known.

Michel Jouvin <>

Michel Jouvin <>

### VERSION

1.3.3

### SEE ALSO

ncm-ncd(1)
