# Frequently Asked Questions

This page answers frequently asked support questions.

## Display
### How can I change my site's name?

Go to **Configuration > System > Basic site settings**. You can change your site's name and slogan in the first two fields. Remember to hit **Save** at the bottom. The title will appear in browser tabs in the format `Page title | Site title`.

### How can I hide the Recent Items or Repository Counts blocks on my front page?
Unlike all other blocks on your site, these two can easily be toggled off in Appearance settings. Go to **Appearance > Settings > DG Digital Collections** and open up the *Front Page* foldout in the first section. At the bottom of the section are two toggles. The first controls the visibility of the Recent Items block and the second controls the Repository Counts block. Make sure to hit **Save configuration** at the bottom of the page after making your adjustments.

## Managing Objects
### If I set an embargo on a collection or parent object, will its children also be embargoed?
Yes, child objects belonging to a parent with a node embargo applied to it will also be restricted. However, if those children are ever moved/reassigned to another parent, they will lose the embargo coverage. 

Conversely, if individual node embargoes are set on child objects, their embargoes will move with them if they change parents. This is because Node IDs for children do not change along with collection/parent membership.

### Is there a way to delete a Repository Item node *and* its media files at the same time?
Yes. You may have noticed that if you delete a Repository Item from the node itself, only the node/metadata record gets deleted and the media files then become orphaned in your system (i.e., they remain visible in Media Overview but are no longer attached to any one object).

To delete a node/metadata record **and** the media belonging to that node at the same time, head to **Content > Overview**.

Find the items you would like to delete, either by navigating through the pager or using some of the filters at the top. Check off the relevant nodes.

Once you've checked off at least one item, an action bar will appear at the bottom of the page. From the dropdown list, select `Delete node(s) and associated media` and then the button that says **Apply to selected items**. You will be brought to a second screen where you can then confirm that you would like to delete the items and associated media.

## Viewing Objects
### I'd like to search for a term within a paged object and have all instances of that term highlighted for me. How can I do that?
Paged objects in the new Arca use the Mirador viewer. On the upper lefthand side of the viewer, click the :octicons-three-bars-16: list icon and then the resulting :fontawesome-solid-magnifying-glass: magnifying glass icon. Enter in your search term and a list of all instances of that term in the paged object should appear with highlights.

Note that this feature is reliant on the quality of the HOCR media file for each page. If Tesseract, the tool Islandora uses to generate OCR and HOCR output, did not identify the correct characters or words in your images to export to your HOCR file, your search may not bring up any results. 


## Solr and Indexing
### My text object has Extracted Text and/or HOCR media files. Are keywords in these files searchable from my site's universal search bar?
Yes. If you notice that an object is not appearing in search results but you know that its Extracted Text or HOCR file contains your search term, Solr may not have indexed your object yet.

## Statistics
### How can I track usage data for my site?
Please see our page on [Usage Statistics](/arca-docs/how-to/statistics/statistics/).