# Customizations by individual sites

Some Arca partners have created unique customizations. These are collected here, with instructions for replicating them.

If you would like to add your own customizations to this list, you can either propose an edit (click the pencil icon on this page) or send your information with appropriate details to the Arca Office.

## Replace the Collection Representative Image with a solid colour, and add a custom thumbnail

Uses a solid colour background in the Collection title header, instead of a cropped image.

- Site: BCRDH
- Use case: Uniformity, branding
- Modules: Asset Injector / CSS Injector

Process:

1. Add a CSS class to the "Collection: Representative Object" view so you can style it:
    - Edit the Representative Object view at `/admin/structure/views/view/collection_representative_object/edit/block_1`
    - In the "Advanced" section on the right, under "Other", find the "CSS Class" option and add a new class name: `rep-obj-display`
2. Create a CSS Injector rule to add a solid background colour to Collection header:
    - Go to `/admin/config/development/asset-injector/css` and create a new Rule with a title like "Collection Header Background"
    - Add the following rule that styles the CSS class you just created:
    ```
    .rep-obj-display{
    	background-color: #8CCDB0;
	}
    ```
3. Remove the Representative Image from collection items:
    - For each collection, go to the Edit screen
    - In the metadata form, find the Representative Image section and click Remove
4. Add a custom Thumbnail:
    - Edit the collection and click the Media tab
    - Add new Media, of type Image
    - Upload the image of your choice. For the Media Use field, select `Thumbnail`.