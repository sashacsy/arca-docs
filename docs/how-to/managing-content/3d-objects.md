# Creating and managing 3D objects in Arca

## Ingesting a 3D object
1. Follow the instructions in the [Ingest Guide](https://bceln.github.io/arca-docs/how-to/managing-content/ingest-guide/) to create a new node with your object metadata, as per usual. Select *3D object* for the content type.
2. When adding media, ensure *Original File* is selected for *Media Use*. 
3. Skip the Threejs Settings tab and move on to the file upload section. GLB is highly recommended as the file format to ensure the smoothest experience on all browsers.
4. Save and preview your object in the viewer. 
    - If your viewer is only showing a black screen, the default lighting/camera controls on your object may need to be overridden:
        1. Navigate back to the Edit Media page.
        2. Open up the Threejs Settings tab and toggle on **EITHER** the *Room Environment* or *Add default lights* options. While you can enable both, it may result in overexposure on the object in your viewer.
        3. Save the media and return to your object viewer to confirm that it is now visible with the Threejs lighting enabled.

## Considerations & Troubleshooting

### File Format
While `.gltf` and `.obj` files are technically accepted for 3D objects, the Admin Centre has experienced issues rendering these files during testing. Until these issues are further investigated with DGI, it is highly recommended that 3D objects be uploaded in the `.glb` format.

### Issues with perspective camera and Threejs camera settings
When ingesting a new 3D object to Arca, you may notice that the perspective camera's default starting point is a little off. For example, when opening a 3D object page, the viewer may load with the camera zoomed in quite close to the object. 

While DGI has added in controls to override your object's default camera settings and adjust the Field of View, these controls are not currently functional. Though the Admin Centre will be exploring these issues more closely post-migration, please be aware that you may need to adjust the field of view manually when browsing 3D objects in the meantime.

!!! warning
    When editing 3D object media, under *Threejs Settings*, there is a button labelled "Add Threejs Perspective Camera Settings". Clicking this button will result in your 3D object viewer going black, even if the actual setting values are not adjusted. Because there is no option in the UI to revert to your object's default camera settings once this button has been clicked, the recommended fix is to delete and re-upload your 3D object media.