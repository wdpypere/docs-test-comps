
### NAME

`NCM::Component::OpenNebula::Ceph` adds `Ceph` backend support to
`NCM::Component::OpenNebula::Host`.

#### Public methods

- enable\_ceph\_node

    Configures `Ceph` client and
    set the `Ceph` key in each host.

- set\_ceph\_secret

    Sets the `Ceph` secret to be used by `libvirt`.

- set\_ceph\_keys

    Sets the `Ceph` keys to be used by `libvirt`.

- detect\_ceph\_datastores

    Detects any OpenNebula `Ceph` datastore setup.
