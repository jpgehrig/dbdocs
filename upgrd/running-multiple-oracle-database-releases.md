## About Running Multiple Oracle Releases

Run multiple releases using Optimal Flexible Architecture (OFA).

Optimal Flexible Architecture (OFA) is a set of configuration guidelines for efficient and reliable Oracle Database and Oracle Grid Infrastructure deployments. Oracle recommends that you deploy all Oracle software installations in accordance with the OFA architecture standard for Oracle Database installations. Following the OFA standard helps to ensure that your installations are easier for you to maintain, and easier for you to obtain rapid assistance from Oracle Support.

OFA provides the following benefits:

- Organizes large amounts of complicated software and data on disk, which can help to avoid device bottlenecks and poor performance

- Facilitates routine administrative tasks, such as software and data backup functions, which are often vulnerable to data corruption

- Simplifies the administration of multiple Oracle databases

- Helps eliminate fragmentation of free space in the data dictionary, isolates other fragmentation, and helps to minimize resource contention

- Assists database administrators to deploy an effective enterprise data management strategy

If you are not currently using the OFA standard, then switching to the OFA standard involves modifying your directory structure and relocating your database files.

For more information about OFA, refer to your operating system-specific Oracle documentation. For more information about managing data files and temp files, refer to Oracle Database Administrator’s Guide.

- Interoperability of Oracle Database Client Releases with Oracle Database
  Review to understand which Oracle Database client versions are supported to work with different Oracle Database releases.
- About the Optimal Flexible Architecture Standard
  Oracle Optimal Flexible Architecture (OFA) rules help you to organize database software and configure databases to allow multiple databases, of different versions, owned by different users to coexist.
- About Multiple Oracle Homes Support
  Oracle Database supports multiple Oracle homes. You can install this release or earlier releases of the software more than once on the same system, in different Oracle home directories.

**Related Topics**

- [Oracle Database Administrator’s Guide](../admin/managing-data-files-and-temp-files.md)

**Parent topic:** [Introduction to Upgrading Oracle Database](intro-to-upgrading-oracle-database.md)

### Interoperability of Oracle Database Client Releases with Oracle Database

Review to understand which Oracle Database client versions are supported to work with different Oracle Database releases.

For information about client support with Oracle Database releases, see "Client / Server Interoperability Support Matrix for Different Oracle Versions (Doc ID 207303.1)"

**Related Topics**

- [Client / Server Interoperability Support Matrix for Different Oracle Versions (Doc ID 207303.1)](https://support.oracle.com/rs?type=doc&id=207303.1)

**Parent topic:** About Running Multiple Oracle Releases

### About the Optimal Flexible Architecture Standard

Oracle Optimal Flexible Architecture (OFA) rules help you to organize database software and configure databases to allow multiple databases, of different versions, owned by different users to coexist.

In earlier Oracle Database releases, the OFA rules provided optimal system performance by isolating fragmentation and minimizing contention. In current releases, OFA rules provide consistency in database management and support, and simplifies expanding or adding databases, or adding additional hardware.

By default, Oracle Universal Installer places Oracle Database components in directory locations and with permissions in compliance with OFA rules. Oracle recommends that you configure all Oracle components in accordance with OFA guidelines.

Oracle recommends that you accept the OFA default. Following OFA rules is especially of value if the database is large, or if you plan to have multiple databases.

**Note:**

OFA assists in identification of an ORACLE_BASE with its Automatic Diagnostic Repository (ADR) diagnostic data to properly collect incidents.

**Parent topic:** About Running Multiple Oracle Releases

### About Multiple Oracle Homes Support

Oracle Database supports multiple Oracle homes. You can install this release or earlier releases of the software more than once on the same system, in different Oracle home directories.

Careful selection of mount point names can make Oracle software easier to administer. Configuring multiple Oracle homes in compliance with Optimal Flexible Architecture (OFA) rules provides the following advantages:

- You can install this release, or earlier releases of the software, more than once on the same system, in different Oracle home directories. However, you cannot install products from one release of Oracle Database into an Oracle home directory of a different release.

- Multiple databases, of different versions, owned by different users can coexist concurrently.

- To install Oracle Database software in multiple Oracle homes, you must extract the image file in each Oracle home, and then run the setup wizard from the respective Oracle home.

- You must install a new Oracle Database release in a new Oracle home that is separate from earlier releases of Oracle Database.

  You cannot install multiple releases in one Oracle home. Oracle recommends that you create a separate Oracle Database Oracle home for each release, in accordance with the Optimal Flexible Architecture (OFA) guidelines.

- In production, the Oracle Database server software release is the release number in the format of major and RU release number. For example, with the release number 19.3.0.0.0, the major release is 19 and the RU release number is 3.

- Later Oracle Database releases can access earlier Oracle Database releases. However, this access is only for upgrades. For example, Oracle Database 19c can access an Oracle Database 18c if the 18c database is started up in upgrade mode.

- Structured organization of directories and files, and consistent naming for database files simplify database administration.

- Login home directories are not at risk when database administrators add, move, or delete Oracle home directories.

- For information about release support timelines, refer to My Oracle Support Doc ID 742060.1

**Related Topics**

- [My Oracle Support Note 742060.1](https://support.oracle.com/rs?type=doc&id=742060.1)

**Parent topic:** About Running Multiple Oracle Releases
