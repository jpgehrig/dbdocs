A  B  C  D  E  F  G  H  I  J  K  L  M  N  O  P  R  S  T  U  V  X  Z  

------------------------------------------------------------------------

## A

- adding Oracle ASM listener [11.10.3](registering-listener-with-em-after-gi-upgrade.md)
- apply patches during install
  - apply patches during upgrade [11.9.3.1](applying-patches-during-oracle-grid-infrastructure-install-or-upgrade.md)
- ASM_DISKSTRING [8.1.7](specifying-oracle-asm-discovery-string.md)
- asmadmin groups
  - creating [6.3.1](creating-osasm-group.md)
- ASMCA
  - Used to create disk groups for older Oracle Database releases on Oracle ASM [10.4.4](using-asmca-to-administer-disk-groups-for-earlier-database-releases.md)
- asmdba groups
  - creating [6.3.2](creating-the-osdba-for-asm-group.md)
- asmoper group
  - creating [6.3.3](creating-the-osoper-for-asm-group.md)
- ASMSNMP [1.4](network-checklist-for-oracle-grid-infrastructure.md)
- Automatic Diagnostic Repository (ADR) [D.1](about-the-optimal-flexible-architecture-standard.md)
- Automatic Storage Management Cluster File System
  - See: Oracle ACFS.

------------------------------------------------------------------------

## B

- backupdba group
  - creating [6.3.6](creating-the-osbackupdba-group-for-database-installations.md)
- Bash shell
  - default user startup file [6.5.2](procedure-for-configuring-oracle-software-owner-environments.md)
- batch upgrade [11.6](understanding-rolling-upgrades-using-batches.md)
- binaries
  - relinking [10.5](modifying-oracle-clusterware-binaries-after-installation.md)
- binary files
  - supported storage options for [7.1](supported-storage-options-for-oracle-grid-infrastructure.md)
- BMC
  - configuring [6.7.3](configuring-the-bmc.md)
- BMC interface
  - preinstallation tasks [6.7](enabling-intelligent-platform-management-interface-ipmi.md)
- Bourne shell
  - default user startup file [6.5.2](procedure-for-configuring-oracle-software-owner-environments.md)

------------------------------------------------------------------------

## C

- central inventory [D.6](optimal-flexible-architecture-file-path-examples.md)
  - See: Oracle inventory directory

  <!-- -->

  - See also: OINSTALL directory, oraInventory
- checkdir error [10.5](modifying-oracle-clusterware-binaries-after-installation.md), [11.4](restrictions-for-oracle-grid-infrastructure-upgrades.md)
- checklists [1](system-hardware-software-and-configuration-checklists.md)
- client-server configurations [D.2](about-multiple-oracle-homes-support.md)
- CLUSTER_INTERCONNECTS parameter [5.2.2](about-the-private-ip-address.md)
- cluster configuration
  - Oracle Domain Services Cluster [9.3.2](about-oracle-domain-services-clusters.md)
  - Oracle Extended Clusters [9.3.4](about-oracle-extended-clusters.md)
  - Oracle Member Clusters [9.3.3](about-oracle-member-clusters.md)
  - Oracle Standalone Clusters [9.3.1](about-oracle-standalone-clusters.md)
- cluster file system
  - storage option for data files [7.3](storage-considerations-for-oracle-grid-infrastructure-and-oracle-rac.md)
- cluster name [1.4](network-checklist-for-oracle-grid-infrastructure.md)
  - requirements for [1.4](network-checklist-for-oracle-grid-infrastructure.md)
- cluster nodes
  - private network node interfaces [1.4](network-checklist-for-oracle-grid-infrastructure.md)
  - public network node names and addresses [1.4](network-checklist-for-oracle-grid-infrastructure.md)
  - virtual node names [1.4](network-checklist-for-oracle-grid-infrastructure.md), [5.2.3](about-the-virtual-ip-address.md)
- Cluster Time Synchronization Service [4.13](setting-network-time-protocol-for-cluster-time-synchronization.md)
- clusterware
  - requirements for third party clusterware [1.4](network-checklist-for-oracle-grid-infrastructure.md)
- Clusterware Installation [9.4.1](about-oracle-grid-infrastructure-installation.md)
- commands
  - /usr/sbin/swap [2.2](checking-server-hardware-and-memory-configuration.md)
  - asmca [8.6](configuring-oracle-automatic-storage-management-cluster-file-system.md)
  - asmcmd [8.1.4](using-an-existing-oracle-asm-disk-group.md)
  - crsctl [11.4](restrictions-for-oracle-grid-infrastructure-upgrades.md)
  - df -h [2.2](checking-server-hardware-and-memory-configuration.md)
  - df -k [2.2](checking-server-hardware-and-memory-configuration.md)
  - grep "Memory size" [2.2](checking-server-hardware-and-memory-configuration.md)
  - gridSetup.sh [9.6.1](installing-software-binaries-for-oracle-grid-infrastructure-for-a-cluster.md)
  - ipadm [8.4.2](checking-tcp-network-protocol-buffer-for-direct-nfs-client.md)
  - ndd [8.4.2](checking-tcp-network-protocol-buffer-for-direct-nfs-client.md)
  - nscd [4.12](enabling-the-name-service-cache-daemon.md)
  - root.sh [10.2.2](creating-a-backup-of-the-root-sh-script.md)
  - rootcrs.pl
    - and deconfig option [12.8](unconfiguring-oracle-clusterware-without-removing-binaries.md)
  - rootcrs.sh [10.5](modifying-oracle-clusterware-binaries-after-installation.md)
  - rootupgrade.sh [11.4](restrictions-for-oracle-grid-infrastructure-upgrades.md)
  - runcluvfy.sh [9.6.1](installing-software-binaries-for-oracle-grid-infrastructure-for-a-cluster.md)
  - srvctl [11.4](restrictions-for-oracle-grid-infrastructure-upgrades.md)
  - umask [6.5.1](environment-requirements-for-oracle-software-owners.md)
  - unset [11.5.2](checks-to-complete-before-upgrading-oracle-clusterware.md)
  - useradd [6.4.1](creating-an-oracle-software-owner-user.md)
- cron jobs [1.8](installer-planning-checklist-for-oracle-grid-infrastructure.md)
- C shell
  - default user startup file [6.5.2](procedure-for-configuring-oracle-software-owner-environments.md)
- ctsdd [4.13](setting-network-time-protocol-for-cluster-time-synchronization.md)
- custom database
  - failure groups for Oracle ASM [8.1.1](identifying-storage-requirements-for-oracle-automatic-storage-management.md)
  - requirements when using Oracle ASM [8.1.1](identifying-storage-requirements-for-oracle-automatic-storage-management.md)

------------------------------------------------------------------------

## D

- Database Configuration Assistant
  - running in silent mode [A.6](running-configuration-assistants-using-response-files.md)
- databases
  - Oracle ASM requirements [8.1.1](identifying-storage-requirements-for-oracle-automatic-storage-management.md)
- data files
  - storage options [7.3](storage-considerations-for-oracle-grid-infrastructure-and-oracle-rac.md)
  - supported storage options for [7.1](supported-storage-options-for-oracle-grid-infrastructure.md)
- data loss
  - minimizing with Oracle ASM [8.1.1](identifying-storage-requirements-for-oracle-automatic-storage-management.md), [8.3.1](identifying-and-using-existing-oracle-database-disk-groups-on-oracle-asm.md)
- DB_RECOVERY_FILE_DEST [10.2.4.1](about-the-fast-recovery-area-and-the-fast-recovery-area-disk-group.md)
- DB_RECOVERY_FILE_DEST_SIZE [10.2.4.1](about-the-fast-recovery-area-and-the-fast-recovery-area-disk-group.md)
- dba group
  - creating [6.3.4](creating-the-osdba-group-for-database-installations.md)
  - description [6.2.2](standard-oracle-database-groups-for-database-administrators.md)
  - SYSDBA privilege [6.2.2](standard-oracle-database-groups-for-database-administrators.md)
- dba groups
  - creating [6.3.8](creating-the-oskmdba-group-for-database-installations.md), [6.3.9](creating-the-osracdba-group.md)
- DBCA
  - no longer used for Oracle ASM disk group administration [10.4.4](using-asmca-to-administer-disk-groups-for-earlier-database-releases.md)
- dbca.rsp file [A.4.1](editing-a-response-file-template.md)
- default file mode creation mask
  - setting [6.5.1](environment-requirements-for-oracle-software-owners.md)
- deinstall [12.1](about-oracle-deinstallation-options.md), [12.2](oracle-deinstallation-tool-deinstall.md)
  - See: removing Oracle software

  <!-- -->

  - Oracle Member Cluster [12.9](unconfiguring-oracle-member-clusters.md)
- deinstallation [12.1](about-oracle-deinstallation-options.md)
  - examples [12.3](deinstallation-examples-for-oracle-database.md)
- Deinstallation tool
  - Restriction for Oracle Flex Clusters and -lastnode flag [12.8](unconfiguring-oracle-clusterware-without-removing-binaries.md)
- deinstall command [12.1](about-oracle-deinstallation-options.md)
- df command [6.5.2](procedure-for-configuring-oracle-software-owner-environments.md)
- dgdba group
  - creating [6.3.7](creating-the-osdgdba-group-for-database-installations.md)
- DHCP
  - and GNS [5.6.1](about-oracle-grid-infrastructure-name-resolution-options.md)
- diagnostic data [D.1](about-the-optimal-flexible-architecture-standard.md)
- Direct NFS
  - disabling [8.4.4](enabling-and-disabling-direct-nfs-client-control-of-nfs.md)
  - enabling [8.4.4](enabling-and-disabling-direct-nfs-client-control-of-nfs.md)
  - oranfstab file [8.4.3](creating-an-oranfstab-file-for-direct-nfs-client.md)
- directory
  - creating separate data file directories [8.3.3](creating-directories-for-oracle-database-files.md)
- disk group
  - Oracle ASM [8.1.1](identifying-storage-requirements-for-oracle-automatic-storage-management.md)
  - recommendations for Oracle ASM disk groups [8.1.1](identifying-storage-requirements-for-oracle-automatic-storage-management.md)
- disk group corruption
  - preventing [8.2.1](about-oracle-asm-with-oracle-asm-filter-driver-asmfd.md)
- disk groups
  - checking [8.1.4](using-an-existing-oracle-asm-disk-group.md)
  - recommendations for [8.1.1](identifying-storage-requirements-for-oracle-automatic-storage-management.md)
- disks
  - selecting for use with Oracle ASM [8.1.6](selecting-disks-to-use-with-oracle-asm-disk-groups.md)
- disk space
  - requirements for preconfigured database in Oracle ASM [8.1.1](identifying-storage-requirements-for-oracle-automatic-storage-management.md)
- display variable [1.5](user-environment-configuration-checklist-for-oracle-grid-infrastructure.md)
- downgrade [11.13](downgrading-oracle-clusterware-after-an-upgrade.md)
- downgrade after failed installation [11.13.3.4](downgrading-oracle-grid-infrastructure-18-using-oui.md), [11.13.4.4](downgrading-oracle-grid-infrastructure-using-oui.md), [11.13.7](downgrading-oracle-grid-infrastructure-after-failed-upgrade-on-first-node.md)
- downgrade after failed upgrade [11.13.3.4](downgrading-oracle-grid-infrastructure-18-using-oui.md), [11.13.4.4](downgrading-oracle-grid-infrastructure-using-oui.md), [11.13.7](downgrading-oracle-grid-infrastructure-after-failed-upgrade-on-first-node.md)
- downgrades [11.13.2](restrictions-for-oracle-grid-infrastructure-downgrades.md), [11.13.3.4](downgrading-oracle-grid-infrastructure-18-using-oui.md), [11.13.4.4](downgrading-oracle-grid-infrastructure-using-oui.md), [11.13.7](downgrading-oracle-grid-infrastructure-after-failed-upgrade-on-first-node.md)
- downgrades restrictions [11.13.2](restrictions-for-oracle-grid-infrastructure-downgrades.md)
- downgrade to 12c Release 2 (12.2) [11.13.4](downgrading-oracle-clusterware-to-12.2.md)
- downgrade to 18c [11.13.3](downgrading-oracle-clusterware-to-18c.md)
- downgrading
  - Oracle Grid Infrastructure [11.13.3.2](downgrading-oracle-domain-services-cluster-18c.md), [11.13.4.2](downgrading-oracle-domain-services-cluster-to-12c-release-2.md), [11.13.5](downgrading-to-oracle-grid-infrastructure-12c-release-1-12-1.md)
  - Oracle Standalone Cluster [11.13.3.1](downgrading-oracle-standalone-cluster-18c.md), [11.13.4.1](downgrading-oracle-standalone-cluster-12crelease2.md)
  - to 12.1 [11.13.5](downgrading-to-oracle-grid-infrastructure-12c-release-1-12-1.md)
  - to 12.2 [11.13.4.1](downgrading-oracle-standalone-cluster-12crelease2.md), [11.13.4.2](downgrading-oracle-domain-services-cluster-to-12c-release-2.md)
  - to 18c [11.13.3.1](downgrading-oracle-standalone-cluster-18c.md), [11.13.3.2](downgrading-oracle-domain-services-cluster-18c.md)
- downgrading,
  - Downgrade Member Cluster [11.13.3.3](downgrading-oracle-member-cluster-18c.md), [11.13.4.3](downgrading-oracle-member-cluster-to-12c-release-2.md)
  - Oracle Grid Infrastructure [11.13.3.3](downgrading-oracle-member-cluster-18c.md), [11.13.4.3](downgrading-oracle-member-cluster-to-12c-release-2.md)
  - to 12.2 [11.13.4.3](downgrading-oracle-member-cluster-to-12c-release-2.md)
  - to 18c [11.13.3.3](downgrading-oracle-member-cluster-18c.md)
- dry-run upgrade
  - check upgrade readiness
    - Clusterware upgrade [11.5.6](using-dry-run-upgrade-mode-to-validate-readiness-for-oracle-grid-infrastructure.md)
  - Oracle Grid Infrastructure preupgrade check [11.5.6.1](about-oracle-clusterware-dry-run-upgrade-mode.md)

------------------------------------------------------------------------

## E

- editing shell startup file [6.5.2](procedure-for-configuring-oracle-software-owner-environments.md)
- enterprise.rsp file [A.4.1](editing-a-response-file-template.md)
- environment
  - configuring for Oracle user [6.5](configuring-gri-infrastructure-software-environments.md)
- environment variables
  - ORACLE_HOME [11.5.2](checks-to-complete-before-upgrading-oracle-clusterware.md)
  - ORACLE_SID [11.5.2](checks-to-complete-before-upgrading-oracle-clusterware.md)
- errors
  - X11 forwarding [6.5.3](setting-remote-display-and-x11-forwarding-configuration.md), [B.1.3](enabling-ssh-user-equivalency-on-cluster-nodes.md)
- errors using Opatch [11.4](restrictions-for-oracle-grid-infrastructure-upgrades.md)
- errors using OPatch [10.5](modifying-oracle-clusterware-binaries-after-installation.md)
- Exadata
  - relinking binaries example for [10.5](modifying-oracle-clusterware-binaries-after-installation.md)
- examples
  - Oracle ASM failure groups [8.1.1](identifying-storage-requirements-for-oracle-automatic-storage-management.md)
- executeConfigTools [A.7.2](running-postinstallation-configuration-using-response-file.md)

------------------------------------------------------------------------

## F

- failed install [11.14.1](completing-failed-installation-upgrade.md)
- failed upgrade [11.14.1](completing-failed-installation-upgrade.md)
- failure group
  - characteristics of Oracle ASM failure group [8.1.1](identifying-storage-requirements-for-oracle-automatic-storage-management.md), [8.3.1](identifying-and-using-existing-oracle-database-disk-groups-on-oracle-asm.md)
  - examples of Oracle ASM failure groups [8.1.1](identifying-storage-requirements-for-oracle-automatic-storage-management.md)
  - Oracle ASM [8.1.1](identifying-storage-requirements-for-oracle-automatic-storage-management.md)
- fast recovery area [10.2.4.2](creating-the-fast-recovery-area-disk-group.md)
  - filepath [D.6](optimal-flexible-architecture-file-path-examples.md)
  - Grid home
    - filepath [D.6](optimal-flexible-architecture-file-path-examples.md)
- fencing
  - and IPMI [6.7](enabling-intelligent-platform-management-interface-ipmi.md)
- file mode creation mask
  - setting [6.5.1](environment-requirements-for-oracle-software-owners.md)
- files
  - bash_profile [6.5.2](procedure-for-configuring-oracle-software-owner-environments.md)
  - dbca.rsp [A.4.1](editing-a-response-file-template.md)
  - enterprise.rsp [A.4.1](editing-a-response-file-template.md)
  - login [6.5.2](procedure-for-configuring-oracle-software-owner-environments.md)
  - profile [6.5.2](procedure-for-configuring-oracle-software-owner-environments.md)
  - response files [A.4](preparing-response-files.md)
- filesets [4.5](about-operating-system-requirements.md)
- file system
  - storage option for data files [7.3](storage-considerations-for-oracle-grid-infrastructure-and-oracle-rac.md)

------------------------------------------------------------------------

## G

- GIMR [8.1.3](about-grid-infrastructure-management-repository.md)
- globalization [1.8](installer-planning-checklist-for-oracle-grid-infrastructure.md)
- global zones
  - deploying Oracle RAC [C.3](deploying-oracle-rac-in-the-global-zone.md)
- GNS
  - about [5.6.3](ip-name-and-address-requirements-for-grid-naming-service-gns.md)
  - configuration example [5.11](grid-naming-service-cluster-configuration-example.md)
  - configuring [5.6.1](about-oracle-grid-infrastructure-name-resolution-options.md)
- GNS client clusters
  - and GNS client data file [5.6.4.4](creating-and-using-a-gns-client-data-file.md)
  - GNS client data file required for installation [5.6.4.1](about-multi-cluster-gns-networks.md)
  - name resolution for [5.6.4.1](about-multi-cluster-gns-networks.md)
- GNS client data file
  - how to create [5.6.4.4](creating-and-using-a-gns-client-data-file.md)
- GNS virtual IP address [1.4](network-checklist-for-oracle-grid-infrastructure.md)
- grid home
  - unlocking [10.5](modifying-oracle-clusterware-binaries-after-installation.md)
- grid infrastructure management repository [9.3.1](about-oracle-standalone-clusters.md)
- Grid Infrastructure Management Repository [8.1.3](about-grid-infrastructure-management-repository.md)
  - about [7.5](guidelines-for-using-nfs-with-oracle-asm.md)
  - global [8.1.3](about-grid-infrastructure-management-repository.md)
  - local [8.1.3](about-grid-infrastructure-management-repository.md)
- gridSetup script [9.4.2](installing-oracle-standalone-cluster.md), [9.4.3](installing-oracle-domain-services-cluster.md), [9.4.4](installing-oracle-member-clusters.md)
- Grid user
  - creating [6.4.1](creating-an-oracle-software-owner-user.md)
- groups
  - creating an Oracle Inventory Group [6.1.2](creating-the-oracle-inventory-group-if-an-oracle-inventory-does-not-exist.md)
  - creating the asmadmin group [6.3.1](creating-osasm-group.md)
  - creating the asmdba group [6.3.2](creating-the-osdba-for-asm-group.md)
  - creating the asmoper group [6.3.3](creating-the-osoper-for-asm-group.md)
  - creating the backupdba group [6.3.6](creating-the-osbackupdba-group-for-database-installations.md)
  - creating the dba group [6.3.4](creating-the-osdba-group-for-database-installations.md)
  - creating the dgdba group [6.3.7](creating-the-osdgdba-group-for-database-installations.md)
  - creating the kmdba group [6.3.8](creating-the-oskmdba-group-for-database-installations.md)
  - creating the racdba group [6.3.9](creating-the-osracdba-group.md)
  - OINSTALL group [1.3](server-configuration-checklist-for-oracle-grid-infrastructure.md)
  - OSBACKUPDBA (backupdba) [6.2.3](extended-oracle-database-groups-for-job-role-separation.md)
  - OSDBA (dba) [6.2.2](standard-oracle-database-groups-for-database-administrators.md)
  - OSDBA group (dba) [6.2.2](standard-oracle-database-groups-for-database-administrators.md)
  - OSDGDBA (dgdba) [6.2.3](extended-oracle-database-groups-for-job-role-separation.md)
  - OSKMDBA (kmdba) [6.2.3](extended-oracle-database-groups-for-job-role-separation.md)
  - OSOPER (oper) [6.2.2](standard-oracle-database-groups-for-database-administrators.md)
  - OSOPER group (oper) [6.2.2](standard-oracle-database-groups-for-database-administrators.md)

------------------------------------------------------------------------

## H

- hardware requirements
  - display [1.1](server-hardware-checklist-for-oracle-grid-infrastructure.md)
  - IPMI [1.1](server-hardware-checklist-for-oracle-grid-infrastructure.md)
  - local storage for Oracle homes [1.1](server-hardware-checklist-for-oracle-grid-infrastructure.md)
  - network [1.1](server-hardware-checklist-for-oracle-grid-infrastructure.md)
  - RAM [1.1](server-hardware-checklist-for-oracle-grid-infrastructure.md)
  - tmp [1.1](server-hardware-checklist-for-oracle-grid-infrastructure.md)
- hared Memory Resource Controls
  - checking [B.2.2](checking-shared-memory-resource-controls.md)
- highly available IP addresses (HAIP) [5.4](private-ip-interface-configuration-requirements.md)
- host names
  - legal host names [1.4](network-checklist-for-oracle-grid-infrastructure.md)
- hugepages [1.3](server-configuration-checklist-for-oracle-grid-infrastructure.md)

------------------------------------------------------------------------

## I

- image
  - install [9.1](about-image-based-oracle-grid-infastructure-installation.md)
- image-based installation of Oracle Grid Infrastructure [9.4.2](installing-oracle-standalone-cluster.md), [9.4.3](installing-oracle-domain-services-cluster.md), [9.4.4](installing-oracle-member-clusters.md)
- inaccessible nodes
  - upgrading [11.7.3](joining-inaccessible-nodes-after-forcing-an-upgrade.md)
- incomplete installations [11.14.5](continuing-incomplete-installation-on-remote-nodes.md)
- init.ora
  - and SGA permissions [10.3](about-changes-in-default-sga-of-databases.md)
- installation
  - cloning a Grid infrastructure installation to other nodes [9.6.2](configuring-software-binaries-for-oracle-grid-infrastructure-for-a-cluster.md)
  - response files [A.4](preparing-response-files.md)
    - preparing [A.4](preparing-response-files.md), [A.4.2](recording-response-files.md)
    - templates [A.4](preparing-response-files.md)
  - silent mode [A.5](running-oracle-universal-installer-using-a-response-file.md)
- installation planning [1](system-hardware-software-and-configuration-checklists.md)
- installation types
  - and Oracle ASM [8.1.1](identifying-storage-requirements-for-oracle-automatic-storage-management.md)
- installer screens
  - ASM Storage Option [8.2.1](about-oracle-asm-with-oracle-asm-filter-driver-asmfd.md)
  - Cluster Node Information [5.10.5](oracle-flex-cluster-manually-assigned-addresses.md)
  - Grid Plug and Play Information [5.6.2](cluster-name-and-scan-requirements.md), [5.10.4](oracle-flex-cluster-dhcp-assigned-virtual-ip-vip-addresses.md), [5.10.5](oracle-flex-cluster-manually-assigned-addresses.md)
  - Network Interface Usage [5.10.2](about-oracle-flex-asm-clusters-networks.md)
  - Node Selection screen [11.5.6.2](running-oui-in-dry-run-upgrade-mode.md), [11.7.1](running-oui-to-upgrade-grid-infrastructure-from-an-earlier-release.md)
- installing Oracle Member Cluster [9.4.4](installing-oracle-member-clusters.md)
- interconnect [1.4](network-checklist-for-oracle-grid-infrastructure.md)
- interconnects
  - single interface [5.4](private-ip-interface-configuration-requirements.md)
- interfaces [1.4](network-checklist-for-oracle-grid-infrastructure.md)
  - requirements for private interconnect [5.2.2](about-the-private-ip-address.md)
- IPMI
  - addresses not configurable by GNS [6.7.2](configuring-the-ipmi-management-network.md)
  - preinstallation tasks [6.7](enabling-intelligent-platform-management-interface-ipmi.md)
- IPv4 requirements [5.1](about-oracle-grid-infrastructure-network-configuration-options.md), [5.5](ipv4-and-ipv6-protocol-requirements.md)
- IPv6 requirements [5.1](about-oracle-grid-infrastructure-network-configuration-options.md), [5.5](ipv4-and-ipv6-protocol-requirements.md)

------------------------------------------------------------------------

## J

- JDK requirements [4.5](about-operating-system-requirements.md)

------------------------------------------------------------------------

## K

- kernel parameters
  - changing [B.2.4](displaying-and-changing-kernel-parameter-values.md)
  - checking [B.2.2](checking-shared-memory-resource-controls.md)
  - displaying [B.2.4](displaying-and-changing-kernel-parameter-values.md)
  - tcp and udp [B.2.5](setting-udp-and-tcp-kernel-parameters-manually.md)
- kernel parameters configuration [B.2](configuring-kernel-parameters-on-oracle-solaris.md)
- kmdba group
  - creating [6.3.8](creating-the-oskmdba-group-for-database-installations.md)
- Korn shell
  - default user startup file [6.5.2](procedure-for-configuring-oracle-software-owner-environments.md)

------------------------------------------------------------------------

## L

- legal host names [1.4](network-checklist-for-oracle-grid-infrastructure.md)
- licensing [1.8](installer-planning-checklist-for-oracle-grid-infrastructure.md)
- LVM
  - recommendations for Oracle ASM [8.1.1](identifying-storage-requirements-for-oracle-automatic-storage-management.md)

------------------------------------------------------------------------

## M

- Management Database [8.1.3](about-grid-infrastructure-management-repository.md)
- management repository service [9.3.1](about-oracle-standalone-clusters.md)
- manifest file [8.5](creating-member-cluster-manifest-file.md)
- mask
  - setting default file mode creation mask [6.5.1](environment-requirements-for-oracle-software-owners.md)
- max_buf [8.4.2](checking-tcp-network-protocol-buffer-for-direct-nfs-client.md)
- mixed binaries [4.5](about-operating-system-requirements.md)
- mode
  - setting default file mode creation mask [6.5.1](environment-requirements-for-oracle-software-owners.md)
- Multiple Oracle Homes Support
  - advantages [D.2](about-multiple-oracle-homes-support.md)
- multiversioning [D.2](about-multiple-oracle-homes-support.md)

------------------------------------------------------------------------

## N

- Name Service Cache Daemon
  - enabling [4.12](enabling-the-name-service-cache-daemon.md)
- netca.rsp file [A.4.1](editing-a-response-file-template.md)
- Net Configuration Assistant (NetCA)
  - response files [A.6.2](running-net-configuration-assistant-using-response-files.md)
  - running at command prompt [A.6.2](running-net-configuration-assistant-using-response-files.md)
- network, minimum requirements [1.1](server-hardware-checklist-for-oracle-grid-infrastructure.md)
- network requirements [1.4](network-checklist-for-oracle-grid-infrastructure.md)
- networks
  - configuring interfaces [5.13](network-interface-configuration-options.md)
  - for Oracle Flex Clusters [5.10.1](understanding-oracle-flex-clusters.md), [5.10.2](about-oracle-flex-asm-clusters-networks.md)
  - IP protocol requirements for [5.1](about-oracle-grid-infrastructure-network-configuration-options.md), [5.5](ipv4-and-ipv6-protocol-requirements.md)
  - manual address configuration example [5.12](manual-ip-address-configuration-example.md)
  - Oracle Flex ASM [1.4](network-checklist-for-oracle-grid-infrastructure.md)
- NFS
  - and data files [7.7](about-nfs-storage-for-data-files.md)
  - and Oracle Clusterware files [7.5](guidelines-for-using-nfs-with-oracle-asm.md)
  - buffer size requirements [8.4.1](configuring-nfs-buffer-size-parameters-for-oracle-database.md)
  - for data files [7.7](about-nfs-storage-for-data-files.md)
- NFS mounts
  - Direct NFS Client
    - requirements [7.8](about-direct-nfs-client-mounts-to-nfs-storage-devices.md)
  - mtab [7.8](about-direct-nfs-client-mounts-to-nfs-storage-devices.md)
  - oranfstab [7.8](about-direct-nfs-client-mounts-to-nfs-storage-devices.md)
- noninteractive mode
  - See: response file mode

------------------------------------------------------------------------

## O

- OCR
  - See: Oracle Cluster Registry
- OFA [D.1](about-the-optimal-flexible-architecture-standard.md)
  - See also: Optimal Flexible Architecture
- oifcfg [5.2.2](about-the-private-ip-address.md)
- OINSTALL directory [D.6](optimal-flexible-architecture-file-path-examples.md)
- oinstall group
  - creating [6.1.2](creating-the-oracle-inventory-group-if-an-oracle-inventory-does-not-exist.md)
- OINSTALL groupl [1.5](user-environment-configuration-checklist-for-oracle-grid-infrastructure.md)
  - See also: Oracle Inventory directory
- Opatch [11.4](restrictions-for-oracle-grid-infrastructure-upgrades.md)
- OPatch [10.5](modifying-oracle-clusterware-binaries-after-installation.md)
- operating system
  - different on cluster members [4.5](about-operating-system-requirements.md)
  - requirements [4.5](about-operating-system-requirements.md)
- operating system privileges groups [1.5](user-environment-configuration-checklist-for-oracle-grid-infrastructure.md)
- operating system requirements [1.2](operating-system-checklist-for-oracle-grid-infrastructure-on-oracle-solaris.md)
- oper group
  - description [6.2.2](standard-oracle-database-groups-for-database-administrators.md)
- Optimal Flexible Architecture
  - about [D.1](about-the-optimal-flexible-architecture-standard.md)
- Oracle ACFS
  - Installing Oracle RAC binaries not supported on Oracle Flex Cluster [7.2.2](restrictions-and-guidelines-for-oracle-acfs.md)
  - restrictions for Oracle Restart [7.2.2](restrictions-and-guidelines-for-oracle-acfs.md)
  - supported Oracle Solaris versions [7.2.1](oracle-acfs-and-oracle-advm-support-on-oracle-solaris.md)
- Oracle ADVM
  - supported Oracle Solaris versions [7.2.1](oracle-acfs-and-oracle-advm-support-on-oracle-solaris.md)
- Oracle ASM
  - characteristics of failure groups [8.1.1](identifying-storage-requirements-for-oracle-automatic-storage-management.md), [8.3.1](identifying-and-using-existing-oracle-database-disk-groups-on-oracle-asm.md)
  - disk groups [8.1.1](identifying-storage-requirements-for-oracle-automatic-storage-management.md)
  - failure groups [8.1.1](identifying-storage-requirements-for-oracle-automatic-storage-management.md)
    - examples [8.1.1](identifying-storage-requirements-for-oracle-automatic-storage-management.md)
    - identifying [8.1.1](identifying-storage-requirements-for-oracle-automatic-storage-management.md)
  - guidelines [7.4](guidelines-for-using-oracle-asm-for-storage.md)
  - installing [9.4.2](installing-oracle-standalone-cluster.md), [9.4.3](installing-oracle-domain-services-cluster.md), [9.4.4](installing-oracle-member-clusters.md)
  - recommendations for disk groups [8.1.1](identifying-storage-requirements-for-oracle-automatic-storage-management.md)
  - space required for preconfigured database [8.1.1](identifying-storage-requirements-for-oracle-automatic-storage-management.md)
- Oracle ASMFD on Oracle Solaris [8.2.2](guidelines-for-using-oracle-asmfd-on-oracle-solaris.md)
- Oracle ASM Filter Driver
  - about [8.2.1](about-oracle-asm-with-oracle-asm-filter-driver-asmfd.md)
  - best practices [8.2.2](guidelines-for-using-oracle-asmfd-on-oracle-solaris.md)
- Oracle ASM Filter Driver (Oracle ASMFD) [9.4.3](installing-oracle-domain-services-cluster.md), [9.4.4](installing-oracle-member-clusters.md)
- Oracle ASM password file [7.4](guidelines-for-using-oracle-asm-for-storage.md)
- Oracle Automatic Storage Management
  - part of Oracle Grid Infrastructure installation [8.1.5](upgrading-existing-oracle-automatic-storage-management-instances.md)
- Oracle base [D.1](about-the-optimal-flexible-architecture-standard.md), [D.6](optimal-flexible-architecture-file-path-examples.md)
- Oracle Base [6.1.6](about-the-oracle-base-directory-for-the-grid-user.md)
- Oracle Cluster Registry
  - configuration of [1.6](storage-checklist-for-oracle-grid-infrastructure.md)
  - mirroring [7.5](guidelines-for-using-nfs-with-oracle-asm.md)
  - partition sizes [7.5](guidelines-for-using-nfs-with-oracle-asm.md)
- Oracle Clusterware
  - upgrading [7.5](guidelines-for-using-nfs-with-oracle-asm.md)
- Oracle Clusterware Files
  - NFS to Oracle ASM [11.5.3](moving-oracle-clusterware-files-from-nfs-to-oracle-asm.md)
- Oracle Database
  - data file storage options [7.3](storage-considerations-for-oracle-grid-infrastructure-and-oracle-rac.md)
  - requirements with Oracle ASM [8.1.1](identifying-storage-requirements-for-oracle-automatic-storage-management.md)
- Oracle Database Configuration Assistant [A.6.1](running-dbca-using-response-files.md)
  - response file [A.4.1](editing-a-response-file-template.md)
- oracle-database-preinstall-19c [3.3](installing-oracle-database-prerequisites-packages-for-solaris.md)
  - checking [3.2](checking-the-oracle-database-prerequisites-packages-configuration.md)
- Oracle Database prerequisites group package [3.3](installing-oracle-database-prerequisites-packages-for-solaris.md)
- Oracle DBCA [A.6.1](running-dbca-using-response-files.md)
- Oracle Disk Manager
  - and Direct NFS [8.4.4](enabling-and-disabling-direct-nfs-client-control-of-nfs.md)
- Oracle Domain Services Cluster [9.3.2](about-oracle-domain-services-clusters.md), [9.3.3](about-oracle-member-clusters.md)
- Oracle Enterprise Manager [11.10.3](registering-listener-with-em-after-gi-upgrade.md)
- Oracle Extended Cluster [9.4.2](installing-oracle-standalone-cluster.md), [11.15](extending-a-cluster-after-upgrading-grid-infrastructure.md)
  - converting to [11.15](extending-a-cluster-after-upgrading-grid-infrastructure.md)
- Oracle Extended Clusters [9.3.4](about-oracle-extended-clusters.md)
- Oracle Fleet Patching and Provisioning [9.7](about-deploying-oracle-grid-infrastructure-using-rapid-home-provisioning.md), [11.8](about-upgrading-grid-infrastructure-using-fleet-patching-and-provisioning.md)
- Oracle Fleet Patching and Provisioning Server [9.3.2](about-oracle-domain-services-clusters.md)
- Oracle Flex ASM
  - and Oracle ASM clients [1.4](network-checklist-for-oracle-grid-infrastructure.md)
  - networks [1.4](network-checklist-for-oracle-grid-infrastructure.md)
- Oracle Flex Clusters
  - about [5.10.1](understanding-oracle-flex-clusters.md)
  - and Oracle Flex ASM [5.10.2](about-oracle-flex-asm-clusters-networks.md)
  - and Oracle Flex ASM cluster [5.10.1](understanding-oracle-flex-clusters.md)
  - Oracle Restart
    - restrictions for [7.2.2](restrictions-and-guidelines-for-oracle-acfs.md)
  - restrictions for Oracle ACFS [7.2.2](restrictions-and-guidelines-for-oracle-acfs.md)
- Oracle FPP [9.7](about-deploying-oracle-grid-infrastructure-using-rapid-home-provisioning.md), [11.8](about-upgrading-grid-infrastructure-using-fleet-patching-and-provisioning.md)
- Oracle Grid Infrastructure
  - restrictions for Oracle ACFS [7.2.2](restrictions-and-guidelines-for-oracle-acfs.md)
- Oracle Grid Infrastructure upgrading [11.8](about-upgrading-grid-infrastructure-using-fleet-patching-and-provisioning.md)
- Oracle home
  - ASCII path restriction for [1.3](server-configuration-checklist-for-oracle-grid-infrastructure.md)
  - file path [D.6](optimal-flexible-architecture-file-path-examples.md)
  - Grid home
    - filepath [D.6](optimal-flexible-architecture-file-path-examples.md)
  - naming conventions [D.5](oracle-home-directory-naming-convention.md)
- Oracle Inventory [1.5](user-environment-configuration-checklist-for-oracle-grid-infrastructure.md)
  - identifying existing [6.1.1](determining-if-an-oracle-inventory-and-oracle-inventory-group-exist.md)
- Oracle Inventory Directory
  - OINSTALL group [D.3](about-the-oracle-inventory-directory-and-installation.md)
- Oracle IO Server [5.10.2](about-oracle-flex-asm-clusters-networks.md)
- Oracle Layered File System [9.7](about-deploying-oracle-grid-infrastructure-using-rapid-home-provisioning.md), [11.8](about-upgrading-grid-infrastructure-using-fleet-patching-and-provisioning.md)
- Oracle Member Clusters [9.3.3](about-oracle-member-clusters.md)
  - for applications [9.3.3](about-oracle-member-clusters.md)
  - for databases [9.3.3](about-oracle-member-clusters.md)
- Oracle Net Configuration Assistant
  - response file [A.4.1](editing-a-response-file-template.md)
- Oracle Optimal Flexible Architecture
  - See: Optimal Flexible Architecture
- Oracle ORAchk
  - and Upgrade Readiness Assessment [1.8](installer-planning-checklist-for-oracle-grid-infrastructure.md)
- Oracle Software Owner user
  - See also: Oracle user

  <!-- -->

  - creating [6.1.5](identifying-oracle-software-owner-user-account.md), [6.4.1](creating-an-oracle-software-owner-user.md)
- Oracle Software Owner users [6.5.2](procedure-for-configuring-oracle-software-owner-environments.md)
  - configuring environment for [6.5](configuring-gri-infrastructure-software-environments.md)
- Oracle Solaris
  - installation options for [4.1](guidelines-for-oracle-solaris-operating-system-installation.md)
  - parameters [B.2.1](minimum-parameter-settings-for-installation.md)
  - zones [4.10](oracle-solaris-cluster-configuration-on-sparc.md)
- Oracle Solaris Cluster [4.10](oracle-solaris-cluster-configuration-on-sparc.md), [4.11](running-rootpre-script-onx86-with-oracle-solaris.md)
  - prerequisites [C.2](prerequisites-for-oracle-rac-deployment-in-oracle-solaris-cluster-zone-clusters.md)
- Oracle Standalone Cluster [9.4.2](installing-oracle-standalone-cluster.md)
- Oracle Standalone Clusters [9.3.1](about-oracle-standalone-clusters.md)
- Oracle Universal Installer
  - response files
    - list of [A.4.1](editing-a-response-file-template.md)
- Oracle Upgrade Companion [4.2.1](general-upgrade-best-practices.md)
- oracle user [1.5](user-environment-configuration-checklist-for-oracle-grid-infrastructure.md)
  - creating [6.1.5](identifying-oracle-software-owner-user-account.md)
- Oracle user
  - configuring environment for [6.5](configuring-gri-infrastructure-software-environments.md)
  - modifying [6.4.2](modifying-oracle-owner-user-groups.md)
- oraInventory [D.6](optimal-flexible-architecture-file-path-examples.md)
- oranfstab configuration file [8.4.3](creating-an-oranfstab-file-for-direct-nfs-client.md)
- oranfstab file [8.4.4](enabling-and-disabling-direct-nfs-client-control-of-nfs.md)
- OSASM
  - creating for Oracle Grid Infrastructure [6.3.1](creating-osasm-group.md)
- OSBACKUPDBA group
  - creating [6.3.6](creating-the-osbackupdba-group-for-database-installations.md)
- OSBACKUPDBA group (backupdba) [6.2.3](extended-oracle-database-groups-for-job-role-separation.md)
- OSDBA [1.5](user-environment-configuration-checklist-for-oracle-grid-infrastructure.md)
- OSDBA for ASM
  - creating for Oracle Grid Infrastructure [6.3.2](creating-the-osdba-for-asm-group.md)
- OSDBA groups
  - creating [6.3.4](creating-the-osdba-group-for-database-installations.md)
  - creating for Oracle Grid Infrastructure [6.3.3](creating-the-osoper-for-asm-group.md)
  - description for database [6.2.2](standard-oracle-database-groups-for-database-administrators.md)
  - SYSDBA privilege [6.2.2](standard-oracle-database-groups-for-database-administrators.md)
- OSDGDBA group
  - creating [6.3.7](creating-the-osdgdba-group-for-database-installations.md)
- OSDGDBA group (dgdba) [6.2.3](extended-oracle-database-groups-for-job-role-separation.md)
- OSKMDBA group
  - creating [6.3.8](creating-the-oskmdba-group-for-database-installations.md)
- OSKMDBA group (kmdba) [6.2.3](extended-oracle-database-groups-for-job-role-separation.md)
- OSOPER group
  - creating [6.3.5](creating-an-osoper-group-for-database-installations.md)
- OSOPER groups
  - description for database [6.2.2](standard-oracle-database-groups-for-database-administrators.md)
  - SYSOPER privilege [6.2.2](standard-oracle-database-groups-for-database-administrators.md)
- OSRACDBA group
  - creating [6.3.9](creating-the-osracdba-group.md)
- other changes
- out-of-place patching
  - switch Oracle Grid Infrastructure home [11.9.4](switching-oracle-grid-infrastructure-home-after-patching.md)

------------------------------------------------------------------------

## P

- parameter file
  - and permissions to read and write the SGA [10.3](about-changes-in-default-sga-of-databases.md)
- partition
  - using with Oracle ASM [8.1.1](identifying-storage-requirements-for-oracle-automatic-storage-management.md)
- patch updates [10.1.1](downloading-and-installing-patch-updates.md)
- postinstallation
  - recommended tasks
    - root.sh script, backing up [10.2.2](creating-a-backup-of-the-root-sh-script.md)
- postinstallation configToolAllCommands script [A.8.1](about-the-postinstallation-configuration-file.md)
- postinstallation -executeConfigTools option [A.7.1](using-the-installation-response-file-for-postinstallation-configuration.md)
- prctl command [B.2.2](checking-shared-memory-resource-controls.md)
- preconfigured database
  - Oracle ASM disk space requirements [8.1.1](identifying-storage-requirements-for-oracle-automatic-storage-management.md)
  - requirements when using Oracle ASM [8.1.1](identifying-storage-requirements-for-oracle-automatic-storage-management.md)
- primary host name [1.4](network-checklist-for-oracle-grid-infrastructure.md)
- project.max-shm-memory
  - checking [B.2.2](checking-shared-memory-resource-controls.md)
- proxy realm [1.8](installer-planning-checklist-for-oracle-grid-infrastructure.md)
- public node name
  - and primary host name [1.4](network-checklist-for-oracle-grid-infrastructure.md)

------------------------------------------------------------------------

## R

- racdba group
  - creating [6.3.9](creating-the-osracdba-group.md)
- RAID
  - and mirroring Oracle Cluster Registry and voting files [7.5](guidelines-for-using-nfs-with-oracle-asm.md)
  - recommended Oracle ASM redundancy level [8.1.1](identifying-storage-requirements-for-oracle-automatic-storage-management.md)
- raw devices
  - upgrading existing partitions [7.5](guidelines-for-using-nfs-with-oracle-asm.md)
- recommendations
  - client access to the cluster [10.2.5](checking-the-scan-configuration.md)
  - private network [5.2.2](about-the-private-ip-address.md)
- recv_hiwat [8.4.2](checking-tcp-network-protocol-buffer-for-direct-nfs-client.md)
- redundancy level
  - and space requirements for preconfigured database [8.1.1](identifying-storage-requirements-for-oracle-automatic-storage-management.md)
- Redundant Interconnect Usage
  - IPv4 requirement [5.4](private-ip-interface-configuration-requirements.md)
- registering resources [11.10.3](registering-listener-with-em-after-gi-upgrade.md)
- releases
  - multiple [D.2](about-multiple-oracle-homes-support.md)
- release update revisions [10.1.1](downloading-and-installing-patch-updates.md)
- release updates [10.1.1](downloading-and-installing-patch-updates.md)
- relinking Oracle Grid Infrastructure home binaries [10.5](modifying-oracle-clusterware-binaries-after-installation.md), [12.6](relinking-oracle-grid-infrastructure-for-a-cluster-binaries.md), [12.7](changing-the-oracle-grid-infrastructure-home-path.md)
- removing Oracle software [12](removing-oracle-database-software.md), [12.1](about-oracle-deinstallation-options.md)
  - examples [12.3](deinstallation-examples-for-oracle-database.md)
- requiremenets
  - interconnects [5.4](private-ip-interface-configuration-requirements.md)
- requirements [8.1.1](identifying-storage-requirements-for-oracle-automatic-storage-management.md)
- resource control [B.2.1](minimum-parameter-settings-for-installation.md)
  - changing [B.2.4](displaying-and-changing-kernel-parameter-values.md)
  - displaying [B.2.4](displaying-and-changing-kernel-parameter-values.md)
  - project.max-shm-memory
    - minimum value [B.2.1](minimum-parameter-settings-for-installation.md)
    - requirements [B.2.1](minimum-parameter-settings-for-installation.md)
- response file [A.6.1](running-dbca-using-response-files.md)
- response file installation
  - preparing [A.4](preparing-response-files.md)
  - response files
    - templates [A.4](preparing-response-files.md)
  - silent mode [A.5](running-oracle-universal-installer-using-a-response-file.md)
- response file mode [A.1](how-response-files-work.md)
  - See also: response files, silent mode

  <!-- -->

  - about [A.1](how-response-files-work.md)
  - reasons for using [A.2](reasons-for-using-silent-mode-or-response-file-mode.md)
- response files [A.1](how-response-files-work.md), [A.6.1](running-dbca-using-response-files.md)
  - See also: silent mode.

  <!-- -->

  - about [A.1](how-response-files-work.md)
  - creating with template [A.4.1](editing-a-response-file-template.md)
  - dbca.rsp [A.4.1](editing-a-response-file-template.md)
  - enterprise.rsp [A.4.1](editing-a-response-file-template.md)
  - general procedure [A.3](using-response-files.md)
  - netca.rsp [A.4.1](editing-a-response-file-template.md)
  - Net Configuration Assistant [A.6.2](running-net-configuration-assistant-using-response-files.md)
  - passing values at command line [A.1](how-response-files-work.md)
  - specifying with Oracle Universal Installer [A.5](running-oracle-universal-installer-using-a-response-file.md)
- root.sh script
  - backing up [10.2.2](creating-a-backup-of-the-root-sh-script.md)
- rootcrs.pl
  - restriction for Oracle Flex Cluster deinstallation [12.8](unconfiguring-oracle-clusterware-without-removing-binaries.md)
- rootcrs.sh [12.1](about-oracle-deinstallation-options.md)
- roothas.sh [12.1](about-oracle-deinstallation-options.md)
- root user
  - logging in as [2.1](logging-in-to-a-remote-system-using-x-window-system.md)
- running gridSetup.sh [11.5.6.2](running-oui-in-dry-run-upgrade-mode.md), [11.7.1](running-oui-to-upgrade-grid-infrastructure-from-an-earlier-release.md)
- running multiple Oracle releases [D.2](about-multiple-oracle-homes-support.md)

------------------------------------------------------------------------

## S

- SCAN
  - shared [5.2.6](about-shared-scan.md)
- SCAN address [1.4](network-checklist-for-oracle-grid-infrastructure.md)
- SCANs [1.4](network-checklist-for-oracle-grid-infrastructure.md), [5.6.5](ip-name-and-address-requirements-for-manual-configuration-of-cluster.md)
  - client access [10.2.5](checking-the-scan-configuration.md)
  - configuring [1.4](network-checklist-for-oracle-grid-infrastructure.md)
  - description [10.2.5](checking-the-scan-configuration.md)
- shared SCAN [5.2.6](about-shared-scan.md)
- silent mode
  - about [A.1](how-response-files-work.md)
  - reasons for using [A.2](reasons-for-using-silent-mode-or-response-file-mode.md)
- silent mode installation [A.5](running-oracle-universal-installer-using-a-response-file.md)
- software requirements [4.5](about-operating-system-requirements.md)
- Solaris kernel parameters [B.2](configuring-kernel-parameters-on-oracle-solaris.md)
- space requirements [8.1.2](oracle-clusterware-storage-space-requirements.md)
- ssh
  - and X11 Forwarding [6.5.3](setting-remote-display-and-x11-forwarding-configuration.md)
  - configuring [B.1](configuring-ssh-manually-on-all-cluster-nodes.md)
- Standard cluster
  - upgrades result in [11.4](restrictions-for-oracle-grid-infrastructure-upgrades.md)
- standard operating environment [9.7](about-deploying-oracle-grid-infrastructure-using-rapid-home-provisioning.md)
- stty
  - suppressing to prevent installation errors [6.5.4](preventing-installation-errors-caused-by-terminal-output-commands.md)
- swap space
  - allocation [1.3](server-configuration-checklist-for-oracle-grid-infrastructure.md)
- SYSBACKUPDBA system privileges [6.2.3](extended-oracle-database-groups-for-job-role-separation.md)
- SYSDBA privilege
  - associated group [6.2.2](standard-oracle-database-groups-for-database-administrators.md)
- SYSDGDBA system privileges [6.2.3](extended-oracle-database-groups-for-job-role-separation.md)
- SYSKMDBA system privileges [6.2.3](extended-oracle-database-groups-for-job-role-separation.md)
- SYSOPER privilege
  - associated group [6.2.2](standard-oracle-database-groups-for-database-administrators.md)
- system global area
  - permissions to read and write [10.3](about-changes-in-default-sga-of-databases.md)
- system privileges
  - SYSBACKUPDBA [6.2.3](extended-oracle-database-groups-for-job-role-separation.md)
  - SYSDGDBA [6.2.3](extended-oracle-database-groups-for-job-role-separation.md)
  - SYSKMDBA [6.2.3](extended-oracle-database-groups-for-job-role-separation.md)
- system requirements [1](system-hardware-software-and-configuration-checklists.md)

------------------------------------------------------------------------

## T

- tcp_max_buf [8.4.2](checking-tcp-network-protocol-buffer-for-direct-nfs-client.md)
- tcp_recv_hiwat [8.4.2](checking-tcp-network-protocol-buffer-for-direct-nfs-client.md)
- tcp_xmit_hiwat [8.4.2](checking-tcp-network-protocol-buffer-for-direct-nfs-client.md)
- terminal output commands
  - suppressing for Oracle installation owner accounts [6.5.4](preventing-installation-errors-caused-by-terminal-output-commands.md)
- troubleshooting
  - cron jobs and installation [1.8](installer-planning-checklist-for-oracle-grid-infrastructure.md)
  - disk space errors [1.3](server-configuration-checklist-for-oracle-grid-infrastructure.md)
  - environment path errors [1.3](server-configuration-checklist-for-oracle-grid-infrastructure.md)
  - garbage strings in script inputs found in log files [6.5.4](preventing-installation-errors-caused-by-terminal-output-commands.md)
  - inventory corruption [6.4.2](modifying-oracle-owner-user-groups.md)
  - nfs mounts [4.12](enabling-the-name-service-cache-daemon.md)
  - public network failures [4.12](enabling-the-name-service-cache-daemon.md)
  - root.sh errors [12.8](unconfiguring-oracle-clusterware-without-removing-binaries.md)
  - ssh [B.1.1](checking-existing-ssh-configuration-on-the-system.md), [B.1.3](enabling-ssh-user-equivalency-on-cluster-nodes.md)
  - ssh errors [6.5.4](preventing-installation-errors-caused-by-terminal-output-commands.md)
  - stty errors [6.5.4](preventing-installation-errors-caused-by-terminal-output-commands.md)
  - unconfiguring Oracle Clusterware to fix causes of root.sh errors [12.8](unconfiguring-oracle-clusterware-without-removing-binaries.md)
  - unset environment variables [1.3](server-configuration-checklist-for-oracle-grid-infrastructure.md)
  - user equivalency [B.1.1](checking-existing-ssh-configuration-on-the-system.md), [B.1.3](enabling-ssh-user-equivalency-on-cluster-nodes.md)
- Troubleshooting
  - DBCA does not recognize Oracle ASM disk size and fails to create disk groups [10.4.4](using-asmca-to-administer-disk-groups-for-earlier-database-releases.md)
- typographic conventions

------------------------------------------------------------------------

## U

- umask command [6.5.1](environment-requirements-for-oracle-software-owners.md)
- unconfiguring Oracle Clusterware [12.8](unconfiguring-oracle-clusterware-without-removing-binaries.md)
- uninstall
  - See: removing Oracle software
- UNIX commands
  - xhost [2.1](logging-in-to-a-remote-system-using-x-window-system.md)
- UNIX workstation
  - installing from [2.1](logging-in-to-a-remote-system-using-x-window-system.md)
- unreachable nodes
  - upgrading [11.7.3](joining-inaccessible-nodes-after-forcing-an-upgrade.md)
- upgrade [4.2.3](oracle-asm-upgrade-notifications.md), [11.8](about-upgrading-grid-infrastructure-using-fleet-patching-and-provisioning.md)
  - Oracle Automatic Storage Management [8.1.5](upgrading-existing-oracle-automatic-storage-management-instances.md)
  - running gridSetup.sh [11.5.6.2](running-oui-in-dry-run-upgrade-mode.md), [11.7.1](running-oui-to-upgrade-grid-infrastructure-from-an-earlier-release.md)
- upgrades [11.4](restrictions-for-oracle-grid-infrastructure-upgrades.md)
  - and OCR partition sizes [7.5](guidelines-for-using-nfs-with-oracle-asm.md)
  - and voting file sizes [7.5](guidelines-for-using-nfs-with-oracle-asm.md)
  - best practices [4.2.1](general-upgrade-best-practices.md)
  - restrictions for [11.4](restrictions-for-oracle-grid-infrastructure-upgrades.md)
  - unsetting environment variables for [11.5.2](checks-to-complete-before-upgrading-oracle-clusterware.md)
- upgrade tasks [11.10.3](registering-listener-with-em-after-gi-upgrade.md)
- upgrading
  - and Oracle ORAchk Upgrade Readiness Assessment [1.8](installer-planning-checklist-for-oracle-grid-infrastructure.md)
  - inaccessible nodes [11.7.3](joining-inaccessible-nodes-after-forcing-an-upgrade.md)
  - options [4.2.2](new-server-operating-system-upgrade-option.md)
- useradd command [6.4.1](creating-an-oracle-software-owner-user.md)
- users
  - creating the oracle user [6.1.5](identifying-oracle-software-owner-user-account.md)

------------------------------------------------------------------------

## V

- vendor clusterware
  - and cluster names for Oracle Grid Infrastructure [1.4](network-checklist-for-oracle-grid-infrastructure.md)
- voting files
  - configuration of [1.6](storage-checklist-for-oracle-grid-infrastructure.md)
  - mirroring [7.5](guidelines-for-using-nfs-with-oracle-asm.md)
  - partition sizes [7.5](guidelines-for-using-nfs-with-oracle-asm.md)

------------------------------------------------------------------------

## X

- X11 forwarding errors [6.5.3](setting-remote-display-and-x11-forwarding-configuration.md), [B.1.3](enabling-ssh-user-equivalency-on-cluster-nodes.md)
- xhost command [2.1](logging-in-to-a-remote-system-using-x-window-system.md)
- xmit_hiwat [8.4.2](checking-tcp-network-protocol-buffer-for-direct-nfs-client.md)
- xtitle
  - suppressing to prevent installation errors [6.5.4](preventing-installation-errors-caused-by-terminal-output-commands.md)
- X Window System
  - enabling remote hosts [2.1](logging-in-to-a-remote-system-using-x-window-system.md)

------------------------------------------------------------------------

## Z

- zone clusters [4.10](oracle-solaris-cluster-configuration-on-sparc.md)
  - deploying Oracle RAC [C.3](deploying-oracle-rac-in-the-global-zone.md), [C.4](deploying-oracle-rac-in-a-zone-cluster.md)
- zones [4.10](oracle-solaris-cluster-configuration-on-sparc.md)
