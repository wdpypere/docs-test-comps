### NAME

CAF::ReporterMany - Class for console & log message reporting in CAF applications,
which allows more than one object instance

### SYNOPSIS

    package myclass;
    use CAF::ReporterMany;
    use CAF::Log;
    @ISA = qw(CAF::ReporterMany);
    ...

    $logger = CAF::Log->new('/path/to/logfile', 'at');

    $self->setup_reporter(2, 0, 1);
    $self->set_report_logfile($logger);

    sub foo {
        my ($self,$a,$b,$c)=@_;
        ...
        $self->report("foo is doing well");
        $self->verbose("foo called with params $a $b $c");
        $self->debug(3,"foo is performing operation xyz");
        ...
    }

### INHERITANCE

none.

### DESCRIPTION

CAF::Reporter provides class methods for message (information,
warnings, error) reporting to standard output and a log file. There is
only one 'instance' of CAF::Reporter in an application. Classes
wanting to use CAF::Reporter have to inherit from it (using @ISA).

Usage of a log file is optional. A log file can be attached/detached
with the set\_logfile method.

#### Public methods

- **setup\_reporter**(_$debuglvl, $quiet, $verbose, $facility_): boolean

    Reporter setup:

    - _$debuglvl_

        sets the (highest) debug level, for messages reported with the **debug** method.
        The following recommendations apply:

            0: no debug information (default)
            1: main package
            2: main libraries/functions
            3: helper libraries
            4: core functions (constructors, destructors)

    - _$quiet_

        if set to a true value (e.g. 1), stop any output to console. Default is false

    - _$verbose_

        if set to a true value (e.g. 1), produce verbose output (via the **verbose**
        method). Default is false

    - _$facility_

        syslog facility the messages will be sent to. Default to local1

    If any of these arguments is `undef`, current application settings
    will be used.

- **set\_report\_logfile**(_$logfile_): bool

    If **$logfile** is defined, it will be used as log file. $logfile can be any type
    of class object reference, but the object must support a 'print(@array)'
    method. Typically, it should be a [CAF::Log](https://metacpan.org/pod/CAF::Log) instance. If $logfile is
    undefined (undef), no log file will be used.

- **report**(_@array_): boolean

    Report general information about the program progression. The output
    to the console is supressed if 'quiet' is set. The strings in _@array_
    are concatenated and sent as a single line to the output(s).

- **info**(_@array_): boolean

    Report _@array_ using the **report** method, but with an '\[INFO\]' prefix.

- **OK**(_@array_): boolean

    Report _@array_ using the **report** method, but with an '\[OK\]' prefix.

- **warn**(_@array_): boolean

    Report _@array_ using the **report** method, but with a '\[WARN\]' prefix.

- **error**(_@array_): boolean

    Report _@array_ using the **report** method, but with an '\[ERROR\]' prefix.

- **verbose**(_@array_): boolean

    Reports _@array_ using the **report** method, but only if 'verbose' is set
    to 1. Output is prefixed with '\[VERB\]'.

- **debug**(_$debuglvl, @array_): boolean

    Reports **@array** using the **report** method iff the current debug level is
    higher or equal than _$debuglvl_.

- **log**(_@array_): boolean

    Write _@array_ to the log file, if any.

- **syslog**(_$priority, @array_);

    Write _@array_ to the syslog, with the given priority.

### SEE ALSO

[LC::Exception](https://metacpan.org/pod/LC::Exception), [CAF::Application](https://metacpan.org/pod/CAF::Application), [CAF::Log](https://metacpan.org/pod/CAF::Log), [CAF::Reporter](https://metacpan.org/pod/CAF::Reporter).
