### Types

- `/software/grub/type_grub_password`
    - decription: 
 the crypted password can be supplied either in the password field
 OR, alternatively, within a file. this could be useful if putting the crypted
 password in the profile is undesirable. for this the file will be scanned
 and the password will be taken from the second field in a colon delimited
 line, where the first field matches the file_user parameter.

    - `/software/grub/type_grub_password/option`
        - required
        - type: string
    - `/software/grub/type_grub_password/password`
        - optional
        - type: string
    - `/software/grub/type_grub_password/enabled`
        - optional
        - type: boolean
    - `/software/grub/type_grub_password/file`
        - optional
        - type: string
    - `/software/grub/type_grub_password/file_user`
        - required
        - type: string
- `/software/grub/type_kernel`
    - `/software/grub/type_kernel/kernelpath`
        - required
        - type: string
    - `/software/grub/type_kernel/kernelargs`
        - optional
        - type: string
    - `/software/grub/type_kernel/multiboot`
        - optional
        - type: string
    - `/software/grub/type_kernel/mbargs`
        - optional
        - type: string
    - `/software/grub/type_kernel/initrd`
        - optional
        - type: string
    - `/software/grub/type_kernel/title`
        - optional
        - type: string
    - `/software/grub/type_kernel/fullcontrol`
        - optional
        - type: boolean
- `/software/grub/component_grub_type`
    - `/software/grub/component_grub_type/prefix`
        - optional
        - type: string
    - `/software/grub/component_grub_type/args`
        - optional
        - type: string
    - `/software/grub/component_grub_type/kernels`
        - optional
        - type: type_kernel
    - `/software/grub/component_grub_type/password`
        - optional
        - type: type_grub_password

