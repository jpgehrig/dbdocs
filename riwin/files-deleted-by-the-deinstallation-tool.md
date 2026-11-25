## Files Deleted by the deinstall Command

The `deinstall` command removes Oracle software and files from your system.

When you run `deinstall`, if the central inventory (`Inventory`) contains no other registered homes besides the home that you are deconfiguring and removing, then the `deinstall` removes the following files and directory contents in the Oracle base directory of the Oracle Database installation owner:

- `admin`

- `cfgtoollogs`

- `checkpoints`

- `diag`

- `oradata`

- `fast_recovery_area`

Oracle strongly recommends that you configure your installations using an Optimal Flexible Architecture (OFA) configuration, and that you reserve Oracle base and Oracle home paths for exclusive use of Oracle software. If you have any user data in these locations in the Oracle base that is owned by the user account that owns the Oracle software, then `deinstall` deletes this data.

**Caution:**

The `deinstall` command deletes Oracle Database configuration files, user data, and fast recovery area (FRA) files even if they are located outside of the Oracle base directory path.

**Parent topic:** [Removing Oracle RAC Software](removing-oracle-rac-software.md)
