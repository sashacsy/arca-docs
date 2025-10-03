# Islandora Workbench Templates

## Download Templates
There are two ways to download the templates linked on Arca's GitHub repository:

1. Visit the page for the relevant file linked below and click on :octicons-download-16: `Download Raw File`.
    - PRO: This method is quick and doesn't require any familiarity with Git/GitHub.
    - CON: You will need to periodically visit the page for each template type to check for any updates and re-download them manually.
2. Clone the template repository with `git clone https://github.com/bceln/arca-templates.git`. Once cloned, navigate to the folder in your terminal and run `git pull` any time you want to fetch updates.
    - PRO: This method takes minimal effort and ensures *all* templates included in the repository pull in the latest changes at once.
    - CON: Requires basic familiarity with Git/GitHub.

### CREATE Templates
**Single Object Templates**

Metadata Spreadsheet: [[Link]](https://github.com/bceln/arca-templates/blob/main/templates/CREATE/single%20object%20ingest/Single_Object_Ingest_Template.xlsx)
<br>Config YAML: [[Link]](https://github.com/bceln/arca-templates/blob/main/templates/CREATE/single%20object%20ingest/single-object-template.yml)

**Paged Object Templates**

Metadata Spreadsheet: [[Link]](https://github.com/bceln/arca-templates/blob/main/templates/CREATE/paged%20object%20ingest/Paged_Object_Ingest_Template.xlsx)
<br>Config YAML: [[Link]](https://github.com/bceln/arca-templates/blob/main/templates/CREATE/paged%20object%20ingest/paged-object-template.yml)

### UPDATE Templates
!!! warning "Coming soon"

## About Metadata Templates

* The first row of the template contains the machine names for every possible field. You can delete any columns you are not using, but do not alter existing headers/field names, as Workbench will be unable to locate the fields in your site if you do. 
* The second row of the template contains descriptions of most fields, including which fields are **REQUIRED** and which fields are **PARAGRAPHS**. Delete this row on the final version of your CSV, before running your task.
    * The descriptions in the template are brief; the [Ingest Guide](/arca-docs/how-to/managing-content/ingest-guide/#filling-in-the-metadata-form) contains more detail on each field if you need it.
* Rows 3 and 4 contain sample data. Remember to delete or overwrite these values before running your task.
* Repeatable fields use a pipe character ` | ` as a delimiter. To enter multiple values into the **Keyword** field for example, enter into your spreadsheet cell: `commmunity planning|urban geography`
    * See the [Paragraphs](/arca-docs/how-to/batch-operations/create/#an-important-note-on-paragraphs) section on the *CREATE Tasks* page for exceptions.
* Some metadata fields allow for custom link text (`field_identifier_uri` and `field_url`). To express this in your metadata spreadsheet, type the URL followed by `%%`, then end with the custom link text. Do not include blank spaces around the `%%`.
    * ex. `https://wwww.sandbox.arcabc.ca%%Arca Sandbox Site`
    * Note that the field for the Related Item Paragraph (`field_related_item_paragraph`) also contains a `field_url` subfield. If using the Arca template, it appears third in the subfield list.

## About Config YAML Templates

* Once downloaded, give your YAML template a distinct name for each ingest. You may make configuration setting changes that vary from ingest to ingest and precise filenaming keeps batches organized.
* For day-to-day operations, you *only* ever need to change the following lines in the YAML template:
    * Host (your site URL)
    * Username (your Islandora Workbench user account)
    * Password (password for that account)
    * input_dir (name of the directory containing your files)
    * input_csv (filename for your CSV)
* Any lines in the YAML template that start with `#` are null (i.e., will not be read by Workbench as part of a task). 
* Headers and notes from the Arca Office start with `# \\`. Please pay attention to these, as they will indicate which sections should be updated and which contain settings that should not be touched.
* **Do not make changes** to the second set of configuration options in the YAML template, under the header `# \\ REQUIRED TAXONOMY SETTINGS`. These settings are configured to allow you to add new terms to open vocabularies (like *Genre* or *Subject*), without making site-breaking changes to protected, controlled vocabularies (e.g., *Islandora Models* or *CSL Type*)
* Settings under the header `# \\ OPTIONAL OUTPUT INFORMATION...` are related to a CREATE task's output CSV. This is a CSV generated automatically by Workbench which includes information about each new node created by the task, including node IDs. While output CSV generation is technically optional (and does add a little time to the ingest process), it is **recommended that you keep these settings turned on**. If you ever wish to make bulk changes to the objects you've just ingested, this is the easiest way to keep track of each object's node ID.
* For more advanced configurations, you can find more information in the [official documentation](https://mjordan.github.io/islandora_workbench_docs/configuration/#the-configuration-file) for a full list of config options.