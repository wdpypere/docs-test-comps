
### DESCRIPTION

The _fstab_ component manages the mount points in a node. It is able
to manipulate `/etc/fstab`, and remount filesystems as specified by the
profile. It doesn't perform any dangerous operations, such as
formatting or partitioning. If you need so, use [filesystems](../components/filesystems.md) in
addition to this component.

It doesn't remove any filesystems specified under
`/software/components/fstab/protected_mounts`.
