### Types

- `/software/lcas/lcas_component_plainfile_content`
    - `/software/lcas/lcas_component_plainfile_content/path`
        - required
        - type: string
    - `/software/lcas/lcas_component_plainfile_content/noheader`
        - required
        - type: boolean
    - `/software/lcas/lcas_component_plainfile_content/content`
        - optional
        - type: string
- `/software/lcas/lcas_component_modulespec`
    - `/software/lcas/lcas_component_modulespec/path`
        - required
        - type: string
    - `/software/lcas/lcas_component_modulespec/args`
        - optional
        - type: string
    - `/software/lcas/lcas_component_modulespec/conf`
        - optional
        - type: lcas_component_plainfile_content
- `/software/lcas/lcas_component_db`
    - `/software/lcas/lcas_component_db/path`
        - required
        - type: string
    - `/software/lcas/lcas_component_db/module`
        - optional
        - type: lcas_component_modulespec
- `/software/lcas/lcas_component`
    - `/software/lcas/lcas_component/db`
        - optional
        - type: lcas_component_db
    - `/software/lcas/lcas_component/dbpath`
        - optional
        - type: string
    - `/software/lcas/lcas_component/module`
        - optional
        - type: lcas_component_modulespec

### Functions

- component_lcas_valid