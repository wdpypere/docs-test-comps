### NAME

EDG::WP4::CCM::Fetch

### SYNOPSIS

    $fetch = EDG::WP4::CCM::Fetch->new({PROFILE_URL => "profile_url or hostname",
                        CONFIG  => "path of config file",
                        FOREIGN => "1/0"});
    $fetch->fetchProfile();

### DESCRIPTION

Module provides Fetch class. This helps in retrieving XML profiles and
contexts from specified URLs. It allows users to retrieve local, as
well as foreign node profiles.

### Functions

- new()

        new({PROFILE_URL => "profile_url or hostname",
             CONFIG  => "path of config file",
             FOREIGN => "1/0"});

    Creates new Fetch object. Full url of the profile can be provided as
    parameter PROFILE\_URL, if it is not a url a profile url will be
    calculated using 'base\_url' config option in `/etc/ccm.conf`.  Path of
    alternative configuration file can be given as CONFIG.

    Returns undef in case of error.

- retrieve

    Stores $url into $cache if it's newer than $time, or if $self->{FORCE}
    is set.

    It returns undef in case of error, 0 if it there were no changes (the
    server returned a 304 code) and a `CAF::FileWriter` object with the
    downloaded contents if they had to be downloaded.

    Should be called ony by `download`

- download

    Downloads the files associated with $type (profile or context). In
    case of error it retries $self->{RETRIEVE\_RETRIES} times, falling back
    to a failover URL if necessary (thus up to 2\*$self->{RETRIEVE\_RETRIES}
    may happen.

    Returns -1 in case of error, 0 if nothing had to be retrieved (files
    in the server were older than our local cache) and a `CAF::FileWriter`
    object with the downloaded contents, if something was actually
    downloaded.

- fetchProfile()

    fetchProfile  fetches the  profile  from  profile  url and keeps it at
    configured area.  The  cache  root variable is set as
    $fetch\_handle{'CACHE\_ROOT'} which can further be passed to CacheManager
    object and use NVA-API to access Resources and Properties.

    If the profile is foreign, then the cache\_root configuration is expected
    to be just for this foreign host and unexpected behaviour will result
    if the cache\_root is shared. Only a single (most recent) copy of the
    foreign copy will be stored: previous versions will be removed. Foreign
    profiles do not use failover URLs: if the primary URL is unavailable,
    then the fetch will fail.

    Returns undef if it cannot fetch the profile due to a network error,
    \-1 in case of other failure, `SUCCESS` in case of successful fetch.

- setProfileFormat

    Define the profile format. If receives an argument, it will use it
    with no further questions. If not, it will try to derive it from the
    URL, being:

    - URLs ending in `xml` are for XML profiles.
    - URLs ending in `json` are for JSON profiles.

    and their gzipped equivalents.

- setNotificationTime()

    Define notification time, if profile modification time is greater than
    notification time then only the profile will be downloaded

- setTimeout()

    Define timeout after which profile fetch will be terminated.

- setProfileFailover()

    Define failover profile url
