# Post-Migration Tasks

The Arca Office is working with Discoverygarden to create a theme, a base configuration, infrastructure, and migrate content, but there will be numerous post-migration tasks for local admins once your site is up, content is migrated, and your account has been created.

## Create an About page

The Arca Office will create a stub About page for you to customize, and add it to the header menu. You can edit this page to add details such as contact information and context for your site.

## Apply access controls

Because of the complexity of XACML policies and embargoes, we are unable to automatically migrate access restrictions on your objects. Instead, these will have to be applied manually after the data is migrated, but before your new site becomes publicly accessible.

Access restrictions in the new platform will primarily be based on the [Embargo module](https://github.com/discoverygarden/embargo). Some sites with special requirements might also use Groups. Training on Embargo, IP Embargo, and Groups will be provided.

Process:

- Before migration, the Arca Office will provide you with a spreadsheet of all Islandora 7 objects from your repository with existing access restrictions, including titles and PIDs.
- After your migration, the Arca Office will provide Islandora training, including training on Embargoes and other access control methods.
- In your new site, with the list provided to you by the Arca Office, you will apply the appropriate restrictions to your objects.
  - The Arca Office will be available to support you as required with this process.

## Add Embed Code to migrated Remote Media objects

If your repository contains objects with the Islandora Remote Media content model, you may need to do some extra post-migration work in order to complete these objects.

For items whose media is hosted on oEmbed-compatible sites like Vimeo and YouTube, if your content has a URL in the MODS field `<identifier displayLabel="remote media URL">`, and you have tested that URL in the [Sandbox](https://bceln.i8.dgicloud.com/), then no work is required for that object.

If your media does not work with an oEmbed link, you will need to migrate the Embed Code manually.

Process:

- Before migration, the Arca Office will provide you with a zip file containing all the OBJ datastreams for your Remote Media objects. These datastreams are text files that contain the embed code you will need to migrate.
- After migration, search the PIDs from the filenames to find your Remote Media objects in the new repository.
- For each Remote Media object:
  - Click the Media tab
  - Click the `+ Add Media` button
  - Click `Embed Code`
  - Set a relevant Name
  - Paste your code directly from the exported file into the `Insert Embed Code` field, without modification, including all HTML tags
  - Under `Media Use`, select "Service File"
  
When viewing your object, the embedded media should display normally.

## Add TRANSCRIPT datastreams back to video and audio content

TRANSCRIPT datastreams, which would have provided subtitles/closed captioning on your video objects, will not be migrated automatically. They need to be re-added after the migration is complete.

Process:

- Before migration, the Arca Office will provide you with a zip file containing all the TRANSCRIPT datastreams for your objects.
- Ensure that your TRANSCRIPT files are in the VTT format. Convert if necessary.
- After migration, search the PIDs from the filenames to find the corresponding objects in the new repository.
- For each object:
  - Click the Media tab
  - Find the video or audio media, and click Edit
  - Under the "Track" section, upload your transcript file.

## Create and review users, roles, and permissions

Before migration, you should already have reviewed and pruned your users list so that only users you want to migrate will appear in your new repository.

Users should be migrated automatically, but you should review them to make sure that (a) all appropriate users are present, (b) no unwanted users have been migrated, and (c) each user has the appropriate Role.

You will also want to review permissions for each role to make sure that they are set appropriately.

## Set up mediated submission

If you want a mediated process for self-submission, follow the [self-submission setup instructions](/arca-docs/how-to/processes/self-submission/).

## Configure Pathauto

If you want to set up custom URLs for your objects, you will need to [configure the Pathauto module](/arca-docs/how-to/display/pathauto/).

This configuration happens after objects are migrated. Once you have configured it in the way you want it, we will run a script to apply the new paths to all migrated objects.

## Theme customizations

Customize your theming as you see fit. You can modify colours, logos, etc. via the Appearance menu at `/admin/appearance/settings/dgi_i8_base`.

You can take more advanced theming steps (block placement, etc.) following the [Theming Customizations guide](/arca-docs/how-to/theming/customizations/).
