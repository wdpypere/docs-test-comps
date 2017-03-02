
### DESCRIPTION

Module to help mock the namespace

### USAGE

E.g. to fake NCM:: namespace provided by the 'ncm' namespace

    BEGIN {
        use Test::Quattor::Namespace qw(ncm);
    }

    ...
    use NCM::Component
    ...

#### Variables

- inc\_orig

    `$inc_orig` holds arrayref to a copy of `@INC` when
    `INC_insert_namespace` was first called.

- inc\_history

    `$inc_history` is an arrayref with copy of all references of all `@INC`s modified

- ignore

    Hashref with namespaces to ignore (if value is true) when `INC_insert_namespace`
    is used.

#### Functions

- INC\_insert\_namespace

    Setup @INC so NCM::Component is provided by Test::Quattor
    Returns modified @INC as reference.
