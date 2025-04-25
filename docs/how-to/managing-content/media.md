# Managing Islandora Media

This document is under construction. For a detailed explanation of how media works in Islandora, [see the Islandora Wiki](https://islandora.github.io/documentation/user-documentation/media/). (Note that we do not use Fedora, so ignore those parts.)

Special media types in Arca:

- oEmbed Remote Media: Takes a URL to a remotely hosted media object from any oEmbed-compatible source, and displays it as an embedded object in the repository. This for the most part is how re replicate the old Islandora Remote Media Solution Pack.
    - Works with the most common media sources, such as YouTube, Vimeo, Hulu, SoundCloud, and even Twitter, Bluesky, and Reddit posts.
    - You can also configure the oEmbed Providers module to add additional custom sources, such as your Kaltura endpoint. (Documentation for this to come.)

## Adding and Changing Thumbnails

Thumbnails for most items are created automatically as derivatives of the Original Media. But you may find yourself wanting to change these automatic thumbnails for something custom-made.

### Changing non-collection thumbnails

To change an item's thumbnail, **do not delete the original thumbnail image**. Instead, edit the existing one:

1. Click the Media tab
2. On the "Thumbnail Image" item, click Edit
3. Under the Image section, click "Remove"
4. Then, under Add New File, choose your new file.

### Thumbnail sizes

Automatically-generated thumbnails will be 256 pixels at their largest dimension (width or height). Custom thumbnails should follow this template.

## Collection Thumbnails

Unlike other repository items, collection thumbnails are set by editing the Node itself. To change a collection thumbnail:

1. Edit the collection node (looking at the collection, click the Edit button in the header image)
2. In the Summary tab, scroll down to the Representative Image section, and click Select Entities
3. The dropdown menu offers a choice, to either `Select existing media image` or `Upload a new media image`.
    * "Existing media image" means an image that already exists in your Media collection -- just check the box to use it.
    * To upload a new image, choose a file from your computer, and then click "Select image" to upload it.
