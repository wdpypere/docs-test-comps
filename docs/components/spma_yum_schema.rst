
Types
-----

 - `/software/spma/SOFTWARE_GROUP`
    - `/software/spma/SOFTWARE_GROUP/default`
        - Optional
        - Type: boolean
    - `/software/spma/SOFTWARE_GROUP/mandatory`
        - Optional
        - Type: boolean
    - `/software/spma/SOFTWARE_GROUP/optional`
        - Optional
        - Type: boolean
 - `/software/spma/spma_yum_main_options`
    - Description: Main configuration options for yum.conf.
    The cleanup_on_remove, obsoletes, reposdir and pluginpath are set internally.
    - `/software/spma/spma_yum_main_options/exclude`
        - Optional
        - Type: string
    - `/software/spma/spma_yum_main_options/installonly_limit`
        - Optional
        - Type: long
        - Range: 0..
    - `/software/spma/spma_yum_main_options/keepcache`
        - Optional
        - Type: boolean
    - `/software/spma/spma_yum_main_options/retries`
        - Optional
        - Type: long
        - Range: 0..
    - `/software/spma/spma_yum_main_options/timeout`
        - Optional
        - Type: long
        - Range: 0..
 - `/software/spma/component_spma_yum`
    - `/software/spma/component_spma_yum/fullsearch`
        - Optional
        - Type: boolean
    - `/software/spma/component_spma_yum/main_options`
        - Optional
        - Type: spma_yum_main_options
    - `/software/spma/component_spma_yum/plugins`
        - Optional
        - Type: spma_yum_plugins
    - `/software/spma/component_spma_yum/process_obsoletes`
        - Optional
        - Type: boolean
    - `/software/spma/component_spma_yum/proxytype`
        - Optional
        - Type: string
    - `/software/spma/component_spma_yum/run`
        - Optional
        - Type: legacy_binary_affirmation_string
    - `/software/spma/component_spma_yum/userpkgs_retry`
        - Optional
        - Type: boolean
    - `/software/spma/component_spma_yum/userpkgs`
        - Optional
        - Type: legacy_binary_affirmation_string
    - `/software/spma/component_spma_yum/reposdirs`
        - Description: List of external repo dirs to be included in addition to the one managed by this component.
        - Optional
        - Type: absolute_file_path
    - `/software/spma/component_spma_yum/filter`
        - Description: regexp pattern to install only matching (unescaped) package names.
      This is an advanced setting, and typically only used in a 2-stage software
      install like spmalight.
      When userpkgs is not defined, it runs as if userpkgs is true.
      (Caution: is userpkgs is false, it will very likely remove
      all non-matching packages. It is advised to remove the userpkgs attribute).
      Versionlocking is not affected by the filter (i.e. all packages are considered
      for version locking, not only the filtered ones).
        - Optional
        - Type: string
