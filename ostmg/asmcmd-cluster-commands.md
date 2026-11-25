This topic provides a summary of the ASMCMD member cluster management commands that are used with Oracle ASM remote instances.

Unless otherwise specified, the ASMCMD cluster management commands should be executed in the Oracle ASM-CSS cluster.

For information about Oracle Flex ASM, refer to "[Managing Oracle Flex ASM](manage-flex-asm.md)".

Table 10-38 lists the ASMCMD member cluster management commands with brief descriptions.

Table 10-38 Summary of ASMCMD member cluster management commands

| Command | Description                                     |
|:--------|:------------------------------------------------|
| chcc    | Modifies a configuration for a member cluster.  |
| mkcc    | Creates a configuration for a member cluster.   |
| lscc    | Lists the configured member clusters.           |
| rmcc    | Removes the configuration for a member cluster. |

**See Also:**

- [Oracle Grid Infrastructure Installation and Upgrade Guide](../install-and-upgrade.md) for information about installing clusters and cluster name requirements

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/introduction-to-oracle-clusterware.md) for information about member clusters

### chcc

#### Purpose

Modifies the configuration for a member cluster.

#### Syntax and Description

    chcc cluster_name [--direct | --indirect]
         [--version member_cluster_version]

The following table lists the options for the `chcc` command.

Table 10-39 Options for the chcc command

| Option                               | Description                                                                                                                                              |
|:-------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------|
| `cluster_name`                       | Specifies the name of the member cluster.                                                                                                                |
| `--direct`                           | Specifies direct storage access.                                                                                                                         |
| `--indirect`                         | Specifies indirect storage access.                                                                                                                       |
| `--version` `member_cluster_version` | Specifies the five digit member cluster version if it is different than the storage server version. The storage server version is used if not specified. |

To modify the storage access method of a member cluster, you perform the following steps.

1.  As the Oracle Grid Infrastructure user at the Domain Services Cluster (DSC), change the member cluster storage access configuration with the `chcc` command.

2.  As the Oracle Grid Infrastructure user at the Domain Services Cluster (DSC), export the member cluster configuration into a new cluster manifest file with the `mkcc` command.

    You can ignore the warning messages reported when the `mkcc` command is issued.

3.  After you have exported the new cluster manifest file, as the root user on the nodes of member cluster you copy the new cluster manifest file to the nodes with the `rootcrs.sh` script.

#### Examples

The following examples show how to modify the storage access method from direct to indirect Oracle ASM storage for the member cluster `—–asm` and `––gimr` components.

Example 10-48 Using the ASMCMD chcc command

As the Oracle Grid Infrastructure user at the Domain Services Cluster (DSC), run the following commands:

    $ asmcmd chcc memberCluster1 --indirect

    $ asmcmd mkcc memberCluster1 /export/cluster_manifest_new.xml --asm --gimr

As the root user at the member cluster, copy the new cluster manifest file to the member cluster with the following commands.

1.  Run the `rootcrs.sh` script on every node in the member cluster.

        # rootcrs.sh --convertcluster STORAGE_ACCESS -manifestfile cluster_manifest_new.xml

2.  Run the `rootcrs.sh` script with the `-lastnode` option on last node in the member cluster.

        # rootcrs.sh --convertcluster STORAGE_ACCESS -manifestfile cluster_manifest_new.xml -lastnode

### lscc

#### Purpose

Lists the configured member clusters.

#### Syntax and Description

    lscc [--suppressheader] [-l] [cluster_name | --file wrap]

The following table lists the options for the `lscc` command.

Table 10-40 Options for the lscc command

| Option            | Description                                                           |
|:------------------|:----------------------------------------------------------------------|
| `–suppressheader` | Suppresses column headings from the output.                           |
| `-l`              | Displays all details.                                                 |
| `cluster_name`    | Specifies the name of the member cluster.                             |
| `--file`          | Displays information about the contents of the cluster manifest file. |
| `wrap`            | Specifies the full path of the XML file to export the credentials.    |

#### Examples

The following example lists the configured member clusters.

Example 10-49 Using the ASMCMD lscc command

    ASMCMD [+] > lscc
    --------------------------------------------------------------------------------
               NAME        VERSION GUID
    ================================================================================
     memberCluster1     12.2.0.0.0 78015b1e78756f88bf119fd8e5146df4
     memberCluster2     12.2.0.0.0 3de3bbd75e9a7f17bfe027b477b5bcae
    ================================================================================

    ASMCMD [+] > lscc -l
    --------------------------------------------------------------------------------
               NAME        VERSION GUID                             ASM GIMR TFA ACFS RHP
    =====================================================================================
     memberCluster1     12.2.0.0.0 78015b1e78756f88bf119fd8e5146df4 YES  YES YES  YES YES
     memberCluster2     12.2.0.0.0 3de3bbd75e9a7f17bfe027b477b5bcae YES  YES YES  YES  NO
    =====================================================================================

    ASMCMD [+] > lscc memberCluster1 --suppressheader
     memberCluster1     12.2.0.0.0 78015b1e78756f88bf119fd8e5146df4

    ASMCMD [+] > lscc memberCluster1 --suppressheader -l
     memberCluster1     12.2.0.0.0 78015b1e78756f88bf119fd8e5146df4 ASM,GIMR,TFA,ACFS,RHP

### mkcc

#### Purpose

Creates the configuration for a member cluster.

#### Syntax and Description

    mkcc cluster_name manifest_file [--direct]
         [--version member_cluster_version]
         [--guid member_cluster_guid]
         [--gimr gimr_pdb/export_dir]
         [--asm] [--gimr] [--rhp] [--acfs] [--tfa]

The following table lists the options for the `mkcc` command.

Table 10-41 Options for the mkcc command

| Option                               | Description                                                                                                                                                                                                                                  |
|:-------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `cluster_name`                       | Specifies the name of the member cluster.                                                                                                                                                                                                    |
| `manifest_file`                      | Specifies the full path of the XML file to export the credentials.                                                                                                                                                                           |
| `--direct`                           | Specifies direct storage access. If not specified, the storage access is indirect.                                                                                                                                                           |
| `--version` `member_cluster_version` | Specifies the five digit member cluster version if it is different than the storage server version. The storage server version is used if not specified.                                                                                     |
| `--guid` `member_cluster_guid`       | Specifies the 32-character, globally unique identifier for the member cluster. When this option is specified, `mkcc` does not generate a new GUID. If there is a cluster already configured with the specified GUID, then the command fails. |
| `--gimr` `gimr_pdb/export_dir`       | Specifies the directory from which to import the GIMR PDB when converting a standalone cluster to a member cluster.                                                                                                                          |
| `--asm`                              | Generate credentials and configuration for an Oracle ASM member cluster.                                                                                                                                                                     |
| `–-gimr`                             | Generate credentials and configuration for an Oracle GIMR member cluster.                                                                                                                                                                    |
| `–-rhp`                              | Generate credentials and configuration for an Oracle RHP member cluster.                                                                                                                                                                     |
| `–-acfs`                             | Generate credentials and configuration for an Oracle ACFS member cluster.                                                                                                                                                                    |
| `--tfa`                              | Generate credentials and configuration for an Oracle TFA member cluster.                                                                                                                                                                     |

The member cluster name must conform to the same rules as a cluster name. The name must be unique across your enterprise, must be at least one character long and no more than 15 characters in length, must be alphanumeric, cannot begin with a numeral, and may contain hyphens (-). Underscore characters (\_) are not allowed.

If no member cluster component options are specified, the default is to configure all of the components and store their credentials in the same manifest file.

GNS credentials are not generated by the `asmcmd` `mkcc` command. To configure the member cluster as a GNS Client, run the following command as a privileged user to export the GNS instance client data configuration to the cluster manifest file:

    srvctl export gns -clientdata manifest_file -role CLIENT

#### Examples

The following example creates credentials for the member cluster `—–asm` and `––gimr` components and exports the credentials to a cluster manifest file.

Example 10-50 Using the ASMCMD mkcc command

    ASMCMD [+] > mkcc memberCluster1 /tmp/member_cluster1.xml --version 12.2.0.0.0 --asm --gimr

### rmcc

#### Purpose

Removes the configuration for a member cluster.

#### Syntax and Description

    rmcc cluster_name [-f]

The following table lists the options for the `rmcc` command.

Table 10-42 Options for the rmcc command

| Option         | Description                                                   |
|:---------------|:--------------------------------------------------------------|
| `cluster_name` | Specifies the name of the member cluster.                     |
| `-f`           | Specifies to force the removal of member cluster credentials. |

#### Examples

The following example removes the configuration for a member cluster.

Example 10-51 Using the ASMCMD rmcc command

    ASMCMD [+] > rmcc memberCluster1
