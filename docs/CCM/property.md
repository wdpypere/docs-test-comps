# NAME

EDG::WP4::CCM::Property - Property class

# SYNOPSIS

    $string = $property->getStringValue();
    $double = $property->getDoubleValue();
    $long = $property->getLongValue();
    $boolean = $property->getBooleanValue();

# DESCRIPTION

The class Property is a derived class of Element class, and implements
methods that are specific to Properties, that is, simple values
like strings or numbers that form the leaves of the configuration
tree.

- getStringValue()

    Return the property's string value,
    raising an exception if the value is not an string or fetch

- getDoubleValue()

    Return the property's double value,
    raising an exception if the value is not a double

- getLongValue()

    Return the property's long value,
    raising an exception if the value is not a long

- getBooleanValue()

    Return the property's boolean value,
    raising an exception if the value is not a boolean
