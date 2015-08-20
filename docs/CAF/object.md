# NAME

CAF::Object - provides basic methods for all CAF objects

# SYNOPSIS

    use vars qw (@ISA);
    use LC::Exception qw (SUCCESS throw_error);
    use CAF::Object;
    ...
    @ISA = qw (CAF::Object ...)
    ...
    sub _initialize {
      ... initialize your component
      return SUCCESS; # Success
    }

# INHERITANCE

none.

# DESCRIPTION

**CAF::Object** is a base class which provides basic functionality to
CAF objects.

All other CAF objects should inherit from it.

All CAF classes use this as their base class and inherit their class
constructor "new" from here. Sub-classes should implement all their
constructor initialisation in an "\_initialize" method which is invoked
from this base class "new" constructor. Sub-classes should NOT need to
override the "new" class method.



## Public methods

- new
- noAction

    Returns the NoAction flag value (boolean)

## Private methods

- \_initialize

    This method must be overwritten in a derived class

- error, warn, info, verbose, debug, report

    Convenience methods to access the log instance that might 
    be passed during initialisation and set to $self->log.

    (When constructing classes via multiple inheritance, 
    `CAF::Reporter` should precede `CAF::Object` if you want 
    to use an absolute rather than a conditional logger). 
