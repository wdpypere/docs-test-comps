### NAME

CAF::Reporter - Class for console & log message reporting in CAF applications

### SYNOPSIS

    package myclass;
    use CAF::Reporter;
    @ISA = qw(CAF::Reporter);
    ...
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

- setup\_reporter ($debuglvl,$quiet,$verbose,$facility): boolean

    Reporter setup:

    \- $debuglvl sets the (highest) debug level, for messages reported with
      the 'debug' method.
      The following recommendations apply:
       0: no debug information
       1: main package
       2: main libraries/functions
       3: helper libraries
       4: core functions (constructors, destructors)

    \- $quiet: if set to a true value (eg. 1), stops any output to console.

    \- $verbose: if set to a true value (eg. 1), produce verbose output
                (produced with the 'verbose' method). Implied by debug >= 1.

    \- $facility: syslog facility the messages will be sent to

- set\_report\_logfile($logfile): bool

    If $logfile is defined, it will be used as log file. $logfile can be
    any type of class object reference, but must the object must support a
    'print(@array)' method. Typically, it should be an CAF::Log
    instance. If $logfile is undefined (undef), no log file will be used.

- report(@array): boolean

    Report general information about the program progression. The output
    to the console is supressed if 'quiet' is set. The strings in @array
    are concatenated and sent as a single line to the output(s).

- info (@array): boolean

    Reports @array using the 'report' method, but with a '\[INFO\]' prefix.

- OK (@array): boolean

    Reports @array using the 'report' method, but with a '\[OK\]' prefix.

- warn (@array): boolean

    Reports @array using the 'report' method, but with a '\[WARN\]' prefix.

- warn (@array): boolean

    Reports @array using the 'report' method, but with a '\[ERROR\]' prefix.

- verbose (@array): boolean

    Reports @array using the 'report' method, but only if 'verbose' is set
    to 1. Output is prefixed with \[VERB\].

- debug ($debuglvl,@array): boolean

    Reports @array using the 'report' method iff the current debug level is
    higher or equal than $debuglvl.

- log (@array): boolean

    Writes @array to the log file, if any.

- syslog ($priority, @array);

    Writes @array to the syslog, with the given priority.

#### Private methods
