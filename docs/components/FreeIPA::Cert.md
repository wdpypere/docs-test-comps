
### NAME

NCM::Component::FreeIPA::Cert adds certificate related methods to
[NCM::Component::FreeIPA::Client](https://metacpan.org/pod/NCM::Component::FreeIPA::Client).

#### Public methods

- cert\_request

    Request certificate using certificate request file `csr` and principal `principal`.

- get\_cert

    Given `serial`, retrieve the certificate and save it in file `crt`.
