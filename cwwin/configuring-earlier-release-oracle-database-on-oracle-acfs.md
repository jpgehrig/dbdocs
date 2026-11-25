## Configuring Earlier Release Oracle Database on Oracle ACFS

Review this information to configure a 11.2 release Oracle Database on Oracle Automatic Storage Management Cluster File System (Oracle ACFS).

1.  Install Oracle Grid Infrastructure 19c as described in this guide.
2.  Navigate to the bin directory in the Grid home.
    `C:\> cd C:\app\19.0.0\grid\bin`
3.  Start Oracle ASM Configuration Assistant (ASMCA) as the grid installation owner:
        C:\> asmca

    Follow the steps in the configuration wizard to create Oracle ACFS storage for the earlier release Oracle Database home.
4.  Install Oracle Database 11g release 2 (11.2) software-only on the Oracle ACFS file system you configured.
5.  From the 11.2 Oracle Database home, run Oracle Database Configuration Assistant (DBCA) and create the Oracle RAC Database, using Oracle ASM as storage for the database data files.
        dbca
6.  Modify the Oracle ACFS path dependency:
        srvctl modify database -d my_112_db -j Oracle_ACFS_path

**Parent topic:** [Using Earlier Oracle Database Releases with Grid Infrastructure](using-earlier-oracle-database-releases-with-grid-infrastructure.md)
