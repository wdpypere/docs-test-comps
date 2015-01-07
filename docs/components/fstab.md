### DESCRIPTION

The _fstab_ component manages the mount points in a node. It is able
to manipulate the fstab, and remount filesystems as specified by the
profile. It doesn't perform any dangerous operations, such as
formatting or partitioning. If you need so, use ncm-filesystems in
addition to this component.

It doesn't remove any filesystems specified under
`/software/components/fstab/protected_mounts`.

It uses the definition of file systems described in
https://twiki.cern.ch/twiki/bin/view/FIOgroup/TsiCDBBlockDevices

### SEE ALSO

[ncm-filesystems](https://metacpan.org/pod/ncm-filesystems)

Luis Fernando Muñoz Mejías, <Luis.Fernando.Munoz.M>

### POD ERRORS

Hey! **The above document had some coding errors, which are explained below:**

- Around line 37:

    Non-ASCII character seen before =encoding in 'Muñoz'. Assuming UTF-8
