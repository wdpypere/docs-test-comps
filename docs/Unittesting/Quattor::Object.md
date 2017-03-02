
####  warn\_is\_ok

By default, Perl warnings are mapped to failing tests.

#### add\_loghist

Add a log `message` for `type` to the log history.

#### reset\_loghist

Reset the log history.

#### loghist\_get

Return the array of log messages for `type`.

#### info

info-type logger, calls diag.
Arguments are converted in message, prefixed with 'INFO'.

#### verbose

verbose-type logger, calls note
Arguments are converted in message, prefixed with 'VERBOSE'.

#### report

report-type logger, calls note
Arguments are converted in message, prefixed with 'REPORT'.

#### debug

verbose logger, ignores debug level

#### warn

warn-type logger, calls diag
Arguments are converted in message, prefixed with 'WARN'.

#### error

error-type logger, calls diag
Arguments are converted in message, prefixed with 'ERROR'.

#### event

event handler, store the metadata and report added event

#### is\_verbose / is\_quiet / get\_debuglevel

Return the respective attributes (or 0 is undefined).

#### notok

Fail a test with message, use error to log the message.
Arguments are converted in message.

#### gather\_pan

Walk the `panpath` and gather all pan templates.

A pan template is a text file with an `.pan` extension;
they are considered 'invalid' when the `pannamespace` is not
correct.

Returns a reference to hash with key path
(relative to `relpath`) and value hashreference
with 'type' of pan templates and 'expected' relative filepath;
and an arrayreference to the invalid pan templates.

#### get\_template\_library\_core

Return path to `template-library-core` to allow "include 'pan/types';"
and friends being used in the templates (in particular the schema).

By default, the `template-library-core` is expected to be in the
parent or parent of parent directory as the current working directory.

One can also specify the location via the `QUATTOR_TEST_TEMPLATE_LIBRARY_CORE`
environment variable.

When `notok_on_missing` is true (or undefined), `notok` is called (i.e. test fails).

#### make\_target\_pan\_path

Create if needed the "target/pan" path in the current directory, and returns the
absolute pathname.
