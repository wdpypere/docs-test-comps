### DESCRIPTION

The _aiiserver_ component manages the configuration of an AII
(Automated Installation Infrastructure) server.

### STRUCTURE

The following fields are provided:

- `/software/components/aiiserver/aii-shellfe`

    Configures the aii-shellfe tool. See the schema for more information.

- `/software/components/aiiserver/aii-dhcp`

    Configures the aii-dhcp legacy tool. See the schema for more information.

    This components also uses configuration parameters related to https from [ncm-ccm](https://metacpan.org/pod/ncm-ccm): ca\_dir, ca\_file, cert\_file, key\_file.
