
### NAME

EDG::WP4::CCM::DB

### SYNOPSIS
    # Class style
    my $db = EDG::WP4::CCM::DB->new($prefix, %opts);
    # Write the hashref to the database file
    $db->write($hashref);
    # Open the database and tie to hashref
    $db->open($hashref);

    # Direct read access to database (combines new and open)
    $success = EDG::WP4::CCM::DB::read($hashref, $prefix);

### DESCRIPTION

This is a wrapper around all access to the profile database
format, which copes with multiple possible data formats.

### Methods

- new / \_initialize

    Create a new DB instance using `prefix`, the filename without extension
    (will be used by both the `.db` file itself and a `.fmt` format description).

    Optional parameters

    - log

        A [Reporter](../CAF/Reporter.md) instance for logging/reporting.

- test\_supported\_format

    Test if `dbformat` is a supported format.

    Returns SUCCESS on success, undef on failure (and sets `fail` attribute).

- write

    Given a hashref `hashref`, write out the
    hash in a database format `dbformat`.
    (If `dbformat` is not defined, the
    default format `DB_File` will be used).

    Once successfully written, the `hashref` will be
    untied and does not remain connected to the
    persistent storage.

    `perms` is an optional hashref with the file permissions
    for both database file and format description
    (owner/mode/group, [FileWriter](../CAF/FileWriter.md) style).

    Returns undef on success, a string with error message otherwise.

- open

    Open the database file.

    The format of the database file will be determined by reading
    the format file. If that file does not exist, then
    default format `DB_File` will be used.

    Returns undef on success, a string with error message otherwise.

    On success, the `hashref` will be tied to the specified database.

### Functions

- read\_db

    Given `hashref` and `prefix`, create a new instance
    using `prefix` (and any other options)
    and return the `open`ed database with hashref.

    `read_db` function is exported

- read

    An alias for read\_db (not exported, kept for legacy).
