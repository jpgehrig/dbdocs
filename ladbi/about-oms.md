## About Oracle Memory Speed

Oracle recommends that you use Oracle Database with the Oracle Memory Speed (OMS) file system to fully utilize the potential of persistent memory (PMEM) devices safely in data centers.

Persistent memory is a new tier in the computer system memory hierarchy. PMEM performance and access characteristics are similar to volatile memory. However, unlike volatile memory and similar to existing storage systems, the data is not lost on system restarts and power failures.

PMEM devices are usually deployed on a DAX-enabled file system. The files placed directly on DAX-enabled file systems backed by PMEM devices may become corrupt in certain scenarios. Applications accessing these files through the file-system kernel interface may also experience higher overhead and lower performance. To avoid these pitfalls, Oracle recommends that you deploy Oracle Database with OMS to eliminate data corruption that may occur when writing to files on a DAX-enabled file system on a raw PMEM device. An Oracle Database deployed on OMS will exhibit I/O performance close to that of the underlying hardware. Also, OMS uses advanced techniques to reduce TLB misses and reduce CPU cache usage and misses.

With PMEM as the backing device, OMS utilizes a memory-mapped file hosted on an XFS-based, DAX-enabled file system to perform I/O operations. You must export the PMEM device as a file using a DAX-enabled file system, such as XFS.

### Benefits of the Oracle Memory Speed File System

- Supports control files, redo log files, data files, and temporary files
- Enables applications to take advantage of the speed and persistence of PMEM devices
- Eliminates the inherent corruption hazard that arises from the lower atomic write size
- OMS is a user-space file system that eliminates the user space to kernel context switch overhead
- Avoids multiple data copies
- OMS takes advantage of HugePages to reduce TLB misses and improve performance
- Bypasses the CPU cache for I/O through non-temporal stores. This enables applications to take advantage of the local cache
- Allows you to examine files even when the database instance is not running
- Provides rich diagnostic data

**Parent topic:** [Deploying the Oracle Memory Speed File System](deploying_oms.md)
