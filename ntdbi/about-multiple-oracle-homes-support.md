## About Multiple Oracle Homes Support

Oracle Database supports multiple Oracle homes. You can install this release or earlier releases of the software more than once on the same system, in different Oracle home directories.

Careful selection of mount point names can make Oracle software easier to administer. Configuring multiple Oracle homes in compliance with Optimal Flexible Architecture (OFA) rules provides the following advantages:

- You can install this release, or earlier releases of the software, more than once on the same system, in different Oracle home directories. However, you cannot install products from one release of Oracle Database into an Oracle home directory of a different release. For example, you cannot install Oracle Database 19c software into an existing Oracle 18c Oracle home directory.

- Multiple databases, of different versions, owned by different users can coexist concurrently.

- You must install a new Oracle Database release in a new Oracle home that is separate from earlier releases of Oracle Database.

  You cannot install multiple releases in one Oracle home. Oracle recommends that you create a separate Oracle Database Oracle home for each release, in accordance with the Optimal Flexible Architecture (OFA) guidelines.

- In production, the Oracle Database server software release must be the same as the Oracle Database dictionary release through the first four digits (the major, maintenance, and patch release number).

- Later Oracle Database releases can access earlier Oracle Database releases. However, this access is only for upgrades. For example, Oracle Database 19c can access an Oracle Database 18c if the 18c database is started up in upgrade mode.

- Oracle Database Client can be installed in the same Oracle Database home if both products are at the same release level. For example, you can install Oracle Database Client 12.2.0.1 into an existing Oracle Database 12.2.0.1 home but you cannot install Oracle Database Client 12.2.0.1 into an existing Oracle Database 12.1.0.2 home. If you apply a patch set before installing the client, then you must apply the patch set again.

- Structured organization of directories and files, and consistent naming for database files simplify database administration.

- Login home directories are not at risk when database administrators add, move, or delete Oracle home directories.

- You can test software upgrades in an Oracle home in a separate directory from the Oracle home where your production database is located.

**Parent topic:** [Optimal Flexible Architecture](optimal-flexible-architecture.md)
