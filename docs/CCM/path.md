# NAME

EDG::WP4::CCM::Path - Path class

# SYNOPSIS

    $path = Path->new(["/hardware/memory/size"]);
    $string = $path->toString();
    $path = $path->down($string);
    $path = $path->up();

# DESCRIPTION

Module provides implementation of the Path class. Class is used
to manipulate absolute paths

- new ($path)

    create new object of Path type. Empty string is not
    allowed as an input parameter. If input parameter is not specified,
    Path is initialized to the root path ("/").

    $path is a string representation of the path as defined in the NVA-API
    Specification document

- toString ()

    get the string representation of path

- up ()

    removes last chunk of the path and returns it.
    if the path is already "/" then then methods
    rises an exception

- down ($chunk)

    add one chunk to a path, chunk cannot be compound path
    (it cannot contain "/" or be empty)

- merge (@subpaths)

    Return a new instance with optional subpaths added
