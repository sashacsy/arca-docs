# CREATE Tasks

CREATE tasks are for batch "creation", or ingest, of repository items.

## Requirements

To run a CREATE task, you will need:

* a **CSV** containing your repository item metadata
* a **config YAML** file that specifies your task type and all options related to that task
* a directory of **media files** (please see [this section](!!!) if ingesting metadata records without media)

The Arca Office has prepared templates for the first two items in this list. Templates are linked in the next section.

Please note there are different templates for **single objects** (e.g., photographs, documents) and **paged content** (e.g., book pages, newspaper issues). 

As values in the metadata spreadsheet will need to comply with the metadata standards and formats outlined in the Arca [Ingest Guide](/arca-docs/how-to/managing-content/ingest-guide), make sure to familiarize yourself or your staff with the guide before working on a Workbench batch.

!!! warning "CSV Encoding"
    Your CSV should use UTF-8 encoding. 
    
    While the Arca metadata template is provided in `.xlsx` format to allow for data validation on controlled fields, we recommend using LibreOffice or Open Office instead of Excel when saving your final CSV to ensure that it is properly encoded and that special characters render appropriately.

## Download Templates
There are two ways to download the templates linked on Arca's GitHub repository:

1. Visit the page for the relevant file linked below and click on :octicons-download-16: `Download Raw File`.
    - PRO: This method is quick and doesn't require any familiarity with Git/GitHub.
    - CON: You will need to periodically visit the page for each template type to check for any updates and re-download them manually.
2. Clone the template repository with `git clone https://github.com/bceln/arca-templates.git`. Once cloned, navigate to the folder in your terminal and run `git pull` any time you want to fetch updates.
    - PRO: This method takes minimal effort and ensures *all* templates included in the repository pull in the latest changes at once.
    - CON: Requires basic familiarity with Git/GitHub.

**Single Object Templates**

Metadata Spreadsheet: [[Link]](https://github.com/bceln/arca-templates/blob/main/templates/CREATE/single%20object%20ingest/Single_Object_Ingest_Template.xlsx)
<br>Config YAML: [[Link]](https://github.com/bceln/arca-templates/blob/main/templates/CREATE/single%20object%20ingest/single-object-template.yml)

**Paged Object Templates**

Metadata Spreadsheet: [[Link]](https://github.com/bceln/arca-templates/blob/main/templates/CREATE/paged%20object%20ingest/Paged_Object_Ingest_Template.xlsx)
<br>Config YAML: [[Link]](https://github.com/bceln/arca-templates/blob/main/templates/CREATE/paged%20object%20ingest/paged-object-template.yml)

## About Metadata Templates

* The first row of the template contains the machine names for every possible field. You can delete any columns you are not using, but do not alter existing headers/field names, as Workbench will be unable to locate the fields in your site if you do. 
* The second row of the template contains descriptions of most fields, including which fields are **REQUIRED** and which fields are **PARAGRAPHS**. Delete this row on the final version of your CSV, before running your task.
    * The descriptions in the template are brief; the [Ingest Guide](/arca-docs/how-to/managing-content/ingest-guide/#filling-in-the-metadata-form) contains more detail on each field if you need it.
* Rows 3 and 4 contain sample data. Remember to delete or overwrite these values before running your task.
* Repeatable fields use a pipe character ` | ` as a delimiter. To enter multiple values into the **Keyword** field for example, enter into your spreadsheet cell: `commmunity planning|urban geography`
    * See the [Paragraphs](/arca-docs/how-to/batch-ingest/create/#an-important-note-on-paragraphs) section for exceptions.
* Some metadata fields allow for custom link text (e.g., Identifier URI, Related Item URL). To express this in your metadata spreadsheet, type the URL followed by `%%`, then end with the custom link text. Do not include blank spaces around the `%%`.
    * ex. `https://wwww.sandbox.arcabc.ca%%Arca Sandbox Site`

## About Config YAML Templates

* Once downloaded, give your YAML template a distinct name for each ingest. You may make configuration setting changes that vary from ingest to ingest and precise filenaming keeps batches organized.
* The Arca YAML templates are intended to be "grab and go", but there are *many* other configuration options that allow you to customize your ingest process or output. As you become more comfortable with Workbench, review the [official documentation](https://mjordan.github.io/islandora_workbench_docs/configuration/#the-configuration-file) for a full list of config options.
* Any lines in the YAML template that start with `#` are null (i.e., will not be read by Workbench as part of a task). 
* Headers and notes from the Arca Office start with `# \\`. Please pay attention to these, as they will indicate which sections should be updated and which contain settings that should not be touched.
* **Do not make changes** to the second set of configuration options in the YAML template, under the header `# \\ REQUIRED TAXONOMY SETTINGS`. These settings are configured to allow you to add new terms to open vocabularies (like *Genre* or *Subject*), without making site-breaking changes to protected, controlled vocabularies (e.g., *Islandora Models* or *CSL Type*)
* Settings under the header `# \\ OPTIONAL OUTPUT INFORMATION...` are related to a CREATE task's output CSV. This is a CSV generated automatically by Workbench which includes information about each new node created by the task, including node IDs. While output CSV generation is technically optional (and does add a little time to the ingest process), it is **recommended that you keep these settings turned on**. If you ever wish to make bulk changes to the objects you've just ingested, this is the easiest way to keep track of each object's node ID.

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

Your YAML file should be saved in your root `islandora_workbench` directory. Run the check command directly from here:

``` bash
./workbench --config sunflower.yml --check
```

If your check returns any errors, consult `workbench.log` for details. If the check passes, proceed to step 5.

### 5. Run CREATE Task

Run the CREATE task with the same command, minus `--check`:

```bash
./workbench --config sunflower.yml
```

If successful, you will see messages in the terminal that the relevant nodes and media have been created.

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

While paged content parents and children can technically be ingested in the same batch as long as they appear sequentially in the spreadsheet (parent before children), the Arca Office recommends creating parent objects as a separate, primary step. It's rare that multiple parents need be ingested at once in an uninterrupted task, and creating the parents separate from the children reduces the opportunities for human error and issues with sequencing, field or value templates, etc.

Before preparing paged content, make sure to review the [official Islandora documentation](http://mjordan.github.io/islandora_workbench_docs/paged_and_compound/#csv-and-directory-structure) on filenaming and subdirectory structure to ensure the proper sequence of pages is maintained upon ingest.

## An Important Note on Paragraphs

Arca's installation of Islandora makes extensive use of **Paragraphs**, a special Drupal unit that allows for sets of repeatable fields. A list of all of the Paragraph types available by default in an Arca site can be viewed at `/admin/structure/paragraphs_type`. One of the most important Paragraph types is *Origin Information*, which includes the primary date field for all repository items.

If the repository items being ingested have metadata in fields that are part of Paragraphs, these fields must be accounted for in the config YAML for the task. Arca's config YAML templates for both paged content and single object content include **all** possible Paragraph fields by default. 

The following excerpt of the **paged content config YAML** template lists the fields for the *Origin Information* Paragraph:

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
* `field_order` is followed by a list of subfields that exist within that paragraph. If you are ingesting a batch of items that does not make use of a particular subfield in the paragraph, the row for that subfield can be nulled out with `#` in the config file. Any null/blank values that aren't nulled out with `#` will need to be accounted for with double delimiters in each row of the metadata.
* `field_delimiter` is the chosen delimiter between each of the subfields in the paragraph.
* `subdelimiter` is the chosen delimiter between several paragraphs on the same object (i.e., multiple Origin Information paragraphs)


## Tips & Tricks

### Node/Term IDs > Full Names

If you are referencing in your metadata a taxonomy term or an object node that already exists in your site, we recommend using **term IDs** or **node IDs** in lieu of writing out the full node title/term in text. 

While the latter option will technically still work with Workbench, when a full node/term name is written out, Workbench has to cross check that name against every term in the vocabulary or against every object in the repository to find potential matches. This exponentially increases the amount of time it takes to ingest your batch.

Node IDs and term IDs can be used both in your metadata CSV and in your config YAML if you are using [Field Templates](/arca-docs/how-to/batch-ingest/create/#field-templates).

!!! tip "Finding Node IDs or Term IDs"

    Node IDs can be found by visiting a node's page on your site and clicking **Edit**. Once you're brought to the metadata form for that item, you'll see that the URL in the browser bar has changed from the node's text-based alias to a raw URL that includes `/node/X/...`, where `X` is the node ID.

    Term IDs can be found in a similar manner. Go to `/admin/structure/taxonomy` and click **List terms** next to the parent vocabulary of the term you are trying to identify. Hover over or click on the relevant term and you should see a URL that ends in `/term/Y`, where `Y` is the term ID. For example, the term ID for `photographs` in the Arca Sandbox's [Genre vocabulary](https://sandbox.arcabc.ca/admin/structure/taxonomy/manage/genre/overview) is 374. 

### Field Templates
If certain columns in your metadata spreadsheet contain the exact same value for every object (i.e., the same value appears in every row down the column), you may wish to employ **field templates** in your config YAML. While not required, templates allow you to declutter your spreadsheet and save time having to fill out repetitive data. 

In both config YAML templates, you will find a section that starts with the header `# \\ OPTIONAL FIELD & VALUE TEMPLATES - Delete or null if not using.` Under this header, include the following:

* a line that simply reads `csv_field_templates:`
* on every subsequent line, the machine names of the fields you would like to create templates for in the format ` - field_name_here: template value`
    * Include a blank space before **and** after the hyphen.
    * Template values can be term IDs/node IDs *or* full text strings but, as noted in the [previous section](/arca-docs/how-to/batch-operations/create/#nodeterm-ids-full-names), IDs are recommended for a faster ingest.
    * If using full text strings, include double quotations around the string (e.g., `field_genre: "newspapers"`)
* the line `ignore_csv_columns:` followed by a space and the machine name of every field listed above in single quotations (`['field_name_1_here', 'field_name_2_here']`)
    * This line makes it so that Workbench knows to defer to the templates in the config YAML instead of your CSV values.
    * These columns should be empty in your CSV but if there happens to be old data in any of them, it will be ignored by Workbench.



!!! example

    You have a batch of 150 newspaper issues to ingest, all belonging to the same newspaper title. The parent newspaper object has already been created and has a node ID of 25663 in your repository. Rather than enter `25663` in 150 rows in the `field_member_of` column in your metadata spreadsheet, you opt to use CSV field templates in your config YAML. 
    
    You also decide to add templates for CSL type (`"periodical"` or the term ID of `45`), genre (`"newspaper"` or `371`), and resource type (`"Newspaper"` or `237`).
    
    Your config YAML now includes the following:

    ```yaml
    # \\ OPTIONAL FIELD & VALUE TEMPLATES - Delete or null if not using.
    csv_field_templates:
     - field_csl_type: 45
     - field_member_of: 25663
     - field_genre: 371
     - field_resource_type: 237
    ignore_csv_columns: ['field_csl_type', 'field_member_of', 'field_genre', 'field_resource_type']
    ```

### Value Templates

Unlike the example above, you may encounter a situation where *part* of a field's value needs to vary from object to object. This is possible with **value templates**, which allow you to insert a placeholder for the dynamic component of the value.

With this method, your metadata spreadsheet should contain only the portion of the value that changes, while the fixed portion is defined in the config YAML. The variable is represented in the YAML as `$csv_value`. 

!!! example

    You have a batch of 150 newspaper issues to ingest, all belonging to the same newspaper title. In `field_extent`, you would like to indicate the total number of pages in each issue, but each row of your metadata spreadsheet includes only the number and no mention of "pages". 
    
    You add the following to your config YAML:

    ```yaml
    csv_value_templates:
     - field_extent: $csv_value pages
    ```

A particularly efficient use of value templates is with Paragraph fields. For `field_origin_information` in particular, there will likely be subfields that repeat for every object in your batch while others, like `field_date_issued`, vary. 

!!! example

    You have opted to include metadata for only 4 of the subfields in the **Origin Information** Paragraph and have nulled the rest. The **Origin Information** section of your YAML file looks as follows: 

    ```yaml
    paragraph_fields:
    node:
        field_origin_information:
        type: origin_information
        field_order:
            - field_event_type
            - field_place
            - field_date_issued
    #        - field_date_captured
    #        - field_other_date
    #        - field_copyright_date
            - field_publisher
    #        - field_edition
    #        - field_issuance
    #        - field_frequency
    ```
    Of the 4 subfields in use, only `field_date_issued` differs for each object. This is reflected in your value templates section:

    ```yaml
    csv_value_templates:
     - field_extent: $csv_value pages
     - field_origin_information: publication:Vancouver (B.C.):$csv_value:Very Good Press
    ```

    With these templates, every object in your batch will have:
    
    * `publication` as the event type,
    * `Vancouver (B.C.)` as the place of publication,
    * `Very Good Press` as the publisher.
    
    The only value pulled from your spreadsheet is the date. As a result, the `field_origin_information` column in your CSV only contains dates in `YYYY-MM-DD` format.

    ### Breaking Up Large Batches

    