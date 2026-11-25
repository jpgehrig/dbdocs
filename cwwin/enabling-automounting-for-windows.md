## Enabling Automounting for Windows

Even though the automount feature is enabled by default, you should verify that automount is enabled.

You must enable automounting when using:

- Raw partitions for Oracle ASM

- Oracle Clusterware

- Logical drives for Oracle ASM

**Note:**

Raw partitions are supported only when upgrading an existing installation using the configured partitions. On new installations, using raw partitions is not supported by ASMCA or OUI, but is supported by the software if you perform manual configuration

1.  To determine if automatic mounting of new volumes is enabled, use the following commands:
        C:\> diskpart
        DISKPART> automount
        Automatic mounting of new volumes disabled.
2.  To enable automounting:
    1.  Enter the following commands at a command prompt:
            C:\> diskpart
            DISKPART> automount enable
            Automatic mounting of new volumes enabled.
    2.  Type `exit` to end the `diskpart` session.
    3.  Repeat steps 1 and 2 for each node in the cluster.

**Note:**

All nodes in the cluster must have automatic mounting enabled to correctly install Oracle RAC and Oracle Clusterware. Oracle recommends that you enable automatic mounting before creating any logical partitions for use by the database or Oracle ASM.

You must restart each node after enabling disk automounting.

After disk automounting is enabled and the node is restarted, automatic mounting remains active until it is disabled.

**Parent topic:** [Preliminary Shared Disk Preparation](preliminary-shared-disk-preparation.md)
