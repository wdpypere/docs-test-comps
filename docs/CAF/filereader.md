### NAME

CAF::FileReader - Class for only reading files in CAF applications.

Normal use:

    use CAF::FileReader;
    my $fh = CAF::FileReader->open ("my/path");
    while (my $line = <$fh>) {
       ### Do something
    }

### DESCRIPTION

This class should be used whenever a file is to be opened for reading,
and no modifications are expected.

Printing to this file is allowed, but changes will be discarded (in
effect, the `FileWriter` is `cancel`-ed.
