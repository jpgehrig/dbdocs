The Oracle Base directory is the database home directory for Oracle Database installation owners, and the log file location for Oracle Grid Infrastructure owners.

Name Oracle base directories using the syntax /pm/h/u, where pm is a string mount point name, h is selected from a small set of standard directory names, and u is the name of the owner of the directory.

You can use the same Oracle base directory for multiple installations. If different operating system users install Oracle software on the same system, then you must create a separate Oracle base directory for each installation owner. For ease of administration, Oracle recommends that you create a unique owner for each Oracle software installation owner, to separate log files.

Because all Oracle installation owners write to the central Oracle inventory file, and that file mountpoint is in the same mount point path as the initial Oracle installation, Oracle recommends that you use the same /pm/h path for all Oracle installation owners.

Table D-1 Examples of OFA-Compliant Oracle Base Directory Names

| Example           | Description                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `/u01/app/oracle` | Oracle Database Oracle base, where the Oracle Database software installation owner name is `oracle`. The Oracle Database binary home is located underneath the Oracle base path.                                                                                                                                                                                                                                                       |
| `/u01/app/grid`   | Oracle Grid Infrastructure Oracle base, where the Oracle Grid Infrastructure software installation owner name is `grid`.<br>**Caution:**<br>The Oracle Grid Infrastructure Oracle base should not contain the Oracle Grid Infrastructure binaries for an Oracle Grid Infrastructure for a cluster installation. Permissions for the file path to the Oracle Grid Infrastructure binary home are changed to `root` during installation. |

**Note:**

Oracle home or Oracle base cannot be `symlinks`, nor can any of their parent directories, all the way to up to the `root` directory.

**Parent topic:** [Optimal Flexible Architecture](optimal-flexible-architecture.md)
