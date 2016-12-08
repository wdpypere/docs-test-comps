### NAME

spma-run - Executes command output from ncm-spma component

### SYNOPSIS

**spma-run** \[**--cmdfile** _file_\] \[**--forcelock**\] \[**--ignorelock**\]
            \[**--logfile** _file_\] \[**--retries** _n_\]
            \[**--timeout** _secs_\] \[**--debug** _n_\] \[**--quiet**\]
            \[**--verbose**\] \[**--help**\] \[**--man**\] \[**--version**\]
            {**--execute**|**--noaction**|
               **--get-be-name**|**--get-install**|**--get-reject**}

### DESCRIPTION

**spma-run --execute** executes the package changes determined by the
Quattor NCM **spma** configuration component.  Currently supported
for IPS packages on Solaris 11 only.

Alternatively, provide the **--noaction** argument instead, and no changes
will be made.  See description of **--noaction** in **OPTIONS** below.

The output file from **ncm-spma** provides all of the
arguments required for a **pkg install** command, including
the name of the boot environment that will be created.  It is
recommended that **ncm-ncd -configure spma** is run immediately
prior to executing **spma-run** so that the commands are
up-to-date with the current system state.

### RETURN VALUE

**spma-run --execute** returns 1 if no changes were made, or 0 if changes
have been made indicating that a new boot environment has
been created with some packaging differences, or >1 if an error
occurred.

In **noaction** mode returns 1 if no changes would have been made,
or 0 if changes would have been made, or >1 if an error occurred.

### OPTIONS

The following options are supported:

- **--cmdfile** _file_

    By default, **spma-run** obtains the name of the output file
    to process by running **ncm-query** and looking at the
    **/software/components/spma/cmdfile** resource.

    This option allows the command filename to be overridden,
    in which case **ncm-query** will not be executed.

- **--debug** _n_

    Set the debugging level.

- **--execute**

    Enables run mode.  Live changes will be made on the system.

- **--forcelock**

    Take over application lock forcibly.  Use with care.

- **--get-be-name**

    Return name of boot environment that would be created if any
    package updates were to be made, but make no changes.  The name
    of the BE can only be determined if **ncm-spma** was provided
    with one via the Quattor host profile.

- **--get-install**

    Return list of package names that would be passed to the **pkg install**
    command.

- **--get-reject**

    Return list of package names that would be passed via **--reject**
    arguments to the **pkg install** command.

- **--help**

    Display help page.  See also --man option.

- **--ignorelock**

    Ignore application lock.  Use with care.

- **--logfile** _file_

    By default, **spma-run** logs to **/var/log/spma-run.log**.  This
    option elects a different log file.

- **--man**

    Display this man page.

- **--noaction**

    Runs the **pkg install** command with the **-n** option to
    make no changes but only determine if any changes would
    have been made, and if so, the **pkg install** command that
    would have been executed and the name of the boot environment
    that would have been created.

    Nothing is written to the log file if this option is given.

- **--quiet**

    Suppresses output to stdout.

- **--retries** _n_

    By default **spma-run** will retry up to 10 times if the application
    is locked by another process invocation.  This option amends the number
    of retries.

- **--timeout** _secs_

    By default **spma-run** will wait 30 seconds between retries if the
    application is locked by another process invocation.  This option amends
    the timeout.

- **--verbose**

    Display more detailed output on operations performed.

- **--version**

    Display version number.

### FILES

- **/var/log/spma-run.log**

    Default log file.
