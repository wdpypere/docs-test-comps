
### NAME

NCM::Component::FreeIPA::Service adds service related methods to
[NCM::Component::FreeIPA::Client](https://metacpan.org/pod/NCM::Component::FreeIPA::Client).

#### Public methods

- add\_service

    Add a service with name `name`.

- add\_service\_host

    Add a per-host service `name` for host `host`
    (actual service name will `<<name`/&lt;host>>>).

    Add host `host` to list of hosts that can manage this service.