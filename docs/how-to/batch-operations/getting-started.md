# Getting Started

Islandora Workbench is a command-line tool. While prior experience working on the command-line would be helpful, the commands and workflow for using Workbench are not prohibitively complicated; the documentation and templates provided by the Arca Office should be sufficient to support you in completing basic tasks.

!!! warning "Caution"

    Permissions for roles with access to Workbench are more expansive than for the average staff role on your site. As you're familiarizing yourself with Workbench, we highly recommend:

    - practicing with a subset of your objects on the Sandbox
    - running `--check` on any tasks prior to a live run, as described below
    - reaching out to the Arca Office with any questions

## Considerations

Though Islandora Workbench has been installed and used on Linux, Mac, and Windows systems, Arca Office staff primarily use MacOS. While commands for Workbench tasks are the same across systems, please be aware that screenshots and support from the Arca Office will be from the perspective of MacOS users.

## Installation & Setup

Review Workbench's [Requirements](https://mjordan.github.io/islandora_workbench_docs/installation/#requirements) page, then follow the steps for installation according to your operating system.

If you are using Workbench for the first time, please notify the Arca Office. Arca Office staff will ensure all the appropriate modules and permissions settings are in place for use with Workbench.

In order to work properly, Workbench config YAML files require the username and password of a user account with advanced permissions. The `Workbench User` role has been created specifically for this purpose. Let the Arca Office know which users on your site should have this role assigned. Exercise caution when assigning this role, as it has more expansive permissions than the default Editor, Ingester, and Submitter roles.

## Running Workbench
Once you have a **config YAML file** prepared for a task, we highly recommend you confirm your materials are valid by running a check with:

```
./workbench --config [name-of-config-file].yml --check
```

This will review both your config.yml and your CSV file(s) for any issues. Error messages may appear directly in your terminal, but you should also consult the `workbench.log` file in your `islandora-workbench` directory for further detail. Reach out to the Arca Office for guidance with any error messages.

If any errors appear related to SSL certs, ensure the following line is included in your **config YAML**:

```
secure_ssl_only: false
```

If there are no errors, you can officially start your Workbench task by running the same command without `--check`:

```
./workbench --config [name-of-config-file].yml
```

If the task has run successfully, messages will appear in your terminal indicating what actions have been taken.

!!! example

    Here is the terminal output after a successful [CREATE](/docs/how-to/batch-ingest/create.md) task was run on the Arca Sandbox:
    ``` bash
    fakeuser@computer123 islandora_workbench % ./workbench --config workbench-sample-create.yml        
    OK, connection to Drupal at https://sandbox.arcabc.ca verified. Ignoring SSL certificates.
    "Create" task started using config file workbench-sample-create.yml.
    Node for "BC ELN Connect – June 2024 (Vol. 22, No. 2)" (record 1) created at https://sandbox.arcabc.ca/node/52 (50%).
    + Media for bceln_connect_summer_2024.pdf created.
    Node for "A Sunflower on the Counter" (record 2) created at https://sandbox.arcabc.ca/node/53 (100%).
    + Media for sunflower.jpg created.
    ```

## Security

As you'll see on the task-specific documentation pages, config YAML files require that you include a username and password for a user with sufficient permissions on your site. 

When troubleshooting with colleagues or Arca Office staff, ensure that you are either **removing** the password from the config file or replacing it with placeholder text.

For added security, you can include the line `remove_password_from_config_file: true` in your *config.yml*. This will automatically remove the password from the file any time you run Workbench.

Visit the official [Workbench documentation](https://mjordan.github.io/islandora_workbench_docs/installation/#password-management) for additional tips.