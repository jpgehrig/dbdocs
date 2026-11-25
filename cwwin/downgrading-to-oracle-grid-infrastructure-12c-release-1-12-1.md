## Downgrading to Oracle Grid Infrastructure 12c Release 1 (12.1.0.2)

Use this procedure to downgrade to Oracle Grid Infrastructure 12c release 1 (12.1.0.2).

1.  **Optional:** Delete the Oracle Grid Infrastructure 19c Management Database:
        dbca -silent -deleteDatabase -sourceDB -MGMTDB
2.  Use the command syntax `rootcrs.bat -downgrade` to downgrade Oracle Grid Infrastructure on all nodes, in any sequence.
    For example:

        C:\>cd 19c_grid_home\crs\install\rootcrs.bat -downgrade

    Run this command from a directory that has write permissions for the Oracle Grid Infrastructure installation user. You can run the downgrade script in parallel on all cluster nodes, but one.
3.  Downgrade the last node after you downgrade all other nodes.
        C:\>cd 19c_grid_home\crs\install\rootcrs.bat -downgrade
4.  Remove the Oracle Grid Infrastructure 19c Grid home as the active Oracle Clusterware home:
    1.  On any of the cluster member nodes where the `rootcrs.bat -downgrade` command has run successfully, log in as the Oracle Grid Infrastructure installation owner.
    2.  Use the following command to start the installer, where `19c_grid_home` is the location of the new (upgraded) Grid home:
            C:\>cd 19c_grid_home\oui\bin
            setup.exe -nowait -waitforcompletion -ignoreSysPrereqs -updateNodeList -silent CRS=false
            ORACLE_HOME=19c_grid_home "CLUSTER_NODES=node1,node2,node3" LOCAL_NODE=local_node_running_the_command
            -doNotUpdateNodeList

        Add the flag `-cfs` if the Grid home is a shared home.
5.  Set Oracle Grid Infrastructure 12c release 1 (12.1.0.2) Grid home as the active Oracle Clusterware home:
    1.  On any of the cluster member nodes where the `rootcrs.bat -downgrade` command has run successfully, log in as the Oracle Grid Infrastructure installation owner.
    2.  Use the following command to start the installer, where the path you provide for `ORACLE_HOME` is the location of the home directory from the earlier Oracle Clusterware installation.
            C:\>cd C:\app\12.1.0\grid\oui\bin
            setup.exe -nowait -waitforcompletion -ignoreSysPrereqs -updateNodeList -silent CRS=true
            ORACLE_HOME=C:\app\12.1.0\grid "CLUSTER_NODES=node1,node2,node3" -doNotUpdateNodeList
6.  Start the Oracle Grid Infrastructure 12c release 1 (12.1.0.2) clusterware stack from the old Grid home on each node to complete the downgrade.
        crsctl start crs
7.  On any node, remove the MGMTDB resource as follows:
        121_Grid_home\bin\srvctl remove mgmtdb
8.  If you are downgrading to Oracle Grid Infrastructure 12c release 1 (12.1.0.2), run the following commands to configure the Grid Infrastructure Management Database:
    1.  Run DBCA in silent mode from the Oracle Database 12c release 1 (12.1.0.2) home and create the Management Database container database (CDB) as follows:
            12102_Grid_home\bin\dbca -silent -createDatabase -createAsContainerDatabase true
            -templateName MGMTSeed_Database.dbc -sid -MGMTDB -gdbName _mgmtdb
            -storageType ASM -diskGroupName ASM_DG_NAME
            -datafileJarLocation 12102_grid_home\assistants\dbca\templates
            -characterset AL32UTF8 -autoGeneratePasswords -skipUserTemplateCheck
    2.  Run DBCA in silent mode from the Oracle Database 12c release 1 (12.1.0.2) home and create the Management Database pluggable database (PDB) as follows:
            12102_Grid_home\bin\dbca -silent -createPluggableDatabase -sourceDB -MGMTDB
            -pdbName cluster_name -createPDBFrom RMANBACKUP
            -PDBBackUpfile 12102_Grid_home\assistants\dbca\templates\mgmtseed_pdb.dfb
            -PDBMetadataFile 12102_Grid_home\assistants\dbca\templates\mgmtseed_pdb.xml
            -createAsClone true -internalSkipGIHomeCheck
9.  Configure the Management Database by running the Configuration Assistant from the location `121_Grid_home``\bin\mgmtca`.

**Parent topic:** [Downgrading Oracle Clusterware to an Earlier Release](downgrading-oracle-clusterware-after-an-upgrade.md)
