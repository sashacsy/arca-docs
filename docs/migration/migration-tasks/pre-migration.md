# Pre-Migration Checklist

## Local Admin Tasks

* Review and complete all steps from [Migration Preparation](/arca-docs/migration/migration-tasks/migration-preparation/)


## Arca Office Tasks

* Alert local admins that ingests and edits are on hold
* Review site for special datastreams:
    * Run an empty search and use the `fedora_datastreams_ms` facet
    * Look for the following:
        * TRANSCRIPT
        * LICENSE
        * LICENSES
        * PERMISSIONS
        * APPROVAL
    * With Islandora Datastreams I/O, Export and Zip the special datastreams and send to local admin
* Review site for Remote Media objects
    * Run a search: `/islandora/search/RELS_EXT_hasModel_uri_mt:remote`
    * Export all OBJ datastreams for these objects with Islandora Datastreams I/O and send to local admin
* Export a [list of all the site's XACML-restricted objects](https://arcabc.ca/viewing-restricted-objects?rels_ext_ismemberofcollection_uri_mt=&pid_namespace_t=)
    * Export the CSV (from the first link) and send to the local admin for post-migration work
* Export a list of Embargoes and send to local admin for post-migration work:
    * Scholar Embargoes(`/admin/islandora/tools/embargo/list`)
    * IP Embargoes (`admin/islandora/tools/ip_embargo/manage`)
* Confirm metadata is still up to standard using Islandora Facet Pages
    * Check particularly on Dates

  
  