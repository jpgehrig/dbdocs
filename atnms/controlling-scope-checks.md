Use the list of commands in this section to control the scope of checks.

### Syntax

    [-b]
    [-p]
    [-m]
    [-u –o pre]
    [-u –o post]
    [-clusternodes nodes]
    [-failedchecks previous_result]
    [-nordbms]
    [-dbnames db_names]
    [-dbnone]
    [-dball]
    [-localonly]
    [-cells cells]
    [-ibswitches switches]
    [-profile profile]
    [-excludeprofile profile]
    [-check check_id]
    [-excludecheck check_id]
    [-skip_usr_def_checks]

### Parameters

Table A-2 Scope of Checks

| Command                           | Description                                                                                                          |
|:----------------------------------|:---------------------------------------------------------------------------------------------------------------------|
| `-b`                              | Runs only the best practice checks.<br>Does not run the recommended patch checks.                                    |
| `-p`                              | Runs only the patch checks.                                                                                          |
| `-m`                              | Excludes the checks for Maximum Availability Architecture (MAA) scorecards.                                          |
| `-u –o pre`                       | Runs the pre-upgrade checks for Oracle Clusterware and database.                                                     |
| `-u –o post`                      | Runs the post-upgrade checks for Oracle Clusterware and database.                                                    |
| `-clusternodes ``nodes`           | Specify a comma-delimited list of node names to run only on a subset of nodes.                                       |
| `-failedchecks ``previous_result` | Runs only checks from the presious_result, which had failed.                                                         |
| `-nordbms`                        | Runs Oracle Grid Infrastructure checks only in environments with no Oracle Database checks performed.                |
| `-dbnames ``db_names`             | Specify a comma-delimited list of database names to run only on a subset of databases.                               |
| `-dbnone`                         | Does not prompt for database selection and skips all the database checks.                                            |
| `-dball`                          | Does not prompt for database selection and runs the database checks on all databases discovered on the system.       |
| `-localonly`                      | Runs only on the local node.                                                                                         |
| `-cells ``cells`                  | Specify a comma-delimited list of storage server names to run the checks only on a subset of storage servers.        |
| `-ibswitches ``switches`          | Specify a comma-delimited list of InfiniBand switch names to run the checks only on a subset of InfiniBand switches. |
| `-profile ``profile`              | Specify a comma-delimited list of profiles to run only the checks in the specified profiles.                         |
| `-excludeprofile ``profile`       | Specify a comma-delimited list of profiles to exclude the checks in the specified profiles.                          |
| `-check ``check_id`               | Specify a comma-delimited list of check IDs to run only the checks specified in the list check IDs.                  |
| `-excludecheck ``check_id`        | Specify a comma-delimited list of check IDs to exclude the checks specified in the list of check IDs.                |
| `-skip_usr_def_checks`            | Does not run the checks specified in the user-defined `xml` file.                                                    |

**Parent topic:** [Oracle ORAchk and Oracle EXAchk Command-Line Options](orachk-and-exachk-command-line-options.md)
