# Metadata Display Customizations and Hacks

This page documents miscellaneous customizations and hacks for the display of repository items, based on requests from membership.

## Adding or Removing Fields from Metadata Display

When viewing a Repository Item, metadata shows up below the object viewer. The metadata displayed is a selection of the metadata fields attached to the item, and is not complete.

To add or remove fields:

1. Manage the Display of the Repository Item content type: `Structure -> Content types -> Repository Item -> Manage Display`
2. Click the `Bottom Metadata` section.
3. The metadata fields are arranged in collapsible groups. To change the group a field is in, simply drag it out of one group and into the next.
4. To remove a field from the display, drag it into the Disabled section.
5. To add a field that isn't already present in the display, drag it from the Disabled section into the group of your choice.
6. To make a field group collapsed or expanded by default:
    - Find the group (at the top level of a hierarchy; e.g. "Access and Rights" or "Persons and Affiliations"); you will see "Default state open" or "Default state closed"
    -  Click the gear icon in that row to open the field group configuration
    - Find the `Display element open by default` toggle, and set as desired.
    - Click the Update button in that section.
    - At the bottom of the page, click Save.
    

## Contextually changing metadata labels

Use case: You want to present different labels for your metadata display depending on the type (model) of the object.

Components:

  - Blocks
  - Context

!!! warning "**THIS HAS NOT YET BEEN TESTED**"

1. Create a custom Block using Javascript to change the label.

- At `structure -> block layout` choose `Add custom block`
- Give it a useful name, like "Javascript - Change name of Publisher field"
- Select the Text Format "Full HTML"
- Enter your javascript code as below, changing as needed for your field's machine name and text. e.g. if you wanted to change the label of the Access Conditions field (machine name `field_access_conditions`), replace `field--name-field-publisher` with `field--name-field-access-conditions`.

```
<script>
  var changeElement = document.getElementsByClassName("field--name-field-publisher")[0].children[0];
  changeElement.innerHTML = "Change to whatever you want";
</script>
```

  Alternately, you may want to change the label of a field group. In this case, you have identify the title of the field group you want to select; the Arca Office may help you with this.

```
<script>
   var changeElement = document.querySelectorAll('[title="Persons and Affiliations"]').children[0].children[0];
   changeElement.innerHTML = "Credits";
   changeElement.setAttribute("title", "Credits");
   changeElement.setAttribute("aria-label", "Credits");
</script>
```

