# Islandora 2 Ingest Guide

In the old Islandora platform, to ingest content, you had to navigate to your collection, manage the collection, add a new object to the collection, select a content model, and fill out a form tailored to that specific kind of content.

In the new platform, it’s much more streamlined, and integrated with the way other Drupal content works.

This guide describes how each field in the ingest form works, and what to do with them.

**Note**: While all Arca members will have each of these fields present in their Repository Item content type, we can suppress the visibility of fields that your institution does not use. This suppression is at the repository level, not for individual types of content. Contact the Arca Admin Centre for support.

Video ingest walkthrough: [https://youtu.be/SSjbLJXc0u8](https://youtu.be/SSjbLJXc0u8)

## Getting started

Log in to your repository. Once logged in, youl have access to the administrative toolbar, where you can manage the repository and its content.

## Creating Collections

Before ingesting images, documents, and videos, you will probably want to create some Collections to organize them. See the [Islandora Wiki](https://islandora.github.io/documentation/tutorials/how-to-create-collection/) for an explanation of how collection creation and management works.

## Ingesting an Islandora Object

1.	In the admin toolbar, find the Content icon, Add Content, and choose “Repository Item”.
    * In Modern Islandora, all repository content – from images to collections to compound objects – has the type “Repository Item”.
2.	Fill out the metadata form as appropriate.


## Filling in the metadata form

In modern Islandora, all objects are created using the same metadata form. The form fields are grouped by type and collapsed, so you can easily ignore the fields that are not relevant to your content.

In your repository, you might have chosen to simplify the ingest process by suppressing the visibility of some of these fields. They still exist in your Repository Item content type, but they are not visible to you when you fill out the form. 

!!! bug "New taxonomy terms and parentheses"
    When creating a new taxonomy term from the node metadata form, please note that the inclusion of parentheses in the term may result in an SQL error. This is the case for any term/entity reference fields, including Genre, Subject, and Name. See [Troubleshooting](/arca-docs/troubleshooting/troubleshooting/#taxonomies-and-term-references) for more detail and solutions.

Our ingest form is organized into Paragraphs - organized groups of metadata fields. These Paragraphs are collapsed; you will need to click into each of their titles to access the next group of fields.

### Summary
####	Title 

* This field is required, and it will act as the label for your object.
* Additional/Alternative titles: Add these if there are other forms of title you wish to add.
    * Title Type:
        * Indicates different kinds of title (alternate, translated, abbreviated, etc.)
    * Part Name/Number:
        * Information about the item’s place in a series.
    * Multiple Titles can be added (“Add Title” button repeats the field set).

    !!! warning "Titles and URL Aliases"
        Unless you have an alternate URL alias pattern in place, URL aliases for repository items are set to generate automatically from item titles by default. If you revise an item's title at any point after creation and you don't toggle `Generate automatic URL alias` off under **URL alias** settings on the object, the URL alias will change with the title.

#### Content Type

* The Islandora Model. Determines how Islandora will handle your object, including the viewers it assigns to display your content, derivatives it creates, etc. 
    3.  Collections(s)
        * References existing “container” type items in the repository – collections, newspapers, compound objects, etc.
        * Autocompletes: Begin typing, and results will appear. Select the correct parent from the list.
        * The Collection must exist first before you can enter it here. Create your collections before you create their children.
        * The item may be in more than one container: click the “Add Container” button to repeat. 
    4.	Resource Type
        * A standardized metadata field describing the type of object with more nuance.
        * The vocabulary for these is the standard [Dublin Core resource types](https://www.dublincore.org/specifications/dublin-core/resource-typelist/).
    5. Object Type (Citation)
        * Islandora creates automatic Citations in different styles when viewing the object.
        * Select the appropriate term here to make sure the right kind citation format is generated.
    6. Genre
        * The Genre field references two taxonomies: 
            * COAR Resource Types, and 
            * Genre (primarily AAT and MARC terms used by current objects).
        * Autocompletes: Start typing in the Genre field, and a list of options from the referenced vocabularies will appear. Select the term that applies.
            * If the term you need isn’t present, you can type in your new term, and it will be added to the Genre vocabulary for use by future objects. You can also edit the term later to add detail, authorities, spelling corrections, etc.
        * You can add multiple Genres with the “Add another item” button.
    7. Peer Review Status
        * Select this if your item is an academic paper that has been peer reviewed.
2. Persons and Affiliations
    * All the contributors to your object are added in this section. Separate fields are created for Persons and Organizations.
        * Names are no longer simple text fields: they are term references, pointing to specific entities in the Person and Corporate Body taxonomies. This allows the same entity to be referenced by any number of repository items, and makes it easier to control forms of name for individuals.
        * Relationship Type is their Role – author, creator, publisher, reviewer, etc. These relator terms come from the [MARC Relator list](https://www.loc.gov/marc/relators/relaterm.html).
        * There are two ways to add new Persons and Organizations:
            1. Enter a new name in this field. It will automatically populate the taxonomy, and that new entity will be available for future ingests. You can edit the term later to flesh it out with more detail.
            2. Create the new Person or Corporate Body taxonomy term first. This will allow you to add more information about the person, such as affiliations, description, etc., before you start relating content to them.
3.	ETDs
    * This section is for information about theses specifically, and is part of what gets sent to Theses canada. Fill in as appropriate. Degree names and levels reference taxonomies.
4.	Institution
    * Institutional and departmental affiliation information. These fields reference their own taxonomies. 
    * These sections are for academic publications – theses, journal articles, etc.
5.  Abstract/Description
    1. Abstract
        * Used specifically for academic papers and theses -- items with a formal Abstract. Put the entire contents of the abstract here.
    2. Description
        * For any non-academic content. A synopsis, a description of the item, etc.
    3. Table of Contents: 
        * If the item has a table of contents, track list, etc., it can be added here.
        * Text Format: not a metadata field; it just determines how the editor is presented when entering the information into the field.
    4. Target Audience:
        * Indicates if the item is targeted to a specific intellectual or age level. Most items would be "general".
    5. Language
        * Language is from a controlled list, a term reference pointing to the Language taxonomy. If you have a language that isn’t in the vocabulary, adding it here should append it to the taxonomy list.
        * You can add more than one language if it’s a multilingual item with the “Add another item” box.6. Identifiers
6. Identifiers
    * There are many different kinds of identifiers. The Local Identifier is an uncontrolled textbox in which you can put whatever type of identifier you use locally. If you have other more standardized identifiers, you can use the other boxes – PURL, DOI, Handle, etc.
    * ARK IDs: 
        * Arca will (eventually) create ARK IDs for your objects automatically; only enter an ARK ID here if the object already has one.
    * Local Contexts Project ID:
        * If your object has a project ID from Local Contexts, this will eventually allow Traditional Knowledge Labels to be displayed (when the module is ready).
    * Other identifiers could at some future point be used with APIs that display other data such as altmetrics and citations.  
7. Subjects and Classifications
    * Keywords: 
        * Any uncontrolled terms you want to add.
        * These can be entered all at once separated by commas, or entered one at a time, using “add another” button
        * Best practice: enter groups of related keywords in each field.
    * Subjects (Topic, Name, Organization, Geographic, Temporal) are all term references which look up entities in the appropriate Taxonomies. If they do not already exist, your entries will be added. 
    * Coordinates:
        * MUST be in decimal format. (e.g. "49.26426643074269, -123.09688106028514")
    * LCC classification, DDC, and others – enter if applicable
8. Conference/Event
    * References an event taxonomy. Enter if applicable to the object.
9. Series
    * If the item is part of a series, enter its number and the series title as appropriate.
10. Publication/Container Information
    * If this item is part of a larger publication (newspaper, journal, book, etc.) the parent item’s information goes here.
    * Note that all metadata in this section applies to the *container item*, and not the repository item you are currently ingesting.
11. Origin Information
    * Multiple entries are possible in this field via the "Add Origin Information" button. Each fieldset under Origin Information describes a particular "origin" for the item.
    * Event type: 
        * This is describes the stages of creation of the item – publication, distribution, etc.  Record if relevant.
    * Place:
        * Records where the event occurred. e.g. if the event is Publication, this would be the publication place.
    * Dates:
        * Date Created/Issued:
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
12.	Physical Description
    * Extent:
        * Size, duration, or other relevant information about the item’s extent. 
    * Number of pages/first page/last page: 
        * Fill as appropriate. 
    * Physical Form:
        * Artistic medium, dimensions, any other relevant information.
    * Reformatting Quality
        * If applicable (i.e. this object is a digitized copy of some original item)
    * Digital Origin:
        * Select list, describes how the object became digitized.
    * Physical Description Note:
        * Anything not covered above.
13.	Relationships:
    * If this item has relationships to other items, whether inside or outside of the repository, you would put that information here.
    * The URL field can point at an external entity, but it can *also* point to another item in your repository. If that item exists in your repository, it is recommended to link it here.
    * **The other fields in this section all describe the item this object has a relationship with, not the item itself.**
        * Fill in these fields only if applicable. These fields are *not necessary, nor recommended, if the related item is also in your repository*, to avoid duplicated and outdated metadata.
14. Notes
    * Multiple Note entries can be made via the "Add Note" button.
    * Notes may be given a Type to differentiate them.
    * Administrative Notes:
        * Only shown to repository staff; hidden from anonymous users. 
15. Location
    * All fields relate to where the item is found, either physically or electronically.
    * Item Identifier: specifically for identifying this object physically within the context of its canonical location.
    * URL: If the object also exists at an external URL, you may include that here.
16. Access and Rights
    * A set of fields describing the access conditions, restrictions, and reproduction rights for your object.
    * Access Conditions: 
        * A controlled list of brief terms to indicate the kind of access available to this item. 
        * Autocomplete, but each term has “access” in it. If you type “a” you’ll get the full list.
    * Restriction on Access:
        * Free-text field. Explain here details on the access restrictions – who is allowed, under what conditions, etc.
    * Use and Reproduction:
        * Free-text field. A textual description of how the object might be used. An uncontrolled field; subsequent fields are used for controlled terms.
    * Rights Statement:
        * A [statement from rightsstatements.org](https://rightsstatements.org/page/1.0/?language=en). Autocompletes: choose the name of the appropriate statement, and it will produce a URI in the back end.
    * Use License:
        * Applies a [Creative Commons License](https://creativecommons.org/share-your-work/). Autocompletes from typing.
17. Record Information
    * If you need to provide information about the creation of the record itself, you can add it here.
    * Note that the date fields **do not need your input**. That information is captured automatically when you create and edit items.
    * Record origin and information note: 
        * If you need to capture the provenance and process of record creation.
18.	Add media
    * The “add media” toggle, if turned on, means that after you save this Repository Item, you will be sent to the Media page. That is where you will add a file that will become part of the object.
    * If you choose not to add media, you will create a metadata-only record, but you can choose to add media to the item later via the object’s Media tab. Adding media later is a bit more complex than doing it from ingest, so it is recommended to start with a file in mind.
    * After Saving the item, you will be taken to the Media interface. Follow the [detailed instructions on adding media](/arca-docs/docs/how-to/managing-content/media.md).
