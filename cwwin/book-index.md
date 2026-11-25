## Index

Numerics  A  B  C  D  E  F  G  H  I  J  K  L  M  N  O  P  Q  R  S  T  U  V  W  X  

------------------------------------------------------------------------

## Numerics

- 32-bit and 64-bit
  - software versions in the same cluster not supported [2.2](general-server-requirements.md)

------------------------------------------------------------------------

## A

- Access Control Lists [5.1.2](about-the-oracle-home-user-for-the-oracle-grid-infrastructure-installation.md), [5.1.3](about-the-oracle-home-user-for-the-oracle-rac-installation.md)
- adding Oracle ASM listener [11.9.3](registering-resources-with-enterprise-manager-after-upgrades.md)
- address resolution protocol [4.7](broadcast-requirements-for-networks-used-by-oracle-grid-infrastructure.md), [4.8](multicast-requirements-for-networks-used-by-oracle-grid-infrastructure.md)
- Administrators group [5.1.1](about-the-oracle-installation-user.md), [5.3.2](verifying-user-privileges-to-update-remote-nodes.md), [5.3.3](managing-user-accounts-with-user-account-control.md)
- ARP
  - See: address resolution protocol
- ASM
  - See: Oracle ASM

  <!-- -->

  - OSASM or ASM administrator [5.2.4](oracle-asm-groups-for-job-role-separation.md)
  - OSDBA for ASM group [5.2.4](oracle-asm-groups-for-job-role-separation.md)
  - OSOPER for ASM group [5.2.4](oracle-asm-groups-for-job-role-separation.md)
- ASM_DISKSTRING [7.5.3](specifying-the-oracle-asm-disk-discovery-string.md)
- ASMADMIN group [5.1.1](about-the-oracle-installation-user.md)
- ASMCA
  - and upgrades [6.5](about-migrating-existing-oracle-asm-instances.md)
  - enabling Oracle Restart disk group volumes [12.2](migrating-standalone-grid-infrastructure-servers-to-a-cluster.md)
  - starting [7.7](configuring-oracle-automatic-storage-management-cluster-file-system.md), [9.5](installing-oracle-grid-infrastructure-for-a-new-cluster.md), [10.2.3.2](creating-the-fast-recovery-area-disk-group.md)
- ASMDBA group [5.1.1](about-the-oracle-installation-user.md)
- ASM network
  - multiple NICs [4.9](multiple-private-interconnects-on-microsoft-windows-platforms.md)
- ASMSNMP [1.4](oracle-grid-infrastructure-network-checklist.md)
- asmtool utility [7.6.1](using-asmtoolg-graphical-user-interface-to-mark-disks.md)
- Automatic Diagnostic Repository (ADR) [B.1](about-the-optimal-flexible-architecture-standard.md)
- Automatic Storage Management Cluster File System
  - See: Oracle ACFS
- automount
  - enable [6.6.2](enabling-automounting-for-windows.md)

------------------------------------------------------------------------

## B

- batch upgrades [11.6](understanding-rolling-upgrades-using-batches.md)
- BMC interface
  - preinstallation tasks [5.5](enabling-intelligent-platform-management-interface-ipmi.md)

------------------------------------------------------------------------

## C

- central inventory [5.1.6](understanding-the-oracle-inventory-directory-and-the-oracle-inventory-group.md), [5.2.2](oracle-software-owner-for-each-oracle-software-product.md), [B.5](optimal-flexible-architecture-file-path-examples.md)
  - See also: OINSTALL directory, oraInventory
- changing host names [4.2.1](about-the-public-ip-address.md)
- checkdir error [11.4](restrictions-and-guidelines-for-oracle-grid-infrastructure-upgrades.md)
- checklist
  - upgrades [11.5.1](upgrade-checklist-for-oracle-grid-infrastructure.md)
- checklists [1](oracle-grid-infrastructure-installation-checklist.md)
- chip architecture [2.2](general-server-requirements.md)
- CIFS
  - Common Internet File System [8.1](about-direct-nfs-client-storage.md)
- clients
  - and upgrades [4.2.5](about-the-scan.md)
  - certification [3.7](checking-hardware-and-software-certification-on-my-oracle-support.md)
  - connecting to SCAN [4.2.5](about-the-scan.md)
  - Direct NFS Client [6.4.2](guidelines-for-using-direct-network-file-system-nfs-with-oracle-rac.md)
  - trace files [10.1.2.8](troubleshooting-windows-firewall-exceptions.md)
  - using SCAN [4.2.5](about-the-scan.md)
  - using the public interface [4.2.1](about-the-public-ip-address.md)
- client-server configurations [B.2](about-multiple-oracle-homes-support.md)
- CLSRSC-661 [11.5.3](create-oracle-asm-password-file-win.md)
- CLUSTER_INTERCONNECTS parameter [4.2.2](about-the-private-ip-address.md)
- cluster configuration
  - Oracle Extended Clusters [9.3.2](about-oracle-extended-clusters.md)
  - Oracle Standalone Clusters [9.3.1](about-oracle-standalone-cluster.md)
- cluster file system
  - storage option for data files [6.3](storage-considerations-for-oracle-gird-infrastructure-and-oracle-rac.md)
- cluster name
  - requirements for [1.4](oracle-grid-infrastructure-network-checklist.md)
- cluster nodes
  - private network node interfaces [1.4](oracle-grid-infrastructure-network-checklist.md)
  - private node names [4.2.5](about-the-scan.md)
  - public network node names and addresses [1.4](oracle-grid-infrastructure-network-checklist.md)
  - public node names [9.5](installing-oracle-grid-infrastructure-for-a-new-cluster.md)
  - virtual node names [1.4](oracle-grid-infrastructure-network-checklist.md), [4.2.3](about-the-virtual-ip-address.md)
- cluster privileges
  - verifying for OUI cluster installation [5.3.2](verifying-user-privileges-to-update-remote-nodes.md)
- Cluster Time Synchronization Service [2.6.1](about-cluster-time-synchronization.md), [2.6.2](understanding-network-time-requirements.md), [2.6.3](configuring-the-windows-time-service.md)
  - configuring [2.6.5](configuring-cluster-time-synchronization-service.md)
  - installed components [2.6.2](understanding-network-time-requirements.md)
  - observer mode [2.6.5](configuring-cluster-time-synchronization-service.md)
- Cluster Verification Utility (CVU)
  - and upgrades [11.5.2](tasks-to-complete-before-upgrading-grid-infrastructure.md)
- commands
  - asmca [7.7](configuring-oracle-automatic-storage-management-cluster-file-system.md), [10.2.3.2](creating-the-fast-recovery-area-disk-group.md)
  - configToolAllCommands [A.8.3](running-postinstallation-configuration-using-a-script-and-response-files.md)
  - crsctl [2.6.5](configuring-cluster-time-synchronization-service.md), [9.11](confirming-oracle-clusterware-function.md), [11.4](restrictions-and-guidelines-for-oracle-grid-infrastructure-upgrades.md)
  - executeConfigTools [A.7.2](running-postinstallation-configuration-using-response-file.md)
  - gridSetup.bat [9.7](installing-software-binaries-for-oracle-grid-infrastructure.md), [A.5](running-the-installer-using-a-response-file.md)
  - lsnrctl [10.3.4](using-the-correct-lsnrctl-commands.md)
  - msinfo32 [2.1.3](checking-the-system-processor-type.md)
  - net start and net stop [2.6.4](configuring-network-time-protocol.md)
  - net use [3.3](verify-privileges-for-copying-files-in-the-cluster.md), [5.3.2](verifying-user-privileges-to-update-remote-nodes.md)
  - ocopy.exe [10.1](required-postinstallation-tasks.md)
  - ping [4.3.2](network-requirements-for-the-private-network.md)
  - regedit [2.6.3](configuring-the-windows-time-service.md), [5.3.2](verifying-user-privileges-to-update-remote-nodes.md)
  - rootcrs.bat
    - and deconfigure option [12.4](unconfiguring-oracle-clusterware-without-removing-the-software.md)
  - roothas.bat [12.2](migrating-standalone-grid-infrastructure-servers-to-a-cluster.md)
  - runcluvfy.bat [9.7](installing-software-binaries-for-oracle-grid-infrastructure.md)
  - srvctl [11.4](restrictions-and-guidelines-for-oracle-grid-infrastructure-upgrades.md), [12.2](migrating-standalone-grid-infrastructure-servers-to-a-cluster.md)
  - W32tm [2.6.3](configuring-the-windows-time-service.md)
- configToolAllCommands [A.8.2](creating-a-password-response-file.md), [A.8.3](running-postinstallation-configuration-using-a-script-and-response-files.md)
- configToolAllCommands script [A.8.1](about-the-postinstallation-configuration-file.md)
- configuration wizard [9.8](configuring-software-binaries-for-oracle-grid-infrastructure.md)
- creating
  - oranfstab file [8.2](creating-an-oranfstab-file-for-direct-nfs-client.md)
- cron jobs [1.7](installer-planning-checklist-for-oracle-grid-infrastructure.md)
- crs_install.rsp file [A.4.2](editing-a-response-file-template.md)
- CTSS
  - See: Cluster Time Synchronization Service
- ctssd [2.6.1](about-cluster-time-synchronization.md), [2.6.5](configuring-cluster-time-synchronization-service.md)
- customized database
  - failure groups for Oracle ASM [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
  - requirements when using Oracle ASM [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)

------------------------------------------------------------------------

## D

- Database Configuration Assistant (DBCA)
  - response file [A.4.1](about-response-file-templates.md)
- database files
  - supported storage options [6.1](configuring-shared-storage-for-oracle-grid-infrastructure-oracle-rac.md)
- databases
  - Oracle ASM requirements [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
- data files
  - storage options [6.3](storage-considerations-for-oracle-gird-infrastructure-and-oracle-rac.md)
- data loss
  - minimizing with Oracle ASM [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md), [7.5.1](identifying-existing-oracle-asm-disk-groups-to-use.md)
- DB_RECOVERY_FILE_DEST [10.2.3.1](about-fast-recovery-area-and-fast-recovery-area-disk-group.md)
- DBCA
  - no longer used for Oracle ASM disk group administration [10.3.3](using-asmca-to-administer-disk-groups-for-earlier-database-releases.md)
- dbca.rsp file [A.4.1](about-response-file-templates.md)
- deconfiguring Oracle Clusterware [12.4](unconfiguring-oracle-clusterware-without-removing-the-software.md)
- deinstall.bat [12.5.1](about-the-deinstallation-tool.md)
- deinstallation [12.1](deciding-when-to-deinstall-oracle-clusterware.md)
  - files removed [12.5.2](files-deleted-by-the-deinstallation-tool.md)
- Deinstallation tool
  - restriction for Flex Clusters and —lastnode option [12.4](unconfiguring-oracle-clusterware-without-removing-the-software.md)
- deinstall command
  - location of log files [12.5.3](deinstallation-tool-command-reference.md)
  - syntax [12.5.3](deinstallation-tool-command-reference.md)
- device names
  - creating with asmtool [7.6.3](asmtool-command-line-reference.md)
  - creating with asmtoolg [7.6.1](using-asmtoolg-graphical-user-interface-to-mark-disks.md)
- DHCP [4.2.1](about-the-public-ip-address.md)
  - and GNS [4.5.1](about-oracle-grid-infrastructure-name-resolution-options.md)
- diagnostic data [B.1](about-the-optimal-flexible-architecture-standard.md)
- Direct NFS Client [6.1](configuring-shared-storage-for-oracle-grid-infrastructure-oracle-rac.md), [6.4.2](guidelines-for-using-direct-network-file-system-nfs-with-oracle-rac.md)
  - and fast recovery area [10.2.3.1](about-fast-recovery-area-and-fast-recovery-area-disk-group.md)
  - description [8.1](about-direct-nfs-client-storage.md)
  - dictionary views [8.8](monitoring-direct-nfs-client-usage.md)
  - enabling [8.6](enabling-direct-nfs-client.md)
  - load balancing [8.5](specifying-network-paths-for-a-nfs-server.md)
  - managing [8.8](monitoring-direct-nfs-client-usage.md)
  - ORADNFS utility [8.7](performing-basic-file-operations-using-the-oradnfs-utility.md)
- Direct NFS dispatcher [8.1](about-direct-nfs-client-storage.md)
- DisableDHCPMediaSense parameter [4.4.1](disabling-windows-media-sensing.md)
- disk automount
  - enable [6.6.2](enabling-automounting-for-windows.md)
- disk group
  - Oracle ASM with redundancy levels [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
  - recommendations for Oracle ASM disk groups [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
- disks
  - NTFS formatted [2.5](disk-format-requirements.md)
  - remove labels [7.6.2](using-asmtoolg-to-remove-disk-stamps.md)
  - selecting for use with Oracle ASM [7.5.2](selecting-disks-to-use-with-oracle-asm-disk-groups.md)
- disk space
  - checking [2.1.4](checking-the-available-disk-space-for-oracle-home-directories.md)
  - requirements
    - for Oracle ASM [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
    - for preconfigured database in Oracle ASM [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
- display monitor
  - resolution settings [2.3](server-minimum-hardware-and-memory-requirements.md)
- DNS
  - configuring to use with GNS [4.5.8](domain-delegation-to-grid-naming-service.md)
  - multicast (mDNS) [4.8](multicast-requirements-for-networks-used-by-oracle-grid-infrastructure.md)
- domain user
  - used in installation [5.1.1](about-the-oracle-installation-user.md)
- downgrade [11.11](downgrading-oracle-clusterware-after-an-upgrade.md)
- downgrade after failed installation [11.11.1.2](downgrading-oracle-grid-infrastructure-to-18c-when-upgrade-fails.md), [11.11.2.2](downgrading-oracle-grid-infrastructure-to-12c-release-2-12-2-when-upgrade-fails.md)
- downgrade after failed upgrade [11.11.1.2](downgrading-oracle-grid-infrastructure-to-18c-when-upgrade-fails.md), [11.11.2.2](downgrading-oracle-grid-infrastructure-to-12c-release-2-12-2-when-upgrade-fails.md)
- downgrades [11.11.1.2](downgrading-oracle-grid-infrastructure-to-18c-when-upgrade-fails.md), [11.11.2.2](downgrading-oracle-grid-infrastructure-to-12c-release-2-12-2-when-upgrade-fails.md)
- downgrade to 12c Release 2 (12.2) [11.11.2](downgrading-oracle-clusterware-to-12c-release-2-12-2.md)
- downgrade to 18c [11.11.1](downgrading-oracle-clusterware-to-18c.md)
- downgrading [11.11.3](downgrading-to-oracle-grid-infrastructure-12c-release-1-12-1.md)
  - Oracle Grid Infrastructure to 12.2 [11.11.1.1](downgrading-oracle-standalone-cluster-to-18c.md), [11.11.2.1](downgrading-oracle-standalone-cluster-to-12c-release-2-12-2.md)

------------------------------------------------------------------------

## E

- enable disk automount [6.6.2](enabling-automounting-for-windows.md)
- enterprise.rsp file [A.4.1](about-response-file-templates.md)
- Enterprise Management agent [11.9.2](updating-the-enterprise-manager-agent-base-directory-after-upgrades.md)
- environment variables
  - TEMP [2.1.5](checking-the-available-temp-disk-space.md)
- errors using Opatch [11.4](restrictions-and-guidelines-for-oracle-grid-infrastructure-upgrades.md)
- executable files [2.2](general-server-requirements.md), [6.2](understanding-oracle-asm-cluster-file-system.md)
- executeConfigTools [A.7.1](using-the-installation-response-file-for-postinstallation-configuration.md)
- external redundancy [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)

------------------------------------------------------------------------

## F

- failed install [11.12.1](completing-failed-installations-and-upgrades.md)
- failed upgrade [11.12.1](completing-failed-installations-and-upgrades.md)
- failure group
  - characteristics of Oracle ASM failure group [7.5.1](identifying-existing-oracle-asm-disk-groups-to-use.md)
- failure groups [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
  - characteristics in Oracle ASM [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
  - examples in Oracle ASM [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
  - Oracle ASM [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
- fast recovery area [10.2.3.1](about-fast-recovery-area-and-fast-recovery-area-disk-group.md)
  - filepath [B.5](optimal-flexible-architecture-file-path-examples.md)
  - Grid home
    - filepath [B.5](optimal-flexible-architecture-file-path-examples.md)
- FAT disk sizes [2.5](disk-format-requirements.md)
- files
  - dbca.rsp [A.4.1](about-response-file-templates.md)
  - enterprise.rsp [A.4.1](about-response-file-templates.md)
  - netca.rsp [A.4.1](about-response-file-templates.md)
  - removed by deinstallation [12.5.2](files-deleted-by-the-deinstallation-tool.md)
- file system
  - storage option for data files [6.3](storage-considerations-for-oracle-gird-infrastructure-and-oracle-rac.md)
- firewall
  - interconnect
    - and firewalls [3.5](windows-firewall-feature-on-windows-servers.md)
  - Microsoft Windows [3.5](windows-firewall-feature-on-windows-servers.md)
- flex redundancy [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)

------------------------------------------------------------------------

## G

- GIMR [7.3](about-grid-insfrastructure-management-repository.md), [7.3.1](guidelines-for-configuring-grid-insfrastructure-management-repository.md)
- globalization [1.7](installer-planning-checklist-for-oracle-grid-infrastructure.md)
- GNS
  - about [4.5.3](ip-name-and-address-requirements-for-grid-naming-service-gns.md)
  - choosing a subdomain name [4.5.8.1](choosing-a-subdomain-name-for-use-with-grid-naming-service.md)
  - configuring [4.5.1](about-oracle-grid-infrastructure-name-resolution-options.md)
  - configuring DNS for domain delegation [4.5.8.2](configuring-dns-for-domain-delegation-to-grid-naming-service.md)
  - name resolution [4.5.3](ip-name-and-address-requirements-for-grid-naming-service-gns.md)
  - virtual IP address [4.5.3](ip-name-and-address-requirements-for-grid-naming-service-gns.md)
- GNS client clusters
  - GNS client data file required for installation [4.5.4.1](about-multi-cluster-gns-networks.md)
  - name resolution for [4.5.4.1](about-multi-cluster-gns-networks.md)
- GNS instance [4.5.1](about-oracle-grid-infrastructure-name-resolution-options.md)
- GNS virtual IP address [1.4](oracle-grid-infrastructure-network-checklist.md)
- Grid home
  - changing location of [12.3](changing-the-oracle-grid-infrastructure-home-path.md)
  - creating [5.4.2](requirements-for-the-oracle-grid-infrastructure-home-directory.md)
  - definition [5.4.1.3](grid-home-directory.md)
  - modifying [10.4](modifying-oracle-clusterware-binaries-after-installation.md)
  - requirements [5.4.1.2](oracle-base-directory.md)
- Grid home disk space [2.1.4](checking-the-available-disk-space-for-oracle-home-directories.md)
- grid infrastructure management repository [9.3.1](about-oracle-standalone-cluster.md)
- Grid Infrastructure Management Repository
  - guidelines [7.3.1](guidelines-for-configuring-grid-insfrastructure-management-repository.md)
  - local [7.3](about-grid-insfrastructure-management-repository.md)
- grid naming service
  - See: GNS
- grid user [5.2.2](oracle-software-owner-for-each-oracle-software-product.md)
- Group Managed Service Account (GMSA) [5.1.2](about-the-oracle-home-user-for-the-oracle-grid-infrastructure-installation.md)
- groups
  - Administrators group [5.1.1](about-the-oracle-installation-user.md), [5.3.2](verifying-user-privileges-to-update-remote-nodes.md), [5.3.3](managing-user-accounts-with-user-account-control.md)
  - OINSTALL [5.1.6](understanding-the-oracle-inventory-directory-and-the-oracle-inventory-group.md)
  - ORA_DBA [5.2.3](standard-oracle-database-groups-for-database-administrators.md), [A.4.2](editing-a-response-file-template.md)
  - ORA_HOMENAME_DBA [5.2.3](standard-oracle-database-groups-for-database-administrators.md)
  - ORA_HOMENAME_OPER [5.2.3](standard-oracle-database-groups-for-database-administrators.md)
  - ORA_OPER [5.2.3](standard-oracle-database-groups-for-database-administrators.md)
  - OSASM (ORA_ASMADMIN) [5.2.4](oracle-asm-groups-for-job-role-separation.md)
  - OSDBA for ASM (ORA_ASMDBA) [5.2.4](oracle-asm-groups-for-job-role-separation.md)
  - OSOPER for ASM (ORA_ASMOPER) [5.2.4](oracle-asm-groups-for-job-role-separation.md)
  - required for Oracle Installation user [5.2.2](oracle-software-owner-for-each-oracle-software-product.md)

------------------------------------------------------------------------

## H

- hardware requirements
  - display [1.1](oracle-grid-infrastructure-installation-server-hardware-checklist.md)
  - IPMI [1.1](oracle-grid-infrastructure-installation-server-hardware-checklist.md)
  - RAM [1.1](oracle-grid-infrastructure-installation-server-hardware-checklist.md)
- high redundancy [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
- host names
  - changing [4.2.1](about-the-public-ip-address.md)
  - legal host names [1.4](oracle-grid-infrastructure-network-checklist.md)
- hosts file [4.2.1](about-the-public-ip-address.md)

------------------------------------------------------------------------

## I

- image
  - install [9.1](about-image-based-oracle-grid-infrastructure-installation.md)
- INS-40937 [5.3.2](verifying-user-privileges-to-update-remote-nodes.md)
- inst_loc [5.4.1.4](oracle-inventory-directory.md)
- installation
  - Oracle ASM requirements [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
  - response files
    - preparing [A.4](preparing-response-files.md), [A.4.3](recording-response-files.md)
  - silent mode [A.5](running-the-installer-using-a-response-file.md)
- installation planning [1](oracle-grid-infrastructure-installation-checklist.md)
- installer screens
  - Grid Plug and Play Information [4.5.2](cluster-name-and-scan-requirements.md)
- instruction sets
  - processors [2.2](general-server-requirements.md)
- interconnect [1.4](oracle-grid-infrastructure-network-checklist.md)
  - switch [4.3.2](network-requirements-for-the-private-network.md)
- interfaces [1.4](oracle-grid-infrastructure-network-checklist.md)
  - requirements for private interconnect [4.2.2](about-the-private-ip-address.md)
- intermittent hangs
  - and socket files [9.11](confirming-oracle-clusterware-function.md)
- invalid hostnames error [5.3.2](verifying-user-privileges-to-update-remote-nodes.md)
- IP addresses
  - private [4.5.5](ip-address-requirements-for-manual-configuration.md)
  - public [4.5.5](ip-address-requirements-for-manual-configuration.md)
  - requirements [4.5](oracle-grid-infrastructure-ip-name-and-address-requirements.md)
  - virtual [4.5.5](ip-address-requirements-for-manual-configuration.md)
- IPMI
  - addresses not configurable by GNS [5.5.2](configuring-the-ipmi-management-network.md)
  - configuring driver for [5.5.3](configuring-the-ipmi-driver.md)
  - preinstallation tasks [5.5](enabling-intelligent-platform-management-interface-ipmi.md)
  - preparing for installation [1.1](oracle-grid-infrastructure-installation-server-hardware-checklist.md)
  - requirements [5.5.1](requirements-for-enabling-ipmi.md)
- IPv4 requirements [4.1](about-oracle-grid-infrastructure-network-configuration-options.md)
- IPv6 requirements [4.1](about-oracle-grid-infrastructure-network-configuration-options.md)
- IPv6 support [4.3.4](ipv6-protocol-support-for-windows.md)

------------------------------------------------------------------------

## J

- JDK
  - requirements [3.4](identifying-software-requirements.md)
- job role separation users [5.2.2](oracle-software-owner-for-each-oracle-software-product.md)

------------------------------------------------------------------------

## K

- Kerberos Based Authentication for Direct NFS [8.6](enabling-direct-nfs-client.md)

------------------------------------------------------------------------

## L

- legal host names [1.4](oracle-grid-infrastructure-network-checklist.md)
- licensing [1.7](installer-planning-checklist-for-oracle-grid-infrastructure.md)
- log file
  - how to access during installation [9.5](installing-oracle-grid-infrastructure-for-a-new-cluster.md)
- lsnrctl [10.3.4](using-the-correct-lsnrctl-commands.md)

------------------------------------------------------------------------

## M

- management repository service [9.3.1](about-oracle-standalone-cluster.md)
- Media Sensing
  - disabling [4.4.1](disabling-windows-media-sensing.md)
- memory requirements
  - for Grid Infrastructure [2.3](server-minimum-hardware-and-memory-requirements.md)
  - RAM [2.1.1](checking-the-available-ram-on-windows-systems.md)
- mirroring Oracle ASM disk groups [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
- mixed binaries [3.4](identifying-software-requirements.md)
- modifying
  - Grid home [10.4](modifying-oracle-clusterware-binaries-after-installation.md)
  - Oracle ASM binaries [10.4](modifying-oracle-clusterware-binaries-after-installation.md)
  - Oracle Clusterware binaries [10.4](modifying-oracle-clusterware-binaries-after-installation.md)
- multicast DNS (mDNS) [4.8](multicast-requirements-for-networks-used-by-oracle-grid-infrastructure.md)
- Multicluster GNS [4.5.1](about-oracle-grid-infrastructure-name-resolution-options.md)
- Multiple Oracle Homes Support
  - advantages [B.2](about-multiple-oracle-homes-support.md)
- multiversioning [B.2](about-multiple-oracle-homes-support.md)
- My Oracle Support website
  - about [3.7](checking-hardware-and-software-certification-on-my-oracle-support.md)
  - accessing [3.7](checking-hardware-and-software-certification-on-my-oracle-support.md)

------------------------------------------------------------------------

## N

- NAS [6.4.2](guidelines-for-using-direct-network-file-system-nfs-with-oracle-rac.md)
- netca.rsp file [A.4.1](about-response-file-templates.md)
- Net Configuration Assistant
  - See: Oracle Net Configuration Assistant (NETCA)
- netsh [4.9](multiple-private-interconnects-on-microsoft-windows-platforms.md)
- network file system (NFS) [2.5](disk-format-requirements.md), [6.1](configuring-shared-storage-for-oracle-grid-infrastructure-oracle-rac.md), [6.4.2](guidelines-for-using-direct-network-file-system-nfs-with-oracle-rac.md), [8.1](about-direct-nfs-client-storage.md)
  - See also: Direct NFS Client
- Network Information Services (NIS) [5.2.1](about-job-role-separation-operating-system-privileges-groups-and-users.md)
- networks
  - IP protocol requirements for [4.1](about-oracle-grid-infrastructure-network-configuration-options.md)
- Network Time Protocol [2.6.2](understanding-network-time-requirements.md), [2.6.5](configuring-cluster-time-synchronization-service.md)
- Network Time Protocol;Windows Time Service [2.6.1](about-cluster-time-synchronization.md)
- noninteractive mode
  - See: response file mode
- normal redundancy [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
- NTFS [2.5](disk-format-requirements.md)
  - formatted disks [2.5](disk-format-requirements.md)
- NTP
  - See: Network Time Protocol

------------------------------------------------------------------------

## O

- OCFS for Windows
  - upgrading [11.2](about-oracle-grid-infrastructure-and-oracle-asm-upgrade-and-downgrade.md)
- OCR
  - See: Oracle Cluster Registry
- OFA [B.1](about-the-optimal-flexible-architecture-standard.md)
  - See also: Optimal Flexible Architecture
- oifcfg [4.2.2](about-the-private-ip-address.md)
- OINSTALL directory [B.5](optimal-flexible-architecture-file-path-examples.md)
- Opatch [11.4](restrictions-and-guidelines-for-oracle-grid-infrastructure-upgrades.md)
- operating system
  - 32–bit [2.1.3](checking-the-system-processor-type.md)
  - Administrators group [5.1.1](about-the-oracle-installation-user.md), [5.3.2](verifying-user-privileges-to-update-remote-nodes.md), [5.3.3](managing-user-accounts-with-user-account-control.md)
  - different versions on cluster members [3.4](identifying-software-requirements.md)
  - mixed versions [3.1.3](rolling-upgrade-procedure-notifications.md)
  - requirements [3.4](identifying-software-requirements.md)
  - using different versions [3.4](identifying-software-requirements.md)
  - version checks [3.4](identifying-software-requirements.md)
  - x86 [2.1.3](checking-the-system-processor-type.md)
- operating system groups [5.2.1](about-job-role-separation-operating-system-privileges-groups-and-users.md)
- operating system requirements [1.2](operating-system-checklist-for-oracle-grid-infrastructure-and-oracle-rac.md)
- Optimal Flexible Architecture
  - about [B.1](about-the-optimal-flexible-architecture-standard.md)
- ORA_DBA group [A.4.2](editing-a-response-file-template.md)
  - and SYSDBA privilege [5.2.3](standard-oracle-database-groups-for-database-administrators.md)
  - description [5.2.3](standard-oracle-database-groups-for-database-administrators.md)
- ORA_HOMENAME_DBA group
  - and SYSDBA privilege [5.2.3](standard-oracle-database-groups-for-database-administrators.md)
  - description [5.2.3](standard-oracle-database-groups-for-database-administrators.md)
- ORA_HOMENAME_OPER group
  - and SYSOPER privilege [5.2.3](standard-oracle-database-groups-for-database-administrators.md)
  - description [5.2.3](standard-oracle-database-groups-for-database-administrators.md)
- ORA_INSTALL group [5.1.6](understanding-the-oracle-inventory-directory-and-the-oracle-inventory-group.md)
  - See also: Oracle Inventory group
- ORA_OPER group
  - and SYSOPER privilege [5.2.3](standard-oracle-database-groups-for-database-administrators.md)
  - description [5.2.3](standard-oracle-database-groups-for-database-administrators.md)
- Oracle ACFS
  - and Oracle Clusterware files [6.2](understanding-oracle-asm-cluster-file-system.md)
  - restrictions and guidelines for usage [6.2](understanding-oracle-asm-cluster-file-system.md)
- Oracle ADVM [6.2](understanding-oracle-asm-cluster-file-system.md)
- Oracle ASM
  - and Oracle Clusterware files [2.1.4](checking-the-available-disk-space-for-oracle-home-directories.md)
  - asmtoolg utility [7.6.1](using-asmtoolg-graphical-user-interface-to-mark-disks.md)
  - asmtool utility reference [7.6.3](asmtool-command-line-reference.md)
  - characteristics of failure groups [7.5.1](identifying-existing-oracle-asm-disk-groups-to-use.md)
  - disk groups
    - recommendations for [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
    - redundancy levels [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
  - failure groups [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
    - characteristics [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
    - examples [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
    - identifying [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
  - mirroring [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
  - partitions
    - marking [7.6](configuring-marking-disk-partitions-for-asm.md)
    - restrictions [7.4](restrictions-for-disk-partitions-used-by-oracle-asm.md)
  - redundancy levels [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
  - space required for Oracle Clusterware files [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
  - space required for preconfigured database [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
  - upgrading [11.2](about-oracle-grid-infrastructure-and-oracle-asm-upgrade-and-downgrade.md)
- Oracle ASM redundancy levels
  - high redundancy [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
- Oracle Automatic Storage Management (Oracle ASM)
  - password file [11.5.3](create-oracle-asm-password-file-win.md)
- Oracle base [B.1](about-the-optimal-flexible-architecture-standard.md), [B.5](optimal-flexible-architecture-file-path-examples.md)
- Oracle base directory [5.4.1.2](oracle-base-directory.md)
  - creating [5.4.3](about-creating-the-oracle-base-directory-path.md)
  - Grid home must not be in an Oracle Database Oracle base [5.4.1.2](oracle-base-directory.md)
- Oracle Cluster Registry
  - configuration of [1.6](storage-checklist-for-oracle-grid-infrastructure.md)
  - supported storage options [6.1](configuring-shared-storage-for-oracle-grid-infrastructure-oracle-rac.md)
- Oracle Clusterware
  - installing [9](installing-oracle-grid-infrastructure-for-a-cluster.md)
  - supported storage options for [6.1](configuring-shared-storage-for-oracle-grid-infrastructure-oracle-rac.md)
- Oracle Clusterware files [6.1](configuring-shared-storage-for-oracle-grid-infrastructure-oracle-rac.md), [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
  - and NTFS formatted disks [2.5](disk-format-requirements.md)
  - and Oracle ACFS [6.2](understanding-oracle-asm-cluster-file-system.md)
  - and Oracle ASM [2.1.4](checking-the-available-disk-space-for-oracle-home-directories.md)
  - Oracle ASM disk space requirements [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
  - Oracle ASM requirements [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
  - raw partitions [2.1.4](checking-the-available-disk-space-for-oracle-home-directories.md)
- Oracle Database
  - data file storage options [6.3](storage-considerations-for-oracle-gird-infrastructure-and-oracle-rac.md)
  - privileged groups [5.2.2](oracle-software-owner-for-each-oracle-software-product.md)
  - requirements with Oracle ASM [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
- Oracle Disk Manager (ODM) [8.1](about-direct-nfs-client-storage.md)
  - library file [8.6](enabling-direct-nfs-client.md)
- Oracle Enterprise Manager [11.9.3](registering-resources-with-enterprise-manager-after-upgrades.md)
  - firewall exceptions [10.1.2.6](firewall-exceptions-for-oracle-rac-database.md)
- Oracle Extended Clusters [9.3.2](about-oracle-extended-clusters.md)
- Oracle Grid Infrastructure
  - upgrading [11.2](about-oracle-grid-infrastructure-and-oracle-asm-upgrade-and-downgrade.md)
- Oracle Grid Infrastructure owner (grid) [5.2.2](oracle-software-owner-for-each-oracle-software-product.md)
- Oracle home
  - ASCII path restriction for [1.3](server-configuration-checklist-for-oracle-grid-infrastructure.md), [1.5](user-environment-configuration-checklist-for-oracle-grid-infrastructure.md)
  - definition [5.4.1.3](grid-home-directory.md)
  - file path [B.5](optimal-flexible-architecture-file-path-examples.md)
  - Grid home
    - filepath [B.5](optimal-flexible-architecture-file-path-examples.md)
  - naming conventions [B.4](oracle-home-directory-naming-convention.md)
- Oracle Home User
  - See: Oracle Service User

  <!-- -->

  - permissions [9.4](about-default-file-permissions-set-by-oracle-universal-installer.md)
- Oracle Installation user
  - required group membership [5.2.2](oracle-software-owner-for-each-oracle-software-product.md)
- Oracle Installation User
  - permissions [9.4](about-default-file-permissions-set-by-oracle-universal-installer.md)
- Oracle Inventory directory
  - definition [5.4.1.4](oracle-inventory-directory.md)
- Oracle Inventory group
  - about [5.1.6](understanding-the-oracle-inventory-directory-and-the-oracle-inventory-group.md)
  - checking for existing [5.1.6](understanding-the-oracle-inventory-directory-and-the-oracle-inventory-group.md)
- Oracle Net Configuration Assistant (NETCA)
  - response file [A.4.1](about-response-file-templates.md)
  - response files [A.6](running-oracle-net-configuration-assistant-using-response-files.md)
  - running at command prompt [A.6](running-oracle-net-configuration-assistant-using-response-files.md)
- Oracle Notification Server Configuration Assistant [9.5](installing-oracle-grid-infrastructure-for-a-new-cluster.md)
- Oracle Optimal Flexible Architecture
  - See: Optimal Flexible Architecture
- Oracle ORAchk
  - and Upgrade Readiness Assessment [1.7](installer-planning-checklist-for-oracle-grid-infrastructure.md)
- Oracle Private Interconnect Configuration Assistant [9.5](installing-oracle-grid-infrastructure-for-a-new-cluster.md)
- Oracle Restart
  - password file [A.7.1](using-the-installation-response-file-for-postinstallation-configuration.md)
- Oracle Service User [5.1.2](about-the-oracle-home-user-for-the-oracle-grid-infrastructure-installation.md), [5.1.3](about-the-oracle-home-user-for-the-oracle-rac-installation.md)
- Oracle software owner user
  - creating [5.1.1](about-the-oracle-installation-user.md)
  - description [5.2.2](oracle-software-owner-for-each-oracle-software-product.md)
- Oracle Standalone Clusters [9.3.1](about-oracle-standalone-cluster.md)
- Oracle Universal Installer
  - default permissions [9.4](about-default-file-permissions-set-by-oracle-universal-installer.md)
- Oracle Universal Installer (OUI)
  - response files [A.4.1](about-response-file-templates.md)
- Oracle Upgrade Companion [3.1.1](general-upgrade-best-practices.md)
- oracle user
  - creating [5.1.1](about-the-oracle-installation-user.md)
  - description [5.2.2](oracle-software-owner-for-each-oracle-software-product.md)
  - required group membership [5.2.2](oracle-software-owner-for-each-oracle-software-product.md)
- ORADNFS utility [8.7](performing-basic-file-operations-using-the-oradnfs-utility.md)
- oraInventory [5.2.2](oracle-software-owner-for-each-oracle-software-product.md), [B.5](optimal-flexible-architecture-file-path-examples.md)
  - See: Oracle Inventory Directory

  <!-- -->

  - about [5.1.6](understanding-the-oracle-inventory-directory-and-the-oracle-inventory-group.md)
- oranfstab file
  - creating [8.2](creating-an-oranfstab-file-for-direct-nfs-client.md)
- OSASM group [5.2.4](oracle-asm-groups-for-job-role-separation.md)
  - about [5.2.4](oracle-asm-groups-for-job-role-separation.md)
- OSDBA for ASM group [5.2.4](oracle-asm-groups-for-job-role-separation.md)
  - about [5.2.4](oracle-asm-groups-for-job-role-separation.md)
- OSOPER for ASM group [5.2.4](oracle-asm-groups-for-job-role-separation.md)
  - about [5.2.4](oracle-asm-groups-for-job-role-separation.md)
- OUI
  - See: Oracle Universal Installer (OUI)

------------------------------------------------------------------------

## P

- paging file [1.1](oracle-grid-infrastructure-installation-server-hardware-checklist.md), [2.1.2](checking-the-currently-configured-virtual-memory-on-windows-systems.md), [2.3](server-minimum-hardware-and-memory-requirements.md)
- Parallel NFS [8.1](about-direct-nfs-client-storage.md)
- partitions
  - using with Oracle ASM [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
- password file [A.8.2](creating-a-password-response-file.md)
  - Oracle ASM, required for upgrade [11.5.3](create-oracle-asm-password-file-win.md)
- patch updates [10.1.1](downloading-and-installing-patch-updates.md)
- permissions
  - Administrators [9.4](about-default-file-permissions-set-by-oracle-universal-installer.md)
  - Authenticated Users group [9.4](about-default-file-permissions-set-by-oracle-universal-installer.md)
  - Oracle Home User [9.4](about-default-file-permissions-set-by-oracle-universal-installer.md)
  - Oracle Installation User [9.4](about-default-file-permissions-set-by-oracle-universal-installer.md)
  - SYSTEM [9.4](about-default-file-permissions-set-by-oracle-universal-installer.md)
- physical RAM
  - requirements [2.3](server-minimum-hardware-and-memory-requirements.md)
- policy-managed databases
  - and SCAN [4.2.5](about-the-scan.md)
- postinstallation
  - backing up voting files [10.1](required-postinstallation-tasks.md)
  - configuration of Oracle software [A.7.1](using-the-installation-response-file-for-postinstallation-configuration.md), [A.8.1](about-the-postinstallation-configuration-file.md)
  - recommended tasks [10.2](recommended-postinstallation-tasks.md)
  - required tasks [10.1](required-postinstallation-tasks.md)
  - resource status OFFLINE [9.13](understanding-offline-processes-in-oracle-grid-infrastructure.md)
- preconfigured database
  - Oracle ASM disk space requirements [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
  - requirements when using Oracle ASM [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
- preinstallation
  - verifying installation requirements [9.7](installing-software-binaries-for-oracle-grid-infrastructure.md)
- primary host name [1.4](oracle-grid-infrastructure-network-checklist.md)
- private IP addresses [4.5.5](ip-address-requirements-for-manual-configuration.md)
- privileged groups
  - for Oracle Database [5.2.2](oracle-software-owner-for-each-oracle-software-product.md)
- privileges
  - verifying for OUI cluster installation [5.3.2](verifying-user-privileges-to-update-remote-nodes.md)
- processors
  - instruction sets [2.2](general-server-requirements.md)
  - minimum requirements [2.3](server-minimum-hardware-and-memory-requirements.md)
- proxy realm [1.7](installer-planning-checklist-for-oracle-grid-infrastructure.md)
- public IP addresses [4.5.5](ip-address-requirements-for-manual-configuration.md)
- public node name
  - and primary host name [1.4](oracle-grid-infrastructure-network-checklist.md)

------------------------------------------------------------------------

## Q

- quorum failure group [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)

------------------------------------------------------------------------

## R

- RAID
  - recommended Oracle ASM redundancy level [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
- RAM
  - requirements [2.3](server-minimum-hardware-and-memory-requirements.md)
- raw partitions [2.5](disk-format-requirements.md)
- recommendataions
  - backing up Oracle software [11.5.1](upgrade-checklist-for-oracle-grid-infrastructure.md)
- recommendations
  - client access to the cluster [10.2.4](checking-the-scan-configuration.md)
  - configuring BMC [5.5.2](configuring-the-ipmi-management-network.md)
  - enable disk automounting [6.6.2](enabling-automounting-for-windows.md)
  - for creating Oracle Grid Infrastructure home and Oracle Inventory directories [5.4.1.3](grid-home-directory.md)
  - for using NTFS formatted disks [2.5](disk-format-requirements.md)
  - limiting the number of partitions on a single disk [7.4](restrictions-for-disk-partitions-used-by-oracle-asm.md)
  - managing Oracle Clusterware files [2.5](disk-format-requirements.md)
  - managing Oracle Database data files [2.5](disk-format-requirements.md)
  - minimum RAM size [2.1.1](checking-the-available-ram-on-windows-systems.md)
  - number of IP address for SCAN resolution [4.2.5](about-the-scan.md), [4.5.5](ip-address-requirements-for-manual-configuration.md)
  - Oracle ASM redundancy level [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
  - postinstallation tasks [10.2](recommended-postinstallation-tasks.md)
  - private network [4.2.2](about-the-private-ip-address.md)
  - secure response files after modification [A.4.2](editing-a-response-file-template.md)
  - temporary directory configuration [5.4.1.1](temporary-directories.md)
  - using static host names [4.5.1](about-oracle-grid-infrastructure-name-resolution-options.md)
- recovery files
  - and NFS [6.4.2](guidelines-for-using-direct-network-file-system-nfs-with-oracle-rac.md)
  - required disk space [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
  - supported storage options [6.1](configuring-shared-storage-for-oracle-grid-infrastructure-oracle-rac.md)
- redundancy level
  - and space requirements for preconfigured database [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
  - for Oracle ASM [7.1](identifying-storage-requirements-for-using-oracle-asm-for-shared-storage.md)
- registering resources [11.9.3](registering-resources-with-enterprise-manager-after-upgrades.md)
- Registry keys
  - Tcpip
    - parameters [4.4.1](disabling-windows-media-sensing.md)
  - W32Time:Config [2.6.3](configuring-the-windows-time-service.md)
- releases
  - multiple [B.2](about-multiple-oracle-homes-support.md)
- release update revisions [10.1.1](downloading-and-installing-patch-updates.md)
- release updates [10.1.1](downloading-and-installing-patch-updates.md)
- remove Oracle software [12](modifying-or-deinstalling-oracle-grid-infrastructure.md)
- requirements
  - hardware certification [3.7](checking-hardware-and-software-certification-on-my-oracle-support.md)
  - memory [2.3](server-minimum-hardware-and-memory-requirements.md)
  - processors [2.3](server-minimum-hardware-and-memory-requirements.md)
  - software certification [3.7](checking-hardware-and-software-certification-on-my-oracle-support.md)
  - temporary disk space [2.1.5](checking-the-available-temp-disk-space.md)
- resource status OFFLINE [9.13](understanding-offline-processes-in-oracle-grid-infrastructure.md)
- response file mode [A.1](how-response-files-work.md)
  - See also: response files

  <!-- -->

  - about [A.1](how-response-files-work.md)
  - installation [A.5](running-the-installer-using-a-response-file.md)
    - preparing [A.4](preparing-response-files.md)
  - reasons for using [A.2](deciding-to-use-silent-mode-or-response-file-mode.md)
- response files
  - about [A.1](how-response-files-work.md)
  - creating with template [A.4.1](about-response-file-templates.md), [A.4.2](editing-a-response-file-template.md)
  - crs_install.rsp [A.4.2](editing-a-response-file-template.md)
  - dbca.rsp [A.4.1](about-response-file-templates.md)
  - enterprise.rsp [A.4.1](about-response-file-templates.md)
  - general procedure [A.3](general-procedure-for-using-response-files.md)
  - netca.rsp [A.4.1](about-response-file-templates.md)
  - Oracle Net Configuration Assistant (NETCA) [A.6](running-oracle-net-configuration-assistant-using-response-files.md)
  - passing values at command line [A.1](how-response-files-work.md)
  - reasons for using [A.2](deciding-to-use-silent-mode-or-response-file-mode.md)
  - specifying with the installer [A.5](running-the-installer-using-a-response-file.md)
- reverse lookup [4.5.8.2](configuring-dns-for-domain-delegation-to-grid-naming-service.md)
- rootcrs.bat
  - restriction for Flex Cluster deinstallation [12.4](unconfiguring-oracle-clusterware-without-removing-the-software.md)
- running multiple Oracle releases [B.2](about-multiple-oracle-homes-support.md)

------------------------------------------------------------------------

## S

- SCAN
  - client access [10.2.4](checking-the-scan-configuration.md)
  - description [10.2.4](checking-the-scan-configuration.md)
  - required for clients of policy-managed databases [4.2.5](about-the-scan.md)
  - shared [4.2.6](about-shared-scan.md)
  - understanding [4.2.5](about-the-scan.md)
- SCAN address [1.4](oracle-grid-infrastructure-network-checklist.md)
- SCAN addresses [4.2.5](about-the-scan.md), [4.5.9](manual-ip-address-configuration-example.md)
- SCAN listeners [4.2.5](about-the-scan.md), [10.3.4](using-the-correct-lsnrctl-commands.md)
- SCANs [1.4](oracle-grid-infrastructure-network-checklist.md)
  - configuring [1.4](oracle-grid-infrastructure-network-checklist.md)
- setup.bat [A.5](running-the-installer-using-a-response-file.md)
- shared SCAN [4.2.6](about-shared-scan.md)
- silent mode
  - See: response file moderesponse files.
- single client access names
  - See: SCAN addresses
- socket files [9.11](confirming-oracle-clusterware-function.md)
- software
  - removing [12.5.1](about-the-deinstallation-tool.md)
  - uninstalling [12.5.1](about-the-deinstallation-tool.md)
- software requirements [3.4](identifying-software-requirements.md)
- space requirements [7.2](oracle-clusterware-storage-requirements.md)
- supported storage options
  - Grid home [2.5](disk-format-requirements.md)
  - My Oracle Support website [3.7](checking-hardware-and-software-certification-on-my-oracle-support.md)
  - Oracle Clusterware [6.1](configuring-shared-storage-for-oracle-grid-infrastructure-oracle-rac.md)
- switch
  - recommendations
    - using a dedicated switch [4.3.2](network-requirements-for-the-private-network.md)
- SYSASM [5.2.4](oracle-asm-groups-for-job-role-separation.md)
- SYSBACKUP [5.2.5](extended-oracle-database-administration-groups-for-job-role-separation.md)
- SYSDBA privilege
  - associated group [5.2.3](standard-oracle-database-groups-for-database-administrators.md)
- SYSDG [5.2.5](extended-oracle-database-administration-groups-for-job-role-separation.md)
- SYSKM [5.2.5](extended-oracle-database-administration-groups-for-job-role-separation.md)
- SYSOPER privilege
  - associated group [5.2.3](standard-oracle-database-groups-for-database-administrators.md)
- SYSRAC [5.2.5](extended-oracle-database-administration-groups-for-job-role-separation.md)
- system requirements [1](oracle-grid-infrastructure-installation-checklist.md)
  - for Grid Infrastructure [2.3](server-minimum-hardware-and-memory-requirements.md)
  - latest information [3.7](checking-hardware-and-software-certification-on-my-oracle-support.md)
  - memory [2.1.1](checking-the-available-ram-on-windows-systems.md)
- SYSTEM user
  - permissions [9.4](about-default-file-permissions-set-by-oracle-universal-installer.md)

------------------------------------------------------------------------

## T

- TCP [4.3.2](network-requirements-for-the-private-network.md)
- TEMP environment variable [2.1.5](checking-the-available-temp-disk-space.md)
- temporary disk space
  - requirements [2.1.5](checking-the-available-temp-disk-space.md)
- to 12c release 1 (12.1.0.2) [11.11.3](downgrading-to-oracle-grid-infrastructure-12c-release-1-12-1.md)
- troubleshooting
  - and deinstalling [12.1](deciding-when-to-deinstall-oracle-clusterware.md)
  - cron jobs and installation [1.7](installer-planning-checklist-for-oracle-grid-infrastructure.md)
  - DBCA does not recognize Oracle ASM disk size and fails to create disk groups [10.3.3](using-asmca-to-administer-disk-groups-for-earlier-database-releases.md)
  - deconfiguring Oracle Clusterware to fix causes of installation errors [12.4](unconfiguring-oracle-clusterware-without-removing-the-software.md)
  - disk space errors [1.3](server-configuration-checklist-for-oracle-grid-infrastructure.md), [1.5](user-environment-configuration-checklist-for-oracle-grid-infrastructure.md)
  - environment path errors [1.3](server-configuration-checklist-for-oracle-grid-infrastructure.md), [1.5](user-environment-configuration-checklist-for-oracle-grid-infrastructure.md)
  - installation errors [12.4](unconfiguring-oracle-clusterware-without-removing-the-software.md)
  - installation owner environment variables and installation errors [11.5.2](tasks-to-complete-before-upgrading-grid-infrastructure.md)
  - intermittent hangs [9.11](confirming-oracle-clusterware-function.md)
  - log file [9.5](installing-oracle-grid-infrastructure-for-a-new-cluster.md)
  - permissions errors and oraInventory [5.1.6](understanding-the-oracle-inventory-directory-and-the-oracle-inventory-group.md)
  - unset environment variables [1.3](server-configuration-checklist-for-oracle-grid-infrastructure.md)

------------------------------------------------------------------------

## U

- UAC remote restrictions [5.3.2](verifying-user-privileges-to-update-remote-nodes.md)
- unconfiguring Oracle Clusterware [12.4](unconfiguring-oracle-clusterware-without-removing-the-software.md)
- uninstall [12.1](deciding-when-to-deinstall-oracle-clusterware.md)
  - Oracle software [12](modifying-or-deinstalling-oracle-grid-infrastructure.md)
- unset installation owners environment variables [11.5.2](tasks-to-complete-before-upgrading-grid-infrastructure.md)
- upgrade
  - Oracle Grid Infrastructure 12.1
    - create Oracle ASM password file [11.5.3](create-oracle-asm-password-file-win.md)
- upgrades
  - and SCAN [4.2.5](about-the-scan.md)
  - best practices [3.1.1](general-upgrade-best-practices.md)
  - checklist [11.5.1](upgrade-checklist-for-oracle-grid-infrastructure.md)
  - Oracle ASM [3.1.2](oracle-asm-upgrade-notifications.md), [11.2](about-oracle-grid-infrastructure-and-oracle-asm-upgrade-and-downgrade.md)
  - Oracle Grid Infrastructure [11.2](about-oracle-grid-infrastructure-and-oracle-asm-upgrade-and-downgrade.md)
  - restrictions [11.4](restrictions-and-guidelines-for-oracle-grid-infrastructure-upgrades.md)
  - standalone database [3.1.2](oracle-asm-upgrade-notifications.md)
  - unsetting environment variables [11.5.2](tasks-to-complete-before-upgrading-grid-infrastructure.md)
- upgrade tasks [11.9.3](registering-resources-with-enterprise-manager-after-upgrades.md)
- upgrading
  - and Oracle ORAchk Upgrade Readiness Assessment [1.7](installer-planning-checklist-for-oracle-grid-infrastructure.md)
  - batches [11.6](understanding-rolling-upgrades-using-batches.md)
  - groups of nodes [11.6](understanding-rolling-upgrades-using-batches.md)
- user
  - domain [5.1.1](about-the-oracle-installation-user.md)
  - Oracle Service User [5.1.2](about-the-oracle-home-user-for-the-oracle-grid-infrastructure-installation.md), [5.1.3](about-the-oracle-home-user-for-the-oracle-rac-installation.md)
- User Account Control settings [5.3.3](managing-user-accounts-with-user-account-control.md)
- users
  - creating the grid user [5.1.1](about-the-oracle-installation-user.md)
  - Oracle software owner user (oracle) [5.2.2](oracle-software-owner-for-each-oracle-software-product.md)

------------------------------------------------------------------------

## V

- video adapter requirements [2.3](server-minimum-hardware-and-memory-requirements.md)
- virtual IP addresses [4.5.5](ip-address-requirements-for-manual-configuration.md)
- virtual local area network [4.7](broadcast-requirements-for-networks-used-by-oracle-grid-infrastructure.md)
- virtual memory [1.1](oracle-grid-infrastructure-installation-server-hardware-checklist.md)
  - requirements [2.3](server-minimum-hardware-and-memory-requirements.md)
- VLAN
  - virtual local area network [4.7](broadcast-requirements-for-networks-used-by-oracle-grid-infrastructure.md)
- voting files
  - backing up [10.1](required-postinstallation-tasks.md)
  - configuration of [1.6](storage-checklist-for-oracle-grid-infrastructure.md)
  - supported storage options [6.1](configuring-shared-storage-for-oracle-grid-infrastructure-oracle-rac.md)

------------------------------------------------------------------------

## W

- W32Time [2.6.3](configuring-the-windows-time-service.md)
- weakhostsend [4.9](multiple-private-interconnects-on-microsoft-windows-platforms.md)
- Windows
  - supported operating system versions [3.4](identifying-software-requirements.md)
- Windows Media Sensing
  - disabling [4.4.1](disabling-windows-media-sensing.md)
- Windows registry
  - backup before upgrades [11.5.1](upgrade-checklist-for-oracle-grid-infrastructure.md)
- Windows Time Service [2.6.2](understanding-network-time-requirements.md), [2.6.5](configuring-cluster-time-synchronization-service.md)
  - configuring [2.6.3](configuring-the-windows-time-service.md)

------------------------------------------------------------------------

## X

- x64 software versions [2.3](server-minimum-hardware-and-memory-requirements.md)
- x86 software versions [2.3](server-minimum-hardware-and-memory-requirements.md)
