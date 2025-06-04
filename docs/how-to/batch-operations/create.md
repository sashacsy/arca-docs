# CREATE Tasks

CREATE tasks are for batch "creation", or ingest, of repository items.

## Requirements

To run a CREATE task, you will need:

* a **CSV** containing your repository item metadata
* a **config YAML** file that specifies your task type and all options related to that task
* a directory of **media files** (please see [this section](!!!) if ingesting metadata records without media)

The Arca Office has prepared templates for the first two items in this list. Visit the [Templates page](/arca-docs/how-to/batch-operations/templates) for more detail on how to download and work with them.

Please note there are different templates for **single objects** (e.g., photographs, documents) and **paged content** (e.g., book pages, newspaper issues). 

As values in the metadata spreadsheet will need to comply with the metadata standards and formats outlined in the Arca [Ingest Guide](/arca-docs/how-to/managing-content/ingest-guide), make sure to familiarize yourself or your staff with the guide before working on a Workbench batch.

!!! warning "CSV Encoding"
    Your CSV should use UTF-8 encoding. 
    
    While the Arca metadata template is provided in `.xlsx` format to allow for data validation on controlled fields, we recommend using LibreOffice or Open Office instead of Excel when saving your final CSV to ensure that it is properly encoded and that special characters render appropriately.

## CREATE Task Steps

### 1. Prepare Media Files
Create a subdirectory in your `islandora_workbench` directory. This subdirectory will contain files specific to this task. 

We recommend giving the directory a descriptive filename that makes the content within easily identifiable (e.g., `sunflower_photo_archive`). Deposit any media files for this ingest into the project subdirectory.

### 2. Prepare Metadata CSV
Download the appropriate metadata template for your ingest type (single objects or paged content).

Fill out the metadata on the first sheet. There should be one row for every item you are ingesting. Once you've finished filling out the metadata, confirm that the number of rows matches the number of media files you have.

Ensuring it uses UTF-8 encoding, save the first sheet as a CSV into the same project subdirectory as your media files. Give it a descriptive name (e.g., `sunflower_photo_archive.csv`)

### 3. Prepare Config YAML 
Download the appropriate config YAML for your ingest type (single objects or page content). Give your YAML template a distinct filename for the current ingest (e.g., `sunflower_photo_archive.yml`).

Replace anything in ==square brackets==, as these are required settings that are likely to change from task to task. Pay particular attention to the directives in the headers that start with `# \\`, as some sections contain settings that should not be altered.

Save your config YAML in your root `islandora_workbench` directory.

### 4. Perform Checks
Open your preferred **terminal** application. Navigate to your `islandora_workbench` directory:

``` bash
cd islandora_workbench
```

Your YAML file should be saved in your root `islandora_workbench` directory. We highly recommend you first confirm your materials are valid by running a check with:

``` bash
./workbench --config sunflower.yml --check
```

If your check returns any errors, consult `workbench.log` for details. If the check passes, proceed to step 5.

### 5. Run CREATE Task

Run the CREATE task with the same command, minus `--check`:

```bash
./workbench --config sunflower.yml
```

If the task has run successfully, messages will appear in your terminal indicating what actions have been taken.

!!! example

    Here is the terminal output after a successful CREATE task was run on the Arca Sandbox:

    ``` bash
    fakeuser@computer123 islandora_workbench % ./workbench --config workbench-sample-create.yml        
    OK, connection to Drupal at https://sandbox.arcabc.ca verified. Ignoring SSL certificates.
    "Create" task started using config file workbench-sample-create.yml.
    Node for "BC ELN Connect – June 2024 (Vol. 22, No. 2)" (record 1) created at https://sandbox.arcabc.ca/node/52 (50%).
    + Media for bceln_connect_summer_2024.pdf created.
    Node for "A Sunflower on the Counter" (record 2) created at https://sandbox.arcabc.ca/node/53 (100%).
    + Media for sunflower.jpg created.
    ```

### 6. QC & Clean Up
Visit your site and confirm:

* Objects have been ingested to the appropriate collections
* All metadata is appearing in the expected fields
* Media is appearing with the appropriate viewer

Small issues can likely be addressed with manual fixes to the object through the browser UI. If, however, you have concerns with the ingest that cannot be addressed with simple fixes, the batch is relatively small, *and* you would like to start over:

* Run `rollback.yml` to reverse the ingest (see [here](!!!))
* Make the appropriate changes to the metadata or config files
* Re-run the CREATE task with the steps outlined above

Once you are satisfied with your ingest, you may wish to reorganize your `islandora_workbench` directory to keep it clean for future tasks. 

Archive your config YAML in the project subdirectory in case you need to return to it for future troubleshooting or clean-up. Ensure the batch's OUTPUT CSV, which should contain all the node IDs of the repository items you just created, is also saved in the project subdirectory. This can be used for future UPDATE tasks.

## Single Object vs. Paged Content

By "single object" content, we are referring to standalone repository items that are **not** paged objects (e.g., newspapers, books).

Single object ingests can be run by following the steps above in order. Media files for each object can all exist in a flat directory, so you may have images appearing alongside document PDFs. The `file` column in your metadata spreadsheet is the critical piece in this type of ingest; it is what ties a row of metadata to a particular media file.

!!! warning
    For the purposes of structuring a CSV and config YAML, **PDF newspaper issues** are considered **single objects** and not paged content. When working with PDF issues, please refer to the [Single Object Content](/arca-docs/how-to/batch-ingest/create/#ingesting-single-object-content) guidance above.

Ingests of paged content differ in that the media files for each child item are separated into their own subdirectory. Instead of a `file` column, the metadata spreadsheet contains a `directory` column to point to the subdirectory containing all media files for that child. These subdirectories should include image files at the very least, but may optionally contain OCR/HOCR text files if available for each page.

While paged content parents and children can technically be ingested in the same batch as long as they appear sequentially in the spreadsheet (parent before children), the Arca Office recommends creating parent objects as a separate, primary step. Creating the parents (e.g. collections, books and newspapers) separately from the children reduces the opportunities for human error and issues with sequencing, field or value templates, etc.

Before preparing paged content, make sure to review the [official Islandora documentation](http://mjordan.github.io/islandora_workbench_docs/paged_and_compound/#csv-and-directory-structure) on filenaming and subdirectory structure to ensure the proper sequence of pages is maintained upon ingest.

## An Important Note on Paragraphs

Arca's installation of Islandora makes extensive use of **Paragraphs**, a special Drupal unit that allows for sets of repeatable fields. A list of all of the Paragraph types available by default in an Arca site can be viewed at `/admin/structure/paragraphs_type`. One of the most important Paragraph types is *Origin Information*, which includes the primary date field for all repository items (`field_date_issued`).

Because repository items being ingested may have metadata in fields that are part of Paragraphs, these fields must be accounted for in the config YAML for the task. Arca's config YAML templates for both paged content and single object content include **all** possible Paragraph fields by default.

If you are ingesting a batch of items that does not make use of a particular subfield in a paragraph, the row for that subfield can be nulled out by adding a `#` to the start of the line in the config file. Any null/blank values that aren't nulled out with `#` will need to be accounted for with double delimiters in each row of the metadata. See [Paragraph Data Entry](/arca-docs/how-to/batch-operations/create/#paragraph-data-entry) for further detail.

Let's take a closer look at how Paragraphs and their subfields are structured in the config YAML templates. The following excerpt of the **paged content config YAML** template lists the fields for the *Origin Information* Paragraph:

``` yaml linenums="1"
paragraph_fields:
  node:
    field_origin_information:
      type: origin_information
      field_order:
        - field_event_type
        - field_place
        - field_date_issued
        - field_date_captured
        - field_other_date
        - field_copyright_date
        - field_publisher
        - field_edition
        - field_issuance
        - field_frequency
      field_delimiter: ':'
      subdelimiter: '|'
```

In this example:

* `field_origin_information` is the machine name of the Paragraph's field on Repository Items. It can be found on your site here: `/admin/structure/types/manage/islandora_object/fields`. This is the field name/header that you will be adding values under in your metadata CSV.
* `type` is the machine name of the Paragraph Type, available here: `/admin/structure/paragraphs_type`. It's usually just the field name without `field_`.
* `field_order` is followed by a list of subfields that exist within that paragraph. As noted earlier in this section, you can null out any subfields you are not using by adding a `#` to the start of the subfield's line in the config file.
* `field_delimiter` is the chosen delimiter between each of the subfields in the paragraph.
* `subdelimiter` is the chosen delimiter between several paragraphs on the same object (i.e., multiple Origin Information paragraphs)

### Paragraph Data Entry

#### Single Paragraph
The metadata spreadsheet templates contain columns for Paragraph fields as a whole. Subfields are not broken out into their own columns. When entering data into Paragraph fields in the spreadsheet, data for each subfield is separated by the `field_delimiter` indicated in your config YAML. 

!!! example

    Let's look at an example for an ingest where you only want to include 3 subfields from the Origin Information Paragraph: `field_place`, `field_date_issued`, and `field_publisher`. There are two possible options moving forward.

    === "Option 1 (Recommended)"

        You null out the unwanted subfields in your config YAML template:

        ```yaml
        paragraph_fields:
            node:
                field_origin_information:
                type: origin_information
                field_order:
        #            - field_event_type
                    - field_place
                    - field_date_issued
        #            - field_date_captured
        #            - field_other_date
        #            - field_copyright_date
                    - field_publisher
        #            - field_edition
        #            - field_issuance
        #            - field_frequency
                field_delimiter: ':'
                subdelimiter: '|'
        ```

        In your metadata spreadsheet, you enter the values in the `field_origin_information` column as follows for every relevant object:

        ```yaml
        Burnaby (B.C.):2024-06:BC Electronic Library Network
        ```

    === "Option 2"

        You don't change the visibility of any subfields in your config YAML template:

        ```yaml
        paragraph_fields:
            node:
                field_origin_information:
                type: origin_information
                field_order:
                    - field_event_type
                    - field_place
                    - field_date_issued
                    - field_date_captured
                    - field_other_date
                    - field_copyright_date
                    - field_publisher
                    - field_edition
                    - field_issuance
                    - field_frequency
                field_delimiter: ':'
                subdelimiter: '|'
        ```

        In your metadata spreadsheet, you enter the values in the `field_origin_information` column with extra delimiters as placeholders for the missing data:

        ```yaml
        :Burnaby (B.C.):2024-06::::BC Electronic Library Network
        ```

        The data in this spreadsheet cell starts with a `:` to account for `field_event_type` being empty. This is followed by values for `field_place` and `field_date_issued`. The subsequent series of `:` delimiters is to account for the next 3 subfields being skipped. The cell ends with metadata for `field_publisher`.

        Note that even though there are technically 3 more subfields available after `field_publisher` (`field_edition`, `field_issuance`, and `field_frequency`), no placeholder delimiters are needed after the last subfield containing data.

As you'll see in the config YAML templates, the field delimiter for almost every Paragraph type is a colon `:`. The only exception is the Related Item Paragraph, which uses a caret `^` instead. This is because the Related Item Paragraph contains an entity reference field (`field_relationship_type`) that refers to two possible vocabularies: DCMI Relation Types and MODS Relation Types. 

In order to indicate to Workbench which vocabulary a relationship taxonomy term is coming from, the value has to be expressed in the format `vocabulary:term`. 

* Ex. 1: When describing a Related Item with the *preceding* relationship type, you would need to structure your subfield metadata as: `mods_relation_types:preceding`
* Ex. 2: When describing a Related Item with the DCMI relation type *hasFormat*, you would enter: `dcmi_relation_types:hasFormat`. 

Because the convention for referring to either vocabulary requires the use of a colon, the `field_delimiter` for the Related Item Paragraph cannot also be a colon and a caret `^` has been assigned instead in the templates.

The full value of a Related Item Paragraph cell in your spreadsheet would therefore look something like:

>`mods_relation_types:preceding^BC ELN Connect – April 2024^https://bceln.ca/news-events/news/2024/05/april-2024-vol-22-no-1%%BC ELN Website Link^1 page^newsletters^6393`

#### Multiple Paragraphs

Use **subdelimiters** when you want your object to include multiple Paragraphs. The subdelimiter for every Paragraph type is a pipe `|` character.

!!! example

    In this example, you are ingesting newspaper objects and want to include **2 Related Item Paragraphs** in the metadata for each object – one paragraph to describe a **preceding** title and one paragraph to describe a **succeeding** title.

    You first opt to null out any unwanted subfields in the Related Item Paragraph section of your config YAML: 

    ```yaml
    field_related_item_paragraph:
      type: related_item
      field_order:
        - field_relationship_type
        - field_title_plain
        - field_url
    #    - field_related_item_extent
        - field_related_item_genre
    #    - field_related_item_identifier
      field_delimiter: '^'
      subdelimiter: '|'
    ```

    You then structure the values in the `field_related_item_paragraph` column in your metadata spreadsheet as follows:

    >```
    mods_relation_types:preceding^The Semiahmoo Sun 1940-1947^https://bchdp.arcabc.ca/islandora/object/whiterock%3A1%%The Semiahmoo Sun 1940-1947^newspaper|mods_relation_types:succeeding^The White Rock Sun 1958-1972^https://bchdp.arcabc.ca/islandora/object/whiterock%3A3%%The White Rock Sun 1958-1972^newspaper
    ```

    Note that the information related to the **preceding** title, the Semiahmoo Sun, and the **succeeding** title, the White Rock Sun, is separated by a pipe `|`. 
