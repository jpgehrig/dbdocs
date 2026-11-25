## Tasks to Complete Before Upgrading Oracle Grid Infrastructure

Review the tasks before upgrading Oracle Clusterware.

Before upgrading, you must unset the following environment variables:

- `ORACLE_BASE`

- `ORACLE_HOME`

- `ORACLE_SID`

- `ORA_NLS10`

- `TNS_ADMIN`

- `ORA_CRS_HOME`

If you have set `ORA_CRS_HOME` as an environment variable, following instructions from Oracle Support, then unset it before starting an installation or upgrade. You should never use `ORA_CRS_HOME` as an environment variable except under explicit direction from Oracle Support.

1.  For each node, use the Cluster Verification Utility (CVU) to assist you with system checks in preparation for patching or upgrading.
    You can run CVU before starting the upgrade, however, the installer runs the appropriate CVU checks automatically, and prompts you to fix problems before proceeding with the upgrade.
2.  Ensure that you have information you will need during installation, including the following:
    - An Oracle base location for Oracle Clusterware

    - An Oracle Grid Infrastructure home location that is different from your existing Grid home location

    - SCAN name and addresses, and other network addresses

    - Privileged user operating system groups

    - Local Administrator user access, or access as the user who performed the previous Oracle Clusterware installation
3.  For the installation user running the installation, if you have environment variables set for the existing installation, then unset the environment variables `%ORACLE_HOME%` and `%ORACLE_SID%`, because these environment variables are used during upgrade. For example, as the `grid` user, run the following commands on the local node:
        C:\> set ORACLE_HOME=
        C:\> set ORACLE_BASE=
        C:\> set ORACLE_SID=
4.  If you have set `ORA_CRS_HOME` as an environment variable, following instructions from Oracle Support, then unset it before starting an installation or upgrade.
    You should never use `ORA_CRS_HOME` as an environment variable except under explicit direction from Oracle Support.
5.  If you have an existing installation on your system, and you are using the same user account to upgrade this installation, then unset the following environment variables:
    `ORA_CRS_HOME`, `ORACLE_HOME`, `ORA_NLS10`, `TNS_ADMIN` and any other environment variable set for the Oracle installation user that is connected with Oracle software homes.
6.  Check to ensure that the user profile for the Oracle Installation User does not set any of these environment variables.

**Related Topics**

- [Configuring Users, Groups and Environments for Oracle Grid Infrastructure and Oracle RAC](configuring-users-groups-and-environments-for-oracle-grid-infrastructure-and-oracle-rac.md)
- [Configuring Networks for Oracle Grid Infrastructure and Oracle RAC](configuring-networks-for-oracle-grid-infrastructure-and-oracle-rac.md)

**Parent topic:** [Preparing to Upgrade an Existing Oracle Clusterware Installation](preparing-to-upgrade-an-existing-oracle-clusterware-installation.md)
