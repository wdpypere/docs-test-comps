### Types

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
### Functions
