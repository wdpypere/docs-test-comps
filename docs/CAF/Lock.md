
### NAME

CAF::Lock - Class for handling application instance locking

### SYNOPSIS

    use CAF::Lock;

    $lock = CAF::Lock->new('/var/lock/quattor/spma', log => $reporter);

    unless ($lock->set_lock()) {...}
    unless ($lock->set_lock(10, 2) {...}
    unless ($lock->set_lock(3, 3, FORCE_ALWAYS)) {...}

    unless ($lock->unlock()) {....}

### INHERITANCE

    CAF::Object

### DESCRIPTION

The **CAF::Lock** class provides methods for handling application locking.

### PUBLIC METHODS

- set\_lock(_retries_, _timeout_, _force_)

    Tries _retries_ times to set the lock.  If _force_ is set to **FORCE\_NONE**
    or not defined and the lock is set, it sleeps for _timeout_.  Returns
    **SUCCESS**, or **undef** on failure.

    If _retries_ or _timeout_ are not defined or set to 0, only a single
    attempt is done to acquire the lock.

    If _force_ is set to **FORCE\_ALWAYS** then the lock file is just set
    again, even if the lock is already set by another application
    instance, and neither _timeout_ nor _retries_ are taken
    into account.

- unlock()

    Releases the lock and returns **SUCCESS**.  Reports an error and returns
    **undef** if the lock cannot be released.  If the object (application
    instance) does not hold the lock, an error is reported and **undef**
    is returned.

- is\_set()

    Returns **SUCCESS** if lock is set by application instance, **undef** otherwise.

### PRIVATE METHODS

- \_initialize(_lockfilename_)

    Initialize the object.  Called by new(_lockfilename_).

    Optional arguments

    - `log`

        A `CAF::Reporter` object to log to.

- \_try\_lock(_force_)

    Called by set\_lock() to create the lock file and return **SUCCESS** if we were
    able to flock() the file.

    If _force_ is set to **FORCE\_ALWAYS** then this method will return **SUCCESS**
    even if flock() was unsuccessful.
