# Viewing and Displaying Matomo Usage Statistics in Arca

For a complete picture of your visitors' usage, ask the Admin Centre for a Matomo account. This will give you access to your own dashboard at [https://analytics.bceln.ca](https://analytics.bceln.ca), where you will be able to access all sorts of data and views on that data.

## Displaying a Visitor Map Block
What: Display a realtime visitor map based on usage statistics from Matomo.

How: Create a custom content block and configure it to display on a "Usage Data" page or any other desired page.

Instructions:

1. Create a usage map block
    1. Go to `Structure > Block Layout > Add Custom Block`.
    2. Give your block a title / description.
    3. In a new window, go to [https://analytics.bceln.ca](https://analytics.bceln.ca). Click the gear icon on the top-right to get to the Settings page. In the lefthand menu, under *Platform*, click *Widgets*. In the bottom section, under *Widgetize reports*, go to `Visitors - Locations > Visitor Map`. Copy the code under *Embed iframe*.
    4. Return to your block creation page and change the Text Format for the Body to **Full HTML**. Paste the iframe code into the Body.
    5. Save. You will be automatically redirected to the configuration page for your new block. Scroll down to *Region* and select where you would like your new block to appear (likely *Content*). Save again.
2. *OPTIONAL:* Create a unique page to display usage data
    1. Go to `Content > Add content > Basic Page`. 
    2. Give your new page a title.
    3. Unfold *URL alias* in the righthand menu. Give the page a user-friendly alias, starting with a forward slash (e.g., `/usage`).
3. Display your new block
    1. Go to `Structure > Block layout`. Scroll down to whichever region you selected for your new block in step 1e above.
    2. Click the *Configure* button on your block. 
    3. Go to *Pages* in the *Visibility* section and with *Show for the listed pages* selected, enter the path for the page you would like to display your block on. If you created a custom page for your usage data, this would be the alias that you have chosen for your page, starting with a forward slash.
    4. Save.

!!! info
    The Block Description/Title for your custom block is configured to display by default. Keep this in mind as you decide which text to add into your block description vs. the body.