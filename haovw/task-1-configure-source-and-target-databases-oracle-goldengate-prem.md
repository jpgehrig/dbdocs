## Task 1: Configure the Source and Target Databases for Oracle GoldenGate

The source and target Oracle GoldenGate databases should be configured using the following recommendations.

Perform the following steps to complete this task:

- Step 1.1 - Database Configuration
- Step 1.2 - Create the Database Replication Administrator User
- Step 1.3 - Create the Database Services

Step 1.1 - Database Configuration

The source and target Oracle GoldenGate databases should be configured using the following recommendations:

| Configuration                                                  | Scope                                                            | Example                                                                                                                                                                                                                                                                                                                                     |
|:---------------------------------------------------------------|:-----------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Enable Archivelog Mode                                         | Source and Target                                                | `SQL> ARCHIVE LOG LIST`<br>`Database log mode              Archive Mode`<br>`Automatic archival             Enabled`<br>`Archive destination            USE_DB_RECOVERY_FILE_DEST`<br>`Oldest online log sequence     110`<br>`Next log sequence to archive   113`<br>`Current log sequence           113`                                  |
| Enable `FORCE LOGGING`                                         | Source and Target                                                | `ALTER DATABASE FORCE LOGGING;`                                                                                                                                                                                                                                                                                                             |
| `ENABLE_GOLDENGATE_REPLICATION`                                | Source, Target, and Standbys                                     | `ALTER SYSTEM SET ENABLE_GOLDENGATE_REPLICATION=TRUE SCOPE=BOTH SID='*';`                                                                                                                                                                                                                                                                   |
| Add Supplemental Logging                                       | Source<br>Required on Target for cases when replication reverses | `ALTER DATABASE ADD SUPPLEMENTAL LOG DATA;`                                                                                                                                                                                                                                                                                                 |
| Configure `STREAMS_POOL_SIZE` larger to accommodate GoldenGate | Source<br>Required on Target for cases when replication reverses | The value of `STREAMS_POOL_SIZE` should be set to the following value:<br>`STREAMS_POOL_SIZE` = (((#Extracts + \#Integrated Replicats) \* 1GB) \* 1.25)<br>For example, in a database with 2 Extracts and 2 integrated Replicats:<br>`STREAMS_POOL_SIZE` = 4GB \* 1.25 = 5GB<br>`ALTER SYSTEM SET STREAMS_POOL_SIZE=5G SCOPE=BOTH SID='*';` |

For the steps on preparing the database for Oracle GoldenGate, see [Preparing the Database for Oracle GoldenGate](https://docs.oracle.com/en/middleware/goldengate/core/21.3/oracle-db/preparing-database-oracle-goldengate.html#GUID-E06838BD-0933-4027-8A6C-D4A17BDF4E41).

Step 1.2 - Create the Database Replication Administrator User

The source and target databases need a GoldenGate administrator user created, with appropriate privileges assigned as follows:

- For the multitenant container database (CDB):
  - Source database, GoldenGate Extract must be configured to connect to a user in the root container database, using a c##
  - Target database, a separate GoldenGate administrator user is needed for each pluggable database (PDB).
  - For more details about creating a GoldenGate administrator in an Oracle Multitenant Database, see [Configuring Oracle GoldenGate in a Multitenant Container Database](https://docs.oracle.com/en/middleware/goldengate/core/21.3/oracle-db/configuring-oracle-goldengate-multitenant-container-database-1.html#GUID-0B0CEB35-51C6-4319-BEE1-FA208FF4DE05).
- For non-CDB databases, see [Establishing Oracle GoldenGate Credentials](https://docs.oracle.com/en/middleware/goldengate/core/21.3/oracle-db/establishing-oracle-goldengate-credentials.html#GUID-E40B375A-5042-4195-B563-BE7EDC251880)

As the `oracle` OS user on the source database system, run the following SQL instructions to create the database user for Oracle GoldenGate and assign the required privileges:

    [oracle@exadb1_node1 ~]$ sqlplus / as sysdba

    # Source CDB
    SQL>
    alter session set container=cdb$root;
    create user c##ggadmin identified by "<ggadmin_password>" container=all default tablespace USERS temporary tablespace temp;
    alter user c##ggadmin quota unlimited on users;
    grant set container to c##ggadmin container=all;
    grant alter system to c##ggadmin container=all;
    grant create session to c##ggadmin container=all;
    grant alter any table to c##ggadmin container=all;
    grant resource to c##ggadmin container=all;
    exec dbms_goldengate_auth.grant_admin_privilege('c##ggadmin',container=>'all');

    # Source PDB
    SQL>
    alter session set container=<pdbName>;
    create user ggadmin identified by "<ggadmin_password>" container=current;
    grant create session to ggadmin container=current;
    grant alter any table to ggadmin container=current;
    grant resource to ggadmin container=current;
    exec dbms_goldengate_auth.grant_admin_privilege('ggadmin');

As the `oracle` OS user on the target database system, run the following SQL instructions to create the database user for Oracle GoldenGate and assign it the required privileges:

    [oracle@exadb2_node1 ~]$ sqlplus / as sysdba

    # Target PDB
    SQL>
    alter session set container=<pdbName>;
    create user ggadmin identified by "<ggadmin_password>" container=current;
    grant alter system to ggadmin container=current;
    grant create session to ggadmin container=current;
    grant alter any table to ggadmin container=current;
    grant resource to ggadmin container=current;
    grant dv_goldengate_admin, dv_goldengate_redo_access to ggadmin container=current;
    exec dbms_goldengate_auth.grant_admin_privilege('ggadmin');

Step 1.3 - Create the Database Services

If the source and target databases are running the recommended configuration on an Oracle RAC cluster with Oracle Data Guard, a role-based service must be created that allows the Extract or Replicat processes to connect to the correct Data Guard primary database instance.

When using a source multitenant database, a separate service is required for the root container database (CDB) and the pluggable database (PDB) that contains the schema being replicated. For a target multitenant database, a single service is required for the PDB.

As the `oracle` OS user on the primary and standby database systems, create and start the CDB database service using the following command:

    [oracle@exadb1_node1 ~]$ srvctl add service -db <dbName>
     -service <dbName>_goldengate -preferred <ORACLE_SID1> -available <ORACLE_SID2>
     -role PRIMARY

As the oracle OS user on the primary and standby database systems, create and start the PDB database service using the following command:

    [oracle@exadb1_node1 ~]$ srvctl add service -db <dbName>
     -service <dbName>_<pdbName>_goldengate -preferred <ORACLE_SID1>
     -available <ORACLE_SID2> -pdb <pdbName> -role PRIMARY

As the `oracle` OS user on the primary and standby database systems, start and verify that the services are running, as shown here:

    [oracle@exadb1_node1 ~]$ srvctl start service -db <dbName> -role
    [oracle@exadb1_node1 ~]$ srvctl status service -db <dbName> |grep goldengate

    Service <dbName>_goldengate  is running on instance(s) <SID1>
    Service <dbName>_<pdbName>_goldengate is running on instance(s) <SID1>

**Note:**

Repeat step 1.3 in the source and target database system.
