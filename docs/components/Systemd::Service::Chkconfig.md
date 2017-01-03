
### NAME

NCM::Component::Systemd::Service::Chkconfig is a class handling services
that can be controlled via (older) [ncm-chkconfig](../components/chkconfig.md).

#### Public methods

- new

    Returns a new object, accepts the following options

    - log

        A logger instance (compatible with `CAF::Object`).

- current\_units

    Return hash reference with current configured units
    determined via `chkconfig --list`.

    (No type to specify, `sysv` type is forced).

- current\_target

    Return the current target based on legacy `current_runlevel`.

- default\_target

    Return the default target based on legacy `default_runlevel`.

- configured\_units

    `configured_units` parses the `tree` hash reference and builds up the
    units to be configured. It returns a hash reference with key the unit name and
    values the details of the unit.

    (`tree` is typically `$config-`getElement('/software/components/chkconfig/service')->getTree>.)

    This method converts the legacy states as following

    - del : masked
    - add: disabled
    - off : disabled
    - on : enabled
    - reset: this state is ignored / not supported.

#### Private methods

- is\_possible\_missing

    Determine if `unit` is `possible_missing`
    (see `make_cache_alias`). (Returns 0 or 1).

    A unit is possible\_missing if

    - the unit is in state masked or disabled
    (i.e. unit that is not expected to be running anyway).

        Other then pure systemd, chkconfig state off always implies
        that a disabled service unit is not running.

- generate\_runlevel2target

    Create, set and return the `runlevel2target` map
    (will reset existing one, return is merely for testing).

- convert\_runlevels

    Convert the [ncm-chkconfig](../components/chkconfig.md) levels to new systemsctl targets

    `legacylevel` is a string with integers e.g. "234".
    Retrun a array reference with the targets.

- default\_runlevel

    `default_runlevel` returns the default runlevel
    via the INITTAB file. If that fails, the default
    DEFAULT\_RUNLEVEL is returned.

- current\_runlevel

    Return the current legacy runlevel.

    The rulevel is determined by trying (in order)
    `/sbin/runlevel` or `who -r`. If both fail, the
    `default_runlevel` method is called and its value
    is returned.
