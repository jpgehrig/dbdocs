## Configuring Device Persistence Manually for Oracle ASM

Complete these tasks to create device path persistence manually for Oracle ASM.

1.  On existing systems (single instance or clustered), to obtain current mount paths, run the command `scsi_id` (`/sbin/scsi_id`) on storage devices on a server to obtain their unique device identifiers. When you run the command `scsi_id` with the `-s` argument, the device path and name you provide should be relative to the `sysfs` directory `/sys` (for example, `/block/device`) when referring to `/sys/block/device`.

    For example, as the `root` user:

        # /sbin/scsi_id -g -s /block/sdb/sdb1
        360a98000686f6959684a453333524174

        # /sbin/scsi_id -g -s /block/sde/sde1
        360a98000686f6959684a453333524179

    Record the unique SCSI identifiers, so you can provide them when required.

    **Note:**

    The command `scsi_id` should return the same device identifier value for a given device, regardless of which node the command is run from.

2.  Configure SCSI devices as trusted devices, by editing the `/etc/scsi_id.config` file and adding `options=-g` to the file.

        # cat > /etc/scsi_id.config
        vendor="ATA",options=-p 0x80
        options=-g

3.  Using a text editor, create a UDEV rules file for the Oracle ASM devices, setting permissions to 0660 for the installation owner and the operating system group you have designated the OSDBA group, whose members are granted access privileges to Oracle ASM. For example, on Oracle Linux, to create a role-based configuration `rules.d` file where the installation owner is `grid` and the OSDBA group for `asmdba`, enter commands similar to the following:

        # vi /etc/udev/rules.d/99-oracle-asmdevices.rules

        KERNEL=="sdb1, OWNER="grid", GROUP="asmdba", MODE="0660",
        BUS=="scsi", PROGRAM=="/sbin/scsi_id", RESULT=="14f70656e66696c00000000"
        KERNEL=="sdc1", OWNER="grid", GROUP="asmdba", MODE="0660",
        BUS=="scsi", PROGRAM=="/sbin/scsi_id", RESULT=="14f70656e66696c00000001"
        KERNEL=="sdd1", OWNER="grid", GROUP="asmdba", MODE="0660",
        BUS=="scsi", PROGRAM=="/sbin/scsi_id", RESULT=="14f70656e66696c00000002"

4.  On clustered systems, copy the `rules.d` file to all other nodes on the cluster. For example:

        # sftp 99-oracle-asmdevices.rules root@node2:/etc/udev/rules.d/99-oracle-asmdevices.rules

5.  Run the `partprobe` command using the syntax `/sbin/partprobe ``devicename`.

    For example:

        # /sbin/partprobe /dev/sdc1
        # /sbin/partprobe /dev/sdd1
        # /sbin/partprobe /dev/sde1
        # /sbin/partprobe /dev/sdf1

6.  Run the command `udevtest` (`/sbin/udevtest`) to test the UDEV rules configuration you have created. The output should indicate that the devices are available and the rules are applied as expected. For example, for `/dev/ssd1`:

        # udevtest /block/sdd/sdd1
        main: looking at device '/block/sdd/sdd1' from subsystem 'block'
        udev_rules_get_name: add symlink
        'disk/by-id/scsi-360a98000686f6959684a453333524174-part1'
        udev_rules_get_name: add symlink
        'disk/by-path/ip-192.168.1.1:3260-iscsi-iqn.1992-08.com.netapp:sn.887085-part1'
        udev_node_mknod: preserve file '/dev/.tmp-8-17', because it has correct dev_t
        run_program: '/lib/udev/vol_id --export /dev/.tmp-8-17'
        run_program: '/lib/udev/vol_id' returned with status 4
        run_program: '/sbin/scsi_id'
        run_program: '/sbin/scsi_id' (stdout) '360a98000686f6959684a453333524174'
        run_program: '/sbin/scsi_id' returned with status 0
        udev_rules_get_name: rule applied, 'sdd1' becomes 'data1'
        udev_device_event: device '/block/sdd/sdd1' validate currently present symlinks
        udev_node_add: creating device node '/dev/data1', major = '8', minor = '17',
        mode = '0640', uid = '0', gid = '500'
        udev_node_add: creating symlink
        '/dev/disk/by-id/scsi-360a98000686f6959684a453333524174-part1' to '../../data1'
        udev_node_add: creating symlink
        '/dev/disk/by-path/ip-192.168.1.1:3260-iscsi-iqn.1992-08.com.netapp:sn.84187085
        -part1' to '../../data1'
        main: run: 'socket:/org/kernel/udev/monitor'
        main: run: '/lib/udev/udev_run_devd'
        main: run: 'socket:/org/freedesktop/hal/udev_event'
        main: run: '/sbin/pam_console_apply /dev/data1
        /dev/disk/by-id/scsi-360a98000686f6959684a453333524174-part1
        /dev/disk/by-path/ip-192.168.1.1:3260-iscsi-iqn.1992-08.com.netapp:sn.84187085-
        part1'

    In the example output, note that applying the rules renames OCR device `/dev/sdd1` to `/dev/data1`.

7.  Load the rules and restart the UDEV service. For example:

    - Oracle Linux and Red Hat Enterprise Linux

          # udevadm control --reload-rules && udevadm trigger

    - SUSE Linux Enterprise Server

          # /etc/init.d boot.udev restart

Verify that the device permissions and ownerships are set correctly.

**Parent topic:** [Configuring Storage Device Path Persistence Manually](configuring-storage-device-path-persistence-manually.md)
