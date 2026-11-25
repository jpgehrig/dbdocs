This appendix describes database limits.

### F.1 Database Limits

These are the default and maximum values for parameters in a `CREATE DATABASE` or `CREATE CONTROLFILE` statement.

**Note:**

Interdependencies between these parameters may affect permissible values.

Table F-1 CREATE CONTROLFILE and CREATE DATABASE Parameters

| Parameter       | Default | Maximum Value |
|:----------------|:--------|:--------------|
| `MAXLOGFILES`   | 16      | 4220          |
| `MAXLOGMEMBERS` | 2       | 5             |
| `MAXLOGHISTORY` | 100     | 65534         |
| `MAXDATAFILES`  | 30      | 65534         |
| `MAXINSTANCES`  | 1       | 1055          |

The following table lists the Oracle Database file size limits in bytes.

Table F-2 File Size Limits

| File Type                                 | Platform                                                                          | File size limit                                                                                              |
|:------------------------------------------|:----------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------|
| Data files                                | Any                                                                               | 4,194,303 multiplied by the value of the `DB_BLOCK_SIZE` parameter                                           |
| Import/Export files and SQL\*Loader files | Oracle Solaris, Linux, IBM AIX on POWER Systems (64-Bit), and HP-UX: 32-bit files | 2,147,483,647 bytes                                                                                          |
| Import/Export files and SQL\*Loader files | Oracle Solaris, Linux, IBM AIX on POWER Systems (64-Bit), and HP-UX: 64-bit files | Unlimited<br>Note: File size is limited by limits allowed by the operating system on different file systems. |
| Control files                             | Oracle Solaris, Linux, IBM AIX on POWER Systems (64-Bit), and HP-UX               | Maximum of 201031680 logical blocks                                                                          |
