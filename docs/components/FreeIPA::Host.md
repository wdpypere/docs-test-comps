
### NAME

NCM::Component::FreeIPA::Host adds host related methods to
[FreeIPA::Client](../components/FreeIPA::Client.md).

#### Public methods

- add\_host

    Add a host. If the host already exists, return undef.

    - Arguments
        - fqdn: FQDN hostname
    - Options (passed to `Net::FreeIPA::API::api_host_add`).
        - ip\_address: IP to configure DNS entry
        - macaddress: macaddress

- disable\_host

    Disable a host with `fqdn` hostname.

- remove\_host

    Remove the host `fqdn`.

- host\_passwd

    Reset and return the one-time password for host `fqdn`.
    Returns undef if the host already has a keytab or if it doesn't exist.
