# Troubleshooting

This page will be populated with common troubleshooting tips for the new platform.

!!! tip
    Perennial tip for all circumstances: If something is going wrong, first, **try clearing the Drupal cache**.

## Taxonomies and term references

### Website error when adding terms with parentheses in the Genre, Subject, Name, etc. fields

#### Issue

In any term/entity reference field that is able to create new terms (e.g. Genre, Subject, Name), we run into an SQL error in the following circumstance:

- Entering a term that contains parentheses,
- Which does not already exist (and would be created automatically)

#### Cause

Term and Entity Reference fields interpret parentheses as a reference to the node/term ID. For example, if “stuff” is taxonomy term 5, and it already exists in the taxonomy, the autocomplete will show “stuff (5)” as you enter it.

If you are entering a new, unknown term (e.g. “things (objects)”), Drupal thinks the parenthetical “objects” is a term ID that is being referenced, and errors out when it can’t find it.

#### Solution

To ingest a new object that uses terms with parentheticals: **Create the term before ingesting the object.**

- Terms with parentheses may be created directly with the Taxonomy “Add Term” process, as they are not creating references, just creating new terms. Go to `Structure -> Taxonomy`, find your taxonomy, and click the `Add term` button.
- This allows you to create the term “things (objects)” into the Genre taxonomy directly.
- When ingesting a new object and using that term, Autocomplete will identify it properly: “things (objects) (35)”


