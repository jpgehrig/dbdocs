Configure a set of persistent, automatic channels for use in all RMAN sessions.

This example configures automatic disk channels across two file systems:

    CONFIGURE DEVICE TYPE DISK PARALLELISM 2;
    CONFIGURE CHANNEL 1 DEVICE TYPE DISK FORMAT '/disk1/%U';
    CONFIGURE CHANNEL 2 DEVICE TYPE DISK FORMAT '/disk2/%U';

Because `PARALLELISM` is set to 2, the following command divides the backup pieces between two file systems:

    BACKUP DEVICE TYPE DISK
      DATABASE PLUS ARCHIVELOG;

The following `LIST` command shows how the data file backup was parallelized:

    RMAN> LIST BACKUPSET 2031, 2032;

    List of Backup Sets
    ===================

    BS Key  Type LV Size       Device Type Elapsed Time Completion Time
    ------- ---- -- ---------- ----------- ------------ ---------------
    2031    Full    401.99M    DISK        00:00:57     19-JAN-07
            BP Key: 2038   Status: AVAILABLE  Compressed: NO  Tag: TAG20070119T100532
            Piece Name: /disk1/24i7ssnc_1_1
      List of Datafiles in backup set 2031
      File LV Type Ckp SCN    Ckp Time  Name
      ---- -- ---- ---------- --------- ----
      1       Full 973497     19-JAN-07 /disk3/oracle/dbs/t_db1.f
      5       Full 973497     19-JAN-07 /disk3/oracle/dbs/tbs_112.f

    BS Key  Type LV Size       Device Type Elapsed Time Completion Time
    ------- ---- -- ---------- ----------- ------------ ---------------
    2032    Full    133.29M    DISK        00:00:57     19-JAN-07
            BP Key: 2039   Status: AVAILABLE  Compressed: NO  Tag: TAG20070119T100532
            Piece Name: /disk2/25i7ssnc_1_1
      List of Datafiles in backup set 2032
      File LV Type Ckp SCN    Ckp Time  Name
      ---- -- ---- ---------- --------- ----
      2       Full 973501     19-JAN-07 /disk3/oracle/dbs/t_ax1.f
      3       Full 973501     19-JAN-07 /disk3/oracle/dbs/t_undo1.f
      4       Full 973501     19-JAN-07 /disk3/oracle/dbs/tbs_111.f

**Parent topic:** [Preparing Servers and Network for Database Duplication](preparing-servers-and-network-for-db-duplication.md)
