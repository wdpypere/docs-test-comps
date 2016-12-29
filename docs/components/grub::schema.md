
### Types

 - `/software/grub/type_grub_password`
    - Description: 
 the crypted password can be supplied either in the password field
 OR, alternatively, within a file. this could be useful if putting the crypted
 password in the profile is undesirable. for this the file will be scanned
 and the password will be taken from the second field in a colon delimited
 line, where the first field matches the file_user parameter.

    - `/software/grub/type_grub_password/option`
        - Optional
        - Type: string
    - `/software/grub/type_grub_password/password`
        - Optional
        - Type: string
    - `/software/grub/type_grub_password/enabled`
        - Optional
        - Type: boolean
    - `/software/grub/type_grub_password/file`
        - Optional
        - Type: string
    - `/software/grub/type_grub_password/file_user`
        - Optional
        - Type: string
 - `/software/grub/type_kernel`
    - `/software/grub/type_kernel/kernelpath`
        - Optional
        - Type: string
    - `/software/grub/type_kernel/kernelargs`
        - Optional
        - Type: string
    - `/software/grub/type_kernel/multiboot`
        - Optional
        - Type: string
    - `/software/grub/type_kernel/mbargs`
        - Optional
        - Type: string
    - `/software/grub/type_kernel/initrd`
        - Optional
        - Type: string
    - `/software/grub/type_kernel/title`
        - Optional
        - Type: string
    - `/software/grub/type_kernel/fullcontrol`
        - Optional
        - Type: boolean
 - `/software/grub/component_grub_type`
    - `/software/grub/component_grub_type/prefix`
        - Optional
        - Type: string
    - `/software/grub/component_grub_type/args`
        - Optional
        - Type: string
    - `/software/grub/component_grub_type/kernels`
        - Optional
        - Type: type_kernel
    - `/software/grub/component_grub_type/password`
        - Optional
        - Type: type_grub_password
