## Deinstallation Response File Example for Oracle Grid Infrastructure for a Cluster

You can run the `deinstall` command with the `-paramfile` option to use the values you specify in the response file.

The following is an example of a response file for a cluster on nodes `node1` and `node2`, in which the Oracle Grid Infrastructure for a cluster software binary owner is `grid`, the Oracle Grid Infrastructure home (Grid home) is in the path `/u01/app/19.0.0/grid`, the Oracle base (the Oracle base for Oracle Grid Infrastructure, containing Oracle ASM log files, Oracle Clusterware logs, and other administrative files) is `/u01/app/grid/`, the central Oracle Inventory home (`oraInventory`) is `/u01/app/oraInventory`, the virtual IP addresses (VIP) are `192.0.2.2` and `192.0.2.4`, the local node (the node where you run the deinstallation session from) is `node1`:

    # Copyright (c) 2005, 2016 Oracle Corporation.  All rights reserved.
    ORACLE_HOME=/u01/app/12.2.0/grid
    CDATA_AUSIZE=4
    BIG_CLUSTER=true
    ISROLLING=true
    LOCAL_NODE=node1
    OCR_VD_DISKGROUPS="+DATA1"
    MGMTDB_DIAG=/u01/app/grid
    OCRID=
    MGMTDB_SPFILE="+DATA1/_MGMTDB/PARAMETERFILE/spfile.271.923210081"
    ObaseCleanupPtrLoc=/tmp/deinstall2016-10-06_09-36-04AM/utl/orabase_cleanup.lst
    CDATA_BACKUP_QUORUM_GROUPS=
    ASM_CREDENTIALS=
    MGMTDB_NODE_LIST=node1,node2
    EXTENDED_CLUSTER=false
    LISTENER_USERNAME=cuser
    local=false
    inventory_loc=/u01/app/oraInventory
    ORACLE_HOME=/u01/app/12.2.0/grid
    ASM_HOME=/u01/app/grid
    ASM_DISK_GROUPS="+DATA1"
    HUB_NODE_VIPS=AUTO,AUTO
    PING_TARGETS=
    ORA_DBA_GROUP=oinstall
    ASM_DISCOVERY_STRING=/dev/rdsk/*
    CDATA_DISKS=/dev/rdsk/c0t600144F0C4A01A3F000056E6A12A0022d0s3
    MinimumSupportedVersion=11.2.0.1.0
    NEW_HOST_NAME_LIST=
    ORACLE_HOME_VERSION=12.2.0.1.0
    PRIVATE_NAME_LIST=
    MGMTDB_DB_UNIQUE_NAME=_mgmtdb
    ASM_DISKSTRING=/dev/rdsk/*,AFD:*
    CDATA_QUORUM_GROUPS=
    CRS_HOME=true
    ODA_CONFIG=
    JLIBDIR=/u01/app/jlib
    CRFHOME="/u01/app/"
    USER_IGNORED_PREREQ=true
    MGMTDB_ORACLE_BASE=/u01/app/grid/
    DROP_MGMTDB=true
    RHP_CONF=false
    OCRLOC=
    GNS_TYPE=local
    CRS_STORAGE_OPTION=1
    CDATA_SITES=
    GIMR_CONFIG=local
    CDATA_BACKUP_SIZE=0
    GPNPGCONFIGDIR=$ORACLE_HOME
    MGMTDB_IN_HOME=true
    CDATA_DISK_GROUP=+DATA2
    LANGUAGE_ID=AMERICAN_AMERICA.AL32UTF8
    CDATA_BACKUP_FAILURE_GROUPS=
    CRS_NODEVIPS='AUTO/255.255.254.0/net0,AUTO/255.255.254.0/net0'
    ORACLE_OWNER=cuser
    GNS_ALLOW_NET_LIST=
    silent=true
    INSTALL_NODE=node1.example.com
    ORACLE_HOME_VERSION_VALID=true
    inst_group=oinstall
    LOGDIR=/tmp/deinstall2016-10-06_09-36-04AM/logs/
    EXTENDED_CLUSTER_SITES=
    CDATA_REDUNDANCY=EXTERNAL
    CDATA_BACKUP_DISK_GROUP=+DATA2
    APPLICATION_VIP=
    HUB_NODE_LIST=node1,node2
    NODE_NAME_LIST=node1,node2
    GNS_DENY_ITF_LIST=
    ORA_CRS_HOME=/u01/app/12.2.0/grid/
    JREDIR=/u01/app/12.2.0/grid/jdk/jre/
    ASM_LOCAL_SID=+ASM1
    ORACLE_BASE=/u01/app/
    GNS_CONF=true
    CLUSTER_CLASS=DOMAINSERVICES
    ORACLE_BINARY_OK=true
    CDATA_BACKUP_REDUNDANCY=EXTERNAL
    CDATA_FAILURE_GROUPS=
    ASM_CONFIG=near
    OCR_LOCATIONS=
    ASM_ORACLE_BASE=/u01/app/12.2.0/
    OLRLOC=
    GIMR_CREDENTIALS=
    GPNPCONFIGDIR=$ORACLE_HOME
    ORA_ASM_GROUP=asmadmin
    GNS_CREDENTIALS=
    CDATA_BACKUP_AUSIZE=4
    GNS_DENY_NET_LIST=
    OLD_CRS_HOME=
    NEW_NODE_NAME_LIST=
    GNS_DOMAIN_LIST=node1.example.com
    ASM_UPGRADE=false
    NETCA_LISTENERS_REGISTERED_WITH_CRS=LISTENER
    CDATA_BACKUP_DISKS=/dev/rdsk/
    ASMCA_ARGS=
    CLUSTER_GUID=
    CLUSTER_NODES=node1,node2
    MGMTDB_NODE=node2
    ASM_DIAGNOSTIC_DEST=/u01/app/
    NEW_PRIVATE_NAME_LIST=
    AFD_LABELS_NO_DG=
    AFD_CONFIGURED=true
    CLSCFG_MISSCOUNT=
    MGMT_DB=true
    SCAN_PORT=1521
    ASM_DROP_DISKGROUPS=true
    OPC_NAT_ADDRESS=
    CLUSTER_TYPE=DB
    NETWORKS="net0"/IP_Address:public,"net1"/IP_Address:asm,"net1"/IP_Address:cluster_interconnect
    OCR_VOTINGDISK_IN_ASM=true
    HUB_SIZE=32
    CDATA_BACKUP_SITES=
    CDATA_SIZE=0
    REUSEDG=false
    MGMTDB_DATAFILE=
    ASM_IN_HOME=true
    HOME_TYPE=CRS
    MGMTDB_SID="-MGMTDB"
    GNS_ADDR_LIST=mycluster-gns.example.com
    CLUSTER_NAME=node1-cluster
    AFD_CONF=true
    MGMTDB_PWDFILE=
    OPC_CLUSTER_TYPE=
    VOTING_DISKS=
    SILENT=false
    VNDR_CLUSTER=false
    TZ=localtime
    GPNP_PA=
    DC_HOME=/tmp/deinstall2016-10-06_09-36-04AM/logs/
    CSS_LEASEDURATION=400
    REMOTE_NODES=node2
    ASM_SPFILE=
    NEW_NODEVIPS='n1-vip/255.255.252.0/eth0,n2-vip/255.255.252.0/eth0'
    SCAN_NAME=node1-cluster-scan.node1-cluster.com
    RIM_NODE_LIST=
    INVENTORY_LOCATION=/u01/app/oraInventory

**Note:**

Do not use quotation marks with variables except in the following cases:

- Around addresses in CRS_NODEVIPS:

      CRS_NODEVIPS='n1-vip/255.255.252.0/eth0,n2-vip/255.255.252.0/eth0'

- Around interface names in NETWORKS:

      NETWORKS="eth0"/192.0.2.1\:public,"eth1"/10.0.0.1\:cluster_interconnect VIP1_IP=192.0.2.2

**Parent topic:** [Removing Oracle Database Software](removing-oracle-database-software.md)
