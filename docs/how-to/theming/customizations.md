# Theming Customizations

The items outlined here are taken from the findings of the Theming Group, and submissions to the [Arca Migration Use Cases webform](https://arca.bcelnapps.ca/migration-use-cases). To submit more requests, please [use the form](https://arca.bcelnapps.ca/migration-use-cases).

These are offered in no particular order; they'll be cleaned up and categorized eventually.

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
    * Select the name of the menu in your header/navigation block.
    * Save your page.

## Views

Views are ways that content gets grouped and displayed. A View can display selected fields from selected content types, according to filters of your choice and relationships to other content. Views are very powerful.

This section will focus on certain Arca-specific use cases; for more general information about using Views, a pleathora of [courses and documentation can be found online](https://drupalize.me/course/user-guide/views-chapter).

### Customizing the Repo Content Counts view

What: Changing what kind of content gets listed and counted in the summary on the front page.

How: Modifying the Repo Content Counts view

Instructions:

1. Get the URI for the content model you want to add:
    1. Identify the content model you want to add in the Islandora Models taxonomy: `/admin/structure/taxonomy/manage/islandora_models/overview`
    2. Find the model you're interested in, and click it
    3. Copy the value under External URI.
2. Modify the view:
    1. In a separate window, find the Repo Content Counts view at `/admin/structure/views`, or click the pencil icon when mousing over the block.
    2. The default view has several Attachments, which specify particular types of repository content: Digital Documents, Collections, and Publication Issues. To create another one filtered on a different model:
        1. Click on one of the existing Attachments
        2. In the dropdown menu on the right, select `Duplicate attachment`.
        3. Your new attachment tab will appear with a `*` next to the title. Give it a more useful name, like "Attachment - image count".
        4. Change the Filter to use the new content model:
            1. Under Filter Criteria, click the existing filter to edit it.
            2. Under the "Value" field, paste the URI you took from the taxonomy term.
        5. Modify the Field display to show the correct words:
            1. Under Fields, click `COUNT (Content:ID)` to edit it.
            2. Change the text to reflect the model you're using (e.g. the original said "Publication issue"; change to "Image")
    3. Save and review.
