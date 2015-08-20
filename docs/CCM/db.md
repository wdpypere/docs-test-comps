# NAME

EDG::WP4::CCM::DB

# SYNOPSIS

    $success = EDG::WP4::CCM::DB->read($HASHREF, $PREFIX);

# DESCRIPTION

This is a wrapper around all access to the profile database
format, which copes with multiple possible data formats.

# Functions

- write ($HASHREF, $PREFIX, $FORMAT)

    Given a reference to a hash, write out the
    hash in a database format. The specific format
    to use should be passed in as a string value
    of DB\_File, GDBM\_File or CDB\_File. Once
    successfully written, the HASHREF will be
    untied and does not remain connected to the
    persistent storage.

    The return value will be undef if no errors
    were found, else a string error message will
    be returned.

- read ($HASHREF, $PREFIX)

    Open the database file named by the prefix (the prefix
    is the full filename, without any extension). The format
    of the database file will be determined by reading the
    file ${PREFIX}.fmt. If that file does not exist, then
    DB\_File will be used as a default.

    The routine will return an error message if there
    is a failure, else undef. If there is no errror, then
    the HASHREF will be tied to the specified database.
