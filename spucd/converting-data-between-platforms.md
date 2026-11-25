When you perform a transportable operation, and the source platform and the target platform are of different endianness, you must convert the data being transported to the target platform format. If the source platform and the target platform are of the same endianness, then data conversion is not necessary. You can use the `DBMS_FILE_TRANSFER` package or the RMAN `CONVERT` command to convert data.

**Note:**

Some limitations might apply that are not described in these sections. Refer to the following documentation for more information:

- "[Transporting Data Across Platforms](transporting-data-across-platforms.md)" for information about checking the endianness of platforms

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_FILE_TRANSFER.md) for information about limitations related to the `DBMS_FILE_TRANSFER` package

- [Oracle Database Backup and Recovery Reference](../rcmrf/CONVERT.md) for information about limitations related to the RMAN `CONVERT` command

**Parent topic:** [Converting Data to the Endian Format of the Target Operating System](converting-data-files.md)
