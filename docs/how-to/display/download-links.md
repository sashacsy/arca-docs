# Restrict access to Media Download blocks

By default, repository items display blocks that invite users to download any attached media, including thumbnails, original files, or whatever other unembargoed media are attached.

These blocks are provided by the `display_media` view, which provides numerous blocks referencing media.

If you want to restrict access to the Download links without embargoing the media, follow these steps:

1. Go to `Structure -> Views -> Media EVAs`
2. Under Displays, click "All Attached Media (Block)"
3. Under Block Settings, next to the "Access" line, click the "Permission" link.
4. **IMPORTANT**: At the top of this window where it says "For all displays", change to "This block (override)". Otherwise, you will change these settings for all iterations of this view.
    - Change from Permission to Role.
    - Select the roles you want to allow access to this block. Do not exclude the three highest level roles (Administrator, Site Administrator, and Repository Administrator).
5. Apply your changes
6. Under the Displays header, click "All Attached Media (EVA)"
7. Repeat steps 3, 4, and 5.
8. Save.
9. Review your content in an anonymous browser to make sure it's working as intended. You may need to apply those changes to other displays as well (e.g. "original file") depending on your desired results.