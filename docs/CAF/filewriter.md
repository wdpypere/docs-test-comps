# NAME

CAF::FileWriter - Class for securely writing to files in CAF
applications.

# SYNOPSIS

Normal use:

    use CAF::FileWriter;
    my $fh = CAF::FileWriter->open ("my/path");
    print $fh "My text";
    $fh->close();

Aborting changes:

    use CAF::FileWriter;
    my $fh = CAF::FileWriter->open ("my/path");
    print $fh, "My text";
    $fh->cancel();
    $fh->close();

# DESCRIPTION

This class should be used whenever a file is to be opened for writing.

If the file already exists and the printed contents are the same as
the contents present on disk, the actual file won't be modified. This
way, timestamps will be kept.

It also provides a secure way of opening files, avoiding symlink
attacks.

In case of errors, changes can be cancelled, and nothing will happen
to disk.

Finally, the file names to be handled will be logged at the verbose
level.

## Gory details

This is just a wrapper class for `LC::Check::file`

## Public methods

- new

    Returns a new object. It accepts the file name as its first argument,
    and the next hash as additional options:

    - `log`

        The log object. If not supplied, no logging will be performed.

    - `owner`

        UID for the file.

    - `group`

        File's GID.

    - `mode`

        File's permissions.

    - `backup`

        Path for the backup file, if this one has to be re-written.

- open

    Synonimous of new.

- close

    Closes the file. If it has not been saved and it has not been
    cancelled, it checks its contents and perhaps re-writes it, in a
    secure way (not following symlinks, etc).

    Under a verbose level, it will show in the standard output a diff of
    the old and the newly-generated contents for this file before actually
    saving to disk. This diff will **not** be stored in any logs to prevent
    any leakages of confidential information (f.i. when writing to
    /etc/shadow).

- cancel

    Marks the printed contents as invalid. The existing file will not be
    altered.

- noAction

    Returns the NoAction flag value (boolean)

- stringify

    Returns a string with the contents of the file, so far. It overloads
    `""`, so it's now possible to do "$fh" and get the contents of the
    file so far.

## Private methods

- DESTROY

    Class destructor. Closes the file, perhaps saving it to disk.

# EXAMPLES

## Opening /etc/sudoers

This a part of what _ncm-sudo_ should do, if it used this module:

    my $fh = CAF::FileWriter->open ("/etc/sudoers", mode => 0440,
                                    log => $self);
    print $fh "User_Alias\t$_\n" foreach @{$aliases->{USER_ALIASES()}};
    print $fh "Runas_Alias\t$_\n" foreach @{$aliases->{RUNAS_ALIASES()}};
    ...
    $fh->close();

Which is actually simpler and safer than current code.

## Specifying owner and group

Owner and group are set at the time of creating the object:

    my $fh = CAF::FileWriter->open ("/some/file",
                                    owner => 100
                                    group => 200);
    print $fh "Hello, world!\n";
    # I don't like what I did, just drop the changes:
    $fh->cancel();
    $fh->close();

## Changing the default filehandle

If you don't want `STDOUT` as your default filehandle, you can just
`select` a `CAF::FileWriter` object:

    my $fh = CAF::FileWriter->open ("/some/file",
                                    owner => 100,
                                    group => 200);
    select ($fh);
    print "Hello, world!\n";
    $fh->close();
    select (STDOUT);

## Using here-documents

You can use them, as always:

    my $fh = CAF::FileWriter->open ("/some/file");
    print $fh <<EOF
    Hello, World!
    EOF
    $fh->close();

## Closing when destroying

If you forget to explictly close the `CAF::FileWriter` object, it
will be closed automatically when it is destroyed:

    my $fh = CAF::FileWriter->open ("/some/file");
    print $fh "Hello, world!\n";
    undef $fh;

# SEE ALSO

This package inherits from [IO::String(3pm)](http://man.he.net/man3pm/IO::String). Check its man page to
do powerful things with the already printed contents.

# TODO

This has became too heavy: in some circumstances, manipulating a file
involves opening it three times, reading it twice and executing two
commands. We probably need to drop LC::\* and do things in our own way.
