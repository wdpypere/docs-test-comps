# NAME

    CCM::TextRender - Class for rendering structured text using Element instances

# DESCRIPTION

This class is an extension of the `CAF::TextRender` class; with the main
difference the support of a `EDG::WP4::CCM:Element` instance as contents.

## Private methods

- `_initialize`

    Initialize the process object. Arguments:

    - module

        The rendering module to use (see `CAF::TextRender` for details).

    - contents

        `contents` is either a hash reference holding the contents to pass to the rendering module;
        or a `EDG::WP4::CCM:Element` instance, on which `getTree` is called with any `element`
        options.

    All optional arguments from `CAF::TextRender` are supported unmodified:

    - log
    - includepath
    - relpath
    - eol
    - usecache
    - ttoptions

    Extra optional arguments:

    - element

        A hashref holding any `getTree` options to pass. These can be the
        anonymous convert methods `convert_boolean`, `convert_string`,
        `convert_long` and `convert_double`; or one of the
        predefined convert methods (key is the name, value a boolean
        wheter or not to use them).

        The `convert_` methods are added as last methods.

        The predefined convert methods are:

        - cast

            Convert the scalar values to a more exact internal representation.
            The internal representaiton is important when passed on to other
            non-pure perl code, in particular the `XS` modules like `JSON::XS`
            and `YAML::XS`.

        - json

            Enable JSON output, in particular JSON boolean (`cast` is implied,
            so the other types should already be in proper format).
            This is automatically enabled when the json
            module is used (and not explicitly set).

        - yaml

            Enable YAML output, in particular YAML boolean (`cast` is implied,
            so the other types should already be in proper format).
            This is automatically enabled when the yaml
            module is used (and not explicitly set).

        - yesno

            Convert boolean to (lowercase) 'yes' and 'no'.

        - YESNO

            Convert boolean to (uppercase) 'YES' and 'NO'.

        - truefalse

            Convert boolean to (lowercase) 'true' and 'false'.

        - TRUEFALSE

            Convert boolean to (uppercase) 'TRUE' and 'FALSE'.

        - doublequote

            Convert string to doublequoted string.

        - singlequote

            Convert string to singlequoted string.

        Other `getTree` options

        - depth

            Only return the next `depth` levels of nesting (and use the
            Element instances as values). A `depth == 0` is the element itself,
            `depth == 1` is the first level, ...

            Default or depth `undef` returns all levels.

- ccm\_format

    Returns the CCM::TextRender instance for predefined `format` and `element`.
    Returns undef incase the format is not defined. An array with valid formats is
    exported via `@CCM_FORMATS`.

    Supported formats are:

    - json
    - yaml
    - pan
    - pancxml

    Usage example:

        use EDG::WP4::CCM::TextRender qw(ccm_format);
        my $format = 'json';
        my $element = $config->getElement("/");
        my $trd = ccm_format($format, $element);

        if (defined $trd->get_text()) {
            print "$trd";
        } else {
            $logger->error("Failed to textrender format $format: $trd->{fail}")
        }
