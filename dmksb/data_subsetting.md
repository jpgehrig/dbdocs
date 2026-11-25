This chapter covers the Integrated Subset and Mask capability, where you perform data masking and subsetting in a single taskflow and outlines a number of scenarios to demonstrate the process. You must have the Oracle Data Masking and Subsetting Pack license to use data subsetting features.

**Note:**

Data subsetting is supported only in Oracle Database versions 10.1 and higher. The procedures in this chapter are applicable only to Oracle Enterprise Manager Cloud Control 12.1 and higher.

### Creating a Data Subset Definition

The procedure described in this section enables you to create a subset database, after which you can perform other tasks, such as editing the properties of the subset definition or exporting a subset definition.

The interface also allows you to perform inline, or at the source, masking while creating the subset definition.

Before proceeding, ensure that you have the following privileges:

- `EM_ALL_OPERATOR` for Enterprise Manager Cloud Control users

  **Note:**

  The EM_ALL_OPERATOR privilege is not required, if you have the following privileges:

  Target Privileges (applicable to all targets):

  - Connect to any viewable target

  - Execute Command Anywhere

  - View Any Target

  Resource Privileges:

  - Job System

  - Named Credential

  - Oracle Data Masking and Subsetting resource privilege

- `SELECT_ANY_DICTIONARY` privilege for database users

- To perform an in-place delete operation, the DBA user must be granted `EXECUTE_ANY_TYPE` privilege.

- To subset tables that have Virtual Private Database (VPD) policies, the user performing subsetting must be granted `Exempt Access Policy` privilege.

#### To create a data subset definition:

1.  From the Enterprise menu, select Quality Management, then Data Subsetting Definitions.

2.  Open the Actions menu in the Data Subsetting Definitions page, then select Create, or just click the Create icon.

3.  Define the data subset definition properties:

    1.  Provide the requisite information in the General pop-up that appears, then click Continue.

        You can select any source database associated with the Application Data Model.

        If you are performing masking within the subset definition, you must select the same ADM and target used in creating the masking definition.

    2.  Provide a job name, credentials, and specify a schedule in the Schedule Application Detail Collection pop-up that appears, then click Submit.

        If you want to use new credentials, choose the New Credentials option. Otherwise, choose the Preferred Credentials or Named Credentials option.

    The space estimate collection job runs, and then displays the Data Subset Definitions page. Your definition appears in the table, and the Most Recent Job Status column should indicate Scheduled, Running, or Succeeded, depending on the schedule option selected and time required to complete the job.

4.  Select the definition within the table, open the Actions menu, then select Edit.

    The Database Login page appears.

5.  Select either Named Credentials or New Credentials if you have not already set preferred credentials, then click Login.

6.  In the Applications subpage of the Edit page, move applications from the Available list to the Selected list as follows:

    - If you intend only to mask the data (no subsetting), select all applications.

    - If you intend only to subset the data (no masking), select specific applications as appropriate.

    - If you intend both to subset and mask the data, the applications selected must include those that the masking definitions require.

    The names of application suites, applications, or application modules are maintained in the Application Data Model.

7.  Click the Object Rules tab.

    **Note:**

    If you are masking only, set the Default Object Rows option to include all rows and skip to Step 13. The Column Mask Rules tab, Rule Parameters tab, and additional features on the Object Rules tab pertain specifically to subsetting.

    You can add rules here to define the data to include in the subset.

8.  Select Actions, then Create to display the Object Rule pop-up, or just click the Create icon.

    1.  Select the application for which you want to provide a rule.

        Associate the rule with all objects, a specific object, or a specific type of object.

    2.  If you select All Objects, in the Rows to Include section, select all rows or some rows by specifying a percentage portion of the rows.

    3.  If you select Specified as the object type, the tables from the selected Application appear in the drop-down list.

        In the Rows to Include section, select all rows, or some rows by specifying a percentage portion of the rows. For finer granularity, you could specify a Where clause, such as where region_id=6.

        If the selected table is partitioned, click Add/Remove Partitions to choose the partitions and sub-partitions from which the objects must be included in the subset.

    4.  In the Include Related Rows section, do one of the following:

        - Select Ancestor and Descendant Objects

          This rule impacts the parent and child columns, and ensures that referential integrity is maintained, and that child columns are also selected as part of the subset.

        - Select Ancestor Objects Only

          This option will be disabled if the global rule is set to “Include All Rows”, and will be enabled if it is set to “Include No Rows”. This rule only impacts the parent columns, and ensures that referential integrity is maintained.

          Select Descendant Objects Only

          This option will be disabled if the global rule is set to “Include No Rows”, and will be enabled if it is set to “Include All Rows”.

        In Oracle Data Masking and Subsetting release 13.2, users can now set the rule scope to “Include Related Rows” with global rule scope set to “Include All Rows” and vice versa, and all unrelated tables are processed using the global rule “Include All Rows” .

        If you disable the Include Related Rows check box, referential integrity might not be maintained. However, you can define additional rules on the related tables to restore the referential integrity. You can disable this check box whether or not you specify a Where clause.

    5.  If you want to specify a Where clause, go to the next step. Otherwise, skip to Step 9.

    6.  Provide a rule parameter, if desired, for the clause.

        For instance, if you specify a particular value for an employee ID as employee_id=:emp_id, you could enter query values for the default of 100:

        - Select the Rows Where button and enter employee_id=:emp_id.

        - Click OK to save the rule and return to the Object Rules tab.

          If this is a new rule, a warning appears stating that "Rule parameters corresponding to the bind variables 'emp_id' should be created before generating subset."

        - Select the table rule, click the Rule Parameters tab, then click Create.

          The Rule Parameter Properties pop-up appears.

        - Enter emp_id for the Name and 100 for the Value.

          **Note:**

          The colon ( : ) preceding emp_id is only present in the Where clause, and not required when creating a new rule parameter.

        - Click OK to save the properties, which now appear in the Rule Parameters tab.

        - Skip to Step 10.

9.  Click OK to save the rule and return to the Object Rules tab.

    The new rule is displayed in the list. The related objects are displayed in the table below. Related rows from the objects are included in the subset to provide referential integrity in the subset database.

10. In the Related Objects section of the Object Rules tab, you can manage the size of the subset by controlling the levels of ancestors and descendants within the subset. Notice that each node in the table has a check box. By default, all nodes are included in the subset, as indicated by the check mark. Deselect the check box to exclude a node from the subset. The deselection option is disabled for parent rows (the join columns to the right identify parent and child rows). In addition, you can make these other refinements to subset content:

    - Click Allow Excluding Parent Objects. This enables the check marks that were grayed out. You can now selectively exclude parent rows from the subset by deselecting the check box.

    - Select a node within the table and click Add Descendants to include related rows. In the dialog that opens, make appropriate selections and click OK.

    As you make these refinements, columns on the right reflect the effect on space estimates for the subset. The Related Objects section also denotes the processing order of the ancestor and descendant tables, including the detailed impact of including each object. When you are done with the refinements, go to the Space Estimates tab to see a finer granularity of the impact on the overall size of the subset.

11. In the Default Object Rows section of the Object Rules tab, choose whether you want to include or exclude the objects not affected by the defined rules in the subset.

    When you select the Include All Rows option, all of the rows for the object are selected as part of the subset.

    This is a global rule and applies to the entire subset. You can only select the Include All Rows option when all of the rules have a scope of None. A scope of None is established when you uncheck the Include Related Rows option in the Object Rule pop-up.

    **Note:**

    For a subset definition that has column rules (see Step 12), be sure to use object rules to include the corresponding objects. You can use the Default Object Rows option to include all objects not affected by object rules, if required.

12. Optional: Click the Column Mask Rules tab to perform inline masking as part of the subset definition.

    1.  Click Create and enter search criteria to filter on columns within the schema. These would typically be vertical columns such as CLOB AND BLOB columns.

        **Note:**

        If you are using column mask rules instead of masking definitions (see Step 13), you can select no more than 10 columns in a given table. This restriction applies to the export method but not to the in-place delete method.

        Click OK.

    2.  Select a row or rows in the column search results and click Manage Masking Formats.

    3.  In the pop-up dialog, select a masking format and value to apply to the columns. For multiselection, the same format must be appropriate for all columns. If you select multiple columns, ensure that the column rule format you choose is applicable to the selected columns. Use the columns (flags) not null and unique to enforce compliance.

        Click OK to apply the masking format to the columns.

13. Optional: Click the Data Masking Definitions tab to include masking definitions as part of the subsetting operation or to perform at the source data masking only.

    1.  Click Add.

    2.  In the pop-up dialog, enter search criteria to retrieve appropriate definitions. Be sure to select the desired radio button (All or Any). All formats except compound masking are supported for inline masking.

        **Note:**

        No single table within a masking definition can have more than 10 masked columns if you are using the export method. The restriction does not apply to the in-place delete method.

        Click OK.

    The search results appear in the data masking table.

14. Click the Space Estimates tab.

    - Note the value in the Estimated Subset Size MB column. The space estimates depend on optimizer statistics, and the actual distribution of data can only be calculated if histogram statistics are present.

    - Whenever you add new rules, recheck the space estimates for updated values.

    - Data in the Space Estimates subpage is sorted with the largest applications appearing at the top.

    **Note:**

    Space estimates are accurate only if “dbms_stats.gather_table_stats” is used. Also, space estimates do not reflect the effect of data masking, if used.

    If you provide a Where clause and subsequent rule parameter properties, the Space Estimates subpage is updated with the value contained in the Rule Parameters tab.

15. Optional: click the Pre/Post Subset Script tab.

    - You can specify a pre-subset script to run on the subset database before you select subset data.

    - You can specify a post-subset script to run on the subset database after you assemble the subset data.

    - Either script type runs on the source database.

    **Note:**

    Ensure that the PL/SQL block defined the pre-susbset or post-subset script includes a “/” at the end.

16. Click Return.

    The definition is complete and displayed in the Data Subsetting Definitions table.

You can now proceed with script generation. Alternatively, you may want to save the script for future use. In either case, you must decide whether to export data to a dump file or delete data from a target database.

**Tip:**

If you have a very large database of 4 terabytes, for instance, and you want to export a small percentage of the rows, such as 10%, it is more advantageous to use the export method. Using the in-place delete method would require 3.6 terabytes of data, which would not perform as quickly as the export method.

The in-place delete method is recommended when the amount of data being deleted is a small percentage of the overall data size.

There is an EMCLI verb if you want to perform an in-place delete remotely or script it.

#### Generating a Subset Script

To prepare and submit a job to generate a subset script:

1.  Select the definition within the table, open the Actions menu, then select Generate Subset.
    The Generate Subset pop-up appears.
2.  Select a target database that is either the same target database you used to create the subset model, or similar to this database regarding the table schema and objects.
3.  Decide if you want to create a subset by writing subset data to export files, or by deleting data from a target database.
    **Note:**

    Choosing to delete data creates an in-place subset by removing or deleting unwanted data from a cloned copy of the production database, rather than a production database. Only data satisfying the rules are retained. You should never use this option on a production database.

    Select either Named Credentials or New Credentials if you have not already set preferred credentials.

    If you have defined any parameters from the Rule Parameters tab, they appear in the table at the bottom. You can change a parameter value by clicking on the associated field in the Value column.
4.  Click Continue to access the Parameters pop-up. The contents of the pop-up depend on whether you chose the export or delete option in the previous step.
    For Writing Subset Data to Export Files, provide the requisite information, then click Continue to schedule the job.

    - Specify a subset directory where to save the export dump. The drop-down list consists of directory objects for which you have access. Alternatively, you can select a custom directory path. Click the check box if you want to speed the process by using an external directory. Recommended default: `DATA_PUMP_DIR`.

    - Specify appropriate values if you want to override the defaults: enter a name for the export file; specify a maximum file size in megabytes; specify the maximum number of threads of active execution operating on behalf of the export job. This enables you to consider trade-offs between resource consumption and elapsed time.

    - Specify whether you want to export only the subsetted data or the entire database along with the subsetted data.

    - Select whether to enable dump file compression and encryption. Enter and confirm an encryption password, if appropriate. Log file generation is selected by default.

    For Deleting Data From a Target Database, provide the requisite information, then click Continue to schedule the job.

    - Specify a subset directory where to save the subset scripts. The drop-down list consists of directory objects for which you have access. Alternatively, you can select a custom directory path. Recommended default: `DATA_FILE_DIR`.

    - You must enable the check box indicating that the selected target is not a production database in order to proceed.
5.  Click Continue to review the estimated storage requirement for generating the subset script.
    **Note:**

    If the required storage for generating the susbset script is much more than the available space, allocate the necessary space to ensure that you have enough space to proceed with generating the subset script.
6.  Specify a name for the subset job, and provide a description. Schedule the job to run immediately or at a later point of time, then click Submit.
    The Data Subset Definitions page reappears, and the Most Recent Job Status column shows that the subset job is running, and subsequently that it has succeeded.

After performing this procedure, you can now create a subset database with the generated export files at any time.

#### Saving a Subset Script

To prepare and submit a job to save a subset script:

1.  Select the definition within the table, open the Actions menu, then select Save Subset Script. The Subset Mode pop-up appears.

2.  Select a target database that is either the same target database you used to create the subset model, or similar to this database regarding the table schema and objects.

3.  Decide if you want to create a subset by writing subset data to export files, or by deleting data from a target database.

    Choosing to delete data creates an in-place subset by removing/deleting unwanted data from a cloned copy of the production database, rather than a production database. Only data satisfying the rules are retained. You should never use this option on a production database.

    Select either Named Credentials or New Credentials if you have not already set preferred credentials.

    If you have defined any parameters from the Rule Parameters tab, they appear in the table at the bottom. You can change a parameter value by clicking on the associated field in the Value column.

4.  Click Continue to access the Parameters pop-up. The contents of the pop-up depend on whether you chose the export or delete option in the previous step.

    For Writing Subset Data to Export Files, provide the requisite information, then click Continue to schedule the job.

    - Specify a subset directory where to save the export dump. The drop-down list consists of directory objects for which you have access. Alternatively, you can select a custom directory path. Click the check box if you want to speed the process by using an external directory. Recommended default: `DATA_PUMP_DIR`.

    - Specify appropriate values if you want to override the defaults: enter a name for the export file; specify a maximum file size in megabytes; specify the maximum number of threads of active execution operating on behalf of the export job. This enables you to consider trade-offs between resource consumption and elapsed time.

    - Specify whether to export only the subsetted data or the entire database along with the subsetted data.

    - Select whether to enable dump file compression and encryption. Enter and confirm an encryption password, if appropriate. Log file generation is selected by default.

    For Deleting Data From a Target Database, provide the requisite information, then click Continue to schedule the job.

    - Specify a subset directory where to save the subset scripts. The drop-down list consists of directory objects for which you have access. Alternatively, you can select a custom directory path. Recommended default: `DATA_FILE_DIR`.

    - You must enable the check box indicating that the selected target is not a production database in order to proceed.

5.  Click Continue. A progress indicator tracks script generation. When complete, the Files table lists the results of script generation.

6.  Click Download. In the File Download pop-up that appears, click Save.

7.  In the Save As pop-up that appears, navigate to a file location and click Save.

    The file containing the scripts (SubsetBundle.zip) now appears at the specified location on your desktop.

To run the saved script at a later time:

1.  Port the ZIP file to the target database and extract it to a directory on which you have the requisite privileges.
2.  Change directory to where you extracted the files.
3.  Execute the following script from the SQL command line:
        subset_exec.sql

    Note that if you want to change generated parameter settings, you can do so by editing the following file in a text editor prior to executing the script:

        subset_exec_params.lst

### Importing and Exporting Subset Templates and Dumps

A subset template is an XML file that contains the details of the subset, consisting of the application, subset rules, rule parameters, and pre-scripts or post-scripts. When you create a subset definition and specify that you want to write subset data to export files, the export files become a template that you can subsequently import for reuse. You would import the template to perform subset operations on a different database.

Typically, the workflow is that you would first import a previously exported ADM template, which is another XML file, while creating an ADM. You would then import the related subset template while creating a data subset definition. You could alternatively select an existing ADM (skipping the import ADM flow) while importing the subset template.

**Note:**

There are EMCLI verbs to export and import subset definitions and subset dumps if you want to perform these operations remotely or script them.

#### Importing a Subset Definition

There are three methods of import:

- Importing a Subset Definition XML File From Your Desktop

- Importing a Subset Dump

- Importing a Subset Definition XML File From the Software Library

##### Importing a Subset Definition XML File From Your Desktop

1.  From the Actions menu, select Import, then select File from Desktop.

2.  In the pop-up that appears:

    1.  Specify a name for the subset definition.

    2.  The ADM on which the subset is based.

    3.  A source database.

    4.  The location on your desktop from which you want to import the subset definition.

    5.  Click Continue.

3.  In the pop-up that appears:

    1.  Enter a descriptive job name (or accept the default).

    2.  Provide credentials.

    3.  Schedule the job.

    4.  Click Submit.

After the job runs successfully, the imported subset appears in the list of subsets in the table on the Data Subset Definitions page.

##### Importing a Subset Dump

1.  From the Actions menu, select Import, then select Subset Dump.

2.  In the pop-up that appears:

    1.  Select a target database.

    2.  Provide database and host credentials, then click Login.

    3.  Specify the location of the dump file, which can be in a selected directory on the target database or at a custom path on the target. Note that if the original export action used an external location for the dump files, the location must be specified as well.

    4.  Click Continue.

3.  In the pop-up that appears:

    1.  Select whether to import both metadata and data, or data only. If data only, indicate if you want to truncate, that is, overlay existing data or append to existing data.

    2.  Enable OID transform during type or object creation to create a new OID.

        Creating a new OID will break the REF columns that point to the object.

    3.  Specify whether to use the default tablespace on the target database or remap the tablespaces from the existing tablespace to another tablespace.

    4.  Perform tablespace remapping as necessary.

    5.  Specify whether you want to retain the existing tables in the destination schema or drop the existing tables in the destination schema.

    6.  Perform schema remapping as necessary.

    7.  Select log file options.

    8.  Click Continue.

4.  In the pop-up that appears:

    1.  Enter a descriptive job name (or accept the default).

    2.  Schedule the job.

    3.  Click Submit.

The job reads the dump files and loads the data into the selected target database.

##### Importing a Subset Definition XML File From the Software Library

1.  From the Actions menu, select Import, then select File from Software Library.

2.  In the Import Data Subset Definition from Software Library pop-up that appears:

    1.  Selected the desired subset definition XML file on the left.

    2.  Provide the ADM properties on the right.

    3.  Click Continue.

3.  In the pop-up that appears:

    1.  Enter a descriptive job name (or accept the default).

    2.  Provide credentials.

    3.  Schedule the job.

    4.  Click Submit.

After the job runs successfully, the imported subset appears in the list of subsets in the table on the Data Subset Definitions page.

#### Exporting a Subset Definition

There are two methods of export:

- Exporting a Subset Definition as an XML File to Your Desktop

- Exporting a Subset Definition From the Software Library

##### Exporting a Subset Definition as an XML File to Your Desktop

1.  From the Data Subset Definitions page, select the subset definition you want to export.

2.  From the Actions menu, select Export, then select Selected Subset Definition.

3.  In the File Download pop-up that appears, click Save.

4.  In the Save As pop-up that appears, navigate to a file location and click Save.

    The system converts the subset definition into an XML file that now appears at the specified location on your desktop.

##### Exporting a Subset Definition From the Software Library

1.  From the Actions menu, select Export, then select File from Software Library.
2.  In the Export Subset Definition from Software Library pop-up that appears, select the desired subset definition and click Export.
3.  In the File Download pop-up that appears, click Save.
4.  In the Save As pop-up that appears, navigate to a file location and click Save.
    The system converts the subset definition into an XML file that now appears at the specified location on your desktop.

After the job runs successfully, the subset template appears in the list of subsets in the table on the Data Subset Definitions page.

### Creating a Subset Version of a Target Database

After a subset is defined, analyzed, and validated, you can execute the subset operation to create a subset version of the source data.

The procedure assumes the following prerequisites:

- A subset definition already exists that contains the rules needed to subset the database.

- You have the requisite privileges to extract the data from the source and create the subset version in a target database. Depending on the subset technique, different levels of file or database privileges may be created. The required privileges include:

  - Target Privileges (applicable to all targets):

    - Connect to any viewable target

    - Execute Command Anywhere

    - View Any Target

  - Resource Privileges:

    - Job System

    - Named Credential

    - Oracle Data Masking and Subsetting resource privilege

    **Note:**

    The `EM_ALL_OPERATOR` privilege for Enterprise Manager Cloud Control users includes all of the above privileges.

  - `SELECT_CATALOG_ROLE` for database users

  - `SELECT ANY DICTIONARY` privilege for database users

  - DBA privileges on a database for target database users

- Additionally, to perform an in-place delete operation, the DBA user must be granted the `EXECUTE_ANY_TYPE` privilege

#### To create a subset version of a target database:

1.  Create a subset operation by selecting a subset definition and associating it with a source database.

    Enterprise Manager validates the subset definition against the source database and flags schema differences. Note that this association may be different from the original association that an application developer may have created.

2.  Edit the definition to remap the defined schema to a test schema.

    You are prompted to connect to a database, whereupon the database is associated with the subset definition. This also enables you to remap the vendor-provided schema names to actual schema names in the database.

3.  Select one of the various subset creation techniques:

    - Data Pump dump file followed by a Data Pump import

    - In-place delete, in which rows in the specified database not matching the rule conditions are deleted

    - In-transit subset creation or refresh

    Enterprise Manager generates the appropriate response file (that is, SQL script, Data Pump script, or OS script), checks the target system for appropriate privileges to be able proceed with the operation, and estimates the size of the target.

4.  After reviewing the analysis, submit the subset process.

    Enterprise Manager executes the subset process and summarizes the results of the execution.

### Synchronizing a Subset Definition with an Application Data Model

Changes to an ADM, adding referential relationships or deleting tables, for example, can render a subset definition stale. The Subset Definitions page clearly indicates this condition with a lock icon next to the subset name and an invalid status. Also, most menu items on the Actions menu are disabled. To revert the status to valid and unlock the subset definition, you have to synchronize the definition with its associated ADM.

1.  On the Subset Definitions page, select the locked subset definition.
2.  From the Actions menu, select Synchronize.
3.  Complete the job submission dialog, then click Submit.
    When the job completes, the subset definition is unlocked and available for use.

### Granting Privileges on a Subset Definition

You can grant privileges on a subset definition that you create so that others can have access. To do so, you must be an Enterprise Manager Administrator with at least Designer privileges on the subset definition.

1.  From the Enterprise menu, select Quality Management, then select Data Subset Definitions.
2.  Select the subset definition to which you want to grant privileges.
3.  From the Actions menu, select Grant, then select as follows:
    - Operator–to grant Operator privileges on the subset definition to selected roles or administrators, which means the grantees can view and copy but not edit the definition.

    - Designer–to grant Designer privileges on the subset definition to selected roles or administrators, which means the grantees can view and edit the definition.
4.  In the dialog that opens, select the type (administrator or role, or both). Search by name, if desired. Make your selections and click Select.
    Those selected now have privileges on the subset definition.
5.  Use the Revoke action if you want to deny privileges previously granted.

See "[Oracle Data Masking and Subsetting Access Rights](before_you_begin.md)" for more information on privileges within the test data management area.

### About Inline Masking and Subsetting

You can reduce the size of the database simultaneous with masking sensitive data. This serves the dual purpose of obscuring exported production data while greatly reducing hardware costs related to storing large masked production databases for testing.

**Note:**

Inline masking is available only with Oracle Database 11g and higher releases.

The benefits of integrating data masking with subsetting include the following:

- Prepare the test system in a single flow

- Avoid the necessity of maintaining large-size masked databases for test purposes

- Exported data in the form of a dump file can be imported into multiple databases without exposing sensitive data

- Subsetting is enhanced by ability to discard columns containing chunks of large data

You can select one or more data masking definitions during subset creation. The masking definitions must be based on the same ADM as the current subset definition. At the same time, you can significantly reduce the subset size by defining column rules to set CLOB and BLOB columns to null (or another supported format such as Fixed String, Fixed Number).

You generate a subset in two ways:

- Export Dump–if masking definitions are part of the subset model, mapping tables are created during generation, and the resulting dump contains masked values

- In-Place Delete–subsetting is performed on a cloned copy of the production database; if data masking is part of the subset model, pregenerated masking scripts are executed on the target sequentially

Advantages of inline masking include the following:

- Sensitive data never leaves the production environment and thus is not exposed (Export Dump option).

- There is no need to temporarily store data in a staging area.

- Exported data can subsequently be imported into multiple environments.

- You can define table rules to export only a subset of data, and can further trim the volume by using column rules to eliminate large vertical columns.

- You can mask the same data in different ways and import into different test databases.

- You can use the provisioning framework to create multiple copies of trimmed down, referentially intact databases containing no sensitive data (in-place delete), or import a dump file into multiple databases (export dump).

The section "Creating a Data Subset Definition" includes instructions for combining data subsetting and data masking within the process of creating a subset definition. See [Data Masking](data_masking.md),for information on data masking and creating a data masking definition.

### Inline Masking and Subsetting Scenarios

The scenarios described below assume that an Application Data Model (ADM) exists for a production (or test) database in which sensitive column details are captured. The steps outlined are at a high level. See "[Masking with an Application Data Model and Workloads](data_masking.md)" for details on creating a masking definition; see "Creating a Data Subset Definition" for details on creating and editing a subset definition.

### Lifecycle Management

This section discusses the lifecycle management of Application Data Models, Data Masking, and Data Subsetting definitions.

In the event of an Enterprise Manager user being dropped or modified, the user can reassign the Application Data Model, data masking and data subsetting definitions to another user in the system. However, if the user doesn’t reassign the Application Data Model, data masking and data subsetting definitions to another user, these definitions are automatically reassigned to the SYSMAN user.

When you try to reassign the Application Data Model, data masking and data subsetting definitions to another user in the system, and if the reassigned user already has a definition with the same name, the original definitions are renamed.

For example: User A has an Application Data Model, ADM1, and user B also has an Application Data Model, named ADM1. If user B is being dropped, and you choose to assign its definitions to user A, the original definition ADM1 is renamed to ADM1_B, The original definitions with the same name are renamed by suffixing "\_" and adding the user name that is being dropped. After the reassignment, user A will now have both definitions ADM1 and ADM1_B.
