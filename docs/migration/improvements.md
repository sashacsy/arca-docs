# A non-exhaustive list of improvements in the new platform

Following is a list of some of the improvements and advancements that the migration to our new platform has brought us. The list is posted here for your reference, and may be added to over time.

- Infrastructure:
    - Some major back-end improvements Arca’s architecture. We have gone from a shared stack with a single Drupal install covering all 30 Arca members, to a distributed cluster of virtual machines that share the same code repository – meaning that, while the management of Arca sites is still centralized, problems happening on one site do not affect the others. This is a huge improvement to stability.
    - Code and versioning of all sites managed with Git, making it easy to track changes, fix problems, and roll things back.
    - Configuration sync allows admins at individual sites to make all kinds of customizations to their sites, without impacting the actual codebase – and making it easy to recover if they make damaging changes.
- Structure:
    - Repository objects are natively Drupal nodes now, which means they are fully available to the website – all kinds of unique things can be done with the fields and media because they are fully integrated with the site.
- Metdata:
    - Taxonomies and entity references: Many metadata fields are now controlled with Taxonomies, making it easier to connect all items by a particular author, or in a particular genre or subject, and reducing human error when creating metadata.
- User interface:
    - Much more modern look and feel
    - Paged object viewing is much sleeker and usable
    - File and media management is simpler and more accessible to local admins
- Tools:
    - Admins have more freedom and power to run batch operations without the Arca Office, thanks to Islandora Workbench – they can ingest large batches right from their desktops.
- Documentation:
    - The migration led to an overhaul of the documentation for Arca Admins, including the creation of a new, streamlined documentation site that is easily searchable and can be contributed to by our partners.
