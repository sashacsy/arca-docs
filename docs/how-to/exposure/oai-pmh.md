# OAI-PMH Configuration and Harvesting

Your OAI-PMH endpoint is at `/oai/request` (formerly `/oai2` in Islandora 7).

In order to properly enable OAI-PMH harvesting, you will need to configure your OAI module at `/admin/config/services/rest/oai-pmh`.

Some basic settings:

- What to expose:
    - Check all boxes except Entity Reference
- Metadata mappings:
    - mdRecord: DPLAVA
    - oai_qdc: DGI Standard Qualified Dublin Core
    - oai_raw: None
    - oai_dc: OAI Dublin Core (RDF Mapping)
    - mods: None
- Set your repository name and admin email
- Leave other settings as-is

The fullest sets of metadata are either `mdRecord` or `oai_qdc`. `mdRecord` is recommended, as it includes a link to the media, in the field `edm:preview`. 

A request will look something like this: `https://yoursite.arcabc.ca/oai/request?verb=ListSets&metadataPrefix=mdrecord`

If you have provided harvesting information to an outside organization for your Islandora 7 site, you will need to give them the new request path and metadata schema.