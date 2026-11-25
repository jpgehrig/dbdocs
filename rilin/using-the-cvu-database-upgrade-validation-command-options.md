## Using the CVU Database Upgrade Validation Command Options

Use the Cluster Verification Utility (CVU) command `cluvfy stage -pre dbinst -upgrade` to check the readiness of your Oracle RAC installation for upgrades.

Running `cluvfy` with the ` -predbinst -upgrade` options performs system checks to confirm if the cluster is in a correct state for upgrading from an existing Oracle RAC installation.

The command uses the following syntax, where variable content is indicated by italics:

    cluvfy stage -pre dbinst -upgrade -src_dbhome src_RAChome [-dbname
    db_names_list] -dest_dbhome dest_RAChome -dest_version dest_version
    [-fixup] [-fixupnoexec][-method root|-method sudo -user user_name
    [-location dir_path ]] [-verbose]

The command performs the appropriate checks on all the nodes in the cluster before setting up an Oracle RAC Database. The following table describes the options for the command.

Table C-1 Cluster Verification Utility Command Options for Oracle RAC Databases

| Option                        | Description                                                                                                                                                                                          |
|:------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-src_dbhome ` src_RAChome    | Location of the source Oracle RAC home that you are upgrading, where src_RAChome is the path to the home to upgrade.                                                                                 |
| `-dest_dbhome ` dest_RAChome  | Location of the Oracle RAC home for upgrade, where dest_RAChome is the path to the Oracle RAC home.                                                                                                  |
| `-dest_version ` dest_version | Release number of the upgrade, including any patchset. The release number must include the five digits designating the release to the level of the platform-specific patch. For example: 12.2.0.1.0. |
| `—user` user_name             | User name to access all the nodes with root privileges.                                                                                                                                              |
| `-location` dir_path          | Full file system path for the `sudo` executable.                                                                                                                                                     |
| `-dbname` db_names_list       | List of unique names of the databases being upgraded.                                                                                                                                                |
| `-verbose`                    | Displays detailed output of individual checks.                                                                                                                                                       |
| `-fixup`                      | If specified, on verification failure, performs fixup operations.                                                                                                                                    |
| `-fixupnoexec`                | If specified, on verification failure, fix up data is generated and the instruction for manual execution of the generated fix ups is displayed.                                                      |

**See Also:**

[Oracle Database Administrator's Guide](../admin/getting-started-with-database-administration.md) for information about release number format

**Parent topic:** [Using CVU to Validate Readiness for Oracle RAC Upgrades](using-cvu-to-validate-readiness-for-oracle-rac-upgrades.md)
