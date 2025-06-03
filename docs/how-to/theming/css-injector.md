# Modifying page display with CSS Injector

The Arca theme provides a good baseline for page design, but you might encounter cases where you want to make certain adjustments to the spacing, colour, and layout of your pages. You can do that using CSS Injector.

## Requirements:

* Enable the Asset Injector module
* Ensure you have permission to use the CSS Injector (ask the Arca Office to enable this)
* Know [how to use CSS](https://www.w3schools.com/css/)

## Identifying the changes you want to make

First, you must figure out what elements need to be edited, and how you'll do that. Your Web browser can help.

1. Navigate to the page where you want to make changes.
2. Enable the Inspection window:
    - Right click anywhere on the page, and click "Inspect" or "Inspect element" or similar (wording depends on your browser)
    ![<# Inspect menu in browser #>](/arca-docs/assets/inspect.png "Screenshot")
3. The Inspect panel shows you the HTML behind the page content, as well as the CSS that styles the HTML. 
    - If you move your mouse over the different HTML elements, the areas they govern are highlighted on the page.
    ![<# Highlighted HTML in the browser's Inspect pane #>](/brandon/arca-docs/assets/inspect-panel.png "Screenshot")
    - Right clicking on a page area and clicking `Inspect` will jump to the relevant HTML.
4. Click on the HTML element that you want to style. The CSS pane to the right shows the CSS rules that are active on this element.
![<# CSS Elements pane in the browser Inspect tool #>](/arca-docs/assets/css-elements.png "Screenshot")
5. Make changes to the CSS in the pane to preview them:
    - If you want to change an existing rule (e.g. increase the font size), find the line that governs that element and make an edit.
    ![<# Changing font size in CSS pane #>](/arca-docs/assets/css-font.png "Screenshot")
    - If you want to create a brand-new rule for this element, click the `+` button. It will start a new, empty rule with the HTML element selected.
    ![<# alt text #>](/arca-docs/assets/css-plus-button.png "Screenshot")

    ![<# alt text #>](/arca-docs/assets/css-new-rule.png "Screenshot")

    !!! warning "Selecting appropriate elements" 
        Make sure you have selected the correct element, and that it only affects the pieces you want to change. 
        e.g. if you select an HTML element like `p`, that will affect the styling for all `<p>` elements on the page. 
        If you select a class like `.my-class` or an ID like `#this-thing`, your rule will only affect elements tagged with that class or ID. 
        Follow the [CSS tutorial](https://www.w3schools.com/css/) for lessons on different elements. 

6. Scroll up and down on your page to make sure your rule is working, and that it is only applied to the specific parts you want it applied to.
7. If it looks good, highlight and copy the *entire* new rule, and proceed to the next section.

## Creating a CSS Injector rule

CSS Injector rules are configured at `/admin/config/development/asset-injector/css`.

!!! warning "Test in Sandbox first" 
    Poorly-formatted or over-scoped rules could break display on your site. Test your rules in the [Arca Sandbox](https://sandbox.arcabc.ca) first.

1. To create a new rule, click the "Add CSS Injector" button.
2. Under "Label", give it a title that describes what the rule accomplishes. 
    - e.g. If your rule changes the font size for `<p>` elements just on the `About` page, title it "Change font size on About page paragraphs"
3. The "Enabled" toggle sets whether or not this rule is active. You can disable a rule and keep it in your system for later use.
4. Under "Code", paste the CSS rule that you copied from your Inspector tests. ***Make sure it is properly formatted, or you will get errors that may render your site unusable.***
5. Under "Conditions", choose how and when this rule is applied. You will want to limit your conditions to either Pages or Content Types.
    - For "Pages"", set the paths to the pages you want the rule to apply. e.g. if the rule affects only the front page, enter `<front>`. If it affects all pages under the `/about/` path, enter `/about/*`.
    - For "Content Type", your rule will apply to all items with the selected content type. Check off the ones you want the rule to apply to (probably either Basic Page or Repository Item). 
    !!! warning "Limiting the scope of your changes"
        It is ***very important*** to apply your rules ***only to specific pages or content types***, and not universally. Otherwise you may get unexpected results.
6. Save your rule
7. Browse your site to make sure your rule is working and is correctly applied and limited.
