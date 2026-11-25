This chapter helps you prepare with the prerequisites and other important things that you must consider before installing and using Oracle Data Masking and Subsetting.

### Oracle Data Masking and Subsetting Access Rights

#### Prerequisites

The following privileges must be assigned to the users on Oracle Enterprise Manager repositories to administer and view the Oracle Data Masking and Subsetting user interface pages.

- DB_MASK_ADMIN: to manage and use data masking feature in Oracle Enterprise Manager.

- DB_ADM_ADMIN: to manage and use the application data model feature in Oracle Enterprise Manager.

  DB_SUBSET_ADMIN: to manage and use the data subsetting feature in Oracle Enterprise Manager

By default, Enterprise Manager administrators can access the following primary Oracle Data Management and Subsetting pages:

- Application Data Models

- Data Subset Definitions

- Data Masking Definitions

- Data Masking Formats

This is by virtue of having the TDM_ACCESS privilege, which is included in the PUBLIC role. The Super Administrator can revoke this privilege for designated administrators, thereby restricting access to the TDM pages. Without the privilege, the respective menu items do not appear in the Cloud Control console.

Additionally, Enterprise Manager provides a privilege access model that enables Super Administrators and administrators to limit access to TDM objects to authorized users only. The model involves the ability to grant Operator or Designer privileges to selected users.

#### Operator Privileges

Those granted Operator privileges can perform data masking and subsetting operations. Privileges can be granted on TDM objects; that is, on Application Data Models (ADM), data subsetting definitions, and data masking definitions. Operator privileges do not include the ability to edit and delete these objects.

- ADM–a user (other than Super Administrator) with ADM Operator privileges can view an ADM, but cannot edit and delete it, nor view its properties. To enforce this, the Edit and Delete icons, and the Properties menu are disabled. Additionally, the Sync option on the Create Verification Job page is disabled.

- Data subset definition–a user (other than Super DSD Administrator) with Operator privileges can view but not edit and delete a subset definition. To enforce this, the Edit and Delete icons are disabled.

  A user with Data Subset Definition Operator privileges can do any other operation except for editing and deleting the data subset definition, and has the following rights:

  - Viewing the data subset definition.

  - Creating a data subset to export files.

  - Creating a data subset on a database.

  - Saving the subset script.

- Data masking definition–a user with Data Masking Definition Operator privileges can do any other operation except for editing and deleting the data masking definition, and has the following rights:

  - Viewing the data masking definition.

  - Generating a data masking script.

  - Scheduling a data masking job.

  - Exporting a data masking definition.

#### Designer Privileges

Those granted Designer privileges can enhance, modify, and manage TDM objects. These users can also grant and revoke Operator and Designer privileges to others. Designer privileges imply the corresponding Operator privileges on a TDM object.

- ADM–a user with Designer privileges can perform all operations on an ADM including delete.

- Data subset definition–a user with Designer privileges can perform all operations on a subset definition including delete.

- Data masking definition–a user with Designer privileges can perform all operations on a masking definition including delete.

### Access Control For Oracle Data Masking and Subsetting Objects

This section describes the procedure to grant privileges on Application Data Models, Data Masking definitions, and Data Subsetting definitions.

- [Assigning Privileges to an Existing ADM](data_modeling.md)

- [Granting Privileges on a Subset Definition](data_subsetting.md)

### Storage Requirements

Although Oracle Data Masking and Subsetting objects such as data models, masking and subsetting definitions consume a negligible amount of storage space, depending on the amount of data being stored over a period of time, you may need to allocate additional storage space to Oracle Enterprise Manager's repository database.

This section details the storage recommendations for masking and subsetting.

- In-Database Masking: 3X of additional space in the user tablespace (X being the largest table in size) 2X of additional space in temporary tablespace

- In-Export Masking: 2X additional space in the user tablespace (X being the largest table in size) 2X of additional space in temporary tablespace Sufficient disk space to store the generated export dump file

- In-Database Subsetting: 2X additional space in the user tablespace (X being the largest table in size) 2X additional space in temporary tablespace

- In-Export Subsetting: X additional space in the user tablespace (X being the largest table in size) Sufficient space to store the generated dump files

**Note:**

The recommended storage requirement for integrated masking and subsetting is the sum total of the storage requirement for masking and subsetting as mentioned above.

### Security and Regulatory Compliance

Masked data is a sensible precaution from a business security standpoint, because masked test information can help prevent accidental data escapes. In many cases, masked data is a legal obligation. The Enterprise Manager Data Masking Pack can help organizations fulfill legal obligations and comply with global regulatory requirements, such as Sarbanes-Oxley, the California Database Security Breach Notification Act (CA Senate Bill 1386), and the European Union Data Protection Directive.

The legal requirements vary from country to country, but most countries now have regulations of some form to protect the confidentiality and integrity of personal consumer information. For example, in the United States, The Right to Financial Privacy Act of 1978 creates statutory Fourth Amendment protection for financial records, and a host of individual state laws require this. Similarly, the U.S. Health Insurance Portability and Accountability Act (HIPAA) created protection of personal medical information.

### Supported Data Types

The list of supported data types varies by release.

- Grid Control, Database, and Cloud Control

  - Numeric Types

    The following Numeric Types can use Array List, Delete, Fixed Number, Null Value, Post Processing Function, Preserve Original Data, Random Decimal Numbers, Random Numbers, Shuffle, SQL Expression, Substitute, Table Column, Truncate, Encrypt, and User Defined Function masking formats:

    - `NUMBER`

    - `FLOAT`

    - `RAW`

    - `BINARY_FLOAT`

    - `BINARY_DOUBLE`

  - String Types

    The following String Types can use Array List, Delete, Fixed Number, Fixed String, Null Value, Post Processing Function, Preserve Original Data, Random Decimal Numbers, Random Digits, Random Numbers, Random Strings, Shuffle, SQL Expression, Substitute, Substring, Table Column, Truncate, Encrypt, and User Defined Function masking formats:

    - `CHAR`

    - `NCHAR`

    - `VARCHAR2`

    - `NVARCHAR2`

  - Date Types

    The following Date Types can use Array List, Delete, Null Value, Post Processing Function, Preserve Original Data, Random Dates, Shuffle, SQL Expression, Substitute, Table Column, Truncate, Encrypt, and User Defined Function masking formats:

    - `DATE`

    - `TIMESTAMP`

- Grid Control and Cloud Control

  - Large Object (LOB) Data Types

    The following Data Types can use Fixed Number, Fixed String, Null Value, Regular Expression, and SQL Expression masking formats:

    - BLOB

    - CLOB

    - NCLOB

### Unsupported Objects

Oracle Data Masking and Subsetting does not support:

- external tables

- clustered tables

- long columns

- column of type “XML”; XML-type columns

- virtual columns

**Note:**

Masking is supported for relational tables and tables containing long columns.
