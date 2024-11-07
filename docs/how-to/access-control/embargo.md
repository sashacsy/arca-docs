# Adding and Editing Embargoes

Embargoes are the primary form of access control in Islandora 2. Exemptions to embargoes can be set for individual users and emails, as well as IP ranges. 

While specific Drupal Roles may also be given permission to bypass *all* embargoes, embargoes for specific items cannot be set at the Role level. For this kind of granularity, use Groups.

## Setting embargoes

1. Access the Embargo menu:
    a. From the object you want to embargo:
        * Navigate to or Edit the object you want to embargo, and click the Embargoes tab
        * Click "Add Embargo"
    b. From the Content menu: 
        * Click the Embargoes tab, click Add Embargo
        * In the `Embargoed Node field`, begin typing the name of the item you want to embargo. It will auto-complete for you. 
2. Set up your embargo:
    * Embargo Type: 
        * "File" restricts access to the Media (eg the PDF or the video), while leaving the Node (object page with metadata) visible. The item will appear in collection listings and search results to all users, but only authorized users may access the media.
        * "Node" restricts access to the entire Repository Item - unauthorized users will not even see that the item exists.
    * Expiration Type:
        * Indefinite: A permanent restriction (no set end date).
        * Scheduled: Set an expiration date, at which point the content becomes publicly available.
    * Exempt IP Range:
        * Select an IP range that is allowed to access the item. 
        * IP ranges must be configured separately - see further below.
    * List of Exempt Users:
        * Enter the usernames of the specific users who are allowed to bypass the embargo.
        * Exemption by Role does not exist currently, but it is being worked on.
    * Additional Emails:
        * Email addresses that will be automatically contacted when the embargo is changed/lifted.
3. Save

Your object should now be restricted from unauthorized users.

## Embargo permissions

The Embargo module comes with three Permissions that can be granted to different Roles, set at `/admin/people/permissions`:

1. Administer Embargo
    * Users with this permission can change configuration of the Embargo module and all embargoed items.
    * Only the Administrator (Arca Office) and Site Administrator (local admin) should have this permission.
2. Bypass Embargo Access Control
    * Users with this permission can see all embargoed items, whether or not they were added to the Exempt list.
    * This permission should be granted to any Roles that manage repository content on the whole (e.g. Site Administrator, Repository Administrator). It should not be given to more general roles like Submitter.
3. Manage Embargo
    * Users with this permission can apply, update, and lift embargo policies on any content.
    * Roles with this permission should also have the Bypass permission, so that they cannot lock themselves out of managing objects.

## Setting IP ranges

IP ranges allow any user who is working from an authorized IP address to access embargoed content. This is useful in cases where, for example, repository content is limited to on-campus users, or users in a specific building.

IP ranges must be created before they can be applied to an Embargo.

1. Go to Content
2. Click the Embargoes tab
3. Click the IP Ranges tab
4. Click "Add IP Range"
5. Create the range:
    * Label: Give the range a title that makes it easy to select (e.g. "Douglas College Campus")
    * IP Range: Enter an individual IP address, or a range of IP addresses in CIDR format (e.g. `10.0.0.0/24`). 
        * You can [use a calculator](https://www.ipaddressguide.com/cidr) to enter the start and end addresses of an IP range and generate a CIDR format version.
    * To enter multiple IP addresses or ranges to the same group, click "Add another item".
6. Save

Your new IP Range should now be available to select when setting up an Embargo.