# NAME

CAF::RepLogger - Class for console & log message reporting for generic
applications

# SYNOPSIS

## Object-oriented usage

Allow for more objects to be instantiated, thus several log files can be used.

    use CAF::RepLogger;
    use LC::Exception;

    my $logger;
    unless($logger = CAF::RepLogger->new(
        'log-file'  => $0.'.log',
        # no report on console
        'quiet      => 1')) {
        my $err = $ec->error;
        $ec->ignore_error;
        die "$err\n";
    }
    $logger->warn('ahem...');
    $logger->error('ouch!');

## Procedural usage

Only a single log file can be used.

    use CAF::RepLogger qw(
        setup_replogger log_debug log_ok log_verb);
    use LC::Exception;

    my $ec = LC::Exception::Context->new->will_store_all;

    unless(setup_replogger(
            'debug-level'   => 3,
            'log-file'      => $0.'.log',
            'verbose'       => 1)) {
        my $err = $ec->error;
        $ec->ignore_error;
        die "$err\n";
    }

    log_debug(3, 'foo debug');
    log_ok('all fine');
    log_verb('blah, blah');

# INHERITANCE

[CAF::Object](https://metacpan.org/pod/CAF::Object), [CAF::Reporter](https://metacpan.org/pod/CAF::Reporter).

# DESCRIPTION

This modules provides console message reporting and logging facilities to
applications which can either be or not CAF-based, and want one or more
log files. It inherits from CAF::Reporter and uses a CAF::Log's object.

Multiple logs can be handled via the object-oriented interface, so that, if
your application is composed of more modules, each of them can instantiate
a different RepLogger object. Conversely, a one-for-all log mode is obtained
through the procedural interface which uses a shared configuration.

# Public methods/functions

For each of the following items, the first name is the OO interface's method,
the second name is procedural interface's function.

- **new, setup\_replogger** _(%module\_options)_

    Initialize LoggerSingle with options passed in a hash. **new** is used with the
    OO interface, **setup\_replogger** with the procedural interface. Options are

    - _debug-level_ integer \[0-9\]

        Default is 0.

    - _log-file_ string

        Absolute path: check permissions! **Mandatory**.

    - _log-file-opt_ string

        Options to be passed to [CAF::Log](https://metacpan.org/pod/CAF::Log). Default is 'at' (append, timestamp).

    - _quiet_ boolean \[0,1\]

        Disable logging to the console. Default is 0.

    - _session-ids_ array reference

        Pointer to a list of pointers to extra information tokens which are logged
        enclosed in square brackets; the line will look like

            [<type-tag>] [<session-ids>] <message>

        where each token in <session-ids> is replaced by a dash '-', when the token
        itself is undefined at logging time. This is useful when session information is
        recorded in some global variables which might be undefined, so one would code:

            my ($sid, $uid);
            setup_replogger('log-file' => 'mylog', 'session-ids' => [\$sid, \$uid]);
            log_ok('initialized');
            # prints
            #   [OK] [- -] initialized
            ...
            # wait for session information to be there
            ($sid, $uid) = ('sessX', 'userY');
            log_ok('session open');
            # prints
            #   [OK] [sessX userY] session open

        Default is undef.

    - _stack-frame_ integer \[0-N\]

        If > 0, enable printing of the stack frame corresponding to the depth value
        given. For instance, if your code is

            sub my_fun1 {
                log_error('ouch!');
            }
            sub my_fun2 {
                my_fun1;
            }
            my_fun2;

        and you set, respectively, 'stack-frame', to 0, 1 and 2, you get

            ... ouch!
            ... main::my_fun1: ouch!
            ... main::my_fun2: ouch!

        Default is 0.

    - _verbose_ boolean \[0,1\]

        Enable logging of messages passed to **\[log\_\]verb()**. Default is 0.

- **\*, log\_\*** _(;@messages)_

    Logging functions. \* is one of:

        debug
        error
        info
        ok
        warn

    So, f.i., you would say either

        $logger->debug(2, 'this is debug');

    or

        log_debug(2, 'this is debug');

# SEE ALSO

[CAF::Log(3)](http://man.he.net/man3/CAF::Log), [CAF::Reporter(3)](http://man.he.net/man3/CAF::Reporter)
