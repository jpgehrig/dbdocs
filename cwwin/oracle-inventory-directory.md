## Oracle Inventory Directory

The Oracle Inventory directory is the central inventory location for all Oracle software installed on a server.

The first time you install Oracle software on a system, the installer checks to see if an Oracle Inventory directory exists. The location of the Oracle Inventory directory is determined by the Windows Registry key `HKEY_LOCAL_MACHINE\SOFTWARE\Oracle\inst_loc`. If an Oracle Inventory directory does not exist, then the installer creates one in the default location of `C:\Program Files\Oracle\Inventory`. The central inventory is created on all cluster nodes.

**Note:**

Changing the value for `inst_loc` in the Windows registry is not supported.

The Oracle Inventory directory is not installed under the Oracle base directory for the Oracle Installation user. This is because all Oracle software installations share a common Oracle Inventory, so there is only one Oracle Inventory for all users, whereas there is a separate Oracle Base directory for each user.

The Oracle Inventory directory contains the following:

- A registry of the Oracle home directories (Oracle Grid Infrastructure and Oracle Database) on the system

- Installation logs and trace files from installations of Oracle software. These files are also copied to the respective Oracle homes for future reference.

- Other metadata inventory information regarding Oracle installations are stored in the individual Oracle home inventory directories, and are separate from the central inventory.

**Parent topic:** [About the Directories Used During Installation of Oracle Grid Infrastructure](about-the-directories-used-during-installation-of-oracle-grid-infrastructure.md)
