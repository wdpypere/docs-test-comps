### NAME

CAF::Path - check that things are really the way we expect them to be

### DESCRIPTION

Simplify common file and directory related operations e.g.

- directory creation
- cleanup
- (mockable) file/directory tests

The class is based on **LC::Check** with following major difference

- `CAF::Object::NoAction` support builtin (and `keeps_state` option to override it).
- support `CAF::Reporter` (incl. `CAF::History`)
- raised exceptions are catched, methods return SUCCESS on succes,
undef on failure and store the error message in the `fail` attribute.
- available as class-methods
- return values
    - undef: failure occured
    - SUCCESS: nothing changed (boolean true)
    - CHANGED: something changed (boolean true).

#### Methods

- \_get\_noaction

    Return NoAction setting:

    - Return 0 is `keeps_state` is true

        Any other value of `keeps_state` is ignored. (In particular,
        you cannot use `keeps_state` to enable NoAction).

    - Return value of `CAF::Object::NoAction` otherwise.

    Supports an optional `msg` that is prefixed to reporter.

- \_reset\_exception\_fail

    Reset previous exceptions and/or fail attribute.

- \_function\_catch

    Execute function reference `funcref` with arrayref `$args` and hashref `$opts`.

    Method resets/ignores any existing errors and fail attribute, and catches any exception thrown.
    No error is reported, it returns undef in this case and the fail attribute is set.

- \_safe\_eval

    Run function reference `funcref` with arrayref `argsref` and hashref `optsref`.

    Return and set fail attribute with `failmsg` on die, verbose `msg` on success
    (resp. $@ and stringified result are appended).

    Resets previous exceptions and/or fail attribute

- LC\_Check

    Execute function `<LC::Check::<function`>> with arrayref `$args` and hashref `$opts`.

    `CAF::Object::NoAction` is added to the options, unless `keeps_state` is set.

    The function is executed with `_function_catch`.

- \_untaint\_path

    Untaint the `path` argument.

    Returns undef on failure and sets the fail attribute with `msg`

- directory\_exists

    Test if `directory` exists and is a directory.

    This is basically the perl builtin `-d`,
    wrapped in a method to allow unittesting.

    A broken symlink is not a directory. (As `-d` follows a symlink,
    a broken symlink either exists with `-l` or not.)

- file\_exists

    Test if `filename` exists ans is a directory.

    This is basically the perl builtin `-f`,
    wrapped in a method to allow unittesting.

    A broken symlink is not a file. (As `-f` follows a symlink,
    a broken symlink either exists with `-l` or not.)

- any\_exists

    Test if `path` exists.

    This is basically the perl builtin `-e || -l`,
    wrapped in a method to allow unittesting.

    A broken symlink exists. As `-e` follows a symlink,
    a broken symlink either exists with `-l` or not.

- cleanup

    cleanup removes `dest` with backup support.

    (Works like `LC::Check::_unlink`, but has directory support
    and no error throwing).

    Returns CHANGED is something was cleaned-up, SUCCESS if nothing was done
    and undef on failure (and sets the fail attribute).

    The &lt;backup> is a suffix for `dest`.

    If backup is undefined, use `backup` attribute.
    (Pass an empty string to disable backup with `backup` attribute defined)
    Any previous backup is `cleanup`ed (without backup).
    (Aside from the `backup` attribute, this is the same as `LC::Check::_unlink`
    (and thus also `CAF::File*`)).

    Additional options

    - keeps\_state: boolean passed to `_get_noaction`.

- directory

    Make sure a directory exists with proper options.

    If the directory does not exists (or the `temp` option is set),
    it is created (including the parent directories as needed),
    and uses `LC::Check::directory` via `LC_Check`.

    Returns CHANGED if a change was made, SUCCESS if no changes were made
    and undef in case of failure (and the `fail` attribute is set).

    The return value in absence of failure is a dualvar with integer value
    SUCCESS/CHANGED, and the directory as string value
    (in particular relevant for temporary directories).

    Additional options

    - owner/group/mode/mtime : options for `CAF::Path::status`
    - temp

        A boolean if true will create a a temporary directory using
        **File::Temp::tempdir**.

        The directory name is the template to use (any trailing
        `X` characters will be replaced with random characters by `tempdir`;
        and the directory name will be padded up to at least 4 `X`).

        The `CLEANUP` option is also set (an removal
        attempt (incl. any files and/or subdirectries)
        will be made at the end of the program).

    - keeps\_state: boolean passed to `_get_noaction`.

- status

    Set the path stat options: `owner`, `group`, `mode` and/or `mtime`.

    This is a wrapper around `LC::Check::status`
    and executed with `LC_Check`.

    Returns CHANGED if a change was made, SUCCESS if no changes were made
    and undef in case of failure (and the `fail` attribute is set).

    Additional options

    - keeps\_state: boolean passed to `_get_noaction`.

- move

    Move/rename `src` to `dest`.

    The final goal is to make sure `src` does not exist anymore,
    not that `dest` exists after move (in particular, if `src`
    does not exist to start with, success is immediately returned,
    and no backup of `dest` is created).

    The &lt;backup> is a suffix for the cleanup of `dest`
    (and passed to `cleanup` method).

    (The basedir of `dest` is created using `directory` method.)

    Additional options

    - keeps\_state: boolean passed to `_get_noaction`.
