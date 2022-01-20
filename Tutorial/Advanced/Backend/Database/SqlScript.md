The SqlScript project maintains all basic data schemas scripts, as well as scripts related to platform initialization data, site initialization data.

The repository of the project is https://gitlab.comm100dev.io/x2/common/database/sqlscript

Please contact your manager about permission-related restrictions.

# How to use this project.

If you now need to publish a new version to production. You want to make some changes to the platform's data or the user's data, you need to complete the following steps.

1. Create a branch for this project

2. Modify the database scripts or add some new scripts.
  - If you need to make schema modifications to tables that already exist, you need to modify the old table-creating scripts as well as the data-related scripts.
  - If you need to build some new tables, you'll add new table-creating scripts and initialize scripts.

3. At the same time, maintain your upgrade scripts under the upgrade directory so that other project teams can upgrade their platforms more easily.

4. Submit your script to the repository. Make sure you have no problem later submit a Merge Request to master.

5. The architect team reviews the script and approve the merge if there are no issues.


# Script naming specification

Usually we continue the previous naming specification by adding `00` before the script file name of the table being built and `01` before the script file name that initializes the data. This naming specification is designed to ensure that the application can execute these scripts in the correct order, and we know that we can only operate the table after it has been created.
