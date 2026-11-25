## Grid Home Directory

When installing Oracle Grid Infrastructure, you must determine the location of the Oracle home for Oracle Grid Infrastructure software (Grid home).

The Oracle Home directory that Oracle Grid Infrastructure is installed in is the Grid home. Oracle ASM is also installed in this home directory.

If you plan to install Oracle RAC, you must choose a different directory in which to install the Oracle Database software. The location of the Oracle RAC installation is the Oracle home.

The Grid home should be located in a path that is different from the Oracle home directory paths for any other Oracle software. The Optimal Flexible Architecture guideline for a Grid home is to create a path in the form `\``path``\``version``\``user`, where `\``path` is a string constant (`C:\`), \\version is the version of the software (`19.0.0`), and \\user is the installation owner of the Oracle Grid Infrastructure software (`grid`).

    C:\19.0.0\grid

**Note:**

For Oracle Grid Infrastructure for a cluster installations, note the following restriction for the Oracle Grid Infrastructure binary home (Grid home):

It must not be placed in the home directory of an installation owner. These requirements are specific to Oracle Grid Infrastructure for a cluster installations.

Oracle Grid Infrastructure for a standalone server (Oracle Restart) can be installed under the Oracle base for the Oracle Database installation.

**Parent topic:** [About the Directories Used During Installation of Oracle Grid Infrastructure](about-the-directories-used-during-installation-of-oracle-grid-infrastructure.md)
