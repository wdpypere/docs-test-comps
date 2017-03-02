
### SYNOPSIS

    use Test::Quattor qw(test_profile1 test_profile2...);

### DESCRIPTION

`Test::Quattor`

Module preparing the environment for testing Quattor code.

### LOADING

When loading this module it will compile any profiles given as arguments. So,

    use Test::Quattor qw(foo);

will trigger a compilation of `src/test/resources/foo.pan` and the
creation of a binary cache for it. The compiled profile will be stored
as `target/test/profiles/foo.json`, while the cache will be stored in
under `target/test/profiles/foo/`.

This binary cache may be converted in an
`EDG::WP4::CCM::CacheManager::Configuration` object using the
`get_config_for_profile` function.

### INTERNAL INFRASTRUCTURE

#### Module variables

This module provides backup methods for several `CAF` modules. They
will prevent tests from actually modifying the state of the system,
while allowing an NCM component to follow a realistic execution path.

These backups record what files are being written, what commands are
being run, and allow for inspection by a test.

This is done with several functions, see **Redefined functions** below,
that control the following variables:

- QUATTOR\_TEST\_LOG\_DEBUGLEVEL

    If the environment variable QUATTOR\_TEST\_LOG\_DEBUGLEVEL is set, the unittests
    will run with this debuglevel (0-5). Otherwise the default loglevel is 'verbose'.

    To actually see the verbose or debug output, you need to run prove with verbose flag
    (e.g. by passing `-Dprove.args=-v` or by setting `-v` in the `<~/.proverc`>).

- `$log_cmd`

    A boolean to enable logging of each command that is run via CAF::Process.
    Can also be set via the QUATTOR\_TEST\_LOG\_CMD environment variable.

- `$log_cmd_missing`

    A boolean to log each cmd that has output mocked but has no output set.
    Can also be set via the QUATTOR\_TEST\_LOG\_CMD\_MISSING environment variable.

- `%files_contents`

    Contents of a file after it is closed. The keys of this hash are the
    absolute paths to the files.

- `%commands_run`

    CAF::Process objects being associated to a command execution.

- `%commands_status`

    Desired exit status for a command. If the command is not present here,
    it is assumed to succeed.

- `%desired_outputs`

    When we know the component will call `CAF::Process::output` and
    friends, we prepare here an output that the component will have to
    deal with.

- `%desired_err`

    When the component may analyse the standard error of a component, we
    supply it through this hash.

- `%desired_file_contents`

    Optionally, initial contents for a file that should be "edited".

- `@command_history`

    CAF::Process commands that were run.

- `caf_path`

    A hashref with [Path](../CAF/Path.md) methods and arrayref of reference of used arguments

- `NoAction`

    Set `Test::Quattor::NoAction` to override `CAF::Object::NoAction`
    in any of the mocked `Test::Quattor` methods (where relevant, e.g.
    mocked FileWriter and FileEditor).

    E.g. if you want to run tests with `CAF::Object::NoAction` not set
    (to test the behaviour of regular `CAF::Object::NoAction`).

- `caf_file_close_diff`

    A boolean to mimic the regular (i.e. when no `NoAction` is set) behaviour of a
    [FileWriter](../CAF/FileWriter.md) or [FileEditor](../CAF/FileEditor.md) `close` (it returns whether or not the
    file changed). With `NoAction` set, this check is skipped and `undef` is returned.

    With this boolean set to true, contents difference is reported ( but not any changes
    due to e.g. file permissions or anything else checked with `LC::Check::file)`.

    Defaults to false (to keep regular `NoAction` behaviour).

#### Redefined functions

In order to achieve this, the following functions are redefined
automatically:

- `CAF::Process::{run,execute,output,trun,toutput}`

    Prevent any command from being executed.

- `CAF::FileWriter::open`

    Overriding this function allows us to inspect its contents after the
    unit under tests has released it.

- `CAF::FileEditor::new`

    It's just calling CAF::FileWriter::new, plus initialising its contnts
    with the value of the appropriate entry in `%desired_file_contents`

- `CAF::Reporter::debug`

    Checks that each debug() call starts with a debuglevel between 0 and 5.

- `CAF::Reporter::debug`

    Checks that each debug() call starts with a debuglevel between 0 and 5.

- `IO::String::close`

    Prevents the buffers from being released when explicitly closing a file.

- `CAF::Path::file_exists`

    Return the mocked `is_file`

- `CAF::Path::directory_exists`

    Return the mocked `is_directory`

- `CAF::Path::any_exists`

    Return the mocked `is_any`

- `CAF::Path::directory`

    Return directory name unless mocked `make_directory` or mocked `LC_Check` fail.

    (The `temp` is ignored wrt creating the directory name).

- `CAF::Path::LC_Check`

    Store args in `caf_path` using `add_caf_path`.

- `CAF::Path::cleanup`

    `remove_any` and store args in `caf_path` using `add_caf_path`.

- `CAF::Path::move`

    `remove_any` and store args in `caf_path` using `add_caf_path`.

### FUNCTIONS FOR EXTERNAL USE

The following functions are exported by default:

- `get_file`

    Returns the object that has manipulated `$filename`

- `set_file_contents`

    For file `$filename`, sets the initial `$contents` the component shuold see.

- `get_command`

    Returns all the information recorded about the execution of `$cmd`,
    if it has been executed. This is a hash reference in which the
    `object` element is the [Process](../CAF/Process.md) object itself, and the
    `method` element is the function that executed the command.

- `set_command_status`

    Sets the "exit status" we'll report for a given command.

- `set_desired_output`

    Sets the standard output we'll return when the caller issues `output`
    on this command

- `set_desired_err`

    Sets the standard error we'll receive when the caller issues
    `execute` on this command.

- `command_history_reset`

    Reset the command history to empty list.

- `command_history_ok`

    Given an arrayref of `required_commands`,
    it checks the `@command_history` if all commands were
    called in the given order (it allows for other commands to exist inbetween).
    The commands are interpreted as regular expressions.

    E.g. if `@command_history` is (x1, x2, x3) then
    `command_history_ok([x1,X3])` returns 1
    (Both x1 and x3 were called and in that order,
    the fact that x2 was also called but not checked is allowed.).
    `command_history_ok([x3,x2])` returns 0 (wrong order),
    `command_history_ok([x1,x4])` returns 0 (no x4 command).

    A second arrayref of `forbidden_commands` can be given,
    and the `@command_history` is then first checked that
    none of those commands occured.
    If you only want to check the non-occurence of commands,
    pass an undef as the first argument
    (and not an empty arrayref).

- `set_service_variant`

    Sets the [Service](../CAF/Service.md) variant to the one given in the command line:

    - `linux_sysv`

        Linux SysV, e.g, `/sbin/service foo start`

    - `linux_systemd`

        Linux, Systemd variant.

    - `solaris`

        Solaris and SMF variant.

    `Test::Quattor` defaults to `linux_sysv`.

- `force_service_variant`

    Force the variant by bypassing [Service](../CAF/Service.md) `AUTOLOAD` magic
    and defining the methods
    via glob assignments in the namespace.

    The first argument is the `$variant` to use.

    When testing subclassed [Service](../CAF/Service.md),
    the second (optional) argument is the subclass, followed by
    all other arguments as additional non-standard actions.

- `set_caf_file_close_diff`

    Set the `caf_file_close_diff` boolean.

- sane\_path

    sanitize path by

    - squash multiple '/' into one
    - remove all trailing '/'

- is\_file

    Test if given `$path` is a mocked file

- is\_directory

    Test if given `$path` is a mocked directory

- is\_any

    Test if given `path` is known (as file or directory or anything else)

- make\_directory

    Add a directory to the mocked directories.
    If `rec` is true or undef, also add all underlying directories.

    If directory already exists and is a directory, return SUCCESS (undef otherwise).

- remove\_any

    Recursive removal of a `path` from the files\_contents / desired\_file\_contents

- move

    move `src` to `dest`. If `backup` is defined and not empty string,
    move `dest` to backup (`backup` is a suffix).

- add\_caf\_path

    Add array of arguments to `caf_path` hashref using `name`

- reset\_caf\_path

    Reset `caf_path` ref. If `name` is defined, only reset that cache.

### BUGS

Probably many. It does quite a lot of internal black magic to make
your executions safe. Please ensure your component doesn't try to
outsmart the `CAF` library and everything should be fine.
