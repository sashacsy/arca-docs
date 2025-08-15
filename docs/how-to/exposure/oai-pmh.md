# OAI-PMH Configuration and Harvesting

Your OAI-PMH endpoint is at `/oai/request` (formerly `/oai2` in Islandora 7).

In order to properly enable OAI-PMH harvesting, you will need to configure your OAI module at `/admin/config/services/rest/oai-pmh`.

Some basic settings:

- Metadata mappings:
    - oai_qdc: DGI Standard Qualified Dublin Core
    - oai_raw: None
    - oai_dc: OAI Dublin Core (RDF Mapping)
    - mods: None
- Set your repository name and admin email
- Leave other settings as-is

For the fullest set of metadata, use `oai_qdc` for your mappings. A request will look something like this: `https://yoursite.arcabc.ca/oai/request?verb=ListSets&metadataPrefix=oai_qdc`

If you have provided harvesting information to an outside organization for your Islandora 7 site, you will need to give them the new request path and metadata schema.