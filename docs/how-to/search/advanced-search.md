# Advanced Search

Advanced Search allows a user to choose specific fields for their search terms. You can set up an Advanced Search page by following the steps below.

1. Enable the Advanced Search module (NOT the "Islandora Advanced Search" module; this is deprecated and will be removed eventually).
2. Configure the module at `/admin/config/search/advanced` if desired.
    - Configuration allows you to allow/disallow searching all fields, and to change the operator icons.
3. Create a Basic Page to hold your Advanced Search block. Give it a useful path, e.g. `/advanced-search`. 
    - If desired, include it in a menu.
4. Embed the block on your new page:
    1. Go to Structure -> Block layout
    2. In the Content region, click Place Block
    3. Add the block "Advanced Search for Page (Grid)"
    4. On the block's configuration screen, choose which fields are available to select, by dragging them up from the Hidden section
        ![image](/arca-docs/assets/advanced-search-config-1.png)
    5. Still on the block configuration page, scroll down to the Visibility section. 
        - Choose "Page"
        - Select "Show for the listed pages" - this means that your block will appear only on the pages you list in the Path section
        - In the Path section, enter the path to your Advanced Search page (e.g. `/advanced-search`)
        ![image](/arca-docs/assets/advanced-search-config-2.png)
	6. Save your block settings

