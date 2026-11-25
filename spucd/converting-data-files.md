Prepare for migrating your data by converting the endian format of the data to the endian format that is used on your target operating system platform.

- [Converting Data Between Platforms](converting-data-between-platforms.md)
  When you perform a transportable operation, and the source platform and the target platform are of different endianness, you must convert the data being transported to the target platform format. If the source platform and the target platform are of the same endianness, then data conversion is not necessary. You can use the `DBMS_FILE_TRANSFER` package or the RMAN `CONVERT` command to convert data.
- [Converting Data Between Platforms Using the DBMS_FILE_TRANSFER Package](converting-data-using-the-dbms-file-transfer-package.md)
  You can use the `GET_FILE` or `PUT_FILE` procedure of the `DBMS_FILE_TRANSFER` package to convert data between platforms during a data file transfer.
- [Converting Data Between Platforms Using RMAN](converting-data-using-rman.md)
  When you use the RMAN `CONVERT` command to convert data, you can either convert the data on the source platform after running Data Pump export, or you can convert the data on the target platform before running Data Pump import. In either case, you must transfer the data files from the source system to the target system.
