By default, Oracle Universal Installer configures Oracle home directories using these Oracle Optimal Flexible Architecture conventions.

The directory pattern syntax for Oracle homes is /pm/s/u/product/v/type\_\[n\]. The following table describes the variables used in this syntax:

| Variable | Description                                                                                                                                                                          |
|:---------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| pm       | A mount point name.                                                                                                                                                                  |
| s        | A standard directory name.                                                                                                                                                           |
| u        | The name of the owner of the directory.                                                                                                                                              |
| v        | The version of the software.                                                                                                                                                         |
| type     | The type of installation. For example: Database (`dbhome`), Client (`client`), or Oracle Grid Infrastructure (`grid`)                                                                |
| n        | An optional counter, which enables you to install the same product more than once in the same Oracle base directory. For example: Database 1 and Database 2 (`dbhome_1`, `dbhome_2`) |

For example, the following path is typical for the first installation of Oracle Database on this system:

    /u01/app/oracle/product/19.0.0/dbhome_1

**Note:**

Oracle home or Oracle base cannot be `symlinks`, nor can any of their parent directories, all the way to up to the `root` directory.

**Parent topic:** [Optimal Flexible Architecture](optimal-flexible-architecture.md)
