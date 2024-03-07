# Bulk metadata updates

While individual objects' metadata can usually be corrected through the normal Web browser interface, in some cases you may have dozens or even hundreds of items that need the same correction. These corrections may be made in bulk, with the help of [Islandora Datastreams I/O](https://github.com/ulsdevteam/islandora_datastreams_io) and text editing tools on your computer such as [BBedit](https://www.google.com/search?q=bbedit+mac&oq=bbedit+mac&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTIGCAEQLhhA0gEIMTU2NGowajGoAgCwAgA&sourceid=chrome&ie=UTF-8) (Mac) or [Notepad++](https://notepad-plus-plus.org/) (Windows).

To make bulk updates:

1. Export your MODS datastreams with Islandora Datastreams I/O
2. Find and replace the metadata you need to change using a text editor on your computer
3. Import your edited datastreams

For detailed instructions, you can [follow our video walkthrough](https://youtu.be/hjBRml74_eY), or the documentation below.

## Export MODS datastreams

### Identify the objects that need changing

To bulk export MODS datastreams, you will first need either a list of PIDs, or a Solr query. The easiest way to find that information is to use Islandora Solr Facet Pages (see the [Metadata Corrections documentation](/arca-docs/migration/migration-tasks/metadata-corrections.md) for details).

**If you are using Islandora Solr Facet Pages:**

1. On the page for the metadata field in question, click into the value that needs to be changed. For example, on your [list of genre terms](https://arcabc.ca/browse/genre), you find a term that needs to be changed: "brochure" should be "[brochures](https://arcabc.ca/islandora/search/%2A%3A%2A?f%5B0%5D=mods_genre_ms%3A%22brochures%22)".
2. In the URL bar for the facet page, you'll find the Solr query at the end: `https://arcabc.ca/islandora/search/%2A%3A%2A?f%5B0%5D=mods_genre_ms%3A%22brochure%22`
    The snippet we're looking for is `mods_genre_ms%3A%22brochure%22`.
3. [Convert encoded characters to human-readable ones](https://www.url-encode-decode.com/). The above example becomes `mods_genre_ms:"brochure"`. 

If you've found your objects with a search, you can extract the Solr query from the URL in the same way.

Alternatively, you can record your PIDs manually or export a CSV.

**To produce a search result CSV**, you can configure Solr to provide one:

1. Go to `/admin/islandora/search/islandora_solr/settings`
2. Under "Secondary display profiles", check "CSV"
3. Under Display Fields, make sure `PID` is one of the fields present.
4. Your search results will now produce a downloadable CSV, which will include the objects' PIDs.

### Export the Datastreams

1. Open Islandora Datastreams I/O at `admin/islandora/datastreams_io/export` (Islandora -> Islandora Datastreams Input/Output Relationships -> Export).
2. Under "Datastream", select MODS.
3. Under "Select Objects", choose either "Solr query" or "List of PID values" as required.
4. In the text area, either paste the Solr query you identified (e.g. `mods_genre_ms:"brochure"`) or your list of PIDs (one per line).
5. Click "Export batch" and download the Zip file.

## Bulk edit your MODS

Unzip the file you downloaded, and then open one of the MODS XML files in your text editor. The following instructions are specifically for BBedit, but a similar process will apply to any editor.

1. Find the snippet of XML that needs to be changed. Be sure to select the *entire* XML snippet -- both opening and closing tags -- to ensure you don't replace other text in your file.
    - In our example, you'll highlight and copy the snippet `<genre authority="aat">brochure</genre>`.
2. Under the Search menu, open "Multi-File Search".
3. In the "Find" field, paste your metadata snippet: `<genre authority="aat">brochure</genre>`
4. In the "Replace" field, enter the *complete* replacement version (including opening and closing tags): `<genre authority="aat">brochures</genre>`
5. In the "Search In" field, select the folder containing all of the files that need to be changed.
6. If you're confident in your changes, click "Replace All". Otherwise, start with "Find All" to make sure you've identified things correctly.
    - If not all of the files get changed, your original metadata may be using a different authority. Try editing the "find" field and change the authority to `authority="marcgt"` or even no authority at all, to catch all the edge cases.
7. Confirm your changes are producing valid XML, using a validator like [xmlvalidation.com](https://xmlvalidation.com) or [xmllint](https://craigrosie.github.io/posts/essential-command-line-tools-xmllint/).

## Import the edited MODS datastreams

1. *Without changing the filenames*, zip your edited MODS XML files
2. In your repository, go to Islandora Datastreams I/O -> Import
3. Upload your zipped file, submit, and click Finish