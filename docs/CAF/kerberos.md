### NAME

CAF::Kerberos - Class for Kerberos handling using [GSSAPI](https://metacpan.org/pod/GSSAPI).

### DESCRIPTION

This class handles Kerberos tickets and some
utitlities like kerberos en/decryption.

To create a new ticket for principal SERVICE/host@REALM
(using default (server) keytab for the TGT), you can use

    my $krb = CAF::Kerberos->new(
        principal => 'SERVICE/host@REALM',
        log => $self,
    );
    return if(! defined($krb->get_context()));

    ### set environment to temporary credential cache
    ### temporary cache is cleaned-up during destroy of $krb
    local %ENV;
    $krb->update_env(\%ENV);

#### Methods

- `_initialize`

    Initialize the kerberos object. Arguments:

    Optional arguments

    - `log`

        A `CAF::Reporter` object to log to.

    - lifetime, keytab

        Ticket lifetime and keytab are passed to `update_ticket_options` method.

    - primary, instances, realm, principal

        Principal primary, instances, realm and principal are passed to `update_principal` method.

- update\_ticket\_options

    Update ticket details using optional named arguments
    (and set the keytab ENV attributes).

    - lifetime

        Requested lifetime. (There is no verification if the actual lifetime is
        this long).

    - keytab

        Set the keytab to use to create the TGT.

- update\_principal

    Set the principal details (primary, instances and/or realm)
    using following optional named arguments

    - primary

        The primary component (i.e. username or service) (cannot be empty string).

    - instances

        Array reference with instances for the principal

    - realm

        The realm.

    - principal

        The principal string, will be split in above components.
        Any individual component specified will precede the value from
        this string.

- create\_credential\_cache

    Create the credential cache and add the `KRB5CCNAME` to the temp environment.
    Returns SUCCESS on success, undef otherwise (see fail attribute).

- get\_context

    Create a `GSSAPI::Context`.

    Following options are supported

    - name

        The `GSSAPI::Name` instance to use. If undef,
        `get_name` method will be used to create one.

    - iflags

        Input flags/bits for the Context to create to support certain service options.
        (See e.g. `_spnego_iflags`). Defaults to 0.

    - itoken

        Input token (`q{}` is used if not defined).

    - usecred

        Boolean, if true, (try to) get a credential before getting the context.

    Returns the output token in case of succes, undef in case of failure.

- get\_cred

    Acquire a `GSSAPI::Cred` instance.

    Following options are supported

    - name

        The `GSSAPI::Name` instance to use. If undef,
        `get_name` method will be used to create one.

    - usage

        Specify the credential usage, one of `GSSAPI` constants
        `GSS_C_INITIATE`, `GSS_C_ACCEPT` or (default) `GSS_C_BOTH`.

    Returns the `GSSAPI::Cred` instance in case of succes, undef in case of failure.

- get\_hrname

    Return human readablename from `GSSAPI::Name` instance.
    Return undef on failure (and set `fail` attribute with reason).

- get\_name

    Return a imported `GSSAPI::Name` instance.

    Returns undef on failure.

    Optional `principal` hashref is passed to `_principal_string`.

- DESTROY

    On DESTROY, following cleanup will be triggered

    - Cleanup of credential cache

- \_principal\_string

    Convert the principal hashref into a principal string.

    Optional `principal` hashref can be passed, if none is provided,
    use the instance `$self-`{principal}>.

    Returns the principal string, undef in case or problem.

- \_split\_principal\_string

    Split a principal string in primary, instances and realm components.

    Returns a hashref with the components, undef incase the string is invalid.

- \_spnego\_iflags

    Create the SPNEGO iflags for Context instance.

    Optional `$delegate` boolean.

- \_gss\_decrypt

    Given `token`, decrypt `inbuf` that is encrypted with GSSAPI wrap'ping.
    Returns human readable `GSSAPI::Name` and decrypted output buffer.
    Returns undef on failure.

- \_gss\_status

    Evaulatues `status`: on success, returns SUCCESS reports with `verbose`, on failure
    returns `fail` (The fail message is set in the `fail` attribute).

    Optional `text` can be used to construct the message prefix.

- \_gssapi\_{init,accept,wrap,unwrap,import,display}

    Interfaces to GSSAPI methods returning a `GSSAPI::Status` instance.

    Given an `instance` of `GSSAPI::Context` (for accept,init,valid\_time\_left,wrap,unwrap)
    or `GSSAPI::Name` (for display,import), call the metod on the instacne
    with the remaining arguments. The returned status is processed by
    `_gss_status`.

    Returns undef in case of failure (with message in `fail` attribute),
    SUCCESS otherwise.

- \_process

    Run arrayref $cmd via `CAF::Process-`new->output> in updated environment.

    Returns the output.

- \_kinit

    Obtain the `TGT` using kinit, using the credential
    cache specified in the 'KRB5CCNAME' environment variable.

    Principal used is generated via `_principal_string`.

    Returns SUCCESS on success, undef otherwise.
