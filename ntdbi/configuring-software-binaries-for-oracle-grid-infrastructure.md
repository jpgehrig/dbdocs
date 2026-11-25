## Configuring Software Binaries for Oracle Grid Infrastructure for a Standalone Server

Use this procedure to configure and activate a software-only Oracle Restart without Oracle Automatic Storage Management (Oracle ASM).

1.  Log in as a member of the Administrators group and run the `roothas.bat` script from the `Grid_home`, using the following syntax:
        C:\>DRIVE_LETTER:\Grid_home\crs\install\roothas.bat

    For example, if your Grid home is `C:\app\oracle\product\19.0.0\grid`, then run the following script:

        C:\>C:\app\oracle\product\19.0.0\grid\crs\install\roothas.bat
2.  Change the home directory to the path of the Oracle Restart home as follows:
    `Grid_home``\oui\bin`, where `Grid_home` is the path of the Oracle Restart home.
3.  Enter the following command:
        setup.exe -updateNodeList ORACLE_HOME=Grid_home
        CLUSTER_NODES= CRS=TRUE

    For example:

        C:\app\oracle\product\19.0.0\grid> setup.exe -updateNodeList ORACLE_HOME=C:\app\oracle\product\19.0.0\grid
        CLUSTER_NODES= CRS=TRUE
4.  Use the `SRVCTL` utility along with Network Configuration Assistant and Oracle Automatic Storage Management Configuration Assistant to add the listener, the Oracle Automatic Storage Management instance, and all Oracle Automatic Storage Management disk groups to the Oracle Restart configuration.
    **See Also:**

    - [Oracle Database Net Services Administrator's Guide](../netag/managing-oracle-net-services.md)

    - [Oracle Automatic Storage Management Administrator's Guide](../ostmg/manage-asm-asmca.md)

    - [Oracle Database Administrator's Guide](../admin/configuring-automatic-restart-of-an-oracle-database.md)

**Parent topic:** [Installing Oracle Grid Infrastructure for a Standalone Server Using a Software-Only Installation](installing-oracle-grid-infrastructure-for-a-standalone-server-using-a-software-only-installation.md)
