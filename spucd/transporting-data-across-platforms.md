You can transport data across platforms.

The functionality of transporting data across platforms can be used to:

- Enable a database to be migrated from one platform to another.

- Provide an easier and more efficient means for content providers to publish structured data and distribute it to customers running Oracle Database on different platforms.

- Simplify the distribution of data from a data warehouse environment to data marts, which are often running on smaller platforms.

- Enable the sharing of read-only tablespaces between Oracle Database installations on different operating systems or platforms, assuming that your storage system is accessible from those platforms and the platforms all have the same endianness, as described in the sections that follow.

Many, but not all, platforms are supported for cross-platform data transport. You can query the `V$TRANSPORTABLE_PLATFORM` view to see the platforms that are supported, and to determine each platform's endian format (byte ordering). The following query displays the platforms that support cross-platform data transport:

    COLUMN PLATFORM_NAME FORMAT A40
    COLUMN ENDIAN_FORMAT A14

    SELECT PLATFORM_ID, PLATFORM_NAME, ENDIAN_FORMAT
      FROM V$TRANSPORTABLE_PLATFORM
      ORDER BY PLATFORM_ID;

    PLATFORM_ID PLATFORM_NAME                            ENDIAN_FORMAT
    ----------- ---------------------------------------- --------------
              1 Solaris[tm] OE (32-bit)                  Big
              2 Solaris[tm] OE (64-bit)                  Big
              3 HP-UX (64-bit)                           Big
              4 HP-UX IA (64-bit)                        Big
              5 HP Tru64 UNIX                            Little
              6 AIX-Based Systems (64-bit)               Big
              7 Microsoft Windows IA (32-bit)            Little
              8 Microsoft Windows IA (64-bit)            Little
              9 IBM zSeries Based Linux                  Big
             10 Linux IA (32-bit)                        Little
             11 Linux IA (64-bit)                        Little
             12 Microsoft Windows x86 64-bit             Little
             13 Linux x86 64-bit                         Little
             15 HP Open VMS                              Little
             16 Apple Mac OS                             Big
             17 Solaris Operating System (x86)           Little
             18 IBM Power Based Linux                    Big
             19 HP IA Open VMS                           Little
             20 Solaris Operating System (x86-64)        Little
             21 Apple Mac OS (x86-64)                    Little

If the source platform and the target platform are of the same endianness, then the data is transported from the source platform to the target platform without any data conversion.

If the source platform and the target platform are of different endianness, then the data being transported must be converted to the target platform format. You can convert the data using one of the following methods:

- The `GET_FILE` or `PUT_FILE` procedure in the `DBMS_FILE_TRANSFER` package

  When you use one of these procedures to move data files between the source platform and the target platform, each block in each data file is converted to the target platform's endianness. The conversion occurs on the target platform.

- The RMAN `CONVERT` command

  Run the RMAN `CONVERT` command on the source or target platform. This command converts the data being transported to the target platform format.

  **Note:**

  Conversion of data files between different endian formats is not supported for data files having undo segments.

Before the data in a data file can be transported to a different platform, the data file header must identify the platform to which it belongs. To transport read-only tablespaces between Oracle Database installations on different platforms, make the data file read/write at least once.

**See Also:**

"[Converting Data Between Platforms](converting-data-between-platforms.md)"

**Parent topic:** [Transporting Databases](transporting-databases.md)
