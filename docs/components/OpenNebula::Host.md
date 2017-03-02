
### NAME

`NCM::Component::OpenNebula::Host` adds `KVM` hosts support to
`NCM::Component::OpenNebula`.

#### Public methods

- manage\_hosts

    Adds or removes `Xen` or `KVM` hosts.

- disable\_host

    Disables failing OpenNebula `host`.
    This method is called when the `host` is not reachable from the `OpenNebula` server.
    Always displays a warning message.
    In that case the `host` is disabled in the scheduler.

- sync\_opennebula\_hosts

    Synchronise hosts `VMM` scripts.

- enable\_node

    Execute ssh commands required by OpenNebula
    also it configures `Ceph` client if necessary.
