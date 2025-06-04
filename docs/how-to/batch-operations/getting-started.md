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

If you are using Workbench for the first time, please notify the Arca Office. Arca Office staff will ensure all the appropriate modules and permissions settings are in place in your repository for use with Workbench.

In order to work properly, Workbench config YAML files require the username and password of a user account with advanced permissions. The `Workbench User` role has been created specifically for this purpose. Let the Arca Office know which users on your site should have this role assigned. 

!!! warning
    Exercise caution when assigning the `Workbench User` role, as it has more expansive permissions than default Editor, Ingester, and Submitter roles. These higher-level permissions could be abused to break site functionality.

## Prepare Templates
Visit the [Templates page](/arca-docs/how-to/batch-operations/templates) for information on how to download and prepare your spreadsheet and config YAML templates. 

Review the documentation specific to your task for additional tips.

## Run Workbench
Once you have a **config YAML file** prepared for a task, we highly recommend you confirm your materials are valid by running a check. Step-by-step instructions for navigating the Terminal and running checks/tasks can be found on the task-specific documentation pages.

## Security

As you'll see on the task-specific documentation pages, config YAML files require that you include a username and password for a user with sufficient permissions on your site. 

When troubleshooting with colleagues or Arca Office staff, ensure that you are either **removing** the password from the config file or replacing it with placeholder text.

For added security, you can include the line `remove_password_from_config_file: true` in your *config.yml*. This will automatically remove the password from the file any time you run Workbench. This means **you will need to re-add your password to the file every time you run it**.

Visit the official [Workbench documentation](https://mjordan.github.io/islandora_workbench_docs/installation/#password-management) for additional tips.