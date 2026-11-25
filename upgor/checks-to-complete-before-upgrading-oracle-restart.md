Complete these preupgrade checks to avoid issues during the Oracle Restart upgrade process.

1.  Review the new features for the Oracle Restart release to which you want to upgrade.

2.  Ensure that you have all of the information you need for the upgrade. For example:

    - An Oracle base location for Oracle Restart.

    - An Oracle Restart home location that is different from your existing Oracle Restart home.

    - Privileged user operating system groups.

    - `root` user access, to run scripts as the `root` user during the upgrade.

3.  Unset the `$ORACLE_HOME`, `$ORACLE_BASE`, and `$ORACLE_SID` environment variables because these environment variables are used during the upgrade. For example, as the `grid` user, run the following commands:

    For bash shell:

        $ unset ORACLE_HOME
        $ unset ORACLE_BASE
        $ unset ORACLE_SID

    For C shell:

        $ unsetenv ORACLE_HOME
        $ unsetenv ORACLE_BASE
        $ unsetenv ORACLE_SID

4.  Ensure that the installation owner user profile, such as `.profile` or `.cshrc`, does not set any of these environment variables.

5.  Unset any environment variables, such as `ORA_NLS10` and `TNS_ADMIN`, set for the installation owner user that is connected with the Oracle software homes.

6.  Ensure that the `$ORACLE_HOME/bin` path is removed from your PATH environment variable.

**Related Topics**

- [Oracle Database New Features Guide](../newft/index.md)

**Parent topic:** [Preparing to Upgrade Oracle Restart](preparing-to-upgrade-oracle-restart.md)
