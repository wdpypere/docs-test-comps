### NAME

moab: NCM component to configure moab server.

### DESCRIPTION

The _moab_ component manages the configuration for the Moab and/or Maui
scheduler. By default the configuration file resides in
`/opt/moab/moab.cfg` for Moab and `/var/spool/maui`/.cfg for Maui.  

### RESOURCES

#### mode (default moab)

Make configurations for moab or maui (eg location of config file)

#### configPath (/opt/moab or `/var/spool/maui`)

The absolute path for the moab or maui configuration directory. 

#### configFile (moab.cfg or maui.cfg)

The file name for the moab or maui configuration file.
