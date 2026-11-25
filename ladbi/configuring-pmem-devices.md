## Configuring PMEM Devices

On your Intel Persistent Memory (PMEM) device, use the `ipmctl` utility to configure the PMEM mode and the `ndctl` utility for namespace management.

A PMEM device can operate in App Direct mode, Memory Mode, or Mixed Mode. To use OMS, you should configure your PMEM device in the `app direct` mode by using the BIOS.

1.  In your BIOS, select EDKII, Socket Config, Memory Config, Memory Map, Volatile Mode and set it to 1LM.
2.  Log in as `root` and check the currently configured capacity:
        $ su -
        # ipmctl show -memoryresources

    The output is similar to the following:

        Capacity=3029.4 GiB
        MemoryCapacity=0.0 GiB
        AppDirectCapacity=3024.0 GiB
        UnconfiguredCapacity=0.0 GiB
        InaccessibleCapacity=5.4 GiB
        ReservedCapacity=0.0 GiB

    In this example, the system has an aggregate capacity of 3024 GiB (3247 GB).

    **Note:**

    A GiB (gibibyte) is a unit of measure that represents 1024 MiB (mebibytes), equivalent to 2<sup>30</sup> bytes.
3.  Verify if the regions are configured in `app direct` mode.
        # ipmctl show -region

    The output is similar to the following:

        SocketID | ISetID             | PersistentMemoryType | Capacity  | FreeCapacity | HealthState
        ===============================================================================================
        0x0000   | 0x97407f48df982ccc | AppDirect            | 1512.0 GiB | 0.0 GiB      | Healthy
        0x0001   | 0xfb907f48d59a2ccc | AppDirect            | 1512.0 GiB | 0.0 GiB      | Healthy

    In this example, there are two PMEM devices; one per socket. Each PMEM device or region has a capacity of 1512 GiB and supports AppDirect mode.
4.  Create the namespace by running the `ndctl` command for each region. In this example, run the command twice as there are two regions in the preceding example.
        # ndctl create-namespace
        # ndctl create-namespace
5.  Check if the namespaces are created.
        # ndctl list -u

    The output is similar to the following:

        [
          {
            "dev":"namespace1.0",
            "mode":"fsdax",
            "map":"dev",
            "size":"1488.37 GiB (1598.13 GB)",
            "uuid":"f8ec094d-5a69-4f87-9198-fb9117f2ea8e",
            "sector_size":512,
            "align":2097152,
            "blockdev":"pmem1"
          },
          {
            "dev":"namespace0.0",
            "mode":"fsdax",
            "map":"dev",
            "size":"1488.37 GiB (1598.13 GB)",
            "uuid":"8924aa35-701f-40cc-ba08-654aa5729611",
            "sector_size":512,
            "align":2097152,
            "blockdev":"pmem0"
          }
        ]

    In this example, two namespaces `namespace0.0` and `namespace1.0` are now available for NUMA `nodes 0` and `node 1` respectively. The block device paths for namespaces `namespace0.0 `and `namespace1.0` are `/dev/pmem0` and `/dev/pmem1` respectively.
6.  Ensure that the PMEM device starts at a 2 MiB aligned physical address.
    To determine the alignment of the persistent memory namespaces, view the `/proc/iomem` file.

        # cat /proc/iomem | grep namespace
          3060000000-1aa5fffffff : namespace0.0
          1da00000000-353ffffffff : namespace1.0

    Check if the hexadecimal addresses are aligned at a 2 MiB boundary.

        0x3060000000 = 198144 MiB

        0x1da00000000 = 1941504 MiB

    In this example, both addresses are aligned at a 2 MiB boundary.
7.  Create two partitions on your PMEM storage device. One small partition of approximately 5 percent for metadata and the rest for the data.
    On `/dev/pmem0` create 2 partitions `pmem0p1` and `pmem0p2`.

    Here `pmem0p1` is the smaller metadata partition and `pmem0p2` is the larger data partition.

    In the following example, 5 percent of the total space of 1488.37 GiB would be approximately 75 GiB. Partition the device as follows:

    1.  Launch `parted` and select the device.
            # parted /dev/pmem0

            GNU Parted 3.2
            Using /dev/pmem0
            Welcome to GNU Parted! Type 'help' to view a list of commands.
    2.  Create the first new 75 GiB partition using the `mkpart` command.
            (parted) mkpart
            Partition type? primary/extended? p
            File system type? [ext2]? xfs
            Start? 2MiB
            End? 75GiB
    3.  Create the second new partition using the `mkpart` command.
            (parted) mkpart
            Partition type? primary/extended? p
            File system type? [ext2]? xfs
            Start? 75GiB
            End? -2MiB
    4.  Quit `parted` and return to the shell prompt.
            (parted) q
            Information: You may need to update /etc/fstab.

        Similarly, partition the `/dev/pmem1` device.
8.  Ensure that you align the starting sector of the data partition at 2 MiB.
    The starting sector number of the data partition should be a multiple of 4096 when you run the `fdisk -l ` command.

    Run the `fdisk -l` command on `/dev/pmem0` and `/dev/pmem1` to check if the sector is aligned properly.

        # fdisk -l /dev/pmem0

        Disk /dev/pmem1: 1598.1 GB, 1598128390144 bytes, 3121344512 sectors
        Units = sectors of 1 * 512 = 512 bytes
        Sector size (logical/physical): 512 bytes / 4096 bytes
        I/O size (minimum/optimal): 4096 bytes / 4096 bytes
        Disk label type: dos
        Disk identifier: 0xc1d8d265

              Device Boot      Start         End      Blocks   Id  System
        /dev/pmem0p1            4096   157286399    78641152   83  Linux
        /dev/pmem0p2       157286400  3121340415  1482027008   83  Linux

        # fdisk -l /dev/pmem1

        Disk /dev/pmem1: 1598.1 GB, 1598128390144 bytes, 3121344512 sectors
        Units = sectors of 1 * 512 = 512 bytes
        Sector size (logical/physical): 512 bytes / 4096 bytes
        I/O size (minimum/optimal): 4096 bytes / 4096 bytes
        Disk label type: dos
        Disk identifier: 0x0003b5eb

              Device Boot      Start         End      Blocks   Id  System
        /dev/pmem1p1            4096   157286399    78641152   83  Linux
        /dev/pmem1p2       157286400  3121340415  1482027008   83  Linux

    In these examples the starting sector of the data partitions are multiples of 4096, which confirms that the data partition is aligned at 2 MiB.

        157286400 / 4096 = 38400

**Parent topic:** [Setting-Up Hardware and Operating System Components for OMS](setting-up-hardware-oms.md)
