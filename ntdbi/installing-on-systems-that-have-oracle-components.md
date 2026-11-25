## Installing on Systems That Already Have Oracle Components

Perform the following steps when other components exist on your computer:

1.  Log on as a member of the Administrators group for the computer on which you want to install Oracle components.

    If you are installing on a Primary Domain Controller (PDC) or a Backup Domain Controller (BDC), log on as a member of the Domain Administrators group.

2.  Delete the `ORACLE_HOME` environment variable if it exists. See the Microsoft online help for more information about deleting environment variables.

    **Note:**

    The `ORACLE_HOME` environment variable is automatically set in the registry. Manually setting this variable prevents installation.

3.  Back up any databases you must upgrade.

**See Also:**

[Oracle Real Application Clusters Installation Guide for Linux and UNIX](../rilin/port-numbers-and-protocols-of-oracle-components.md)

**Parent topic:** [Preinstallation Considerations for Installing Oracle Database](preinstallation-considerations-for-installing-oracle-database.md)
