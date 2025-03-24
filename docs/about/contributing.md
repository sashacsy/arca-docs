# Contributing to Arca Docs

Anyone can contribute to Arca Docs. Doing so requires a [Github account](https://github.com).

The pages on Arca Docs are written in Markdown, a simple text processing language that is easy to learn. [If not familiar with Markdown, follow this tutorial](https://www.markdowntutorial.com/).

## Simple method (for small edits)

1.  Navigate to the page you want to edit.
2.  Click the Edit button (pencil icon) in the top right corner of the page.
    -   You will be taken to an editing screen in the Github repo, and will be required to log into Github if not already logged in.
3.  Make your edits, then click the Commit Changes button.
4.  Write a description of your changes
    -   Select "Create a new branch for this commit and start a pull request"
        -   A Pull Request is how you submit your changes to the repository administrator for review.
    -   Click "Propose changes"
5.  In the Pull Request screen, write a more detailed explanation of your edits, and submit your pull request.
    -   Alert the Arca Office that you have made a pull request, so that it can be reviewed quickly.
6.  A Conversation page is generated, where your pull request will be reviewed and tested by an administrator.
    -   You may be asked to make changes to your branch before they are accepted. Edit the branch you have submitted, and the changes will automatically be added to the existing pull request.
7.  After your changes are approved the administrator will Merge your pull request, and your updates will become part of the site.

## Proper method - in browser (for multiple/complex edits and new pages)

1.  Navigate to the repository: <https://github.com/bceln/arca-docs>
2.  In the page header, click the Fork button to create your own copy of the repository. 

    ![Screenshot showing the Fork button in Github](/arca-docs/assets/fork-button.png)

3.  To make changes such as adding a new page, start by creating a new branch:
    -   Click the branch menu button (it should say "main")

       ![Screenshot showing the Branches menu in Github](/arca-docs/assets/branch-menu.png)

    -   Pick a name that's descriptive of your changes, and type it into the search bar.

        ![Screenshot showing how to create a new branch in Github](/arca-docs/assets/branch-switch.png)

    -   Click the "Create branch [branch-name] option
    
4.  Working in your new branch, the pages you want to edit are in the `docs` folder. (Leave the `site` folder alone!)
5.  Under the `docs` folder, navigate to the pages you want to edit, or the folder you want your new page to live in.
6.  Editing pages:
    -   Click the Edit button (pencil icon), make your changes, and click the "Commit changes" button.
    -   Since you're already in your new branch, commit directly to the current branch.
7.  Adding new pages:
    -   Create your page:
        -   Directories are grouped by topic, and they mirror the path you'll find the pages in the URL. So, navigate to the folder your new page is going to live in.
        -   Click the Add File button, and "Create new file".\
            ![Screenshot showing the "Create new file" button](/arca-docs/assets/add-file.png)

        -   Write the file using Markdown, and save it with an appropriate title reflective of its content. The file extension should be `.md`.
    -   Add your new page to the site navigation structure:
        -   At the root directory of the repository, edit the file `mkdocs.yml`.
        -   Under the `nav:` heading, find the menu header you want your new page to appear under.
        -   Follow the conventions of the other pages under that menu, paying attention to formatting and indentation. Format should be `- Page Title: path/to/page.md`.

          ![Screenshot showing a section of the mkdocs.yml file](/arca-docs/assets/yaml-list.png)

        -   Commit your changes to the current branch.
8.  Submit your changes for review with a Pull Request:
    -   Once you've made changes to your branch click back to the root of the repository. You will see a header with a "Compare and pull request" button. Click it. ![Screenshot showing the "Compare and pull request" button](/arca-docs/assets/recent-push.png)

    -   All of the files you have edited will be included in your pull request. Give it a title and a description that explains what changes you have made and why.
    -   Submit the pull request and alert the Arca Office that you have done so.
9.  Your pull request will be tested and reviewed. You may be asked to make changes. **Make those updates in the same branch you created for this pull request**.
10. Once approved, your changes will be part of the site.

## Local clone - in Terminal (for a local, testable clone of the Arca Docs site)

This method requires some knowledge of Git and comfort working in the command line. You don't need to do this unless you want to do a lot of complex work on the docs site.

1.  Install the prerequisite software on your computer:
    -   Git: check if Git is installed by opening the terminal and typing `git version`. If you get a result, you have Git already. If git is not installed, install it. On a Mac: `brew install git`.
    -   MkDocs: Follow the [installation guide](https://www.mkdocs.org/user-guide/installation/).
    -   Material theme for MkDocs: Follow the [installation guide](https://github.com/squidfunk/mkdocs-material).
2.  Fork the git repository (see steps 1 and 2 under "Proper method").
3.  In your fork, get a cloning link: click the "Code" button and copy the link that is generated.

    ![Screenshot showing the button to click to get a cloning link](/arca-docs/assets/clone-box.png)
    
4.  Open the Terminal on your computer, navigate to the directory you want to host your copy of the repository, and clone it: `git clone (link)`.
5.  You now have a local copy of the git repository. You can edit files using text editors (I recommend BBedit) or in the terminal.
6.  Learn the [basics of using git](https://docs.github.com/en/get-started/using-git), for checking out branches, pulling data from remote repositories, and pushing your changes to the remote.
7.  Push your changes to your fork of the repository, and make pull requests to the original branch when you feel they're ready to go.
