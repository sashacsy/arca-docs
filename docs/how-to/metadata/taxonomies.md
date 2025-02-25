# How Taxonomies Work

Taxonomies provide a way to organize and re-use metadata values, and to link them together. They provide a way to ensure that metadata is consistent throughout your repository, avoiding common errors like misspellings, and also provide a way to give more detail about the metadata value itself. Each taxonomy term has its own Drupal node (page), and lists all items that reference it.

Many of our metadata fields are *taxonomy term references* rather than free text. When filling out metadata forms, existing taxonomy terms are available to select. In many cases, if a term does not already exist, filling out the field will create it for you, so it can be used again later.

## Taxonomies in Arca and their purposes

### COAR Access Rights

Referenced by: Access Conditions

Purpose: Describes the level of access provided to the resource (open access, embargoed, metadata only, etc.) 

Notes: Static and controlled; should not be added to.

### COAR Resource Type:

Not in use; [Library of Congress Resource Types](#library-of-congress-resource-types) are used instead.

### COAR Version Types

Referenced by: Resource Publication Status

Purpose: Version identification

Notes: Static and controlled; should not be added to.

### Conference/Events

Referenced by: Conference/Events

Purpose: Creates an entity for a specific Conference or Event. Identifies objects that are related to that particular event (eg conference papers).

Notes: Entities can be created directly in the Taxonomy menu, or on-the-fly while creating Repository Items. Be sure to watch the auto-complete in case your entity already exists.

### Corporate Body

Referenced by: Funder, Organizations, Subject Name Organization, Institution [Repository Item]; Affiliation [Person taxonomy]

Purpose: Entities for organizations, corporate bodies, etc. Includes institutions, companies, performance groups - any kind of corporate entity. 

Notes: Entities can be created directly in the Taxonomy menu, or on-the-fly while creating Repository Items. Be sure to watch the auto-complete in case your entity already exists.

### Country

Not used

### Creative Commons Licenses 4.0

Referenced by: Use License

Purpose: Specify a Creative Commons license that applies to the item.

Notes: Static and controlled; should not be added to.

### CSL Type

Referenced by: Object Type (Citation)

Purpose: Indicates for the Citation module exactly what kind of object this is, so it can generate the appropriate citations.

Notes: Static and controlled; should not be added to.

### Culture

Referenced by: Person taxonomy

Purpose: Indicates the Person's cultural context. Does not appear on Repository Item metadata, only when viewing the Person and any associated views.

### DCMI Relation Types

Referenced by: Relationships (organizations, persons, related item, etc.)

Purpose: Indicates the type of relation the item has to the referenced entity. Has both functional purposes (e.g. isMemberOf a given collection) and descriptive purposes (e.g. isBasedOn a different entity).

Notes: Static and controlled; should not be added to.

### DCMI Resource Types

Not used as far as we know

### Degree Levels

Referenced by: Thesis metadata

Purpose: Controlled vocabulary indicating degree level. Important for ETD deposits.

Notes: Static and controlled; should not be added to.

### Degree Names

Referenced by: Thesis metadata

Purpose: "Name of the degree associated with the work as it appears within the work." Thesis metadata. Required for ETD deposits.

Notes: Entities can be created directly in the Taxonomy menu, or on-the-fly while creating Repository Items. Be sure to watch the auto-complete in case your entity already exists.

### Discipline

Referenced by: Thesis metadata

Purpose: "Area of study of the intellectual content of the document. Usually the name of a program or department." 

Notes: Entities can be created directly in the Taxonomy menu, or on-the-fly while creating Repository Items. Be sure to watch the auto-complete in case your entity already exists.

### Family

Not used as far as we know

### Funders

Referenced by: "Funder" field

Purpose: Indicates the entity that funded the production/creation of the item.

Notes: The Funder field on repository items draws from both the Funders taxonomy and the Corporate Body taxonomy. Entries in the "Funders" taxonomy specifically must be created ahead of the objects. Any new entires in the "Funder" field on Repository Items are automatically placed in the "Corporate Body" taxonomy.

### Genre

Referenced by: Genre

Purpose: Required field for organizing and classifying content.

Authorities: Authority may be specified, selecting from:

    * Getty AAT
    * Library of Congress Thesaurus for Graphic Terms
    * Library of Congress Genre/Form Terms
    * Library of Congress MARC Genre Terms
    * Local
    * Other

Notes: Entities can be created directly in the Taxonomy menu, or on-the-fly while creating Repository Items. Be sure to watch the auto-complete in case your entity already exists. Authority Source may have to be edited after record creation.

### Geographic Location

Referenced by: Geographic Subject

Purpose: Organizes geographic locations.

Notes: Not a controlled field; it is up to you to standardize your terms.

### Institution

Referenced by: Institution field for ETD metadata; Affiliation field in Person taxonomy

Purpose: Institution entity specifically for academic affiliations.

Notes: OFFICE TODO -- look into including Institution on the list of taxonomies that the Organization field can reference, and including Corporate Body on the list of taxonomies that the Institution and Affiliations can reference.

### Islandora Access

Referenced by: `field_access_terms` on the Repository Item content type.

Purpose: Used in [Permissions By Term](https://www.drupal.org/docs/contributed-modules/permissions-by-term), one of the access control methods available in Arca.

Notes: This is not a recommended approach for access control, particularly in sites with large numbers of objects.

### Islandora Display

Referenced by: The Display Hints section on the Repository Item content type.

Purpose: Defines which methods are used to display Media on Repository Items. Specifically important for paged content, newspapers, documents, and images.

Notes: For the most part, these terms are automatically populated when filling out your metadata. If ingesting with Workbench, you will need to use these terms to tell Islandora how they are going to be displayed.

### Islandora Media Use

Referenced by: Media

Purpose: Tells Islandora how the media will be used - i.e. what derivatives to generate, and how to display.

Notes: For the most part you will be using Original File, though some content types use Service File instead. These differences are documented in the notes about specific types of content. This is a restricted taxonomy; it should not be edited.

### Islandora Models

Referenced by: Content Type field

Purpose: Defines the type of item you are ingesting. Islandora uses this information to determine how to handle the item.

Notes: This is a restricted taxonomy; it should not be edited.

### Language

Referenced by: Language field; Record Cataloguing Language field

Purpose: Descriptive metadata.

Notes: Starts out empty. You may add to this list. Allows for authority sources to be specified.

### Library of Congress Resource Types

Referenced by: Resource Type field

Purpose: Descriptive and categorization.

Notes: This is a restricted taxonomy; it should not be edited.

### Local Access Conditions

Not used

### MODS Relation Types

Referenced by: Relator fields (i.e. Related Item)

Purpose: Describes how the item is related to other items.

Notes: This is a restricted taxonomy; it should not be edited.

### OpenAIRE Object Types

???

### Organizational Units

Referenced by: ???

### Part Type

Referenced by: Part fields on the Repository Item content type

Purpose: If the object is part of another item, defines more specifically what part it is (i.e. chapter, issue, paragraph, volume, etc.)

Notes: This is a restricted taxonomy; it should not be edited.

### Person

Referenced by: Persons and Affiliations fields, relationship fields, collections of scholars

Purpose: Person entities for identifying authors, artists, etc.; as well as identifying Scholars specific to your institution's needs.

Notes: Any named entity should end up here. If when creating a Repository Item your Person does not already exist in the taxonomy, they will be created. There are many fields available on the Person terms, which will be empty in the case of automatically-generated Persons. There is also an "Institution scholar" field which, if selected, will identify the person as a Scholar for use in any particular views you want to generate.

### Physical Form

Referenced by: Physical Form field

Purpose: Defines the physical form of the item. Uses a taxonomy so you can group and classify items by physical form.

Notes: Starts out empty. You may add to this list. 

### PSO Fields

PSO: Publishing Status Ontology. These taxonomies relate specifically to the publishing status of academic articles. It is unclear whether our implementation makes any use of these vocabularies at all.

### Rights Statements

Referenced by: Rights Statement field

Purpose: Controlled list of [Rights Statements](https://rightsstatements.org) defining the usage and copyright status of a work. Good choice for a search facet.

Notes: This is a restricted taxonomy; it should not be edited.

### Scholars

Not in use - all Scholars in Arca are Persons.

### Series Titles

Referenced by: Series Titles field (in the Series paragraph)

Purpose: Allows multiple Repository Items to be linked to the same Series entity

Notes: Starts out empty. You may add to this list.


### Subject

Referenced by: Subject field

Purpose: Controlled or uncontrolled list of Subject terms. Having them in a taxonomy makes your items easier to classify and group together. 

Notes: This is an empty taxonomy that is automatically populated as you add to item metadata. It may also be pre-populated by adding terms. Authority sources may be specified.

### Tags

Default Drupal taxonomy; not in use

### Temporal

Referenced by: Temporal Subject field

Purpose: Defined temporal periods (e.g. "1970s", "Cretaceous Era", etc.)

Notes: Authority sources may be specified. Good idea to follow an authority, but not required.

### Titles

Referenced by: Publication Title

Purpose: Controlled list of titles of works, journals, or other publications. Allows individual articles to be marked as belonging to the same journal.

Notes: This is an empty taxonomy that is automatically populated as you add to item metadata. It may also be pre-populated by adding terms.

