## Verifying HugePages Behavior in XFS Files

For best performance, map the data files placed in DAX-enabled storage in to the virtual address space using HugePages mappings. For a memory-mapped file, set up the virtual-to-physical address translations when the pages are first touched.

If you map pages through DAX using HugePages mappings, then the pages will not use page-cache pages.

You can enable a trace to determine if the page-fault handler granularity is 2 MB or lower, and if it bypasses the page cache.

1.  To view this trace, log in as `root` and run the following trace enabling command:
        # echo 1 >
        /sys/kernel/debug/tracing/events/fs_dax/dax_pmd_fault_done/
        enable
2.  Log out from `root` and create a file in the DAX-mounted XFS file system and run `mkfs` on it using the `omsfscmds` utility.
3.  Log in again as `root` and run the following command to look at the generated trace:
        # cat /sys/kernel/debug/tracing/trace

    Regular 2 MB page faults that bypass the page cache will show the following trace with NOPAGE at the end of the trace:

        oms_test-21456 [024] .... 13566209.645007: dax_pmd_fault_done:
        dev 259:10 ino 0x2005 shared ALLOW_RETRY|KILLABLE|USER address
        0x7fb717e01000 vm_start 0x7fb717e00000 vm_end 0x7fb997e00000
        pgoff 0x1 max_pgoff 0x280000 NOPAGE

    If the page fault occurs at a lower granularity of 4 KB, then you will see a FALLBACK in the page fault handler trace. This indicates that 2 MB granularity page fault handlers failed and the fallback path through the page cache is executed. Systems showing a FALLBACK trace must not be used to run OMS.

        oms_test-21456 [024] .... 13566209.646801: dax_pmd_fault_done:
        dev 259:9 ino 0xc3 shared WRITE|ALLOW_RETRY|KILLABLE|USER
        address 0x7fb717e0c000 vm_start 0x7fb717e00000 vm_end
        0x7fb997e00000 pgoff 0xc max_pgoff 0x280000 FALLBACK
4.  Tracing substantially impinges on performance. You must disable tracing before running workloads. To disable the trace, log in as `root` and run the following command:
        # echo 0 >
        /sys/kernel/debug/tracing/events/fs_dax/dax_pmd_fault_done/
        enable

**Related Topics**

- [Configuring HugePages](../unxar/administering-oracle-database-on-linux.md)

**Parent topic:** [Deploying Oracle Database with Oracle Memory Speed](deploying-database-oms.md)
