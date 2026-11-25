## Downgrading Oracle Standalone Cluster to 12c Release 2 (12.2)

Use this procedure to downgrade Oracle Standalone Cluster to Oracle Grid Infrastructure 12c Release 2 (12.2) after a successful upgrade.

1.  As `grid` user, delete the Oracle Grid Infrastructure 19c Management Database:
    `%ORACLE_HOME%\bin\dbca -silent -deleteDatabase -sourceDB -MGMTDB `
2.  As `root` user, use the command syntax `rootcrs.bat -downgrade` from 19c Grid home to downgrade Oracle Grid Infrastructure on all nodes, in any sequence. For example:
    `%ORACLE_HOME%\crs\install\rootcrs.bat -downgrade`
    Run this command from a directory that has write permissions for the Oracle Grid Infrastructure installation user. You can run the downgrade script in parallel on all cluster nodes, but one.
3.  As `root` user, downgrade the last node after you downgrade all other nodes:
    `%ORACLE_HOME%\crs\install\rootcrs.bat -downgrade`
4.  As `grid` user, remove Oracle Grid Infrastructure 19c Grid home as the active Oracle Clusterware home:
    Use the following command to start the installer, where `C:\app\19.0.0\grid` is the location of the new (upgraded) Grid home:

    Run the `setup.exe` command from the 19c Grid home. Add the flag `-cfs` if the Grid home is a shared home.

        cd %ORACLE_HOME%\oui\bin
        setup.exe -nowait -waitforcompletion -ignoreSysPrereqs
        -updateNodeList -silent CRS=false
        ORACLE_HOME=C:\app\19.0.0\grid
        "CLUSTER_NODES=node1,node2,node3"
5.  As `grid` user, set Oracle Grid Infrastructure 12c Release 2 (12.2) Grid home as the active Oracle Clusterware home:
    Use the following command to start the installer, where the path you provide for `ORACLE_HOME` is the location of the home directory from the earlier Oracle Clusterware installation:

        cd %ORACLE_HOME%\oui\bin
        setup.exe -nowait -waitforcompletion -ignoreSysPrereqs
        -updateNodeList -silent CRS=true
        ORACLE_HOME=C:\app\12.2.0\grid
        "CLUSTER_NODES=node1,node2,node3"
6.  As `root` user, start the 12c Release 2 (12.2) Oracle Clusterware stack on all nodes.
    `crsctl start crs`
7.  As `grid` user, from any Oracle Grid Infrastructure 12c Release 2 (12.2) node, remove the MGMTDB resource as follows:
    `%ORACLE_HOME%\bin\srvctl remove mgmtdb -f`
8.  As `grid` user, run DBCA in the silent mode from the 12.2.0.1 Grid home and create the Management Database container database (CDB) as follows:
        %ORACLE_HOME%\bin\dbca -silent -createDatabase -createAsContainerDatabase true
        -templateName MGMTSeed_Database.dbc -sid -MGMTDB -gdbName _mgmtdb
        -storageType ASM -diskGroupName ASM_DG_NAME
        -datafileJarLocation C:\app\12.2.0\grid\assistants\dbca\templates
        -characterset AL32UTF8 -autoGeneratePasswords -skipUserTemplateCheck
9.  Configure the Management Database by running the Configuration Assistant from the location `%ORACLE_HOME%\bin\mgmtca.bat —local`.

**Parent topic:** [Downgrading Oracle Clusterware to 12c Release 2 (12.2)](downgrading-oracle-clusterware-to-12c-release-2-12-2.md)
