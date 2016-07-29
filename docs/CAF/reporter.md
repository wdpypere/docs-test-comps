### NAME

`CAF::Reporter` - Class for console & log message reporting in CAF applications

### SYNOPSIS

    package myclass;
    use CAF::Log;
    use parent qw(CAF::Reporter);

    my $logger = CAF::Log->new('/path/to/logfile', 'at');

    sub new {
        ...
        $self->setup_reporter(2, 0, 1);
        $self->set_report_logfile($logger);
        ...
    }

    sub foo {
        my ($self, $a, $b, $c) = @_;
        ...
        $self->report("foo is doing well");
        $self->verbose("foo called with params $a $b $c");
        $self->debug(3, "foo is performing operation xyz");
        ...
    }

### DESCRIPTION

`CAF::Reporter` provides class methods for message (information,
warnings, error) reporting to standard output and a log file. There is
only one instance of `CAF::Reporter` in an application. (All `CAF::Reporter`
instances share the same configuration).
Classes wanting to use `CAF::Reporter` have to inherit from it
(using `parent qw(CAF::Reporter)` or via `@ISA`).

Usage of a log file is optional. A log file can be attached/detached
with the `set_logfile` method.

#### Public methods

- init\_reporter

    Setup default/initial values for reporter. Returns success.

- `setup_reporter ($debuglvl, $quiet, $verbose, $facility)`: boolean

    Reporter setup:

    - `$debuglvl` sets the (highest) debug level, for messages reported with
        the 'debug' method.
        The following recommendations apply:
            0: no debug information
            1: main package
            2: main libraries/functions
            3: helper libraries
            4: core functions (constructors, destructors)
    - `$quiet`: if set to a true value (eg. 1), stops any output to console.
    - `$verbose`: if set to a true value (eg. 1), produce verbose output
                (with the `verbose` method). Implied by debug >= 1.
    - `$facility`: syslog facility the messages will be sent to

    If any of these arguments is `undef`, current application settings
    will be preserved.

- `set_report_logfile($loginstance)`: bool

    If `$loginstance` is defined, it will be used as log file. `$loginstance` can be
    any type of class object reference, but the object must support a
    `print(@array)` method. Typically, it should be an `CAF::Log`
    instance. If `$loginstance` is undefined, no log file will be used.

    Returns SUCCESS on success, undef otherwise.

    (The method name is slightly misleading, because is it does not set the logfile's
    filename, but the internal `$LOGFILE` attribute).

- `init_logfile($filename, $options)`: bool

    Create a new [CAF::Log](https://metacpan.org/pod/CAF::Log) instance with `$filename` and `$options` and
    set it using `set_report_logfile`.
    Returns SUCCESS on success, undef otherwise.

    (The method name is slightly misleading, because is it does
    create the logfile with filename, but the internal
    `$LOGFILE` attribute).

- `get_debuglevel`: int

    Return current debuglevel

- `is_quiet`: bool

    Return true if reporter is quiet, false otherwise

- `is_verbose`: bool

    Return true if reporter is verbose, false otherwise

- `report(@array)`: boolean

    Report general information about the program progression
    to stdout (via `print`) and `log` method.
    The output to the console is supressed if `quiet` is set.
    The strings in `@array` are concatenated, newline is added
    and sent as a single line to the output.
    Then `log` method is called with `@array` (irrespective of `quiet`).

    The `report` method does not log to syslog.

- `info(@array)`: boolean

    Logs using `syslog` method with `info` priority
    and reports `@array` using the `report` method, but with a `[INFO]` prefix.

- `OK(@array)`: boolean

    Logs using `syslog` method with `notice` priority
    and reports `@array` using the `report` method, but with a `[OK]` prefix.

- `warn(@array)`: boolean

    Logs using `syslog` method with `warning` priority
    and reports `@array` using the `report` method, but with a `[WARN]` prefix.

- `error(@array)`: boolean

    Logs using `syslog` method with `err` priority
    and reports `@array` using the `report` method, but with a `[ERROR]` prefix.

- `verbose(@array)`: boolean

    If `verbose` is enabled (via `setup_reporter`), the `verbose` method
    logs using `syslog` method with `notice` priority
    and reports `@array` using the `report` method, but with a `[VERB]` prefix.

- `debug($debuglvl, @array)`: boolean

    If `$debuglvl` is higher or equal than then one set via `setup_reporter`,
    the `debug` method
    logs to syslog with `debug` priority
    and reports `@array` using the `report` method, but with a `[DEBUG]` prefix.

    If the `$debuglvl` is not an integer in interval \[0-9\], an error is thrown
    and undef returned (and nothing logged).

- `log(@array)`: boolean

    Writes `@array` as a concatenated string with added newline
    to the log file, if one is setup (via `set_report_logfile`).

- `syslog($priority, @array)`

    Writes `@array` as concatenated string to syslog, with the given priority.

    Nothing will happen is no 'SYSLOG' attribute of logfile is set.
    This attribute is prepended to every message.

    (Return value is always undef.)

- `set_report_history($historyinstance)`: bool

    Set `$historyinstance` as the reporter's history
    (using the `$HISTORY` attribute).

    Returns SUCCESS on success, undef otherwise.

- init\_history

    Create a [CAF::History](https://metacpan.org/pod/CAF::History) instance to track events.
    Argument `keepinstances` is passed to the `CAF::History`
    initialization.

    Returns SUCCESS on success, undef otherwise.

- event

    If a `CAF::History` is initialized, track the event. The following metadata is added

    - `$WHOAMI`

        Current class name `ref($self)`.
