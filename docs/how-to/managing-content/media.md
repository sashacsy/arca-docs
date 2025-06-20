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

#### Thumbnail sizes

Automatically-generated thumbnails will be 256 pixels at their largest dimension (width or height). Custom thumbnails should follow this template.

### Collection thumbnails

Unlike other repository items, collection thumbnails are set by editing the Node itself. To change a collection thumbnail:

1. Edit the collection node (looking at the collection, click the Edit button in the header image)
2. In the Summary tab, scroll down to the Representative Image section, and click Select Entities
3. The dropdown menu offers a choice, to either `Select existing media image` or `Upload a new media image`.
    * "Existing media image" means an image that already exists in your Media collection -- just check the box to use it.
    * To upload a new image, choose a file from your computer, and then click "Select image" to upload it.

## Adding captions to video and audio content

To add captions to your audio or video media, first ensure that you have a track in the VTT file format, then: 

1. Create a new Repository Item with the Content Type "Audio" or "Video". Ensure that "Add Media" is toggled on in the metadata form.
2. Once you finish entering the metadata and arrive at the Add Media screen, select either Audio or Video as the Media Type.
3. Under the "Track" section, upload your transcript/caption file.
4. Click `Save` to complete the ingest of your object. 

!!! warning
  If you are adding captions to media on a Repository Item that has already been created (i.e., a node with already-generated media derivatives), you must add the VTT to the `Service File` derivative. This is the version of your video that the system displays in the viewer, **not** the Original File.

  When you create a *new* Repository Item and add a track at the time of ingest, Islandora will automatically generate the Service File derivative with the VTT attached.
