# Troubleshooting Islandora Workbench

## SSL Certs
If any errors appear related to SSL certs, ensure the following line is included in your **config YAML**:

```
secure_ssl_only: false
```

##  Metadata errors
Make sure your CSV has been encoded correctly by opening it in a text editor, not spreadsheet software. The Arca Office has previously run into an issue where a CSV was exported in UTF-7, which created a lot of artifacts that weren't visible when looking at the CSV in LibreOffice.

## Node created but media failed
You may sometimes encounter a situation where a node has been successfully created but an error appears in your terminal/console and in `workbench.log` about not being able to connect to site when trying to add the media. This may be a result of your media file exceeding size limits. Review your media files and the limitations for different file types to see if resizing or compression is necessary. 

You can view file size limits if you try to add a media file manually on your site (**Content > Media > Add media**).