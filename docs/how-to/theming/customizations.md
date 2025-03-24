# Theming Customizations

The items outlined here are taken from the findings of the Theming Group, and submissions to the [Arca Migration Use Cases webform](https://arca.bcelnapps.ca/migration-use-cases). To submit more requests, please [use the form](https://arca.bcelnapps.ca/migration-use-cases).

These are offered in no particular order; they'll be cleaned up and categorized eventually.

## Appearance Customization
To adjust the basic look and feel of your site, hover over the paintbrush icon in the admin toolbar on the lefthand side of your site.

Navigate to `Appearance -> Settings -> DG Digital Collections` to see a range of options for updating the colours, logo, etc. for your site.

### Front Page Elements and Header Options
At the top of the appearance menu is a subsection of options titled **Bootstrap Settings**. 

Open up the `Front Page` foldout to reveal a series of sliders and options for adjusting the appearance of your front page. Options include:

- Changing the orientation of your front page search box and title text
- Sliders to adjust the opacity and gradient of the overlay on your front page image
- Toggle to change the opacity of the area behind the main link menu on the front page (off by default to allow more of your front page image to be visible)
- Toggle to hide the default *Recent Items* block on your front page
- Toggle to hide the default *Repository Item Counts* banner on your front page

!!! bug
    Note that there's currently a bug with the 3rd slider "Front page image opacity". If the slider is set to 100% opacity, your front page image will disappear. Set at 99% or below.

Open up the `Header Logo` foldout to see additional options for your header. These include options for using a different logo on your front page than any other page on your site, as well as a different logo for mobile versions of your site.

### Breadcrumb Options
Still under the **Bootstrap Settings** section, click on the `Components` tab to the left. Open up the `Breadcrumbs` foldout. 

Breadcrumbs are the link trails that indicate to a user where in a hierarchical site's structure their current page is. You can opt to turn these off entirely with the first dropdown in these settings, though it's generally recommended to keep breadcrumbs on for accessibility reasons.

Here you will also find options for hiding your site's "Home" page (i.e., front page) or a user's active page from the breadcrumbs.

### Logo and Favicon
Your logo is the image that will appear in the top left corner or to the left of the header on all of your site's pages. Your favicon is the shortcut icon that will be displayed in the address bar and/or bookmarks for your site on most browsers.

Instructions for changing either of these images:

1. Scroll down to the section with the header **Override Global Settings**.
2. Select the `Logo image` tab from the options to the left and ensure `Use the logo supplied by the theme` is toggled off. Upload your new logo by clicking `Choose file`. Once you've selected your file, make sure to save your changes by scrolling to the bottom of the settings page and clicking `Save configuration`.
3. Repeat this process in the `Favicon` tab to change your site's favicon.

### Site Colours
The **Colour scheme** section of the Appearance settings allows you to select primary and secondary colours for your site. You can update these colours by entering the new hex codes directly into the boxes, or by clicking on the box for the colour you'd like to change and then making a selection on the colour wheel.

To see descriptions of which parts of the site correspond to each colour, hover over each hex code box. The Preview view underneath the hex code boxes also allows you to see your colour changes live.

!!! warning
    Make sure to save your configuration by clicking the button at the bottom of the Settings page once you're finished changing any hex codes.

### Front page Image
The settings for changing the front page background image in i2 are much more nested than in legacy Islandora. Unlike the logo or favicon, the front page image needs to be edited from the Block settings and not the Appearance settings.

Instructions:

1. Go to `Structure -> Views -> Frontpage (Content)`. Immediately under the header **Displays**, you will see several buttons. Go to the one labelled `Front page Block`.
    * You can also reach these settings by appending `/admin/structure/views/view/frontpage/edit/block_1` to your base repository URL.
2. Scroll down to the Preview section and hover over the default image there. Click on the pencil icon that appears and select `Edit`.
3. You will be brought to the Edit page for *Front page search content*. Scroll down to *Display Block Images* and remove the existing image with the button on the right. Add your new file by clicking `Choose Files`. Add a title, which will appear in a tool tip when a user hovers their mouse over the background image, and some alternative text. Click save in the top right corner when you're done.
4. Go to your homepage to confirm that your image has been successfully uploaded.

## Blocks and Menus

Blocks are chunks of content that might be produced by Menus, Views, or even manually, and can be placed in different regions of your site. They can be configured to appear on certain pages, or be hidden on certain pages.

### Disabling (or enabling) blocks on any page

What: Remove blocks like "Recent Items" to get a cleaner front page look, or add new blocks to any page.

How: Use the Block Layout menu to add and remove blocks.

Instructions:

1. To remove a block:
    * Via the block layout menu:
        1. In the admin menu, go to `Structure -> Block Layout` (`/admin/structure/block`)
        2. Find the title of the block you want to remove, click the dropdown menu on the right, and click `Remove`.
    * From the block's context menu:
        1. On the front page, find the block you want to remove.
        2. When you mouse over the block, in the corner, click the pencil icon.
        3. Click `Remove block`.
        
2. To add (or re-add) a block:
    1. In the admin menu, go to `Structure -> Block Layout` (`/admin/structure/block`)
    2. Find the region you want the block to appear in (e.g. `Content`)
        * To preview the names and locations of each region, click  `Demonstrate block regions ([Theme Name])` near the top of the `Block Layout` page.
    3. Next to the region's header, click `Place block`.
    4. Find the block you want to place (e.g. "Recent Items") and place it.
    5. Drag the block order to position it appropriately in relation to other blocks in that region.
    6. Click the `Configure` box
    7. Under the `Visibility` menu, go to `Pages`.
    8. To include this block on the a particular page (such as the front page):
        * In the text box, enter `<front>`
        * Select "Show for the listed pages"

### Additional menu blocks

What: Create a new menu block, such as a "helpful links" menu on the front page.

How: Create a Menu, and place it in Block Layout.

Instructions: 

1. Create a new menu:
    1. In the admin menu, go to `Structure -> Menus -> Add menu` (`/admin/structure/menu/add`)
    2. Name your menu and add links with the `Add link` button.
2. Place the menu block:
    1. In the admin menu, go to `Structure -> Block Layout` (`/admin/structure/block`)
    2. Find the Region you want your block to appear in.
    3. Next to that region's header, click `Place block`.
    4. Find your menu block and add it.
    5. Position it in the appropriate order relative to other existing blocks.
    6. Configure it to appear on the pages you want, or hide on pages you don't want it to appear (see disabling or enabling blocks, above).

### Institutional Footer

What: A custom block that rests at the bottom of every page, with institutional logo and links. (NOTE: The institutional footer must go above the general Arca footer.)

How: Create a custom block.

Instructions:
   
1. Create a custom block:
    1. In the admin menu, go to `Structure -> Block Layout -> Add custom block` (or, `/add/block`)
    2. In Block Description, describe your block: "Institutional footer"
    3. In Body, write the HTML for your custom block.
        * It may be possible to incorporate Drupal menus here, but the method has not been identified yet. For now, just use HTML.
        * If incorporating CSS styling or other more advanced features, change the text format to "Full HTML".
        * Create your footer with the WYSIWYG editor, or click the `Source` button to write raw HTML.
        * The Arca Footer HTML as an example:
        
```
<style>
table, th, td {
  border: none;
  font-size: medium;
  line-height:normal;
}
</style>
<table class="arca-footer">
    <tbody>
        <tr>
            <td>
                This site is a member of the <a href="https://bceln.ca/services/shared-services/arca-digital-repository">Arca collaborative digital repository</a>, a service managed by the <a href="https://bceln.ca/">BC Electronic Library Network</a>, with support from the <a href="https://www2.gov.bc.ca/gov/content/governments/organizational-structure/ministries-organizations/ministries/post-secondary-education-and-future-skills">BC Ministry of Post-Secondary Education and Future Skills</a>.
            </td>
            <td>
                <a href="https://arcabc.ca"><img class="arca-footer-logo" src="/sites/default/files/inline-images/Arca_Logo_web_0.png" data-entity-uuid="f5eb5d64-5dbc-427e-a347-2de9d75b9ff9" data-entity-type="file" width="83" height="59"></a>
            </td>
        </tr>
    </tbody>
</table>
```

2. Place and activate your custom block:
    1. In the admin menu, go to `Structure -> Block Layout` (`/admin/structure/block`)
    2. In the Footer section, click `Place Block`.
    3. Find the block you created in the list, and click Place Block.
    4. Save and view your site.
3. Edit your custom block:
    1. If you need to make changes to your institutional footer, go to `Structure -> Block layout -> Custom block library` (`/admin/content/block`)
    2. Find your block, and click Edit.
    3. Save your changes.

## Basic Pages
### Creating a new page
Drupal has documentation on creating basic pages available [here](https://www.drupal.org/docs/user_guide/en/content-create.html).

To add a link to your new page to the navigation menu:

    * Unfold `Menu Settings` on the righthand side of the Basic Page editing menu.
    * Toggle on "Provide a menu link" and select a title for the link.
    * Select `<DGI Header Menu>` from the dropdown list for Parent link.
    * Give your page link a weight to indicate where you would like it to appear in the menu. Links with higher weights appear later in the menu.
    * Save your page.

## Views

Views are ways that content gets grouped and displayed. A View can display selected fields from selected content types, according to filters of your choice and relationships to other content. Views are very powerful.

This section will focus on certain Arca-specific use cases; for more general information about using Views, a pleathora of [courses and documentation can be found online](https://drupalize.me/course/user-guide/views-chapter).

### Customizing the Repo Content Counts view

What: Changing what kind of content gets listed and counted in the summary on the front page.

How: Modifying the Repo Content Counts view

The Repo Content Counts view produces the block on the front page saying how many collections, digital documents, etc. exist in your repository. It is built to only count specific kinds of content, but you can add entries to show even more content types, or remove them from the list.

To add a new content model to this group:

1. Get the `External URI` for the content model you want to add:
    1. Identify the content model you want to add in the Islandora Models taxonomy: `/admin/structure/taxonomy/manage/islandora_models/overview`
    2. Find the model you're interested in (e.g. 3D Object), and click it
    3. Copy the value under `External URI`.
2. Modify the view:
    1. In a separate window, find the Repo Content Counts view:
        - Go to `/admin/structure/views`, find the view, and click Edit, or 
        - Mouse over the count block on the front page, and click the pencil icon that appears.
    2. The Attachments produce counts for particular types of repository content: Digital Documents, Collections, Publication Issues, Images, Videos, and Newspapers. To create another one filtered on a different model:
        1. Click on one of the existing Attachments
        2. In the dropdown menu on the right, select `Duplicate attachment`.
        3. Your new attachment tab will appear with a `*` next to the title. Give it a descriptive `Display Name`, like "Attachment - 3D objects".
        4. Change the Filter to use the new content model:
            1. Under Filter Criteria, click the existing External URI filter to edit it.
            2. Under the "Value" field, paste the URI you copied from the taxonomy term.
        5. Modify the Field display to show the correct words:
            1. Under Fields, click `COUNT (Content:ID)` to edit it.
            2. Change the text to reflect the model you're using (e.g. the original said "Publication issue"; change to "3D Object").
                - Note there is both a Singlar field and a Plural field; you will want to edit both.
    3. Save and review.

To remove one of the counted content models:

1. Edit the view as above.
2. Click on the Attachment for the content model that you want to exclude from the count.
3. Below the list of different displays/attachments, click the dropdown where it says "Duplicate attachment", and find the "Disable attachment" option. Click it.
    - Disabling will exclude the information from the view, without deleting the configuration, so it can be enabled later should your needs change.
4. Save your view.