## Using Oracle GoldenGate to Replicate Data Between Sharded and Non-Sharded Databases

You can migrate data from a non-sharded database to a sharded database using Oracle GoldenGate.

Migrating data from a non-sharded database to sharded database using Oracle GoldenGate is done in two phases.

Extraction on source database

- All of the tables from the source database are extracted using single extract on the source database.

Replication on target database

- The replication into sharded tables is performed on the shards and the replication into duplicated tables is performed on the shard catalog.

### Oracle GoldenGate Replication Prerequisites

Make sure your source and target databases, and Oracle GoldenGate environments meet these prerequisites before attempting sharded database Oracle GoldenGate replication.

#### Assumptions

1.  It is assumed that the tables to be migrated from the non-sharded to sharded database have already been classified into sharded and duplicated tables.

2.  The sharding keys for all of the tables to be migrated to sharded tables have already been identified.

3.  Sharded and duplicated tables have been pre-created in the target sharded database.

4.  Oracle GoldenGate software is already installed on the source and target systems.

#### Source and Target Databases

- Oracle Database version: 19c (19.15.0.0.0) or later in a Multitenant architecture

- Target database sharding type: System-managed

#### Oracle GoldenGate Configuration

Oracle GoldenGate Version: 19c Classic Architecture in a hub configuration

### Replicating Data from a Non-Sharded Database to a Sharded Database

Example environment

The examples in the steps below use the following topology

| System/Object      | Source Environment           | Target Environment                                      |
|:-------------------|:-----------------------------|:--------------------------------------------------------|
| CDB Name           | srccdb                       | sdbcdb                                                  |
| PDB Name           | srcpdb                       | Shards: sdbpdb1,sdbpdb2,sdbpdb3<br>Shard catalog: scpdb |
| Application Schema | app_schema                   | app_schema                                              |
| Sharded Tables     | Customers, Orders, LineItems | Customers, Orders, LineItems                            |
| Duplicated Tables  | Products                     | Products                                                |

High Level Steps

1\) Create an extract on the source database to capture transactions from the source tables and start it.

2\) Capture data from source database for initial load using `expdp` and `flashback_scn`.

3\) Perform initial load into the sharded tables on target shards using `impdp`.

4\) Perform initial load into the duplicated tables on the target shard catalog using `impdp`.

5\) Create the same number of replicats as number of target shards to replicate sharded tables.

6\) Create one replicat for the shard catalog to replicate duplicated tables.

7\) Start replicats on the target shards using `at csn`

8\) Start replicat on the shard catalog using `at csn`

9\) Validate the data replication from the source to target tables.

1.  Configure the source (non-sharded) database

    1.  Create an extract on the source database to capture transactions from source tables and start it.

            $ ggsci

            GGSCI > dblogin useridalias ggadmin
            GGSCI > add extract extnshd, integrated tranlog, begin now
            GGSCI > register extract extnshd, database container (SRCPDB)
            GGSCI > add exttrail ./dirdat/tr, extract extnshd

            Add the following parameters in extract parameter file

            GGSCI > edit params extnshd

            extract extnshd
            useridalias  ggadmin
            TranlogOptions IntegratedParams (max_sga_size 256)
            extTrail ./dirdat/tr
            DiscardFile ./dirrpt/extnshd.dsc, Append Megabytes 50
            REPORTCOUNT EVERY 2 HOURS, RATE
            Table SRCPDB.app_schema.customers;
            Table SRCPDB.app_schema.orders;
            Table SRCPDB.app_schema.lineitems;
            Table SRCPDB.app_schema.products;

            GGSCI> start extract extnshd

    2.  Capture data from the source database for initial load using `expdp`.

            SQL> select current_scn from v$database;

            $ expdp app_schema/xxxxx@SRCPDB flashback_scn=current_scn_from_previous_step
             directory=DATA_PUMP_DIR dumpfile=app_schema_exp.dmp
             logfile=app_schema_exp.log

2.  Configure the target (sharded) database.

    1.  Perform the initial load on the target shard databases and shard catalog using `impdp`.

            Import into shards
            $ impdp app_schema/xxxxx@SDBPDB1 directory=DATA_PUMP_DIR dumpfile=app_schema_exp.dmp
             logfile=app_schema_imp.log tables=CUSTOMERS,ORDERS,LINEITEMS, CONTENT=DATA_ONLY
            $ impdp app_schema/xxxxx@SDBPDB2 directory=DATA_PUMP_DIR dumpfile=app_schema_exp.dmp
             logfile=app_schema_imp.log tables=CUSTOMERS,ORDERS,LINEITEMS, CONTENT=DATA_ONLY
            $ impdp app_schema/xxxxx@SDBPDB3 directory=DATA_PUMP_DIR dumpfile=app_schema_exp.dmp
             logfile=app_schema_imp.log tables=CUSTOMERS,ORDERS,LINEITEMS, CONTENT=DATA_ONLY

            Import into shard catalog
            $ impdp app_schema/xxxxx@SCPDB directory=DATA_PUMP_DIR dumpfile=app_schema_exp.dmp
             logfile=app_schema_imp.log tables=PRODUCTS CONTENT=DATA_ONLY

    2.  Create replicats (same as the number of shards) on the target database.

            Replicat for sharded tables on Shard 1
            ======================================
            GGSCI > dblogin useridalias ggadmin_shd1
            GGSCI > add replicat repshd1, INTEGRATED, exttrail ./dirdat/tr
             CHECKPOINTTABLE ggadmin.GGCHKPT

            Add the following parameters in replicat for shard1

            GGSCI > edit params repshd1

            replicat repshd1
            useridalias ggadmin_shd1
            HANDLECOLLISIONS
            SOURCECATALOG SDBPDB1
            MAP NSHDPDB.APP_SCHEMA.CUSTOMERS , target APP_SCHEMA.CUSTOMERS, &
            SQLEXEC (ID chunklookup1, QUERY 'select count(*) count FROM gsmadmin_internal.chunks
             WHERE ora_hash(:CODE_IN_PARAM) >= low_key and ora_hash(:CODE_IN_PARAM) < high_key',&
            PARAMS (CODE_IN_PARAM = CUSTID),
            BEFOREFILTER), &
            FILTER (chunklookup1.COUNT = 1);

            MAP NSHDPDB.APP_SCHEMA.ORDERS, target APP_SCHEMA.ORDERS, &
            SQLEXEC (ID chunklookup2, QUERY 'select count(*) count FROM gsmadmin_internal.chunks
             WHERE ora_hash(:CODE_IN_PARAM) >= low_key and ora_hash(:CODE_IN_PARAM) < high_key',&
            PARAMS (CODE_IN_PARAM = CUSTID),
            BEFOREFILTER), &
            FILTER (chunklookup2.COUNT = 1);

            MAP NSHDPDB.APP_SCHEMA.LINEITEMS, target APP_SCHEMA.LINEITEMS, &
            SQLEXEC (ID chunklookup3, QUERY 'select count(*) count FROM gsmadmin_internal.chunks
             WHERE ora_hash(:CODE_IN_PARAM) >= low_key and ora_hash(:CODE_IN_PARAM) < high_key',&
            PARAMS (CODE_IN_PARAM = CUSTID),
            BEFOREFILTER), &
            FILTER (chunklookup3.COUNT = 1);

            Replicat for sharded tables on Shard 2
            ======================================

            GGSCI > dblogin useridalias ggadmin_shd2
            GGSCI > add replicat repshd2, INTEGRATED, exttrail ./dirdat/tr
             CHECKPOINTTABLE ggadmin.GGCHKPT

            Add the following parameters in replicat for shard2

            GGSCI > edit params repshd2

            replicat repshd2
            useridalias ggadmin_shd2
            HANDLECOLLISIONS
            SOURCECATALOG SDBPDB2
            MAP NSHDPDB.APP_SCHEMA.CUSTOMERS , target APP_SCHEMA.CUSTOMERS, &
            SQLEXEC (ID chunklookup1, QUERY 'select count(*) count FROM gsmadmin_internal.chunks
             WHERE ora_hash(:CODE_IN_PARAM) >= low_key and ora_hash(:CODE_IN_PARAM) < high_key',&
            PARAMS (CODE_IN_PARAM = CUSTID),
            BEFOREFILTER), &
            FILTER (chunklookup1.COUNT = 1);

            MAP NSHDPDB.APP_SCHEMA.ORDERS, target APP_SCHEMA.ORDERS, &
            SQLEXEC (ID chunklookup2, QUERY 'select count(*) count FROM gsmadmin_internal.chunks
             WHERE ora_hash(:CODE_IN_PARAM) >= low_key and ora_hash(:CODE_IN_PARAM) < high_key',&
            PARAMS (CODE_IN_PARAM = CUSTID),
            BEFOREFILTER), &
            FILTER (chunklookup2.COUNT = 1);


            MAP NSHDPDB.APP_SCHEMA.LINEITEMS, target APP_SCHEMA.LINEITEMS, &
            SQLEXEC (ID chunklookup3, QUERY 'select count(*) count FROM gsmadmin_internal.chunks
             WHERE ora_hash(:CODE_IN_PARAM) >= low_key and ora_hash(:CODE_IN_PARAM) < high_key',&
            PARAMS (CODE_IN_PARAM = CUSTID),
            BEFOREFILTER), &
            FILTER (chunklookup3.COUNT = 1);

            Replicat for sharded tables on Shard 3
            ======================================

            GGSCI > dblogin useridalias ggadmin_shd3
            GGSCI > add replicat repshd3, INTEGRATED, exttrail ./dirdat/tr
             CHECKPOINTTABLE ggadmin.GGCHKPT

            Add the following parameters in replicat for shard3

            GGSCI > edit params repshd3

            replicat repshd3
            useridalias ggadmin_shd3
            HANDLECOLLISIONS
            SOURCECATALOG SDBPDB3
            MAP NSHDPDB.APP_SCHEMA.CUSTOMERS , target APP_SCHEMA.CUSTOMERS, &
            SQLEXEC (ID chunklookup1, QUERY 'select count(*) count FROM gsmadmin_internal.chunks
             WHERE ora_hash(:CODE_IN_PARAM) >= low_key and ora_hash(:CODE_IN_PARAM) < high_key',&
            PARAMS (CODE_IN_PARAM = CUSTID),
            BEFOREFILTER), &
            FILTER (chunklookup1.COUNT = 1);

            MAP NSHDPDB.APP_SCHEMA.ORDERS, target APP_SCHEMA.ORDERS, &
            SQLEXEC (ID chunklookup2, QUERY 'select count(*) count FROM gsmadmin_internal.chunks
             WHERE ora_hash(:CODE_IN_PARAM) >= low_key and ora_hash(:CODE_IN_PARAM) < high_key',&
            PARAMS (CODE_IN_PARAM = CUSTID),
            BEFOREFILTER), &
            FILTER (chunklookup2.COUNT = 1);


            MAP NSHDPDB.APP_SCHEMA.LINEITEMS, target APP_SCHEMA.LINEITEMS, &
            SQLEXEC (ID chunklookup3, QUERY 'select count(*) count FROM gsmadmin_internal.chunks
             WHERE ora_hash(:CODE_IN_PARAM) >= low_key and ora_hash(:CODE_IN_PARAM) < high_key',&
            PARAMS (CODE_IN_PARAM = CUSTID),
            BEFOREFILTER), &
            FILTER (chunklookup3.COUNT = 1);

            #### NOTE ####
            1. Remove Handlecollisions parameter and restart replicats after deltas
               have been applied on target shards.
            2. If sharding key column is of  number datatype, please use below sqlexec
               filter which has to_number in ora_hash function.

            SQLEXEC (ID chunklookup, QUERY 'select count(*) count FROM gsmadmin_internal.chunks
             WHERE ora_hash(to_number(:CODE_IN_PARAM)) >= low_key
               and ora_hash(to_number(:CODE_IN_PARAM)) < high_key',&


            Replicat for duplicate tables on Catalog
            ========================================

            GGSCI > dblogin useridalias ggadmin_cat
            GGSCI > add replicat repcat, INTEGRATED, exttrail ./dirdat/tr
             CHECKPOINTTABLE ggadmin.GGCHKPT

            Add the following parameters in replicat for shard1
            GGSCI > edit params repcat

            replicat repcat
            useridalias ggadmin_cat
            HANDLECOLLISIONS
            SOURCECATALOG SCPDB
            map NSHDPDB.APP_SCHEMA.PRODUCTS, target APP_SCHEMA.PRODUCTS;

    3.  Start replicats on target shards using `atcsn`.

            GGSCI> start replicat repshd1, atcsn <SCN captured on source>
            GGSCI> start replicat repshd2, atcsn <SCN captured on source>
            GGSCI> start replicat repshd3, atcsn <SCN captured on source>
            GGSCI> start replicat repcat, atcsn  <SCN captured on source>
            GGSCI > info all

            Program     Status      Group       Lag at Chkpt  Time Since Chkpt

            MANAGER     RUNNING
            EXTRACT     RUNNING     EXTNSHD     00:00:00      00:00:05
            REPLICAT    RUNNING     REPCAT      00:00:00      00:00:00
            REPLICAT    RUNNING     REPSHD1     00:00:00      00:00:03
            REPLICAT    RUNNING     REPSHD2     00:00:00      00:00:06
            REPLICAT    RUNNING     REPSHD3     00:09:01      00:00:09

3.  Validate the data replication from source to target tables.

    To validate that rows are replicated from the non-sharded table to the shards, for example, if you have 9000 rows in the source table, and three target shards, about 3000 rows should be distributed to each shard.
