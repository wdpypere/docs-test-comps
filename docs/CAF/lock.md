# NAME

CAF::Lock - Class for handling application instance locking

# SYNOPSIS

    use CAF::Lock;

    $lock=CAF::Lock->new('/var/lock/quattor/spma');

    if ($lock->is_locked()) {...} else {...};

    $lockpid=$lock->get_lock_pid();

    unless ($lock->set_lock()) {...}
    unless ($lock->set_lock(10,2) {...}
    unless ($lock->set_lock(3,3,FORCE_IF_STALE)) {...}

    if ($lock->is_stale()) {...} else {...};

    unless ($lock->unlock()) {....}

# INHERITANCE

    CAF::Reporter

# DESCRIPTION

The **CAF::Lock** class provides methods for handling application locking.



## Public methods

- is\_locked()

    If a lock is set for the lock file, returns SUCCESS, undef otherwise.

- get\_lock\_pid()

    Returns the PID file of the application holding the lock, undef if no
    lockfile found

- is\_stale()

    Returns SUCCESS if the lock is stale - a lock file is set but the
    corresponding PID does not exist. Returns undef otherwise.

- set\_lock ($retries,$timeout,$force);

    Tries $retries times to set the lock. If $force is set to FORCE\_NONE
    or not defined and the lock is set, it sleeps for
    rand($timeout). Writes the current PID ($$) into the lock
    file. Returns SUCCESS or undef on failure.

    If $retries or $timeout are not defined or set to 0, only a single
    attempt is done to acquire the lock.

    If $force is set to FORCE\_ALWAYS then the lockfile is just set
    again, independently if the lock is already set by another application
    instance.

    If $force is set to FORCE\_IF\_STALE then the lockfile is set if the
    application instance holding the lock is dead (PID not alive).

    If $force is set to FORCE\_ALWAYS, or if $force is defined to
    FORCE\_IF\_STALE and a stale lock file is detected, then neither
    $timeout nor $retries are taken into account.

- unlock

    Releases the lock and returns SUCCESS. Reports an error and returns
    undef if the lock file cannot be released. If the object (application
    instance) does not hold the lockfile, an error is reported and undef
    is returned.

- is\_set

    Returns SUCCESS if lock is set by application instance, undef otherwise

## Private methods

- \_initialize($lockfilename)

    initialize the object. Called by new($lockfilename).

- DESTROY

    called during garbage collection. Invokes unlock() if lock is set by
    application instance.
