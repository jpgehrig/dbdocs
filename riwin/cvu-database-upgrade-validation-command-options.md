## Using the CVU Database Upgrade Validation Command Options

Use the Cluster Verification Utility (CVU) to check the readiness of your Oracle RAC installation for upgrades.

### Purpose

Running `cluvfy` with the `-pre dbinst` and `-upgrade` options performs system checks to confirm if the cluster is in a correct state for upgrading from an existing Oracle RAC installation.

### Command Syntax

    cluvfy stage -pre dbinst -upgrade -src_dbhome src_RAChome [-dbname
    db_names_list] -dest_dbhome dest_RAChome -dest_version dest_version
     [-dest_serviceuser username [-dest_servicepasswd]][-verbose]

### Command Options

Table C-1 Command Options for CLUVFY Pre-upgrade Check

| Command Option                 | Description                                                                                                                                                                                                                                        |
|:-------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-src_dbhome ``src_RAChome`    | The location of the source Oracle RAC home that you are upgrading, where src_RAChome is the path to the home that you want to upgrade.                                                                                                             |
| `-dbname ``db_names_list`      | Optional: List of unique names of the databases being upgraded.                                                                                                                                                                                    |
| `-dest_dbhome ``dest_RAChome`  | The location of the upgraded Oracle RAC home, where dest_RAChome is the path to the Oracle RAC home.                                                                                                                                               |
| `-dest_version ``dest_version` | Use the `dest_version` option to indicate the release number of the upgrade, including any patchset. The release number must include the five digits designating the release to the level of the platform-specific patch, for example: 12.2.0.1.0. |
| `-dest_serviceuser ``username` | Optional: The Oracle Home user for the destination Oracle home.                                                                                                                                                                                    |
| `-dest_servicepasswd`          | Optional: Prompt for the Oracle Home user password                                                                                                                                                                                                 |
| `-verbose`                     | Use the `-verbose` option to produce detailed output of individual checks.                                                                                                                                                                         |

**See Also:**

[Oracle Database Administrator’s Guide](../admin/index.md) for information about release number format.

**Parent topic:** [Using CVU to Validate Readiness for Oracle RAC Upgrades](using-cvu-to-validate-readiness-for-oracle-rac-upgrades.md)
