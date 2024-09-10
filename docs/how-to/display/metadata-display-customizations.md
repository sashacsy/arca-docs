# Metadata Display Customizations and Hacks

This page documents miscellaneous customizations and hacks for the display of repository items, based on requests from membership.

## Contextually changing metadata labels

Use case: You want to present different labels for your metadata display depending on the type (model) of the object.

Components:
  - Blocks
  - Context

**THIS HAS NOT YET BEEN TESTED**

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

