Complete this procedure to upgrade Oracle Grid Infrastructure for a standalone server (Oracle Restart) from an earlier release.

Be prepared to run root scripts before you start the upgrade.

1.  As the Oracle Home user, download the Oracle Grid Infrastructure image files and extract the files to the Grid home.
    For example:

        C:\> md C:\app\grid\product\19.0.0\grid
        C:\> cd C:\app\grid\product\19.0.0\grid
        C:\> unzip -q download_location\grid_home.zip

    `download_location\grid_home.zip` is the path of the downloaded Oracle Grid Infrastructure image file.

    **Note:**

    - You must extract the image software into the directory where you want your new Grid home to be located.
2.  Start the Oracle Grid Infrastructure wizard:
        C:\> C:\app\grid\product\19.0.0\grid\setup.exe
3.  Select the Upgrade Oracle Grid Infrastructure option to upgrade Oracle Grid Infrastructure for a standalone server.
4.  Select the installation options as prompted.
    At any time during the upgrade, if you have a question about what you are being asked to do, or what input you are required to provide during the upgrade, then click the Help button on the installer window.

**Parent topic:** [Upgrading and Patching Oracle Restart](upgrading-and-patching-oracle-restart.md)
