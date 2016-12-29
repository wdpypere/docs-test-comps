
### NAME

NCM::modprobe - NCM modprobe configuration component

### SYNOPSIS

- Configure()

    The method configures the modprobe configuration file `/etc/modules.conf`
    for 2.4 kernels and configuration file `/etc/modprobe.d`/quattor.conf
    for 2.6 kernels. The method also creates a new initial ramdisk images for
    preloading modules for all the kernel releases installed in the node.

- Unconfigure()

    The method unconfigures the modprobe configuration file `/etc/modules.conf`
    for 2.4 kernels and configuration file `/etc/modprobe.d`/quattor.conf
    for 2.6 kernels. The method also creates a new initial ramdisk images for
    preloading modules for all the kernel releases installed in the node.

### RESOURCES

- `/software/components/modprobe/active` : boolean

    activates/deactivates the component.

- `/software/components/modprobe/modules` : list of module

    The modules item is a list of module\_type. The module type is base on
    the fields "name" name of the loadable module, "alias" alias for the
    loadable module, "options" options for the loadable module, "install"
    command to run when loading module, "remove" command to run when
    removing module and "blacklist" to disable a module.
