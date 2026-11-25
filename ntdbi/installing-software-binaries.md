## Installing Software Binaries for Oracle Grid Infrastructure for a Standalone Server

Use this procedure to do a software-only installation of Oracle Grid Infrastructure for a standalone server.

1.  Log in to Windows as an Administrator user.
2.  Download the Oracle Grid Infrastructure installation image files, create the Grid home directory, and extract the image files in this Grid home directory.
    For example:

        C:\> mkdir \app\oracle\product\19.0.0\grid
        C:\> cd \app\oracle\product\19.0.0\grid
        C:\> unzip -q download_location\grid.zip
3.  Verify that the server meets the installation requirements using the command `runcluvfy.bat stage -pre ``hacfg`. Ensure that you have completed all storage and server preinstallation requirements.
    For Example:

        C:\> app\oracle\product\19.0.0\grid\runcluvfy.bat
4.  Log in as the Oracle Restart software owner user and run `setup.exe` to start the Oracle Grid Infrastructure installation wizard.
    `C:\> app\oracle\product\19.0.0\grid\setup.exe`
5.  In the Select Configuration Option screen, select the Set Up Software Only option to perform a software-only installation of Oracle Restart. Click Next.
6.  Respond to the prompts as needed to set up Oracle Grid Infrastructure. Click Help for information.

**Parent topic:** [Installing Oracle Grid Infrastructure for a Standalone Server Using a Software-Only Installation](installing-oracle-grid-infrastructure-for-a-standalone-server-using-a-software-only-installation.md)
