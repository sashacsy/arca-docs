# Managing Taxonomies

Find all your taxonomies under `admin/structure/taxonomy`.

## Adding terms

The taxonomies you will likely deal with most often are:

- Person: All of the persons referenced in your metadata. Includes your own institutional scholars and their full profiles.
- Corporate Body: The corporate equivalent of Person.
- Degree Names: For Theses etc.
- Genre
- Institution: Also mainly for Theses etc.
- Subject

For each of these, terms may be added in two ways:

1. Navigate to the Taxonomy term list, and click "Add term"
2. Enter the new term into the metadata form as you're creating a Repository Item. The new term will be created automatically.

## Editing terms

When editing a term, you can change its name, as well as any metadata fields it contains. Changing the name of a term updates that name for all Repository Items referencing that term automatically.

1. Navigate to the taxonomy you want to manage (`Structure -> Taxonomy -> [Taxonomy name])`) to get the list of terms
2. Find the term you want to edit, and click the Edit button
3. Edit whatever fields need editing
4. Save

Note that *deleting* a term outright will destroy any references made to that term (e.g. metadata in your Repository Items). Only delete terms if you are certain that's what you want.

### Finding a term in a long list

Some term lists, such as Person, can get extremely long. We have provided a special View to make it easier to search through those terms.

To find your Person term so you can edit it:

1. Go to `Structure -> Taxonomy -> Person -> Person Term Search`
2. Search for the Person's name. You can filter the list to show only Persons that you have marked as Faculty Scholars, or Persons who are *not* marked that way.

## Merging duplicate terms

If you have multiple versions of the same term (e.g "Smith, J.", "Smith, J.A.", and "J. Smith"), they are treated as separate entities in Islandora. Deleting any of them would break the references in your Repository Item metadata.

Instead, use the Term Merge module to combine all of the duplicate entities into one. This also updates the references in all of the Repository Items, so that every item authored by J. Smith is linked to the same person.

To use Term Merge:

1. Make sure the Term Merge module is installed (/admin/modules)
2. Make sure you have permission for that module (contact the Arca Office if you don't)
3. Manage your taxonomy (`Structure -> Taxonomy -> [Taxonomy name]`)
4. Click the `Merge` tab
5. You will see a checklist of all the terms in your taxonomy. Check off each duplicate term.
    - If you plan to merge your duplicates into one of the existing terms, do *not* check off the term you want to use.
6. Click the Merge button
7. On the next page, you can choose how to complete the merger:
    a. New term: Create a new term, with a new name, to replace all of the selected terms.
    b. Existing term: Select one of the other terms in your taxonomy, to merge the selected terms into.
8. Submit

All the selected terms will be merged into the target term, and all references to those terms will be updated to refer to the term you've chosen.
