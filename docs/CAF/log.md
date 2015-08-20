### NAME

CAF::Log - Simple class for handling log files

### SYNOPSIS

    use CAF::Log;

    my $log=CAF::Log->new('/foo/bar','at');

    $log->print("this goes to the log file\n");
    $log->close();

### INHERITANCE

    CAF::Reporter

### DESCRIPTION

The **CAF::Log** class allows to instantiate objects for writing log files.
A log file line can be prefixed by a time stamp.

#### Public methods

- close(): boolean

    closes the log file.

- print($string):boolean

    prints a line into the log file.

#### Private methods

- \_initialize($filename,$options)

    initialize the object. Called by new($filename,$options).

    $options can be 'a' for appending to a logfile, and 'w' for
    truncating, and 't' for generating a timestamp on every
    print. If the 'w' option is used and there was a previous
    log file, it is renamed with the extension '.prev'.

    Examples:
    open('/foo/bar','at'): append, enable timestamp
    open('/foo/bar','w') : truncate logfile, no timestamp

- DESTROY

    called during garbage collection. Invokes close()
