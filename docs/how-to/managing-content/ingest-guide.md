# Islandora 2 Ingest Guide

In the old Islandora platform, to ingest content, you had to navigate to your collection, manage the collection, add a new object to the collection, select a content model, and fill out a form tailored to that specific kind of content.

In the new platform, it’s much more streamlined, and integrated with the way other Drupal content works.

This guide describes how each field in the ingest form works, and what to do with them.

**Note**: While all Arca members will have each of these fields present in their Repository Item content type, we can suppress the visibility of fields that your institution does not use. This suppression is at the repository level, not for individual types of content. Contact the Arca Admin Centre for support.

Video ingest walkthrough: [https://youtu.be/SSjbLJXc0u8](https://youtu.be/SSjbLJXc0u8)

## Getting started

Log in to your repository. Once logged in, youl have access to the administrative toolbar, where you can manage the repository and its content.

## Creating Collections

Before ingesting content, you will probably want collections to organize them. See the [Islandora Wiki](https://islandora.github.io/documentation/tutorials/how-to-create-collection/) for an explanation of how collection creation and management works.

## Ingesting an Islandora Object

1.	In the admin toolbar, find the Content icon, Add Content, and choose “Repository Item”.
    * In Modern Islandora, all repository content – from images to collections to compound objects – has the type “Repository Item”.
2.	Fill out the metadata form as appropriate.


## Filling in the metadata form
In modern Islandora, all objects are created using the same metadata form. The form fields are grouped by type and collapsed, so you can easily ignore the fields that are not relevant to your content.

In your repository, you might have chosen to simplify the ingest process by suppressing the visibility of some of these fields. They still exist in your Repository Item content type, but they are not visible to you when you fill out the form. 

!!! bug "New taxonomy terms and parentheses"
    When creating a new taxonomy term from the node metadata form, please note that the inclusion of parentheses in the term may result in an SQL error. This is the case for any term/entity reference fields, including Genre, Subject, and Name. See [Troubleshooting](https://bceln.github.io/arca-docs/troubleshooting/troubleshooting/#taxonomies-and-term-references) for more detail and solutions.

1.	Title 
    * This field is required, and it will act as the label for your object. 
2.	Content Type
    * Determines how Islandora will handle your object, including the viewers it assigns to display your content, derivatives it creates, etc. 
3.	Resource Type
    * A metadata field, with no specific technical effect – best practice is to populate it.
    * The vocabulary for these is the standard [Dublin Core resource types](https://www.dublincore.org/specifications/dublin-core/resource-typelist/).
4.	Title (again)
    * A second instance of “Title”; this field creates a full title record for your object (and not just a label). It will likely be identical to the first Title field, but does not have to be.
    * Title Type:
        * Indicates different kinds of title (alternate, translated, abbreviated, etc.)
    * Part Name/Number:
        * Information about the item’s place in a series.
    * Multiple Titles can be added (“Add Title” button repeats the field set).
5.	Collection
    * Reference to existing “container” type items in the repository – collections, newspapers, compound objects, etc.
    * Autocompletes: Begin typing, and results will appear. Select the correct parent from the list.
    * The item may be in more than one container: click the “Add Container” button to repeat. 
6.	Object Type (Citation)
    * This field lets you specify what type of object you’re ingesting more granularly, specifically for the feature that automatically creates citations. Your selection determines the citation format.
7.	Genre
    * The Genre field references two taxonomies: 
        * COAR Resource Types, and 
        * Genre (primarily AAT and MARC terms used by current objects).
    * Autocompletes: Start typing in the Genre field, and a list of options from the referenced vocabularies will appear. Select the term that applies.
    * If the term you need isn’t present, you can type in your new term, and it will be added to the Genre vocabulary for use by future objects. You can also edit the term later to add detail, authorities, spelling corrections, etc.
    * You can add multiple Genres with the “Add another item” button.
8.	Peer Review Status
    * If applicable; primarily for academic publications.
9.	Persons and Affiliations
    * All the contributors to your object are added in this section. Separate fields are created for Persons and Organizations.
    * Names are no longer simple text fields: they are term references, pointing to specific entities in the Person and Corporate Body taxonomies. This allows the same entity to be referenced by any number of repository items, and makes it easier to control forms of name for individuals.
    * Relationship Type is their Role – author, creator, publisher, reviewer, etc. These relator terms come from the [MARC Relator list](https://www.loc.gov/marc/relators/relaterm.html).
    * There are two ways to add new Persons and Organizations:
        1. Enter a new name in this field. It will automatically populate the taxonomy, and that new entity will be available for future ingests. You can edit the term later to flesh it out with more detail.
        2. Create the new Person or Corporate Body taxonomy term first. This will allow you to add more information about the person, such as affiliations, description, etc., before you start relating content to them.
10.	ETDs
    * This section is for information about theses specifically, and is part of what gets sent to Theses canada. Fill in as appropriate.
11.	Institution and Department
    * Institutional and departmental affiliation information. These fields reference their own taxonomies. 
    * These sections are for academic publications – theses, journal articles, etc.
12.	Version Identification
    * Intended primarily for datasets or software. If this item has a particular version number or code, enter it here.
13.	Resource Publication Status
    * Specific to journal article publication. Identifies the item’s stage in the publication process.
14.	Change Note
    * Version control is already covered by Drupal, so this information is only needed if you are keeping specific versions of content in the repository.
15.	Abstract/Description
    * Abstract: 
        * Primarily for journal articles, reports, theses, and other academic work. 
        * Paste in the actual Abstract from the document.
    * Description/Synopsis:
        * A description of the object, less formal than an academic abstract.
    * Table of Contents: 
        * If the item has a table of contents, it can be added here.
        * Text Format: not a metadata field; it just determines how the editor is presented when entering the information into the field. 
    * Target Audience:
        * Indicates if the item is targeted to a specific intellectual or age level.
16.	Language:
    * Language is from a controlled list, a term reference pointing to the Language taxonomy. If you have a language that isn’t in the vocabulary, adding it here should append it to the taxonomy list.
    * You can add more than one language if it’s a multilingual item with the “Add another item” box.
17.	Identifiers
    * There are many different kinds of identifiers. The Local Identifier is an uncontrolled textbox in which you can put whatever type of identifier you use locally. If you have other more standardized identifiers, you can use the other boxes – PURL, DOI, Handle, etc.
    * ARK IDs: 
        * Arca will create ARK IDs for your objects automatically; only enter an ARK ID here if the object already has one.
18.	Subjects and Classifications
    * Keywords: 
        * Uncontrolled terms
        * Enter one at a time, using “add another” button
    * Subject Topic, Names, etc. are all term references which look up entities in the appropriate Taxonomies. If they do not already exist, your entries will be added. 
    * LCC classification, DDC, and others – enter if applicable
19. Conference/event
    * References an event taxonomy. Enter if applicable to the object.
20. Series
    * If the item is part of a series, enter its number and the series title as appropriate.
21. Publication/container information
    * If this item is part of a larger publication (newspaper, journal, book, etc.) the parent item’s information goes here.
    * Note that all metadata in this section applies to the container item, and not the repository item you are currently ingesting.
22. Origin Information:
    * Multiple entries are possible in this field via the "Add Origin Information" button. Each fieldset under Origin Information describes a particular "origin" for the item.
    * Event type: 
        * This is describes the stages of creation of the item – publication, distribution, etc.  Record if relevant.
    * Place:
        * Records where the event occurred. e.g. if the event is Publication, this would be the publication place.
    * Dates:
        * Date Created:
            * The date the item was created (may be different from when it was published).
        * Date Issued:
            * The most important Date field - every object in your repository should ideally have a Date Issued.
            * When the item was published or otherwise made available.
        * Date Captured: 
            * Digitization date; record only if needed.
        *  Other date: 
            * Any other relevant type of date.
        * Copyright date:
            * Enter if applicable.
        * **Use [EDTF for all date formats](https://www.loc.gov/standards/datetime/).**
    * Publisher, Edition, Issuance, Frequency:
        * Particularly applicable to Book and Serial/Newspaper type items; fill as appropriate.
23.	Physical Description
    * Extent:
        * Size, duration, or other relevant information about the item’s extent. 
    * Number of pages/first page/last page: 
        * Fill as appropriate. 
    * Physical Form:
        * Artistic medium, dimensions, any other relevant information.
    * Digital Origin:
        * Select list, describes how the object became digitized.
    * Physical Description Note:
        * Anything not covered above.
24.	Relationships:
    * If this item has relationships to other items, whether inside or outside of the repository, you would put that information here.
    * **The fields in this section all describe the item this object has a relationship with, not the item itself.**
    * Fill in these fields if applicable; not strictly necessary or recommended if the related item is in your repository, to avoid duplicated and outdated metadata.
25.	Notes:
    * Multiple Note entries can be made via the "Add Note" button.
    * Notes may be given a Type to differentiate them. 
    * Conflict of interest statement:
        * Used particularly for articles.
    * Administrative Notes:
        * Only shown to repository staff; hidden from anonymous users. 
26.	Funding:
    * If your object was created with help from grant funding or sponsorship, that information goes into this section.
27.	Access and Rights
    * A set of fields describing the access conditions, restrictions, and reproduction rights for your object.
    * Access Conditions: 
        * A controlled list of brief terms to indicate the kind of access available to this item. 
        * Autocomplete, but each term has “access” in it. If you type “a” you’ll get the full list.
    * Restriction on Access:
        * Explain here details on the access restrictions – who is allowed, under what conditions, etc.
    * Use and Reproduction:
        * A textual description of how the object might be used. An uncontrolled field; subsequent fields are used for controlled terms.
    * Rights Statement:
        * A [statement from rightsstatements.org](https://rightsstatements.org/page/1.0/?language=en). Autocompletes: choose the name of the appropriate statement, and it will produce a URI in the back end.
    * Use License:
        * Applies a [Creative Commons License](https://creativecommons.org/share-your-work/). Autocompletes from typing.
    * Copyright Holder: Name of copyright holder.
28.	Record Information:
    * If you need to provide information about the creation of the record itself, you can add it here.
    * Note that the date fields **do not need your input**. That information is captured automatically when you create and edit items.
    * Record origin and information note: 
        * If you need to capture the provenance and process of record creation
29.	Add media
    * The “add media” toggle, if turned on, means that after you save this Repository Item, you will be sent to the Media page. That is where you will add a file that will become part of the object.
    * If you choose not to add media, you will create a metadata-only record, but you can choose to add media to the item later via the object’s Media tab. Adding media later is a bit more complex than doing it from ingest, so it is recommended to start with a file in mind.
    * After Saving the item, you will be taken to the Media interface. Follow the [detailed instructions on adding media](/arca-docs/docs/how-to/managing-content/media.md).
