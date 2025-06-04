# Islandora Workbench Tips & Tricks

## Node/Term IDs > Full Names

If you are referencing in your metadata a taxonomy term or an object node that already exists in your site, we recommend using **term IDs** or **node IDs** in lieu of writing out the full node title/term in text. 

While the latter option will technically still work with Workbench, when a full node/term name is written out, Workbench has to cross check that name against every term in the vocabulary or against every object in the repository to find potential matches. This exponentially increases the amount of time it takes to ingest your batch.

Node IDs and term IDs can be used both in your metadata CSV and in your config YAML if you are using [Field Templates](/arca-docs/how-to/batch-ingest/create/#field-templates).

!!! tip "Finding Node IDs or Term IDs"

    Node IDs can be found by visiting a node's page on your site and clicking **Edit**. Once you're brought to the metadata form for that item, you'll see that the URL in the browser bar has changed from the node's text-based alias to a raw URL that includes `/node/X/...`, where `X` is the node ID.

    Term IDs can be found in a similar manner. Go to `/admin/structure/taxonomy` and click **List terms** next to the parent vocabulary of the term you are trying to identify. Hover over or click on the relevant term and you should see a URL that ends in `/term/Y`, where `Y` is the term ID. For example, the term ID for `photographs` in the Arca Sandbox's [Genre vocabulary](https://sandbox.arcabc.ca/admin/structure/taxonomy/manage/genre/overview) is 374. 

## Field Templates
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
    
    You also decide to add templates for CSL type (`"periodical"` or the term ID of `45`), genre (`"newspaper"` or `371`), and resource type (`"Newspaper"` or `237`). **Please note that these term IDs are just examples; make sure to confirm the proper term ID in your repository before using them in Workbench.**
    
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

## Value Templates

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

