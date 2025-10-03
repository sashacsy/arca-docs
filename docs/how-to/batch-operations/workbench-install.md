# Installing Islandora Workbench

If possible, **ask your IT department to install Islandora Workbench for you**. It will save you a lot of headache. Give them the [official Islandora Workbench installation instructions](https://mjordan.github.io/islandora_workbench_docs/installation/#requirements).

These instructions may be slightly different depending on your computer, operating system version, etc. You may wish to consult with your IT department to get Islandora Workbench installed if you have those resources available to you.

## On a Mac

You will be doing all of this work in the Terminal. Find it in your Applications folder, under Utilities.

Life on a Mac is easier if you have Homebrew. Check if you have it installed: `brew doctor`. If you get "command not found: brew", then [install it following the Homebrew instructions](https://brew.sh) or just copy and paste this command: `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`.

1. First, make sure you have a usable version of Python 3 installed. You will need version 3.9 or higher.
    - Enter either `python --version` or `python3 --version`
    - If you get no useful information (eg "command not found"), or an outdated version, [install with Homebrew](https://docs.brew.sh/Homebrew-and-Python): `brew install python`
2. Make sure you have Git installed: `git --version`
    - If you don't, install it with Homebrew: `brew install git`
3. Navigate to your home directory - `cd ~` - and clone the Islandora Workbench Git repository:
    - `git clone https://github.com/mjordan/islandora_workbench.git`
4. Navigate into the Islandora Workbench directory:
    - `cd islandora_workbench`
5. Create a [Python virtual envrionment]9https://stackoverflow.com/questions/78297215/pip-is-installed-but-can-not-add-python-packages-like-django/78297842#78297842)
    - Make sure you're in the Islandora Workbench directory: `cd ~/islandora_workbench`
    - Create the virtual environment: `python3 -m venv venv`
6. Activate the virtual environment, from within your `islandora_workbench` directory:
    -  `source venv/bin/activate`
    - You will see `(venv)` in your command prompt now, letting you know that you're currently in a Python virtual environment.
    - You will need to do this every time you want to work in Workbench, so that you have access to the various required libraries and plugins.
7. Install the required Python libraries (see the list at https://mjordan.github.io/islandora_workbench_docs/installation/)
    - For each of the libraries, enter `pip install [library-name]`. 
    - This is case-sensitive, so copy and paste or enter carefully.
8. Start using Workbench.