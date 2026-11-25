Review this information about creating the Oracle home directory location on each cluster node.

The Oracle home for Oracle Grid Infrastructure software (Grid home) should be located in a path that is different from the Oracle home directory paths for any other Oracle software. The Optimal Flexible Architecture guideline for a Grid home is to create a path in the form` /pm/v/u`, where `p` is a string constant, `m` is a unique fixed-length key (typically a two-digit number), `v` is the version of the software, and `u` is the installation owner of the Oracle Grid Infrastructure software (`grid` user). During Oracle Grid Infrastructure for a cluster installation, the path of the Grid home is changed to the root user, so any other users are unable to read, write, or execute commands in that path. For example, to create a Grid home in the standard mount point path format `u[00-99][00-99]/app/``release``/grid`, where release is the release number of the Oracle Grid Infrastructure software, create the following path:

    /u01/app/19.0.0/grid

**Note:**

Oracle home or Oracle base cannot be `symlinks`, nor can any of their parent directories, all the way to up to the `root` directory.

During installation, ownership of the entire path to the Grid home is changed to `root` (`/u01`, `/u01/app`, `/u01/app/19.0.0`, `/u01/app/19.0.0/grid`). If you do not create a unique path to the Grid home, then after the Grid install, you can encounter permission errors for other installations, including any existing installations under the same path. To avoid placing the application directory in the mount point under root ownership, you can create and select paths such as the following for the Grid home:

    /u01/19.0.0/grid

**Caution:**

For Oracle Grid Infrastructure for a cluster installations, note the following restrictions for the Oracle Grid Infrastructure binary home (Grid home directory for Oracle Grid Infrastructure):

- It must not be placed under one of the Oracle base directories, including the Oracle base directory of the Oracle Grid Infrastructure installation owner.

- It must not be placed in the home directory of an installation owner. These requirements are specific to Oracle Grid Infrastructure for a cluster installations.

Oracle Grid Infrastructure for a standalone server (Oracle Restart) can be installed under the Oracle base for the Oracle Database installation.

**Parent topic:** [Creating Groups, Users and Paths for Oracle Grid Infrastructure](creating-users-and-paths-for-grid-infrastructure.md)
