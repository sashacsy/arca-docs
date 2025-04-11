# Links to Socials with AddToAny

By default, most Basic Pages or Repository Items in your site will display a block with links for sharing content to social media platforms. This feature is made possible by a module called **AddToAny**.

## Changing the Default Platforms

On both Basic Pages and Repository Items, the AddToAny block will contain five icons by default:

- Facebook
- X
- Email
- LinkedIn
- A :octicons-plus-16: icon that opens up the full list of socials when clicked

All but the :octicons-plus-16: icon can be customized by going to the AddToAny configuration page on your site at `/admin/config/services/addtoany`. 

In the text box under *Service Buttons*, you will see four rows with `<a>` tags. To change any of the platforms to something else, simply replace the service code within the tags for a relevant row. 

For example, to change **X/Twitter** to **Bluesky**, find the row with the tags `<a class="a2a_button_x"></a>`. Replace only the `x` with the service code for Bluesky, so that the row now reads `<a class="a2a_button_bluesky"></a>`.

To identify the service code for a given platform, go to the [AddToAny website](https://www.addtoany.com/services/) and click on the platform's icon. You will see a field called `AddToAny service code`, followed by the code you'll need.

## Changing the Universal Button

The :octicons-plus-16: icon that appears at the end of the series of platform links is known as the Universal Button. The icon for the Universal Button can be changed to a custom image by opening up the *Universal Button* foldout on the AddToAny configuration page. The placement and existence of the button can also be customized here.

## Hiding Social Sharing Links from Basic Pages

If you'd like to hide the AddToAny block from all Basic Pages on your site, head to the content type's display settings at `/admin/structure/types/manage/page/display`.

Under the header *Field*, you will see AddToAny listed second. Click and drag this row until it's under the *Disabled* header. Scroll to the bottom of the page and click **Save**.

## Hiding Social Sharing Links from Repository Items

If you'd like to hide the Share/AddToAny block from all Repository Items, head to Block Layout settings at `/admin/structure/block`. 

Find the Share/AddToAny block in the *Block group: Object Page: Split Sidebar* section. Click the :material-chevron-down: down arrow on the button at the right of the AddToAny row. Click **Disable** and then **Save blocks** at the bottom of the page.

!!! warning 
    **DO NOT** click Remove on the AddToAny block (or any other blocks) while in Block Layout or while interacting with the block directly on your site. This will delete the block, making it significantly more difficult to recreate the block/view if you ever decide to re-enable it. If you are ever adjusting the visibility of certain elements on your site, make sure to only select *Disable* so that the block can easily be recovered if needed.

