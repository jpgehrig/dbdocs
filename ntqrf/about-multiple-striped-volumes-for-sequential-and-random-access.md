If there are enough physical disks in Windows Server, create at least two striped volumes (in addition to a standalone hard disk or striped volume for the operating system).

One striped volume can be used for sequential data access, and the other can be used for random data access.

Oracle Database redo logs and archived redo logs, for example, are written in sequential order. Because of a reduced head movement, hard disks perform best when reading or writing sequential data.

Oracle Database data files, however, are usually accessed in random order. Random access in a hard disk results in significant head movement, translating to slower data access.

Unless redo logs are separated from data files (at physical device level), undo file I/O contention may result, increasing access times for both types of files.

**Parent topic:** [Overview of Hardware or Operating System Striping](overview-of-hardware-or-operating-system-striping.md)
