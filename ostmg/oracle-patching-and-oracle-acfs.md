This section discusses patching with Oracle ACFS in a Grid Infrastructure environment.

- Overview of Oracle ACFS Patching

- Updating Oracle Grid Infrastructure Files

- Verifying Oracle ACFS Patching

### Overview of Oracle ACFS Patching

Oracle ACFS is installed as part of Oracle Grid Infrastructure. However, Oracle ACFS runs from various system locations, such as `/lib/modules` and `/sbin` on Linux.

Oracle ACFS integrates with the Oracle Grid Infrastructure delivery and patch mechanisms: OUI and OPatch. Regardless of the delivery mechanism; Oracle Release, Oracle Patchset, Oracle Release Update, or Oracle One-off; Oracle ACFS content is delivered in patches.

When updating the Oracle Grid Infrastructure, without Oracle Zero Downtime Grid Infrastructure Patching, Oracle ACFS is also updated in the system locations, ensuring seamless operation of the Oracle Grid software. During the updates; whether Release, Release Update, Patchset, or One-off; the Oracle Clusterware stack is stopped on a local node and services are migrated to other nodes. The Oracle Grid Software is then patched and services are restarted on the local node.

#### Patching Without Oracle Zero Downtime Oracle Grid Infrastructure Patching

During the patch operation, Oracle ACFS software is updated first in the Grid Home by the OPatch or OUI file placement operation, and then later moved to the appropriate system locations and loaded into memory while Oracle Clusterware is down. The restart of Oracle Clusterware has the side effect of freeing up in operating system (OS) kernel references so that Oracle ACFS can be updated in the OS Kernel.

#### Patching With Zero Downtime Oracle Grid Infrastructure

When using Zero Downtime Oracle Grid Infrastructure Patching, only the Oracle Grid Infrastructure user space binaries in the Oracle Grid Home are patched. Commands which run out of the Oracle Grid Home immediately use the latest versions. Oracle Grid Infrastructure components that are installed outside of the Oracle Grid Home; such as ACFS, AFD, OLFS, and OKA OS system software (OS kernel modules and system tools); are updated in the Grid Home, but not installed to the system locations. They continue to run the version previous to the patch version. After patching, this results in the OPatch inventory displaying the new patch number in the OPatch inventory. However, the running software does not contain these changes, only the software that is available in the Grid Home. Until the newly available software is loaded into memory and accompanying user tools are copied to system locations, the system does not utilize the available fixes that are in the Oracle Grid Infrastructure Home.

To determine which Oracle ACFS system software is running and installed, the following commands can be used:

- `crsctl` `query` `driver` `activeversion` `-all`

  This command shows the Active Version of Oracle ACFS on all nodes of the cluster. The Active Version is the version of the Oracle ACFS Driver that is currently loaded and running on the system. This also implicitly indicates the ACFS system tools version. The `crsctl` `query` command, available from 18c and onwards, shows data from all nodes of the cluster.

  In the following example, 19.4 is available in the Oracle Home, but 19.2 is the current running version. OPatch `lsinventory` reports 19.4 as the patched version. Oracle Grid Infrastructure OS drivers are only running 19.2.

      crsctl query driver activeversion -all
      Node Name : node1
      Driver Name : ACFS
      BuildNumber : 200114
      BuildVersion : 19.0.0.0.0 (19.2.0.0.0)

- `crsctl` `query` `driver` `softwareversion` `-all`

  This command shows the available Software Version of the Oracle Grid Infrastructure software (and by extension, the available Software Version of the Oracle ACFS Software) that is currently installed in the Oracle Grid Home. The `crsctl` `query` command, available from 18c and onwards, shows data from all nodes of the cluster.

      crsctl query driver softwareversion -all
      Node Name : node1
      Driver Name : ACFS
      BuildNumber : 200628
      BuildVersion : 19.0.0.0.0 (19.4.0.0.0)

- `acfsdriverstate` `version` `-v`

  This command shows the full information on the running Oracle ACFS modules on the local node. The ACFS-9548 and ACFS-9547 messages displays the version of the Oracle ACFS software that is available in the Oracle Grid Infrastructure home. `acfsdriverstate` reports on the local node only. Bug numbers are only available when running one-off patches.

      acfsdriverstate version -v
      ACFS-9325: Driver OS kernel version = 4.1.12-112.16.4.el7uek.x86_64.
      ACFS-9326: Driver build number = 200114.
      ACFS-9212: Driver build version = 19.0.0.0.0 (19.2.0.0.0).
      ACFS-9547: Driver available build number = 200628.
      ACFS-9548: Driver available build version = 19.0.0.0.0 (19.2.0.0.0)
      ACFS-9549: Kernel and command versions.
      Kernel:
       Build version: 19.0.0.0.0
       Build full version: 19.2.0.0.0
       Build hash: 9256567290
       Bug numbers: NoTransactionInformation
      Commands:
       Build version: 19.0.0.0.0
       Build full version: 19.2.0.0.0
       Build hash: 9256567290
       Bug numbers: NoTransactionInformation

### Updating Oracle Grid Infrastructure Files

Until the Oracle Clusterware stack is stopped and the Oracle ACFS driver modules are updated, Oracle ACFS fixes are not loaded into memory. The process that loads the Oracle ACFS fixes into system memory also installs the required tools for Oracle ACFS operation into system locations.

You can perform one of the following procedures:

1.  To load Oracle ACFS fixes into memory and system locations, the following commands must be issued on a node by node basis:

    - `crsctl` `stop` `crs` `-f`

      Stops the CRS stack and all applications on the local node

    - `root.sh` `-updateosfiles`

      Updates Oracle ACFS and other Oracle Grid Infrastructure Kernel modules on the system to the latest version

    - `crsctl` `start` `crs` -`wait`

      Restarts CRS on the node

2.  Alternatively, if a node reboots with a kernel version change, then newer drivers are automatically loaded and newer system tools installed into the system directories. It is assumed that all nodes in the cluster change kernel versions at the same time.

After one of these events has occurred, the `crsctl` `query` `activeversion` and `crsctl` `query` `softwareversion` commands report the same information: the loaded and running operating system (OS) software is the same as the latest available in the Oracle Grid Infrastructure Home. You can run other Oracle ACFS version commands as described in Verifying Oracle ACFS Patching.

### Verifying Oracle ACFS Patching

When using standard OPatch patches to apply Oracle Release Updates and Patches, the inventory accurately reflects what is installed in the Grid Infrastructure home and on the system. For example:

    [grid@racnode1]$ opatch lsinventory
    ...
    ..
    Oracle Grid Infrastructure 19c                                       19.0.0.0.0
    There are 1 products installed in this Oracle Home.

    Interim patches (5) :

    Patch  30501910: applied on Sat Mar 07 15:42:08 AEDT 2020
    Unique Patch ID:  23299902
    Patch description:  "Grid Infrastructure Jan 2020 Release Update : 19.4.0.0.200628 (30501910)"
       Created on 28 Dec 2019, 10:44:46 hrs PST8PDT
       Bugs fixed:

The output in the `lsinventory` example lists the OPatch RU and other patches that are applied, as well as the bug numbers and other information. These patches are applied to the Grid Infrastructure home. During normal patching operations, they are also applied to the operating system (OS) locations and loaded into memory, ensuring that Oracle Grid Infrastructure OS system software fixes are in sync with the Grid Infrastructure home. However, when using Zero Downtime Grid Infrastructure Patching, the content for Oracle Grid Infrastructure system software installed on the system, such as Oracle ACFS, is not updated at the same time.

The `crsctl` `query` `driver` and `acfsdriverstate` commands can be used to verify whether the installed Oracle Grid Infrastructure system software level is the same as the software level of the Grid Infrastructure home. Refer to the discussion about Zero Downtime Oracle Grid Infrastructure patching in Overview of Oracle ACFS Patching.

For patching and update operations applied without Zero Downtime Oracle Grid Infrastructure Patching, the active and software version should always be the same.

If it is necessary to install updated Oracle Grid Infrastructure OS system software, refer to the procedures in Updating Oracle Grid Infrastructure Files.

After all the Oracle Grid Infrastructure OS system software is updated, the version should be the same as the Opatch `lsinventory` output displayed for any patches or updates to the Grid Infrastructure home, in this case, 19.4.0.0.0. Additionally, the Oracle Grid Infrastructure OS system software that is available and active should have the same version number displayed. For example:

    Output from the lsinventory command:
    Patch description:  "Grid Infrastructure Jan 2020 Release Update : 19.4.0.0.0.200628 (30501910)"

    crsctl query driver activeversion -all
    Node Name : node1
    Driver Name : ACFS
    BuildNumber : 200628
    BuildVersion : 19.0.0.0.0 (19.4.0.0.0)

    crsctl query driver softwareversion -all
    Node Name : node1
    Driver Name : ACFS
    BuildNumber : 200628
    BuildVersion : 19.0.0.0.0 (19.4.0.0.0)

You can run the `acfsdriverstate` `version` command for additional Oracle ACFS information on the local node, including information on commands and utilities. For example:

    acfsdriverstate version
     ACFS-9325: Driver OS kernel version = 4.1.12-112.16.4.el7uek.x86_64.
     ACFS-9326: Driver build number = 200628.
     ACFS-9212: Driver build version = 19.0.0.0.0 (19.4.0.0.0)
     ACFS-9547: Driver available build number = 200628.
     ACFS-9548: Driver available build version = 19.0.0.0.0 (19.4.0.0.0).
