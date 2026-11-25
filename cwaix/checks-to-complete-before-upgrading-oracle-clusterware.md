Complete the following tasks before upgrading Oracle Grid Infrastructure.

1.  For each node, use Cluster Verification Utility to ensure that you have completed preinstallation steps. It can generate Fixup scripts to help you to prepare servers. In addition, the installer helps you to ensure all required prerequisites are met.

    Ensure that you have the information you need during installation, including the following:

    - An Oracle base location for Oracle Clusterware.

    - An Oracle Grid Infrastructure home location that is different from your existing Oracle Clusterware location.

    - SCAN name and addresses, and other network addresses.

    - Privileged user operating system groups.

    - `root` user access, to run scripts as `root` during installation.

2.  For the installation owner running the installation, if you have environment variables set for the existing installation, then unset the environment variables `$ORACLE_HOME` and `$ORACLE_SID`, as these environment variables are used during upgrade. For example, as `grid` user, run the following commands on the local node:

    For bash shell:

        $ unset ORACLE_BASE
        $ unset ORACLE_HOME
        $ unset ORACLE_SID

    For C shell:

        $ unsetenv ORACLE_BASE
        $ unsetenv ORACLE_HOME
        $ unsetenv ORACLE_SID

3.  If you have set `ORA_CRS_HOME` as an environment variable, following instructions from Oracle Support, then unset it before starting an installation or upgrade. You should never use `ORA_CRS_HOME` as an environment variable except under explicit direction from Oracle Support.

4.  Check to ensure that the user profile for the installation user, for example, .profile or .cshrc, does not set any of these environment variables.

5.  If you have an existing installation on your system, and you are using the same user account to install this installation, then unset the following environment variables: `ORA_CRS_HOME`, `ORACLE_HOME`, `ORA_NLS10`, `TNS_ADMIN` and any other environment variable set for the Oracle installation user that is connected with Oracle software homes.

6.  Ensure that the `$ORACLE_HOME/bin` path is removed from your PATH environment variable.

**Parent topic:** [Preparing to Upgrade an Existing Oracle Clusterware Installation](preparing-to-upgrade-an-existing-oracle-clusterware-installation.md)
