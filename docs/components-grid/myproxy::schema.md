### Types

- `/software/myproxy/myproxy_component_policies`
    - `/software/myproxy/myproxy_component_policies/renewers`
        - optional
        - type: string
    - `/software/myproxy/myproxy_component_policies/retrievers`
        - optional
        - type: string
    - `/software/myproxy/myproxy_component_policies/keyRetrievers`
        - optional
        - type: string
    - `/software/myproxy/myproxy_component_policies/trustedRetrievers`
        - optional
        - type: string
- `/software/myproxy/myproxy_component`
    - `/software/myproxy/myproxy_component/flavor`
        - required
        - type: string
    - `/software/myproxy/myproxy_component/confFile`
        - optional
        - type: string
    - `/software/myproxy/myproxy_component/daemonName`
        - required
        - type: string
    - `/software/myproxy/myproxy_component/trustedDNs`
        - optional
        - type: string
    - `/software/myproxy/myproxy_component/authorizedDNs`
        - optional
        - type: myproxy_component_policies
    - `/software/myproxy/myproxy_component/defaultDNs`
        - optional
        - type: myproxy_component_policies

### Functions

- component_myproxy_options_valid