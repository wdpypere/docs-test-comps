
### NAME

NCM::Component::FreeIPA::NSS handles the certificates using `NSS`.

#### Public methods

- new

    Returns a NSS object with `nssdb`, accepts the following options

    - format: dbm or sql
    - realm: IPA realm, used for CA nick
    - cacrt: IPA CA crt location, default to `/etc/ipa/ca.crt`
    - csr\_bits: key size in bits for a new csr.
    - owner, group, mode: owner, group and permissions for nssdb and/or certs
    - log

        A logger instance (compatible with `CAF::Object`).

- setup\_nssdb

    Setup and initialise nssdb dirrectory

- setup

    Setup temporary workdir with 0700 permissions,
    and initialise nssdb using `setup_nssdb` method.

    Return SUCCESS on success, undef otherwise.

- add\_cert\_trusted

    Add trusted certificate with `nick` from file `crt`.

- add\_cert\_ca

    Add trusted CA certificate (nick and file via `canick` and `cacrt` attributes)

- add\_cert

    Add untrusted certificate to NSSDB with `nick` from file `cert`.

- has\_cert

    Check if certificate for `nick` exists in NSSDB.

    If an ipa client instance is passed,
    also check if the certificate is known in FreeIPA.

- get\_cert

    Extract the certificate from NSSDB for `nick` to file `cert`
    with owner/group/mode options..

- make\_cert\_request

    Make a certificate request for `fqdn` and optional `dn`,
    return filename of the CSR.
    (Used DN is `<CN=<fqdn`,O=&lt;realm>>>).

- ipa\_request\_cert

    Use `NCM::Component::FreeIPA::Client` instance `ipa` to make the certificate request
    using `csr` file. The certificate is stored in `crt` file.

    (The `ipa` instance should be usable, e.g. the correct kerberos
    environment is already setup).

    Return 1 on success, undef otherwise.

- get\_privkey

    Retrieve the private key from certificate with nick `nick` and
    save it in the file `key` with owner/group/mode options.

- get\_cert\_or\_key

    Given `type`, retrieve the cert of private key
    from certificate with nick `nick` and
    save it in the file `fn` with owner/group/mode options.
