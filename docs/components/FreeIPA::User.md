
### NAME

NCM::Component::FreeIPA::User adds host related methods to
[NCM::Component::FreeIPA::Client](https://metacpan.org/pod/NCM::Component::FreeIPA::Client).

#### Public methods

- add\_user

    Add a user. If the user already exists, return undef.

    - Arguments
        - uid: User uid
    - Options (passed to `Net::FreeIPA::API::api_user_add`).
        - homedirectory
        - gecos
        - loginshell
        - uidnumber
        - gidnumber
        - ipasshpubkey

- disable\_user

    Disable a user with `uid`.

- remove\_user

    Remove the user `uid`  (preserve=1).

- user\_passwd

    Reset and return a new random password for user `uid`.
    Returns undef if the user doesn't exist.
