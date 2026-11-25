If the source database uses a server parameter file, then including the `SPFILE` option in the `DUPLICATE` command directs RMAN to use the server parameter file from the source database for the auxiliary instance.

For backup-based duplication, the server parameter file is restored from backups. For active database duplication, the server parameter file is copied from the source database to the auxiliary instance.

When the source database uses a text-based initialization parameter file, use the `PFILE` clause in the `DUPLICATE` command to copy the source database's initialization parameter file to the auxiliary instance.

You can modify the values that were copied or restored from the server parameter file of the source database by using the `PARAMETER_VALUE_CONVERT` option of `SPFILE` or the `SET` clause of the `DUPLICATE`. For example, you can use the `SET` clause to change the value of the `DB_FILE_NAME_CONVERT` parameter in the auxiliary instance's server parameter file.

If the source database does not use a server parameter file or RMAN cannot restore a backup of the server parameter file, then you must manually create a text-based initialization parameter file, as described in [Steps to Create an Initialization Parameter File for the Auxiliary Instance](steps-to-create-an-init-param-file-for-the-aux-instance.md).

**Parent topic:** [Preparing the Auxiliary Instance on the Destination Host](preparing-the-auxiliary-instance-destination-host.md)
