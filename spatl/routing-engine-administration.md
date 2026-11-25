## D Routing Engine Administration

This appendix is for advanced users who need to administer the routing engine. It is not intended for most routing users.

**Note:**

It assumes that you are familiar with the concepts and techniques described in [Routing Engine](routing-engine-concepts.md).

The Oracle Spatial and Graph routing engine uses subprograms to handle the administration of the routing data. There are subprograms to partition the road data, to build a Network Data Model (NDM) network using the road data, to generate user data for trucking and turn restrictions, and to dump and validate the routing engine data and user data.

- Logging Administration Operations
- Network Data Model (NDM) Network Administration
- Routing Engine Data
- User Data
- Other Functions and Procedures

**Parent topic:** [Supplementary Information](spatial-supplementary-information.md)

### D.1 Logging Administration Operations

The routing engine logs all of its administration functions to either a specified log file or to a default log file. All administrative logs are written to the directory described by the Oracle directory object SDO_ROUTER_LOG_DIR.

The SDO_ROUTER_LOG_DIR directory must exist; and both the MDSYS and routing engine schema must have the privileges to read and write to this directory from both PL/SQL and Java.

The following subprograms are related to logging administration operations.

- CREATE_SDO_ROUTER_LOG_DIR Procedure
- VALIDATE_SDO_ROUTER_LOG_DIR Procedure

**Parent topic:** Routing Engine Administration

#### D.1.1 CREATE_SDO_ROUTER_LOG_DIR Procedure

Syntax:

    SDO_ROUTER_PARTITION.CREATE_SDO_ROUTER_LOG_DIR(
      ROUTER_SCHEMA IN VARCHAR2,
      NEW_DIR_PATH  IN VARCHAR2 DEFAULT NULL);

The CREATE_SDO_ROUTER_LOG_DIR procedure must be run from an account that has the Oracle privileges to create directory objects and grant privileges to other database users. Because this procedure grants privileges to the routing engine and MDSYS schemas, it cannot be run from either of these schemas.

The ROUTER_SCHEMA parameter must be specified and must be a valid schema containing the routing engine data.

The NEW_DIR_PATH parameter is an optional parameter. If the directory path is not specified, a valid SDO_ROUTER_LOG_DIR Oracle directory must already exist in the database. If it does not, an exception is raised. If the directory path is specified, a new SDO_ROUTER_LOG_DIR Oracle directory is created. If SDO_ROUTER_LOG_DIR had already been defined, the new definition replaces the old definition.

After the directory is created, read/write access is granted to the routing engine and MDSYS schemas from both PL/SQL and Java.

In previous versions of the routing engine, users ran the individual steps to create the directory and grant the privileges. This is no longer advised. Use of the CREATE_SDO_ROUTER_LOG_DIR procedure is now the recommended way to manage the Oracle directory needed by the routing engine.

**Parent topic:** Logging Administration Operations

#### D.1.2 VALIDATE_SDO_ROUTER_LOG_DIR Procedure

Syntax:

    SDO_ROUTER_PARTITION.VALIDATE_SDO_ROUTER_LOG_DIR(
      LOG_FILE_NAME IN VARCHAR2 := 'sdo_router_partition.log');

The VALIDATE_SDO_ROUTER_LOG_DIR procedure should be run from both the routing engine and MDSYS schema.

The LOG_FILE_NAME parameter is the name of the log file to open and attempt to write to. You can specify a name or use the default log file, `sdo_router_partition.log`.

If the log file does not exist, it is created and opened in the SDO_ROUTER_LOG_DIR directory. If the log file does exist, it is reopened. The validation procedure attempts to write to the log file from both PL/SQL and Java, and then closes the log file.

If the directory does not exist or if PL/SQL and/or Java fail to write to the log file, an exception is thrown.

**Parent topic:** Logging Administration Operations

### D.2 Network Data Model (NDM) Network Administration

The Oracle Routing Engine requires an Oracle Spatial and Graph network data model (NDM) network, built on the routing engine data, to process route requests and to generate responses.

- CREATE_ROUTER_NETWORK Procedure
- DELETE_ROUTER_NETWORK Procedure
- Network Creation Example

**Parent topic:** Routing Engine Administration

#### D.2.1 CREATE_ROUTER_NETWORK Procedure

Syntax:

    SDO_ROUTER_PARTITION.CREATE_ROUTER_NETWORK(
      LOG_FILE_NAME IN VARCHAR2 := 'sdo_router_partition.log',
      NETWORK_NAME IN VARCHAR2 := 'ROUTER_NETWORK');

The CREATE_ROUTER_NETWORK procedure must be run from a routing engine schema that contains routing engine Oracle Data Format (ODF) data.

The LOG_FILE_NAME parameter is the name of the log file written during network creation. This log file is created in the SDO_ROUTER_LOG_DIR directory. You can choose to log network creation in its own log file or write to the default partitioning log file, `sdo_router_partition.log`.

The NETWORK_NAME parameter names the network being created. The name of the network is at the discretion of the user. Oracle recommends including the country code and data version in the name for clarity. For example, for North American data released in the first quarter of 2012 a suitable network name would be ROUTER_NA_Q112.

Creating a network using a name of an already existing network simply replaces the old network with the new network. This is not recommended. The old network should be deleted first (using the DELETE_ROUTER_NETWORK Procedure), then the new network created.

**Parent topic:** Network Data Model (NDM) Network Administration

#### D.2.2 DELETE_ROUTER_NETWORK Procedure

Syntax:

    SDO_ROUTER_PARTITION.DELTE_ROUTER_NETWORK(
      LOG_FILE_NAME IN VARCHAR2 := 'sdo_router_partition.log',
      NETWORK_NAME  IN VARCHAR2 := 'ROUTER_NETWORK',
      LOG_DELETE    IN BOOLEAN DEFAULT TRUE);

The DELETE_ROUTER_NETWORK procedure must be run from a routing engine schema, and a network matching the network name parameter must exist within the schema.

The LOG_FILE_NAME parameter is the name of the log file written during network deletion. This log file is created in the SDO_ROUTER_LOG_DIR directory. You can choose to log network deletion in its own log file or write to the default partitioning log file, `sdo_router_partition.log`.

The NETWORK_NAME parameter is name of the network being deleted. If a network of this name does not exist, an exception is thrown and an error message is written to the log file.

The LOG_DELETE parameter controls whether the delete operation is logged to the log file. This parameter is used primarily for debugging.

**Parent topic:** Network Data Model (NDM) Network Administration

#### D.2.3 Network Creation Example

This section describes the steps for creating a sample NDM network for routing engine use.

1.  Validate the routing engine log directory in the routing engine schema. SDO_ROUTER_LOG_DIR must exist and have the correct privileges. Log in to the routing engine schema and execute the following statement:

        EXECUTE SDO_ROUTER_PARTITION.VALIDATE_ROUTER_LOG_DIR(
            'validate_log.log');

    When validation completes successfully, the `validate_log.log` file should contain the following messages:

        [INFO] PLSQL logging OK (ROUTER_SCHEMA)
        [INFO] Java logging OK (ROUTER_SCHEMA)
        [INFO] PLSQL logging OK (MDSYS)
        [INFO] Java logging OK (MDSYS)

2.  Validate the routing engine log directory in the MDSYS schema. SDO_ROUTER_LOG_DIR must exist and have the correct privileges. Log in to the MDSYS schema and execute the same statement as is step 1.

3.  In the routing engine schema, use the following query to find the name of any existing networks:

        SELECT SUBSTR(view_name, 0, LENGTH(view_name)-7) Network_Name
         FROM user_views
         WHERE view_name LIKE '%PBLOB$';

    If no results are returned, go to step 5. If a result similar to the following is returned, go to the next step to delete the network before creating a new network.

        NETWORK_NAME
        ------------
        <any-network-name>

4.  Use the DELETE_NETWORK procedure to delete an existing network. For example, if the existing network is named ROUTER_NA_Q112:

        EXECUTE SDO_ROUTER_PARTITION.DELETE_ROUTER_NETWORK(
            'delete_net.log', 'ROUTER_NA_Q112');

    When deletion completes successfully, the `delete_net.log` file should contain the following message:

        INFO: deleting the Routeserver network: ROUTER_NA_Q112

5.  Use the CREATE_ROUTER_NETWORK procedure to build a new network. For example:

        EXECUTE SDO_ROUTER_PARTITION.CREATE_ROUTER_NETWORK(
            'create_net.log', 'ROUTER_NA_112');

    When the create operation completes successfully, the `create_net.log` file should contain the following messages:

        INFO: creating the Routeserver network: ROUTER_NA_Q112
        INFO: rebuild edge table statistics
              creating views
              generating metadata

**Parent topic:** Network Data Model (NDM) Network Administration

### D.3 Routing Engine Data

The routing engine uses routing engine data and user data. The routing engine data is stored in the EDGE, NODE, SIGN_POST, and PARTITION tables.

The routing engine data models a road network as a directed graph of nodes and edges. Partitioning breaks this road network into 2\*\*N (2<sup>N</sup>) subgraphs (local partitions) and one highway partition. The nodes of the road network are partitioned topologically, so each local partition contains the same number of nodes. Each node in the network is in one and only one partition. An edge can be entirely within a partition, an internal edge, or a bridge two partitions (that is, a boundary edge). The partitions are stored in the database as BLOBs, so they can easily be read into and removed from a cache. This allows the routing engine to operate without needing the entire road network to be in memory.

Partitions 1 through N, local partitions, are all roughly the same size. Local partitions are read into the cache as needed when computing a route. These partitions remain in the cache until the cache is full, at which point the least used partitions are swapped out to make room for the partitions needed to compute the current route.

Partition 0 (zero), the highway partition, differs from local partitions in two respects:

- It is not a topological partition of the road network. Instead, it is a subgraph of the road network containing only highway information. Because of this, the highway partition is much larger than a local partition.

- It is read into the cache at routing engine start up and remains resident.

The road network is partitioned in three phases. The first phase partitions the data, computing the number of partitions needed and which partitions contain which nodes and edges. The second phase converts these partitions into BLOBs and writes them to the database. The final phase rebuilds the routing engine network, partitions any user data, and writes the user data BLOBs to the database.

Routing engine data is versioned. During the third phase of partitioning the routing engine version is written to the SDO_ROUTER_DATA_VERSION table and becomes the data version for this data set. If the data set is exported for use in another routing engine schema, this new routing engine's version must be compatible with the data version of the data set.

Routing engine data is provided by data vendors in the Oracle Data Format (ODF) and is already partitioned. Generally, there is no need for a customer to repartition the data. However, there may be cases, such as when performance testing different partition sizes or merging data sets, where you may want to repartition the routing engine data.

**Note:**

Repartitioning routing engine data can be a very time and resource intensive operation. Depending on the hardware being used, repartitioning a large data set, such as North America or the European Union, can easily run for a day or more.

- PARTITION_ROUTER Procedure
- CLEANUP_ROUTER Procedure
- DUMP_PARTITIONS Procedure
- VALIDATE_PARTITIONS Procedure
- GET_VERSION Procedure
- Routing Engine Data Examples

**Parent topic:** Routing Engine Administration

#### D.3.1 PARTITION_ROUTER Procedure

Syntax:

    SDO_ROUTER_PARTITION.PARTION_ROUTER(
        LOG_FILE_NAME IN VARCHAR2 := 'sdo_router_partition.log',
        MAX_V_NO      IN NUMBER DEFAULT 10000,
        DRIVING_SIDE  IN VARCHAR2 := 'R',
        NETWORK_NAME  IN VARCHAR := 'ROUTER_NETWORK',
        MAX_MEMORY    IN NUMBER := 1.75,
        CLEANUP       IN BOOLEAN DEFAULT TRUE,
        USE_SECUREFILES           IN BOOLEAN DEFAULT TRUE,
        GENERATE_11G_RESTRICTIONS IN BOOLEAN DEFAULT TRUE);

The PARTITION_ROUTER procedure must be run from a routing engine schema that contains routing engine Oracle Data Format data. This procedure partitions the road network and creates the PARTITION table containing the routing engine data in BLOB format.

The LOG_FILE_NAME parameter specifies the name of the log file written during routing engine partitioning. This log file is created in the SDO_ROUTER_LOG_DIR directory. Users can choose a log file name or use the default partitioning log file sdo_router_partition.log.

The MAX_V_NO parameter specifies the maximum number of nodes allowed in a partition. There must be at least (MAX_V_NO+1) nodes in the NODE table.

The DRIVING_SIDE parameter is a legacy parameter. Its only use was to generate Release 11g turn restrictions. Valid values are R (right side) and L (left side).The NETWORK_NAME parameter specifies the name of the routing engine network that is created during partitioning.

The MAX_MEMORY parameter specifies the maximum Java heap size, in gigabytes, available to the partitioning process. The default value of 1.75G is enough for most data sets. This parameter only needs to be adjusted when partitioning data sets that are much smaller or much larger than normal.

The CLEANUP parameter is used for debugging. By default, all of the intermediate tables created during the partitioning of the routing engine data are cleaned up. If there is problem while partitioning, leaving these tables in place (specifying CLEANUP=\>FALSE) can provide substantial debugging information.

The USE_SECUREFILES parameter lets you create the routing engine's BLOBs in either BASICFILE or SECUREFILE format. Oracle recommends using the SECUREFILE format.

The GENERATE_11G_RESTRICTIONS parameter controls the generation of Release 11g turn restriction data. In Oracle Database Release 11g, basic turn restrictions were implemented and stored in the PARTITION table. In Oracle Database Release 12c, turn restrictions are expanded and are stored in a user data table, ROUTER_TURN_RESTRICTION_DATA. To allow data providers to ship data partitioned under Release 12c to users still using a Release 11g Route Server, both types of turn restrictions are generated by default. When repartitioning data under Oracle Release 12c, for a Release 12c Route Server, you may set this parameter to FALSE.

**Parent topic:** Routing Engine Data

#### D.3.2 CLEANUP_ROUTER Procedure

Syntax:

    SDO_ROUTER_PARTITION.CLEANUP_ROUTER(
        ALL_TABLES IN BOOLEAN DEFAULT TRUE);

The CLEANUP_ROUTER procedure resets the routing engine's state, ensuring that all the tables and indexes are in good order and all intermediate tables are deleted. This is useful if partitioning fails or if partitioning completed successfully with the CLEANUP flag set to FALSE.

The ALL_TABLES parameter controls what is reset. When set to FALSE, the routing engine is reset to a stable state but leaves the intermediate tables for debugging. This can be useful if partitioning failed. When set to TRUE, the routing engine is reset to a stable state and all intermediate tables used in partitioning are deleted. This can be useful when cleaning up after a successful PARTITION_ROUTER Procedure that was run with the CLEANUP parameter set to FALSE.

**Parent topic:** Routing Engine Data

#### D.3.3 DUMP_PARTITIONS Procedure

Syntax:

    DUMP_PARTITIONS(
        LOG_FILE_NAME IN VARCHAR2 := 'sdo_router_partition.log',
        START_PID     IN NUMBER DEFAULT 0,
        END_PID       IN NUMBER DEFAULT -1,
        VERBOSE       IN BOOLEAN DEFAULT FALSE);

The DUMP_PARTITIONS procedure dumps the contents of routing engine data partition BLOBs. This procedure unpacks a BLOB, formats the data, and writes it to a log file. A single running of this procedure can dump a single partition or a contiguous range of partitions. This range is defined from START_PID to END_PID, inclusive. The default is to dump all partitions. A non-contiguous range of partitions cannot be dumped in a single call.

The LOG_FILE_NAME parameter is the name of the log file written when dumping routing engine partitions. This log file is created in the SDO_ROUTER_LOG_DIR directory. You can choose a log file name or write to the default partitioning log file `sdo_router_partition.log`.

The START_PID parameter is the ID of the first partition to dump. The default START_PID is 0. The START_PID must be less than or equal to END_PID.

The END_PID parameter is the ID of the last partition to dump. The default END_PID is -1, which is converted to the highest partition ID in the data set. If the start and end PID values are equal, a single partition is dumped. If END_PID is less than START_PID, an error message is written to the log.

The VERBOSE parameter controls what data is dumped. The default value of FALSE dumps a summary of the partition information, including, the number of node and edges and the size of the BLOB. If this parameter is TRUE, in addition to the summary, all the information describing all the nodes and edges in the partition is dumped.

**Parent topic:** Routing Engine Data

#### D.3.4 VALIDATE_PARTITIONS Procedure

Syntax:

    VALIDATE_PARTITIONS(
        LOG_FILE_NAME IN VARCHAR2 := 'sdo_router_partition.log',
        START_PID     IN NUMBER DEFAULT 0,
        END_PID       IN NUMBER DEFAULT -1,
        VERBOSE       IN BOOLEAN DEFAULT FALSE);

The VALIDATE_PARTITIONS procedure validates the contents of routing engine data partition BLOBs. Validating all the partitions in a large dataset can take some time to run, but it is the fastest way to read every byte in every partition to ensure that the partitions are ready to be used for routing. Validation only needs to be run if you suspect that there may be a problem with the partitions. If validation is run, Oracle recommends running the initial validation on all partitions with the VERBOSE flag set to FALSE. If a problem is found, then rerun the validation on the problem partitions with VERBOSE set to true.

The LOG_FILE_NAME parameter is the name of the log file written while validating the routing engine data partitions. This log file is created in the SDO_ROUTER_LOG_DIR directory. You can choose a log file name or write to the default partitioning log file `sdo_router_partition.log`.

The START_PID parameter is the ID of the first partition to validate. The default START_PID is 0. The START_PID must be less than or equal to END_PID.

The END_PID parameter is the ID of the last partition to validate. The default END_PID is -1, which is converted to the highest partition ID in the data set. If the start and end PID values are equal, a single partition is validated. If END_PID is less than START_PID, an error message is written to the log.

The VERBOSE parameter controls the level of detail of the validation messages. The default value of FALSE simply logs whether a partition passed or failed validation. If this parameter is TRUE, the validation of each element in the BLOB is logged.

**Parent topic:** Routing Engine Data

#### D.3.5 GET_VERSION Procedure

Syntax:

    GET_VERSION(
        LOG_FILE_NAME IN VARCHAR2 := 'sdo_router_partition.log');

The GET_VERSION procedure queries the SDO_ROUTER_DATA_VERSION table to get the routing engine data version and writes the result to the log file. (An an alternative, you can use SQL to query the SDO_ROUTER_DATA_VERSION table.)

The LOG_FILE_NAME parameter is the name of the log file where the routing engine data version is written. This log file is created in the SDO_ROUTER_LOG_DIR directory. You can choose a log file name or write to the default partitioning log file `sdo_router_partition.log`.

**Parent topic:** Routing Engine Data

#### D.3.6 Routing Engine Data Examples

This section contains examples of the following operations.

- Partitioning a Small Data Set
- Partitioning a Full Data Set
- Dumping the Contents of a Partition
- Validating the Contents of a Partition
- Querying the Routing Engine Data Version

**Parent topic:** Routing Engine Data

##### D.3.6.1 Partitioning a Small Data Set

Example D-1 shows partitioning of a small data set. The data set in this example is the road network data for a radius of 100 miles around the center of San Francisco. This data set contains about 520,000 nodes and 1,200,00 edges. To partition the routing engine data, execute the statement from within the routing engine schema.

Example D-1 Partitioning a Small Data Set

    EXECUTE SDO_ROUTER_PARTITION.PARTITION_ROUTER(
       'sdo_router_partition.log', 1000, 'R',
       'ROUTER_SF_NET', .75, FALSE, FALSE, FALSE);

    ******** Beginning SDO Router partitioning
    ** Schema: ROUTER_SF_SCHEMA
    ** Logfile location:/scratch/logs/sdo_router_partition.log
    ** Nodes per partition: 1000
    ** Driving side: R
    ** Router network name: ROUTER_SF_NET
    ** Max JVM Memory Size: .75GB (805306368 bytes)
    ** Cleanup temporary files: FALSE
    ** BLOBs stored in BASICFILE format
    ** Generating 11g turn restrictions: FALSE
    [This header is followed by extensive logging of the partitioning process.]

This example produces 1025 partitions, 1 highway partition, and 1024 local partitions. There are, on average, 516 nodes per partition. The driving side is set but is not used because Release 11g turn restrictions were not requested. The Java maximum heap size was set to three quarters of a gigabyte, more than enough to partition such a small data set. The partition BLOBs were written in Basicfile format, and when the partitioning completed the intermediate tables were not cleaned up.

To clean up the intermediate tables left behind by partitioning, enter the following:

    EXECUTE SDO_ROUTER_PARTITION.CLEANUP_ROUTER()

**Parent topic:** Routing Engine Data Examples

##### D.3.6.2 Partitioning a Full Data Set

Example D-2 shows partitioning of a full data set. The data set for this example is the entire North American road network. This data set contains about 30 million nodes and 74 million edges. To partition the routing engine data, execute the statement from within the routing engine schema.

Example D-2 Partitioning a Full Data Set

    EXECUTE SDO_ROUTER_PARTITION.PARTITION_ROUTER(
       'sdo_router_partition.log, 32000, 'R', 'ROUTER_NA_NET');

    ******** Beginning SDO Router partitioning
    ** Schema: ROUTER_NA_SCHEMA
    ** Logfile location:/scratch/logs/sdo_router_partition.log
    ** Nodes per partition: 32000
    ** Driving side: R
    ** Router network name: ROUTER_NA_NET
    ** Max JVM Memory Size: 1.75GB (1879048192 bytes)
    ** Cleanup temporary files: TRUE
    ** BLOBs stored in SECUREFILE format
    ** Generating 11g turn restrictions: TRUE
    [This header is followed by extensive logging of the partitioning process.]
    ++ Partitioning a data set of this size is time and resource intensive ++


This example produces 1025 partitions, 1 highway partition, and 1024 local partitions. There are, on average, 29443 nodes per partition. The driving side is set to 'Right Side' and is used to generate the requested Oracle 11g turn restrictions. The default Java heap size of 1.75 gigabytes is used. All routing engine data and user data BLOBs are stored in SECUREFILE format, and all intermediate tables are cleaned up after the successful partitioning.

**Parent topic:** Routing Engine Data Examples

##### D.3.6.3 Dumping the Contents of a Partition

Example D-3 shows a dump of partitions 0 through 3 with the default VERBOSE value (FALSE) from the San Francisco data set. Note the BLOB size difference between the highway and local partitions. Also note that the highway partition is completely self-contained so there are no outbound edges. Local partitions have outgoing edges that connect them to other local partitions.

Example D-3 Dumping the Contents of a Partition (VERBOSE = FALSE)

    EXEC SDO_ROUTER_PARTITION.DUMP_PARTITIONS(
       'dump_part0-3.log', 0, 3);

    ******** Beginning partition dump
    ** Logfile location: /scratch/logs/dump_part0-3.log
    ** Routeserver data version: 12.1.0.2.1
    ** Start partition id: 0
    ** End partition id: 3
    ** Verbose mode: FALSE
    [INFO] Starting dump of partition 0
      Number of Nodes: 19392
      Number of Nonboundary Edges: 22706
      Number of Outgoing Boundary Edges: 0
      Number of Incoming Boundary Edges: 0
      Stored Partition ID: 0
      Blob Length: 1748332

    [INFO] Starting dump of partition 1
      Number of Nodes: 516
      Number of Nonboundary Edges: 1190
      Number of Outgoing Boundary Edges: 49
      Number of Incoming Boundary Edges: 49
      Stored Partition ID: 1
      Blob Length: 81372

    [INFO] Starting dump of partition 2
      Number of Nodes: 516
      Number of Nonboundary Edges: 1099
      Number of Outgoing Boundary Edges: 68
      Number of Incoming Boundary Edges: 68
      Stored Partition ID: 2
      Blob Length: 78388
    [INFO] Starting dump of partition 3
      Number of Nodes: 516
      Number of Nonboundary Edges: 1101
      Number of Outgoing Boundary Edges: 60
      Number of Incoming Boundary Edges: 60
      Stored Partition ID: 3
      Blob Length: 77756

Example D-4 Dumping the Contents of a Partition (VERBOSE = TRUE)

Example D-4 shows a dump of partition 8 with VERBOSE set to TRUE from the San Francisco data set. Note that the outbound edges log the partition ID where they terminate, and the inbound edges log the partition ID where they originate.

    EXEC SDO_ROUTER_PARTITION.DUMP_PARTITIONS(
       'dump_part8.log', 8, 8, TRUE);

    ******** Beginning partition dump
    ** Logfile location:/scratch/logs/dump_part8.log
    ** Routeserver data version: 12.1.0.2.1
    ** Start partition id: 8
    ** End partition id: 8
    ** Verbose mode: TRUE
    [INFO] Starting dump of partition 8
      Number of Nodes: 517
      Number of Non-boundary Edges: 1145
      Number of Outgoing Boundary Edges: 37
      Number of Incoming Boundary Edges: 37
      Stored Partition ID: 8
      Blob Length: 77957

      Node information for partition 8:
        Node ID/X/Y/Highway: 84096388/-120.50809/37.98399/false
        In Edges(3): -120862233, -120862227, 120862232
        Out Edges(3): -120862232, 120862227, 120862233
        *******************************
        Node ID/X/Y/Highway: 84098023/-120.4882/37.99961/true
        In Edges(3): -127829801, -120428259, 776737023
        Out Edges(3): -776737023, 120428259, 127829801
        *******************************
    *** Node information for the other 515 nodes...

      Non-boundary Edge information for partition 8:
      Internal Edges(1145):
        Edge ID/Start Node ID/End Node ID: 910681077/942981443/206194644
        Length/Speed Limit/Function Class: 130.3/5/5
        *******************************
        Edge ID/Start Node ID/End Node ID: -105461005/206194651/206194644
        Length/Speed Limit/Function Class: 229.93/11/5
        *******************************
    *** Edge information for the other 1143 internal edges...

       Outbound Boundary Edges(37):
        Edge ID/Start Node ID/End Node ID: -724019630/253265936/810705655
        End Node Partition ID/Length: 7/511.07
        Speed Limit/Function Class: 26/2
        *******************************
        Edge ID/Start Node ID/End Node ID: -105462459/252152310/206193109
        End Node Partition ID/Length: 7/814.68
        Speed Limit/Function Class: 11/5
        *******************************
    *** Edge information for the other 35 outbound boundary edges...

       Inbound Boundary Edges(37):
        Edge ID/Start Node ID/End Node ID: 724019630/810705655/253265936
        Start Node Partition ID/Length: 7/511.07
        Speed Limit/Function Class: 26/2
        *******************************
        Edge ID/Start Node ID/End Node ID: 105462459/206193109/252152310
        Start Node Partition ID/Length: 7/814.68
        Speed Limit/Function Class: 11/5
        *******************************
    *** Edge information for the other 35 inbound boundary edges...

**Parent topic:** Routing Engine Data Examples

##### D.3.6.4 Validating the Contents of a Partition

Example D-5 shows validation of the contents of all the partitions in the data set with the default VERBOSE value (FALSE).

Example D-5 Validating the Contents of Partitions (VERBOSE = FALSE)

    EXEC SDO_ROUTER_PARTITION.VALIDATE_PARTITIONS(
       'validate_all_partitions.log');

    ******** Beginning partition validation
    ** Logfile location:/scratch/logs/validate_all_partitions.log
    ** Routeserver data version: 12.1.0.2.1
    ** Start partition id: 0
    ** End partition id: 1024
    ** Verbose mode: FALSE
    [INFO] Starting validation of partition 0
    [INFO] Starting validation of partition 1
    [INFO] Starting validation of partition 2
    …
    [INFO] Starting validation of partition 1022
    [INFO] Starting validation of partition 1023
    [INFO] Starting validation of partition 1024
    [INFO] Partition validation complete

Example D-6 Validating the Contents of Partitions (VERBOSE = TRUE)

Example D-6 shows validation of the contents of partitions 7 and 8 with VERBOSE set to TRUE.

    EXEC SDO_ROUTER_PARTITION.VALIDATE_PARTITIONS(
       'validate_part7-8.log', 7, 8, TRUE);

    ******** Beginning partition validation
    ** Logfile location: /scratch/logs/validate_part7-8.log
    ** Routeserver data version: 12.1.0.2.1
    ** Start partition id: 7
    ** End partition id: 8
    ** Verbose mode: TRUE
    [INFO] Starting validation of partition 7
      Header node count: OK
      Header edge count: OK
      BLOB partition id: OK
      BLOB length: OK
      BLOB node count: OK
      BLOB information for 516 nodes: OK
      BLOB information for 1154 internal edges: OK
      BLOB information for 66 outbound boundary edges: OK
      BLOB information for 65 inbound boundary edges: OK

    [INFO] Starting validation of partition 8
      Header node count: OK
      Header edge count: OK
      BLOB partition id: OK
      BLOB length: OK
      BLOB node count: OK
      BLOB information for 517 nodes: OK
      BLOB information for 1145 internal edges: OK
      BLOB information for 37 outbound boundary edges: OK
      BLOB information for 37 inbound boundary edges: OK

    [INFO] Partition validation complete

**Parent topic:** Routing Engine Data Examples

##### D.3.6.5 Querying the Routing Engine Data Version

Example D-7 queries the routing engine data version number, writing the result to a log file.

    SELECT * FROM sdo_router_data_version;

Example D-7 Querying the Routing Data Version

    EXEC SDO_ROUTER_PARTITION.GET_VERSION('version.log');

    INFO: Routeserver data version: 12.1.0.2.1

Alternatively, you could use the following SQL query to get the routing engine data version:

**Parent topic:** Routing Engine Data Examples

### D.4 User Data

User data models restrictions on the road network. Currently, there are two kinds of user data in the routing engine: restricted driving maneuvers (turn restrictions) and trucking user data.

User data is versioned. When user data is partitioned, the routing engine data version from the SDO_ROUTER_DATA_VERSION table is stored in the user data BLOBs. When user data is brought into the cache, the version stored in the user data partition must be compatible with the version in the SDO_ROUTER_DATA_VERSION table.

Partitioning user data is generally a very fast operation. It can be done as part of the partitioning the routing engine data or, if the routing engine data is already partitioned, as a standalone operation. In both cases the user data partitioning uses the partitioned routing engine data as a guide, substantially speeding up the partitioning operation.

The number of user data partitions is equal to or less than the number of routing engine data partitions. If there is no user data associated with a routing engine data partition, then no user data partition is produced. User data local partitions move into and out of the cache with their associated routing engine data partition. The user data highway partition is loaded at routing engine startup and remains resident in the cache.

In Release 12c the restricted driving maneuver user data is part of the routing engine ODF data shipped by data vendors. Trucking user data is not shipped with the routing engine ODF data and must be purchased separately. When a Release 12c or later routing engine starts, it detects and uses any available user data. All versions of the routing engine before Release 12c do not detect the user data and will only use routing engine data to compute the routes.

- Restricted Driving Maneuvers User Data
- CREATE_TURN_RESTRICTION_DATA Procedure
- DUMP_TURN_RESTRICTION_DATA Procedure
- CREATE_TRUCKING_DATA Procedure
- DUMP_TRUCKING_DATA Procedure
- CREATE_TIMEZONE_DATA Procedure
- DUMP_TIMEZONE_DATA Procedure
- User Data Examples

**Parent topic:** Routing Engine Administration

#### D.4.1 Restricted Driving Maneuvers User Data

A restricted driving maneuver can be as simple as not allowing movement from one edge to another, such as a simple turn restriction that does not allow a left turn. Or it might be a highly complex maneuver involving many edges, such as a no U-turn restriction on a road divided with a median where there is a start edge, an edge over the median, and the edge on the road going the other direction.

The routing engine uses three tables for restricted driving maneuvers. The first two tables, ROUTER_NAV_STRAND and ROUTER_CONDITION contain the raw data to build the restricted maneuvers user data.

The final table, ROUTER_TURN_RESTRICTION_DATA, contains the partitioned restricted maneuver user data stored in BLOB format. Partitioning the restricted maneuver data allows it to move in and out of the cache with the routing engine data of the same partition.

In Release 12c the restricted driving maneuver user data is part of the ODF data shipped by the data vendors. When a Release 12c routing engine starts, it detects and uses the turn restriction user data. If a Release 11grouting engine starts, it will not detect the user data and will only use routing engine data to compute the routes.

Because the restricted driving maneuver user data is part of the ODF data set, it is already partitioned. Generally, there is no reason to repartition this user data. However, if the routing engine data is repartitioned, the user data will also be repartitioned. It is also possible to repartition the turn restriction user data without having to repartition the routing engine data by re-creating the restricted driving maneuver user data.

**Parent topic:** User Data

#### D.4.2 CREATE_TURN_RESTRICTION_DATA Procedure

Syntax:

    SDO_ROUTER_PARTITION.CREATE_TURN_RESTRICTION_DATA(
        LOG_FILE_NAME IN VARCHAR2 := 'sdo_router_partition.log',
        CLEANUP       IN BOOLEAN DEFAULT TRUE);

The CREATE_TURN_RESTRICTION_DATA procedure must be run from a routing engine schema that contains the restricted driving maneuver raw data tables ROUTER_NAV_STRAND and ROUTER_CONDITION. This procedure partitions the restricted driving maneuver data and creates the ROUTER_TURN_RESTRICTION_DATA table containing the turn restriction user data in BLOB format. Turn restriction user data creation requires access to the data version so the SDO_ROUTER_DATA_VERSION table must exist in the routing engine schema.

The LOG_FILE_NAME parameter is the name of the log file written during turn restriction generation. This log file is created in the SDO_ROUTER_LOG_DIR directory. You can choose a log file name or use the default partitioning log file `sdo_router_partition.log`.

The CLEANUP parameter is used for debugging. By default, all of the intermediate tables created during turn restriction generation are cleaned up. If there is problem with turn restriction generation, leaving these tables in place can provide substantial debugging information.

**Parent topic:** User Data

#### D.4.3 DUMP_TURN_RESTRICTION_DATA Procedure

Syntax:

    SDO_ROUTER_PARTITION.DUMP_TURN_RESTRICTION_DATA(
        LOG_FILE_NAME IN VARCHAR2 := 'sdo_router_partition.log',
        START_PID     IN NUMBER DEFAULT 0,
        END_PID       IN NUMBER DEFAULT -1,
        DUMP_SOFT_RESTRICTIONS IN BOOLEAN DEFAULT FALSE);

The DUMP_TURN_RESTRICTION_DATA procedure dumps the contents of the turn restriction user data partition BLOBs. This procedure unpacks a BLOB, formats the data, and writes it to a log file. A single call to this procedure can dump a single partition or a contiguous range of partitions. This range is defined from START_PID to END_PID, inclusive. The default is to dump all partitions. A non-contiguous range of partitions cannot be dumped in a single call.

The LOG_FILE_NAME parameter specifies the name of the log file written when dumping turn restriction user data partitions. This log file is created in the SDO_ROUTER_LOG_DIR directory. You can choose a log file name or write to the default partitioning log file `sdo_router_partition.log`.

The START_PID parameter is the ID of the first partition to dump. The default START_PID is 0. The START_PID must be less than or equal to END_PID.

The END_PID parameter is the ID of the last partition to dump. The default END_PID is -1, which is converted to the highest partition ID in the data set. If the start and end PID values are equal, a single partition is dumped. If END_PID is less than START_PID, an error message is written to the log.

The DUMP_SOFT_RESTRICTIONS parameter controls how the turn restriction data is dumped. In turn restrictions that have more than two edges, a soft restriction is a series of edges that partially describe the turn restriction. This is a debugging parameter and should generally be left set to its default value, FALSE.

**Parent topic:** User Data

#### D.4.4 CREATE_TRUCKING_DATA Procedure

Syntax:

    SDO_ROUTER_PARTITION.CREATE_TRUCKING_DATA(
        LOG_FILE_NAME IN VARCHAR2 := ' sdo_router_partition.log',
        CLEANUP       IN BOOLEAN DEFAULT TRUE);

The CREATE_TRUCKING_DATA procedure must be run from a routing engine schema that contains the raw trucking data table ROUTER_TRANSPORT. This procedure partitions the trucking data and creates the ROUTER_TRUCKING_DATA table containing the trucking user data in BLOB format. Trucking user data creation requires access to the data version, so the SDO_ROUTER_DATA_VERSION table must exist in the routing engine schema.

The LOG_FILE_NAME parameter is the name of the log file written during trucking restriction generation. This log file is created in the SDO_ROUTER_LOG_DIR directory. You can choose a log file name or use the default partitioning log file` sdo_router_partition.log`.

The CLEANUP parameter is used for debugging. By default, all of the intermediate tables created during trucking restriction generation are cleaned up. If there is problem with trucking restriction generation, leaving these tables in place can provide substantial debugging information.

**Parent topic:** User Data

#### D.4.5 DUMP_TRUCKING_DATA Procedure

Syntax:

    SDO_ROUTER_PARTITION.DUMP_TRUCKING_DATA(
        LOG_FILE_NAME    IN VARCHAR2 := ' sdo_router_partition.log',
        START_PID        IN NUMBER DEFAULT 0,
        END_PID          IN NUMBER DEFAULT -1,
        SKIP_UNSUPPORTED IN BOOLEAN DEFAULT TRUE);

The DUMP_TRUCKING_DATA procedure dumps the contents of the trucking restriction user data partition BLOBs. This procedure unpacks a BLOB, formats the data, and writes it to a log file. A single call to this procedure can dump a single partition or a contiguous range of partitions. This range is defined from START_PID to END_PID, inclusive. The default is to dump all partitions. A non-contiguous range of partitions cannot be dumped in a single call.

The LOG_FILE_NAME parameter specifies the name of the log file written when dumping trucking restriction user data partitions. This log file is created in the SDO_ROUTER_LOG_DIR directory. You can choose a log file name or write to the default partitioning log file `sdo_router_partition.log`.

The START_PID parameter is the ID of the first partition to dump. The default START_PID is 0. The START_PID must be less than or equal to END_PID.

The END_PID parameter is the ID of the last partition to dump. The default END_PID is -1, which is converted to the highest partition ID in the data set. If the start and end PID values are equal, a single partition is dumped. If END_PID is less than START_PID, an error message is written to the log.

The SKIP_UNSUPPORTED parameter controls how the trucking restriction data is dumped. The user data contains a number of restrictions included for future work but not currently supported. Setting SKIP_UNSUPPORTED to TRUE (the default) only dumps currently supported trucking restrictions. Setting SKIP_UNSUPPORTED to FALSE causes all trucking restrictions to be dumped.

**Parent topic:** User Data

#### D.4.6 CREATE_TIMEZONE_DATA Procedure

Syntax:

    SDO_ROUTER_PARTITION.CREATE_TIMEZONE_DATA(
        LOG_FILE_NAME IN VARCHAR2 := 'sdo_router_partition.log',
        CLEANUP       IN BOOLEAN DEFAULT TRUE);

The CREATE_TIMEZONE_DATA procedure creates the user data for the [ROUTER_TIMEZONE_DATA Table](routing-engine-concepts.md). It should also be run every time that the data is repartitioned.

The LOG_FILE_NAME parameter is the name of the log file written during the operation. This log file is created in the SDO_ROUTER_LOG_DIR directory. You can choose a log file name or use the default partitioning log file `sdo_router_partition.log`.

The CLEANUP parameter is used for debugging. By default, all of the intermediate tables created during the operation are cleaned up. If there is problem with the operation, leaving these tables in place can provide substantial debugging information.

**Parent topic:** User Data

#### D.4.7 DUMP_TIMEZONE_DATA Procedure

Syntax:

    SDO_ROUTER_PARTITION.DUMP_TIMEZONE_DATA(
        LOG_FILE_NAME    IN VARCHAR2 := ' sdo_router_partition.log',
        START_PID        IN NUMBER DEFAULT 0,
        END_PID          IN NUMBER DEFAULT -1);

The DUMP_TIMEZONE_DATA procedure dumps the contents of the time zone data partition BLOBs. This procedure unpacks a BLOB, formats the data, and writes it to a log file. A single call to this procedure can dump a single partition or a contiguous range of partitions. This range is defined from START_PID to END_PID, inclusive. The default is to dump all partitions. A non-contiguous range of partitions cannot be dumped in a single call.

The LOG_FILE_NAME parameter specifies the name of the log file written when dumping time zone user data partitions. This log file is created in the SDO_ROUTER_LOG_DIR directory. You can choose a log file name or write to the default partitioning log file `sdo_router_partition.log`.

The START_PID parameter is the ID of the first partition to dump. The default START_PID is 0. The START_PID must be less than or equal to END_PID.

The END_PID parameter is the ID of the last partition to dump. The default END_PID is -1, which is converted to the highest partition ID in the data set. If the start and end PID values are equal, a single partition is dumped. If END_PID is less than START_PID, an error message is written to the log.

**Parent topic:** User Data

#### D.4.8 User Data Examples

This section presents examples of operations involving user data. The data set in these examples is the road network data for a radius of 100 miles around the center of San Francisco. This data set contains about 520,000 nodes and 1,200,00 edges, including 82,000 edges with truck restrictions and 30,000 edges with restricted driving maneuvers.

- Rebuilding the Turn Restriction User Data
- Dumping All Hard Turn Restriction User Data BLOBs
- Rebuilding the Trucking User Data
- Dumping the Trucking User Data Restrictions
- Rebuilding the Time Zone User Data
- Dumping All Time Zone User Data BLOBs

**Parent topic:** User Data

##### D.4.8.1 Rebuilding the Turn Restriction User Data

Example D-8 rebuilds the turn restriction user data. Because cleanup is set to FALSE, the intermediate tables used to rebuild the turn restriction user data will not be deleted. (To delete these tables execute the SDO_ROUTER_PARTITION.CLEANUP_ROUTER Procedure.)

Example D-8 Rebuilding the Turn Restriction User Data

    EXEC SDO_ROUTER_PARTITION.CREATE_TURN_RESTRICTION_DATA('rebuild_turn_restriction_data.log', FALSE);

    ******** Begin generation of turn restriction user data
    ** Logfile location: /scratch/logs/rebuild_turn_restriction_data.log
    [INFO] Generating turn restriction user data for 995 partitions, data version (12.1.0.1.2)

    [INFO] SQL String: CREATE TABLE new_turn_restriction_data(partition_id NUMBER, num_edges NUMBER, turn_restriction_data BLOB) LOB(turn_restriction_data) STORE AS (STORAGE (INITIAL 512K NEXT 128K MAXEXTENTS UNLIMITED) CHUNK 32768 NOCACHE NOLOGGING)
    [INFO] ---- Writing 573 edges for partition 0
    [INFO] ---- Writing 16 edges for partition 1
    [INFO] ---- Writing 10 edges for partition 2

    *** Note that partition 3 contains no turn restriction user data

    [INFO] ---- Writing 8 edges for partition 4
    [INFO] ---- Writing 23 edges for partition 5
    [INFO] ---- Writing 39 edges for partition 6
    *** Many more Writing partition messages
    [INFO] ---- Writing 4 edges for partition 1023
    [INFO] ---- Writing 11 edges for partition 1024

    INFO: creating the final turn restriction user data table
    INFO: create index rtrud_p_idx on router_turn_restriction_data table
    ******** Completed generation of turn restriction user data

**Parent topic:** User Data Examples

##### D.4.8.2 Dumping All Hard Turn Restriction User Data BLOBs

Example D-9 dumps all of the hard turn restriction user data BLOBs. (Dumping soft restrictions produces much larger dump files and is only useful when debugging problems in the turn restrictions constraints.)

Example D-9 Dumping All Hard Turn Restriction User Data BLOBs

    EXEC SDO_ROUTER_PARTITION.DUMP_TURN_RESTRICTION_DATA('dump_all_turn_restrictions.log');

    ******** Beginning turn restriction dump
    ** Logfile location: /scratch/logs/dump_all_turn_restrictions.log
    ** Routeserver data version: 12.1.0.1.2                  (A)
    ** Start partition id: 0
    ** End partition id: 1024
    ** Dumping soft restrictions: FALSE

    Starting turn restriction dump for partition 0, blob length 19956 bytes
      Data version: 12.1.0.1.2
      Partition 0 has 573 edges with turn restrictions       (B)
        edge id -937799058 has 1 turn restrictions
          Restriction Type/Attributes: Hard/None
          AppliesTo(959): Trucks, Through Traffic, Taxies, Motorcycles,
                          Emergency Vehicles, Delivery Vehicles, Carpools,
                          Buses, Automobiles
          Subpath(1): 24501308
        *******************************
        edge id -936524317 has 2 turn restrictions           (C)
          Restriction Type/Attributes: Hard/None
          AppliesTo(943): Trucks, Through Traffic, Taxies, Motorcycles,
                          Delivery Vehicles, Carpools, Buses, Automobiles
          Subpath(1): -724922777
          -------
          Restriction Type/Attributes: Hard/None
          AppliesTo(959): Trucks, Through Traffic, Taxies, Motorcycles,
                          Emergency Vehicles, Delivery Vehicles, Carpools,
                          Buses, Automobiles
          Subpath(1): 936524317
        *******************************
        edge id -932185370 has 2 turn restrictions
          Restriction Type/Attributes: Hard/None
          AppliesTo(1023): All Vehicles
          Subpath(1): 836074944
          -------
          Restriction Type/Attributes: Hard/None
          AppliesTo(1023): All Vehicles
          Subpath(1): -24638792
        *******************************
        edge id 834380593 has 1 turn restrictions            (D)
          Restriction Type/Attributes: Hard/None
          AppliesTo(943): Trucks, Through Traffic, Taxies, Motorcycles,
                          Delivery Vehicles, Carpools, Buses, Automobiles
          Subpath(4): 112065672, -112065610, -112008660, -834380591
        *******************************

    *** Dump of the remaining restrictions in Partition 0
    Starting turn restriction dump for partition 1, blob length 520 bytes
      Partition 1 has 16 edges with turn restrictions        (E)
        edge id -806530190 has 1 turn restrictions
          Restriction Type/Attributes: Hard/None
          AppliesTo(703): Trucks, Taxies, Motorcycles, Emergency Vehicles,
                          Delivery Vehicles, Carpools, Buses, Automobiles
          Subpath(1): 120865027
        *******************************
    *** Dump of the remaining restrictions in Partition 1 through 1024

In Example D-9:

- (A): The standard user dump header contains the location of the log file and the parameters used in the dump. It also contains the routing engine data version as queried from the SDO_ROUTER_DATA_VERSION table. This data version must match the data version stored in the header of the partition 0 BLOB.

- (B): In the BLOB header section for the partition 0 BLOB, all turn restriction user data BLOB headers contain the partition ID, length of the BLOB in bytes, and number of edges with turn restrictions on them. The BLOB header for partition 0 also contains the user data version. This version must match the data version found in the SDO_ROUTER_DATA_VERSION table.

- (C): In the dump of the turn restrictions for edge -936524317., this edge has two simple turn restrictions associated with it. Both restrictions are simple turn restrictions that do not allow movement from the single edge in the subpath to edge -936524317. Also note the difference in the vehicles to which the restrictions apply: the first restriction does not apply to emergency vehicles, but the second restriction does apply to emergency vehicles.

- (D): Edge 834380593 has only one turn restriction, but the restriction being described is much more complicated than a simple turn. If the subpath immediately previous to edge 834380593 matches the subpath that starts at edge -834380591 and goes through edges -112008660, -112065610, 112065672 in precisely that order, then the maneuver is not allowed. If the subpath to the current edge is missing one of the listed subpath edges or if the edges in the subpath are in a different order, then the maneuver is allowed.

- (E): In the BLOB header for local partitions, all turn restriction user data BLOB headers contain the partition ID, length of the BLOB in bytes, and number of edges with turn restrictions on them.

**Parent topic:** User Data Examples

##### D.4.8.3 Rebuilding the Trucking User Data

Example D-10 rebuilds the trucking user data. Since cleanup is using the default value of TRUE the intermediate tables used to rebuild the turn restriction user data are deleted when the build completes.

Example D-10 Rebuilding the Trucking User Data

    EXEC SDO_ROUTER_PARTITION.CREATE_TRUCKING_DATA('rebuild_trucking_data.log');
    ******** Begin generation of trucking user data
    ** Logfile location:/scratch/logs/rebuild_trucking_data.log
    [INFO] Generating trucking user data for 974 partitions,
    data version (12.1.0.1.2)                                (A)

    [INFO] SQL String: CREATE TABLE new_trucking_data
    (partition_id NUMBER, num_edges NUMBER, trucking_data BLOB) LOB(trucking_data) STORE AS (STORAGE (INITIAL 512K NEXT 128K MAXEXTENTS UNLIMITED) CHUNK 32768 NOCACHE NOLOGGING)

    INFO: creating the final trucking user data table
    INFO: create index rtud_p_idx on router_trucking_data table
    ******** Completed generation of trucking user data

In Example D-10:

- (A): Note that there are only 974 partitions of trucking user data compared to the 1023 local partitions (see the output in Example D-9) of routing engine data. If a partition is missing in the user data output, this means there is no trucking data for the associated routing engine data partition.

**Parent topic:** User Data Examples

##### D.4.8.4 Dumping the Trucking User Data Restrictions

Example D-11 dumps the trucking user data restrictions. This example dumps the supported restrictions for partitions 0 through 25. In the dump, Main Type is type of restriction, Subtype is the reason for the restriction, and Value is the means to measure the restriction. For example, a height restriction is a Main Type, the Subtype can be a thing like Bridge or Tunnel or can be Unknown, and Value can be a measure (always metric) like meters for height and width or metric tons for weight. Value can also be 0 for some restrictions (for example legal restrictions) that cannot be physically measured.

Example D-11 Dumping the Trucking User Data Restrictions

    EXEC SDO_ROUTER_PARTITION.DUMP_TRUCKING_DATA('dump_trucking_data0-25.log', 0, 25);

    ******** Beginning trucking data dump
    ** Logfile location: /scratch/logs/dump_trucking_data0-25.log
    ** Routeserver data version: 12.1.0.1.2                  (A)
    ** Start partition id: 0
    ** End partition id: 25

    Starting truck data dump for partition 0, blob length 1019048 bytes
      Data version: 12.1.0.1.2
      Partition 0 has 21808 edges with truck data            (B)
        edge id -939054768 has 4 truck restrictions
          Main Type(10): Physical Height Restriction
          Sub-type(99): Unknown
          Value: 4.65
        *******************************
        edge id -854677940 has 3 truck restrictions
          Main Type(10): Physical Height Restriction
          Sub-type(1): Bridge
          Value: 4.67
        *******************************
        edge id -929320205 has 4 truck restrictions          (C)
          Main Type(10): Physical Height Restriction
          Sub-type(2): Tunnel
          Value: 4.27
          -------
          Main Type(20): Physical Weight Restriction
          Sub-type(99): Unknown
          Value: 4.08
        *******************************

    *** The rest of the trucking data for edges in partition 0

    Starting truck data dump for partition 2, blob length 296 bytes
                                                             (D)

    Starting truck data dump for partition 3, blob length 3272 bytes
      Partition 3 has 91 edges with truck data
        edge id -811551125 has 1 truck restrictions
          Main Type(50): Legal Restriction
          Sub-type(22): All trailers forbidden
          Value: 0.0
        *******************************
        edge id 105439903 has 1 truck restrictions
          Main Type(20): Physical Weight Restriction
          Sub-type(99): Unknown
          Value: 9.07
        *******************************
        edge id -105491810 has 1 truck restrictions          (E)
          Main Type(50): Legal Restriction
          Sub-type(21): All trucks forbidden
          Value: 0.0
        *******************************
        edge id -105449802 has 1 truck restrictions
          Main Type(50): Legal Restriction
          Sub-type(26): All trucks forbidden except deliveries and residents
          Value: 0.0
        *******************************

     *** The rest of the trucking data for edges in partitions 3 through 25

In Example D-11:

- (A): The standard user dump header contains the location of the log file and the parameters used in the dump. It also contains the routing engine data version as queried from the SDO_ROUTER_DATA_VERSION table. This data version must match the data version stored in the header of the partition 0 BLOB.

- (B): In the BLOB header section for the partition 0 BLOB, all turn restriction user data BLOB headers contain the partition ID, length of the BLOB in bytes, and number of edges with turn restrictions on them. The BLOB header for partition 0 also contains the user data version. This version must match the data version found in the SDO_ROUTER_DATA_VERSION table.

  Edge -939054768 is listed as having 4 truck restrictions, but only one is listed. The other three restrictions are there, but are currently unsupported in the routing engine. To see these restrictions, set the SKIP_UNSUPPORTED to FALSE when requesting the dump.

  For edge -929320205 the Height restriction is because of a Bridge. Edge -939054768 also has a Height restriction, but there is no Subtype specified to explain why.

- (C): This is an example of an edge that has multiple restrictions on it, in this case both a height and weight restriction expressed in meters and metric tons.

- (D): Two things to note here: (1) partition 1 is missing, which means there is no trucking user data for partition 1; and (2) a partition header was printed for partition 2 but there is no data dumped, which means that there are trucking restrictions for partition 2 but the routing engine currently supports none of them.

- (E): This is an example of two kinds of legal restrictions that can be modeled. (1) Edge -105491810 is an example of an exclusive legal restriction. There is a legal restriction on the edge that forbids all trucks. (2) Edge -105449802 is an example of an inclusive legal restriction. There is a legal restriction that excludes trucks on the edge but also lists an exception for delivery and resident trucks.

**Parent topic:** User Data Examples

##### D.4.8.5 Rebuilding the Time Zone User Data

The following example rebuilds the time zone user data. Before building the time zones user data, make sure that the SDO_TIMEZONES table exists in the data set. This table can be imported from the Oracle Router demo directory.

Example D-12 Rebuilding the Time Zone User Data

    -- 1) Create a spatial index on the SDO_TIMEZONES table.

    EXEC SDO_ROUTER_TIMEZONE.CREATE_SDO_TIMEZONES_INDEX(‘create_timezone_index.log’);

    ******** Begin indexing of the sdo_timezones table
    ** Logfile location: /scratch/logs/create_timezone_index.log
    [INFO] Creating metadata and spatial index on sdo_timezones for HERE_SF
    [INFO] Added metadata for sdo_timezones to user_sdo_geom_metadata
    [INFO] Rebuilding the spatial index on node table
    [INFO] Added metadata for node to user_sdo_geom_metadata

    -- 2) Associate the edges in the data set with their correct time zone.

    EXEC SDO_ROUTER_TIMEZONE.CREATE_ROUTER_TIMEZONES_EDGES('create_router_timezone_edges.log’);

    ******** Begin generation of router_timezones_edges (timezones raw data)
    ** Logfile location: /scratch/logs/create_router_timezone_edges.log
    [INFO] Creating router_timezones_edges table for HERE_SF
    [INFO] Associate nodes to timezones
    [INFO] Dropped metadata for router_timezones_nodes from user_sdo_geom_metadata
    [INFO] Added metadata for router_timezones_nodes to user_sdo_geom_metadata
    [INFO] Creating node id index on the router_timezones_nodes table
    [INFO] Creating spatial index on the router_timezones_nodes table
    [INFO] Associate orphan nodes to timezone polygons
    [INFO] Duplicate node cleanup
    [INFO] Associate edges to timezones
    [INFO] Creating edge id index on the router_timezones_edges table
    [INFO] Creating partition id index on the router_timezones_edges table
    [INFO] Creating timezone id index on the router_timezones_edges table
    ******** Completed generation of router_timezones_edges

    -- 3) Create the actual Router time zone user data.

    EXEC SDO_ROUTER_PARTITION.CREATE_TIMEZONE_DATA('rebuild_timezone_data.log’);

    ******** Begin generation of timezone user data
    ** Logfile location: /scratch/logs/rebuild_timezone_data.log
    [INFO] Generating timezone user data for 65 partitions, data version (12.2.0.0.0)
    [INFO] SQL String: CREATE TABLE new_timezone_data(partition_id NUMBER, num_edges NUMBER, timezone_data BLOB) LOB(timezone_data) STORE AS (STORAGE (INITIAL 512K NEXT 128K MAXEXTENTS UNLIMITED) CHUNK 32768 NOCACHE NOLOGGING)
    [INFO] ---- Writing 3096 timezones for partition 0
    [INFO] ---- Writing 2063 timezones for partition 1
    [INFO] ---- Writing 1961 timezones for partition 2
    [INFO] ---- Writing 2281 timezones for partition 3
    …
    …
    [INFO] ---- Writing 1839 timezones for partition 64
    INFO: creating the final timezone user data table
    INFO: create index rtd_p_idx on router_timezone_data table

**Parent topic:** User Data Examples

##### D.4.8.6 Dumping All Time Zone User Data BLOBs

The following example dumps all time zone user data BLOBs.

Example D-13 Dumping All Time Zone User Data BLOBs

    EXEC SDO_ROUTER_PARTITION.DUMP_TIMEZONE_DATA('dump_timezone_data.log');

    Starting timezone user data dump for partition 0, blob length 30992 bytes
      Data version: 12.2.0.0.0
      Partition 0 has 3096 edges with timezone user data
        edge id/Timezone -960842086/America/Los_Angeles(0)
        edge id/Timezone -960842085/America/Los_Angeles(0)
        edge id/Timezone -958443422/America/Los_Angeles(0)
    …
    …
    Starting timezone user data dump for partition 64, blob length 18398 bytes
      Partition 64 has 1839 edges with timezone user data
        edge id/Timezone -961912976/America/Los_Angeles(0)
        edge id/Timezone -961912975/America/Los_Angeles(0)
        edge id/Timezone -958078848/America/Los_Angeles(0)
    …
    …

**Parent topic:** User Data Examples

### D.5 Other Functions and Procedures

The following functions and procedures are for internal use by the routing engine during the partitioning process. You should not call them directly unless instructed to by Oracle Support.

- GET_PID: Used to get partition ids during partitioning.

- MIN_EIGENVECTOR: Eigenvector used during partitioning.

- GATHER_TABLE_STATS: Deprecated. Used to rebuild table and index statistics.

- All ELOCATION\_\*: Wrappers for Java code used in partitioning.

- BUILD_TURN_RESTRICTIONS Deprecated. Used to build Release 11g turn restrictions.

- GET_EDGE_INFO: Collects edge information for building driving directions for a route.

- GET_GEOMETRY_INFO: Builds the line string geometry for a route.

**Parent topic:** Routing Engine Administration
