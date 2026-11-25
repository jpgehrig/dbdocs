## Running Setup Wizard to Install Oracle Database Client

Use the `runInstaller` command to start the Oracle Database Client installation.

Have all the information you need to provide regarding users groups, and storage paths before you start the installation.

During installation, you are asked to run configuration scripts as the `root` user. You can either run these scripts manually as `root` when prompted, or you can provide configuration information and passwords using a root privilege delegation option such as `sudo`.

1.  Log in as the Oracle installation owner user account (`oracle`).
2.  From where you have downloaded the installation binaries, run the `runInstaller` command to start the Oracle setup wizard.
    For example:

        $ cd /home/oracle_sw/
        $ ./runInstaller

    **Note:**

    - Run the `runInstaller` command from the Oracle home directory only. Do not use the `runInstaller` command that resides at `$ORACLE_HOME/oui/bin/`, or any other location, to install Oracle Database, Oracle Database Client, or Oracle Grid Infrastructure.
    - Oracle home or Oracle base cannot be `symlinks`, nor can any of their parent directories, all the way to up to the `root` directory.
3.  Select your installation type.
    Installation screens vary depending on the installation option you select. Respond to the configuration prompts as needed.

    **Note:**

    At any time during installation, if you have a question about what you are being asked to do, click Help.

**Parent topic:** [Installing the Oracle Database Client Software](installing-the-oracle-database-client-software.md)
