Use the size guidelines in this section to calculate Oracle Database limits.

Table 15-3 Block Size Guidelines

| Type                                              | Size                                                        |
|:--------------------------------------------------|:------------------------------------------------------------|
| Maximum block size                                | 16,384 bytes or 16 kilobytes (KB)                           |
| Minimum block size                                | 2 kilobytes (KB)                                            |
| Maximum blocks for each file                      | 4,194,304 blocks                                            |
| Maximum possible file size with 16 K sized blocks | 64 Gigabytes (GB) (4,194,304 \* 16,384) = 64 gigabytes (GB) |

Table 15-4 Maximum Number of Files for Each Database

| Block Size | Number of Files |
|:-----------|:----------------|
| 2 KB       | 20,000          |
| 4 KB       | 40,000          |
| 8 KB       | 65,536          |
| 16 KB      | 65,536          |

Table 15-5 Maximum File Sizes

| Type                             | Size                                                  |
|:---------------------------------|:------------------------------------------------------|
| Maximum file size for a FAT file | 4 GB                                                  |
| Maximum file size in NTFS        | 16 Exabytes (EB)                                      |
| Maximum database size            | 65,536 \* 64 GB equals approximately 4 Petabytes (PB) |
| Maximum control file size        | 20,000 blocks                                         |

**Parent topic:** [Oracle Database Specifications for Windows](oracle-database-specifications-for-windows.md)
