## Verifying HugePages Availability

Ensure that the underlying Linux kernel supports HugePages.

HugePages not only reduces TLB misses but also substantially reduces the memory footprint for virtual to physical address translation.

To determine the HugePages size on your system, run:

    $grep Hugepagesize /proc/meminfo
    Hugepagesize: 2048 kB

In this example, the HugePages size is 2 MiB (mebibyte).

**Note:**

An MiB (mebibyte) is a unit of measure that represents 1024 \* 1024 bytes.

Oracle recommends Oracle Linux 7 with the Unbreakable Enterprise Kernel 5 or later for HugePages support.

**Parent topic:** [Setting-Up Hardware and Operating System Components for OMS](setting-up-hardware-oms.md)
