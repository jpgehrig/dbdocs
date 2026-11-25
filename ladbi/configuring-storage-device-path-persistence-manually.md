## Configuring Storage Device Path Persistence Manually

You can maintain storage file path persistence by creating a rules file.

By default, the device file naming scheme `udev` dynamically creates device file names when the server is started, and assigns ownership of them to root. If `udev` applies default settings, then it changes Oracle device file names and owners for the disks, making the disks inaccessible when the server is restarted. For example, a voting disk on a device named `/dev/sdd` owned by the user `grid` may be on a device named `/dev/sdf` owned by root after restarting the server.

If you do not use Oracle ASMLib, then you must create a custom rules file. Linux vendors customize their `udev` configurations and use different orders for reading rules files. For example, on some Linux distributions when `udev` is started, it sequentially carries out rules (configuration directives) defined in rules files. These files are in the path `/etc/udev/rules.d/`. Rules files are read in lexical order. For example, rules in the file `10-wacom.rules` are parsed and carried out before rules in the rules file `90-ib.rules`.

When specifying the device information in the `udev` rules file, ensure that the OWNER, GROUP, and MODE are specified before all other characteristics in the order shown. For example, to include the characteristic ACTION on the UDEV line, specify ACTION after OWNER, GROUP, and MODE.

Where rules files describe the same devices, on the supported Linux kernel versions, the last file read is the one that is applied.

- [Configuring Device Persistence Manually for Oracle ASM](configuring-device-persistence-manually-for-oracle-asm.md)
  Complete these tasks to create device path persistence manually for Oracle ASM.

**Parent topic:** [Completing Preinstallation Tasks Manually](completing-preinstallation-tasks-manually.md)
