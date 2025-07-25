# Adding New Facets to Search Results

Most facets that you might need are pre-built, but not implemented as blocks on your search view. If you find that a facet you need is not available, contact the Arca Office for assistance.

To add a facet to your search view, there are three steps:

1. Make sure the facet you need exists.
    - At `admin/config/search/facets`, check that facets exist for the Repository Item field you need to facet on.
    - You will need a separate facet for each search display mode (Grid, List, Card). 
        - If only one or two of these modes exist, you can click the "Clone facet" option and set your clone to use the other display modes.
    - Contact the Arca Office for help creating facets.

2. Place the facet blocks.
    - At `/admin/structure/block`, scroll down to the "Search Facet Header" section, and click Place Block.
    - Find the blocks for the facets you want to use - they will have the Category "Facets". Click "Place block" for each facet block you want to add. Remember, you need blocks for each of the different display modes (Grid, List, Card).
    - Give the block a title that will help you identify it, including the name of the facet. Edit the machine name to include the display mode it represents, as you will need this later. 
        - For example, Facet "Degree Name Card" might have the machine name `degreename_card`.

3. Add your facet blocks to the search content view.
    - Find the Solr Search Content view under `Structure -> Views`, or `/admin/structure/views/view/solr_search_content`.
    - Click to the display mode you want to add facets to.
        - For Search results, that will be one of "Page (card)," "Page (list)", or "Page (Grid)". 
        - You can also add facet blocks to collection displays (untested) with the same pattern.
    - Under the "Footer" section, click "Add", and select "Rendered Entity - Block".
        - On the configuration screen for your new block, scroll down to the "Block ID" field, and paste in the machine name of the block you placed. **Make sure the block you're adding matches the display mode you're working on.**
    - Go to the next display mode, and follow the above steps to add the next block to the footer, until you've covered Card, List, and Grid.