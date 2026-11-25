Use this procedure to do a software-only installation of Oracle Grid Infrastructure for a standalone server.

1.  Log in as the Oracle Restart software owner user (`oracle`).
2.  Download the Oracle Grid Infrastructure for a standalone server installation image files, create the Grid home directory, and extract the image files in this Grid home directory.
    For example:

        $ mkdir -p /u01/app/oracle/product/19.0.0/grid
        $ chown oracle:oinstall /u01/app/oracle/product/19.0.0/grid
        $ cd /u01/app/oracle/product/19.0.0/grid
        $ unzip -q /tmp/grid_home.zip

    **Note:**

    Ensure that the Grid home directory path you create is in compliance with the Oracle Optimal Flexible Architecture recommendations. Also, unzip the installation image files only in this Grid home directory that you created.
3.  Ensure that you complete all the storage and server preinstallation requirements. Verify that your server meets the installation requirements using the following command:
        $ cd /u01/app/oracle/product/19.0.0/grid
        $ runcluvfy.sh stage -pre hacfg
4.  Run `gridSetup.sh` to start the Oracle Grid Infrastructure setup wizard:
        $ Grid_home/gridSetup.sh

    Where, Grid_home is the Oracle Grid Infrastructure home directory.

    **Note:**

    You must install Oracle Grid Infrastructure for a standalone server from the Oracle Grid Infrastructure media.
5.  In the Select Configuration Option screen, select the Set Up Software Only option to perform a software-only installation of Oracle Grid Infrastructure for a standalone server. Click Next.
6.  Respond to the prompts as needed to set up Oracle Grid Infrastructure. Click Help for information.
7.  The Oracle Grid Infrastructure setup wizard prompts you to run the `root.sh` script and, if required, the `orainstRoot.sh` script.
8.  The `root.sh `script output provides information about how to proceed, depending on the configuration you plan to complete in this installation. Note this information.

**Parent topic:** [Installing Oracle Grid Infrastructure for a Standalone Server Using a Software-Only Installation](installing-oracle-grid-infrastructure-for-a-standalone-server-using-a-software-only-installation.md)
