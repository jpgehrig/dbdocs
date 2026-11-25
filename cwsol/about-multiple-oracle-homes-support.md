Oracle Database supports multiple Oracle homes. You can install this release or earlier releases of the software more than once on the same system, in different Oracle home directories.

Careful selection of mount point names can make Oracle software easier to administer. Configuring multiple Oracle homes in compliance with Optimal Flexible Architecture (OFA) rules provides the following advantages:

- You can install this release, or earlier releases of the software, more than once on the same system, in different Oracle home directories. However, you cannot install products from one release of Oracle Database into an Oracle home directory of a different release.

- Multiple databases, of different versions, owned by different users can coexist concurrently.

- To install Oracle Database software in multiple Oracle homes, you must extract the image file in each Oracle home, and then run the setup wizard from the respective Oracle home.

- You must install a new Oracle Database release in a new Oracle home that is separate from earlier releases of Oracle Database.

  You cannot install multiple releases in one Oracle home. Oracle recommends that you create a separate Oracle Database Oracle home for each release, in accordance with the Optimal Flexible Architecture (OFA) guidelines.

- In production, the Oracle Database server software release is the release number in the format of major and RU release number. For example, with the release number 19.3.0.0.0, the major release is 19 and the RU release number is 3.

- Later Oracle Database releases can access earlier Oracle Database releases. However, this access is only for upgrades. For example, Oracle Database 19c can access an Oracle Database 18c if the 18c database is started up in upgrade mode.

- Oracle Database Client can be installed in the same Oracle Database home if both products are at the same release level. For example, you can install Oracle Database Client 19c into an existing Oracle Database 19c home but you cannot install Oracle Database Client 19c into an existing Oracle Database 18c home. If you apply a patch set or release update before installing the client, then you must apply the patch set or release update again.

- Structured organization of directories and files, and consistent naming for database files simplify database administration.

- Login home directories are not at risk when database administrators add, move, or delete Oracle home directories.

- You can test software upgrades in an Oracle home in a separate directory from the Oracle home where your production database is located.

- For information about release support timelines, refer to My Oracle Support Doc ID 742060.1

**Related Topics**

- [My Oracle Support Note 742060.1](https://support.oracle.com/rs?type=doc&id=742060.1)

**Parent topic:** [Optimal Flexible Architecture](optimal-flexible-architecture.md)
