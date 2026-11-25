Learn about data striping, which is an effective means of reducing the impact of slow hard drives.

Compared to CPU and memory speeds, hard disk drives are extremely slow. Now that the hard disk drives are relatively inexpensive, Oracle recommends that Windows Server use logical volumes composed of striped physical disks. Data striping is an effective means of reducing the impact of relatively slow hard drives by distributing file I/O across a number of hard drives simultaneously.

**Note:**

Data striping through the operating system is not permitted with Oracle Automatic Storage Management (Oracle ASM), which does its own striping. Hardware striping is allowed with Oracle ASM, but it is not necessary.

Striping data across a number of disks is one example of a redundant array of inexpensive disks (RAID). There are several different types of RAID, also referred to as RAID levels, ranging from high performance to high reliability. The three most common RAID levels in Oracle Database installations are RAID-0, RAID-1, and RAID-5. Descriptions of each RAID level are in RAID Levels in Oracle Database Installations, which shows each level's read and write penalties.

Table 8-2 RAID Levels in Oracle Database Installations

| RAID Level                     | Read Penalty Note 1 | Write Penalty Note 2 |
|:-------------------------------|:--------------------|:---------------------|
| 0 (Disk Striping)              | 1:1                 | 1:1                  |
| 1 (Disk Mirroring)             | 1:1                 | 2:1                  |
| 0 + 1                          | 1:1                 | 2:1                  |
| 5 (Distributed Data Gathering) | 1:1                 | 4:1                  |

### Note 1

Read penalty is the ratio of I/O operations to read requests.

### Note 2

Write penalty is the ratio of I/O operations to write requests.

### About Disk Striping

RAID level 0 enables high-performance, fault-intolerant disk striping. Multiple physical hard disks are aggregated into a logical whole, either by a disk controller or through the operating system. Data operations against the logical volume are broken down into as many chunks as there are physical drives in the array, making simultaneous use of all disks. Given identical hard disks, if one hard disk has a throughput rate of `DISKRATE` operations/second, then a RAID 0 logical volume has a rate of:

    (DISKRATE * [number of physical  drives in array]) operations/second

The downside of RAID 0 is its lack of fault tolerance. If one disk in the logical volume fails, the whole volume fails and must be restored from a backup.

### About Disk Mirroring

RAID level 1 enables fault-tolerant disk mirroring with some chance of a performance penalty. Essentially, every write to a mirrored disk is duplicated on another drive dedicated to this purpose (the mirror drive). If the mirrored disk fails, the mirror drive is brought online in real time. After the faulty drive is replaced, the mirror configuration can be reestablished.

The read penalty for RAID level 1 is nominally 1:1, but it might benefit from split reads on some controllers. When the controller knows which mirror can be accessed fastest, for example, it can lower search times by directing I/O operations to that disk.

### About Disk Striping Plus Mirroring

RAID level 0+1 enables mirroring of an array of striped hard disks. This is a blend of RAID 0 and RAID 1, offering high-performing fault tolerance.

### About Distributed Data Guarding

RAID level 5, also known as disk striping with parity, eliminates the costly requirement to mirror. In RAID 5, multiple hard disks are aggregated into a striped logical volume, similar to RAID 0, but each drive contains parity information such that any single drive failure is tolerated. With one failed drive, a RAID-5 system can allow continued access to data, although access times are greatly reduced due to on-the-fly rebuilding of bytes from parity information. RAID-5 solutions usually allow hot-swapping of faulty drives with replacements, triggering a rebuild of the failed drive's data onto the replacement from parity information.

The write penalty of 4:1 results from 2 reads and 2 writes during parity calculation.

**See Also:**

[Oracle Database Administrator's Guide](../admin/managing-memory.md) in "Using Automatic Memory Management."

- [About Multiple Striped Volumes for Sequential and Random Access](about-multiple-striped-volumes-for-sequential-and-random-access.md)
  If there are enough physical disks in Windows Server, create at least two striped volumes (in addition to a standalone hard disk or striped volume for the operating system).

**Parent topic:** [Tuning Windows to Optimize Oracle Database](tuning-windows-to-optimize-oracle-database.md)
