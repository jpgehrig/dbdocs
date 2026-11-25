## Verifying the Disk I/O Scheduler on Linux 8 and Later Systems

Disk I/O schedulers reorder, delay, or merge requests for disk I/O to achieve better throughput and lower latency.

Linux has multiple disk I/O schedulers available, including `mq-deadline`, `none`, `kyber`, and `bfq` on Oracle Linux 8 and later, RHEL 8 and later, and SUSE Linux Enterprise Server 15 and later systems. You should consult with your storage vendor for the appropriate I/O scheduler configuration to achieve best performance on Oracle Automatic Storage Management (Oracle ASM).

In general, Oracle recommends that you set the I/O Scheduler to `mq-deadline` for rotating storage devices (HDDs) and to `none` for non-rotating storage devices such as SSDs and NVMe on Oracle Linux 8 and later, RHEL 8 and later, and SUSE Linux Enterprise Server 15 and later systems.

On all cluster nodes, enter the following command as `root` to verify the configured disk I/O scheduler value.

    cat /sys/block/${ASM_DISK}/queue/scheduler
    none [mq-deadline] kyber bfq

In this example, the default disk I/O scheduler is `mq-deadline` and `ASM_DISK` is a rotational Oracle ASM disk device.

**Note:**

Contact your storage vendor for more information about how to configure I/O scheduler on Linux for your storage devices.

**Parent topic:** [Configuring Operating Systems for Oracle Grid Infrastructure on Linux](configuring-operating-systems-for-oracle-grid-infrastructure-on-linux.md)
