### NAME

CAF::ReporterObject - singleton Reporter object class

### SYNOPSIS

    use CAF::ReporterObject;
    my $r=CAF::ReporterObject->instance();

    $r->report("whatever");
    $r->debug("blah blah");
    ...

### INHERITANCE

    CAF::Reporter
    CAF::Object

### DESCRIPTION

Provides a wrapper class to instantiate the Reporter as a singleton object.

#### Public methods

- instance(): ReporterObject

    returns the ReporterObject instance and creates it if
    neccessary. ReporterObject is a singleton.

- new(): throws error

    new() throws an error, as this method is not to be used (instead,
    create/get the singleton with instance())

#### Private methods

- \_initialize()

    initialize the singleton.

### SEE ALSO

CAF::Object, LC::Exception, CAF::Reporter
