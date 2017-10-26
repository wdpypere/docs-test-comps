
### Types

 - `/software/ntpd/ntpd_clientnet_type`
    - `/software/ntpd/ntpd_clientnet_type/net`
        - Optional
        - Type: type_ip
    - `/software/ntpd/ntpd_clientnet_type/mask`
        - Optional
        - Type: type_ip
 - `/software/ntpd/ntpd_server_options`
    - Description: 
    Server command options
    Refer to man ntp.conf for details.

    - `/software/ntpd/ntpd_server_options/autokey`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_server_options/burst`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_server_options/iburst`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_server_options/key`
        - Optional
        - Type: long
        - Range: 1..655534
    - `/software/ntpd/ntpd_server_options/minpoll`
        - Optional
        - Type: long
        - Range: 3..17
    - `/software/ntpd/ntpd_server_options/maxpoll`
        - Optional
        - Type: long
        - Range: 3..17
    - `/software/ntpd/ntpd_server_options/noselect`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_server_options/preempt`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_server_options/prefer`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_server_options/true`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_server_options/version`
        - Optional
        - Type: long
        - Range: 1..4
 - `/software/ntpd/ntpd_restrict_options`
    - Description: 
    Base restrict command options
    Refer to C<< man ntp_acc >> for more information or access control commands.

    - `/software/ntpd/ntpd_restrict_options/mask`
        - Description: Mask can be a address of a host or network and can be a valid host DNS name.
        - Optional
        - Type: type_ip
    - `/software/ntpd/ntpd_restrict_options/ignore`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_restrict_options/kod`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_restrict_options/limited`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_restrict_options/lowpriotrap`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_restrict_options/nomodify`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_restrict_options/noquery`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_restrict_options/nopeer`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_restrict_options/noserve`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_restrict_options/notrap`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_restrict_options/notrust`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_restrict_options/ntpport`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_restrict_options/version`
        - Description: Deny packets that do not match the current NTP version.
        - Optional
        - Type: long
        - Range: 1..4
 - `/software/ntpd/ntpd_restrict_default`
    - Description: 
    Default restrict command options.
    Default when none-defined: restrict default ignore.

 - `/software/ntpd/ntpd_server_definition`
    - Description: 
    Server address with optional options and access restrictions
    Allows to configure timeservers with their own options.

    - `/software/ntpd/ntpd_server_definition/server`
        - Description: Time server, can be ip address or qualified DNS hostname
        - Optional
        - Type: type_hostname
    - `/software/ntpd/ntpd_server_definition/options`
        - Optional
        - Type: ntpd_server_options
 - `/software/ntpd/ntpd_tinker_options`
    - Description: 
    Alter certain system variables used by the clock discipline algorithm

    - `/software/ntpd/ntpd_tinker_options/allan`
        - Optional
        - Type: long
    - `/software/ntpd/ntpd_tinker_options/dispersion`
        - Optional
        - Type: long
    - `/software/ntpd/ntpd_tinker_options/freq`
        - Optional
        - Type: long
    - `/software/ntpd/ntpd_tinker_options/huffpuff`
        - Optional
        - Type: long
    - `/software/ntpd/ntpd_tinker_options/panic`
        - Optional
        - Type: long
    - `/software/ntpd/ntpd_tinker_options/step`
        - Optional
        - Type: long
    - `/software/ntpd/ntpd_tinker_options/stepout`
        - Optional
        - Type: long
 - `/software/ntpd/ntpd_system_options`
    - Description: 
    System options that can be en/disabled.
    Flags not mentioned are unaffected.
    Note that all of these flags can be controlled remotely using
    the ntpdc utility program.
    Refer to ntp_misc manpage for more details.

    - `/software/ntpd/ntpd_system_options/auth`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_system_options/blient`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_system_options/calibrate`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_system_options/kernel`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_system_options/monitor`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_system_options/ntp`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_system_options/pps`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_system_options/stats`
        - Optional
        - Type: boolean
 - `/software/ntpd/ntpd_logconfig`
    - Description: 
    Log configuration arguments must be defined in a list of strings.
    Values for each argument must follow what is defined in ntp_misc manual.
    Refer to ntp_misc manpage for more details.

    Examples:
        to get command 'logconfig -syncstatus +sysevents'

        prefix "/software/components/ntpd";
        "logconfig" = list("-syncstatus", "+sysevents");

 - `/software/ntpd/ntpd_statistics`
    - Description: 
    Monitoring/statistics options, see ntp_mon manpage.

    - `/software/ntpd/ntpd_statistics/clockstats`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_statistics/cryptostats`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_statistics/loopstats`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_statistics/peerstats`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_statistics/rawstats`
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_statistics/sysstats`
        - Optional
        - Type: boolean
 - `/software/ntpd/ntpd_filegen`
    - Description: 
    Monitoring/statistics options, see ntp_mon manpage.

    - `/software/ntpd/ntpd_filegen/name`
        - Optional
        - Type: string
    - `/software/ntpd/ntpd_filegen/file`
        - Optional
        - Type: string
    - `/software/ntpd/ntpd_filegen/type`
        - Optional
        - Type: string
    - `/software/ntpd/ntpd_filegen/linkornolink`
        - Optional
        - Type: string
    - `/software/ntpd/ntpd_filegen/enableordisable`
        - Optional
        - Type: string
 - `/software/ntpd/ntpd_component`
    - `/software/ntpd/ntpd_component/keyfile`
        - Description: Specifies the absolute path and of the MD5 key file containing the
      keys and key identifiers used by ntpd, ntpq and ntpdc when operating with
      symmetric key cryptography.
      Refer to ntp_auth manpage for more details.
        - Optional
        - Type: absolute_file_path
    - `/software/ntpd/ntpd_component/trustedkey`
        - Description: Refer to ntp_auth manpage for more details.
      Requires keyfile.
        - Optional
        - Type: long
    - `/software/ntpd/ntpd_component/requestkey`
        - Description: Specifies the key identifier to use with the ntpdc utility program.
      Refer to ntp_auth manpage for more details.
      Requires keyfile.
        - Optional
        - Type: long
    - `/software/ntpd/ntpd_component/controlkey`
        - Description: Specifies the key identifier to use with the ntpq utility program.
      Refer to ntp_auth manpage for more details.
      Requires keyfile.
        - Optional
        - Type: long
    - `/software/ntpd/ntpd_component/driftfile`
        - Description: Absolute path of the file used to record the frequency of the local clock oscillator.
        - Optional
        - Type: absolute_file_path
    - `/software/ntpd/ntpd_component/includefile`
        - Description: Additional configuration commands to be included from a separate file.
        - Optional
        - Type: absolute_file_path
    - `/software/ntpd/ntpd_component/useserverip`
        - Description: resolve and use the time server(s) ip address in the config file(s)
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_component/serverlist`
        - Optional
        - Type: ntpd_server_definition
    - `/software/ntpd/ntpd_component/servers`
        - Description: list of time servers (using defaultoptions)
        - Optional
        - Type: type_hostname
    - `/software/ntpd/ntpd_component/defaultoptions`
        - Description: Specifies default command options for each timeserver defined in servers or serverlist.
        - Optional
        - Type: ntpd_server_options
    - `/software/ntpd/ntpd_component/clientnetworks`
        - Description: List of clients that can use this server to synchronize. Default allows connections from localhost only.
        - Optional
        - Type: ntpd_clientnet_type
    - `/software/ntpd/ntpd_component/logfile`
        - Description: Absolute path to alternate logfile instead of default syslog. Refer to ntp_misc manpage for more details.
        - Optional
        - Type: absolute_file_path
    - `/software/ntpd/ntpd_component/logconfig`
        - Optional
        - Type: ntpd_logconfig
    - `/software/ntpd/ntpd_component/statsdir`
        - Description: Directory path prefix for statistics file names.
        - Optional
        - Type: absolute_file_path
    - `/software/ntpd/ntpd_component/statistics`
        - Optional
        - Type: ntpd_statistics
    - `/software/ntpd/ntpd_component/filegen`
        - Optional
        - Type: ntpd_filegen
    - `/software/ntpd/ntpd_component/disable`
        - Description: Provides a way to disable various system options.
        - Optional
        - Type: ntpd_system_options
    - `/software/ntpd/ntpd_component/enable`
        - Description: Provides a way to enable various system options.
        - Optional
        - Type: ntpd_system_options
    - `/software/ntpd/ntpd_component/tinker`
        - Optional
        - Type: ntpd_tinker_options
    - `/software/ntpd/ntpd_component/restrictdefault`
        - Optional
        - Type: ntpd_restrict_default
    - `/software/ntpd/ntpd_component/broadcastdelay`
        - Description: Double value in seconds to set network delay between local and remote servers.
      Refer to ntp_misc manpage for more details.
        - Optional
        - Type: double
    - `/software/ntpd/ntpd_component/authenticate`
        - Description: Adds string 'authenticate yes' to ntp.conf.
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_component/servicename`
        - Description: Override the service name to restart. Some platforms
      use a different service name to represent ntpd.
      Defaults are "ntpd" on linux and "svc:/network/ntpd" on solaris.
        - Optional
        - Type: string
    - `/software/ntpd/ntpd_component/includelocalhost`
        - Description: Includes fudge options for localhost's clock. Defaults to true
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_component/enablelocalhostdebug`
        - Description: Allows some debugging via ntpdc on localhost but does not allow modifications. Defaults to true
        - Optional
        - Type: boolean
    - `/software/ntpd/ntpd_component/group`
        - Description: if the group is set, files are written with root.group ownership and 0640 permission
        - Optional
        - Type: defined_group

### Functions

 - valid_ntpd_logconfig_list
