# Configuring URLs in Islandora

It is possible to set up custom URLs for each object individually, or according to patterns. In Arca, we use the (Pathauto module)[https://www.drupal.org/documentation/modules/pathauto]. 

Pathauto works for all kinds of Drupal content, see the module documentation for details. This page describes its usage specifically in the Arca and Islandora context.

All Drupal content gets a "true" path in the form `node/[id]`, where `[id]` is a number. The content will always be accessible from that path; your custom path is an alias, and can be changed as desired.

## Configuring Pathauto patterns

Pathauto produces URLs based on tokens - pieces of information drawn from Drupal fields; that is, your item's metadata. By default, Arca produces a URL for Repository Item nodes based on their Title. You can change this and produce more sophisticated or complex URLs if you desire.

To access Pathauto configuration, go to `/admin/config/search/path/patterns`. 

If you want to use a new pattern and not the default, click the dropdown under Operations and choose `Disable`. This way you can always go back to the original version.

To create a new pattern:

- Click the `Add Pathauto pattern` button
- Under `Pattern type`, choose `Content`
- Under `Content type`, choose `Repository Item`
- In the `Path Pattern` field, enter the pattern you want to create, using tokens from your Repository Item fields. 
    - How this works:
        - Patterns are based on tokens, which are references to Drupal fields.
        - To see the tokens available to you, click the `Browse available tokens` link. You will see the available tokens organized by category.
        - Click the `Nodes` category to produce a list of all the fields that exist on Drupal nodes.
        - Click the token you want to add to push it to the `Path Pattern` field.
    - Example: `[node:field_member_of]/[node:title]` will produce a path using the parent item's title followed by the item's title.
        - e.g. "My Image" in the "Beautiful Images" collection will have the URl `yoursite.arcabc.ca/beautiful-images/my-image`.
    - If you expand on the field token, you can drill into more details. For example, drilling into `[node:field_member_of]`, you could instead choose `[node:field_member_of:0:target_id]`, which produces the Node ID instead of the title.
        - Using this option with the above example, your path would instead look like `yoursite.arcabc.ca/13/my-image`.
- Give it a label so you remember what it means, and save.

**Note that complex hierarchical paths are not possible**. Pathauto tokens are only available for (1) metadata fields and other information directly from the node in question, and (2) the parent item's name and node number [no other parent metadata].

## Setting custom URLs manually

When creating or editing any Drupal object, including Repository Items, you have the option to manually set the URL Alias.
        
While filling out the fields for your Repository Item, look at the sidebar to the right. Click the `URL Alias` dropdown.

The `Generate automatic URL alias` is on by default -- this will produce a URL according to the pattern defined by Pathauto (as described above).

To create your own custom path, de-select this option, and enter whatever you like into the `URL alias` field. Note that this should be a **relative path**. Do not enter your site's domain here.

For example, if you enter `/old-stuff/my-object`, the actual URL produced will be `https://yoursite.arcabc.ca/old-stuff/my-object`.
