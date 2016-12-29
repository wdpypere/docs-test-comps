
### NAME

NCM::Component::FreeIPA::Group adds group related methods to
[NCM::Component::FreeIPA::Client](https://metacpan.org/pod/NCM::Component::FreeIPA::Client).

#### Public methods

- add\_group

    Add a group with name `gid`.

    - Arguments
        - gid: group gid
    - Options (passed to `Net::FreeIPA::API::api_group_add`).
        - gidnumber

- add\_group\_member

    Add the members to group `gid` using options
    (options are passed to `api_group_add_member`).
