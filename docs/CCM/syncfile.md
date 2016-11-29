### NAME

EDG::WP4::CCM::SyncFile

### SYNOPSIS

    $gl = SyncFile->new ("global.lock");
    $gl -> write ("yes");
    $locked  = $file -> read ();

### DESCRIPTION

SyncFile module provides read/write access to
cid files and global.lock file.

- read ()

    read contents of the file. It reads the first line of the file and
    removes \\n.  If the contents of file does not contain "/n" at the end,
    function behaviour is not guaranteed, most likely it chop last
    character.

- write ($contents)

    remove and write contents of the file. It adds \\n at the and of the
    contents.

- get\_file\_name ()

    get file name

- new

    create new SyncFile object where $file\_name is the name of the sync
    file
