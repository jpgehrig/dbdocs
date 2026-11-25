## Modifying Oracle Grid Infrastructure for a Standalone Server Binaries After Installation

After installation, you must first stop the Oracle Restart stack to modify the software installed in your Grid home.

For example, to apply a one-off patch or modify any of the DLLs used by Oracle Restart or Oracle ASM, you must follow these steps to stop and restart the Oracle Restart stack.

**Caution:**

Before relinking executables, you must shut down all executables that run in the Oracle home directory that you are relinking. In addition, shut down applications linked with Oracle shared libraries.

Prepare the Oracle Restart home for modification using the following procedure:

1.  Log in using a member of the Administrators group and go to the directory `Grid_home``\bin`, where `Grid_home` is the path to the Oracle Restart home.
2.  Shut down the Oracle Restart stack using the following command:
         DRIVE_LETTER:\Grid_home\bin> crsctl stop has -f

    Alternatively, you can use the `roothas.bat` script to stop Oracle Restart, as shown in the following example:

         DRIVE_LETTER:\Grid_home\crs\install> roothas.bat -unlock

    **Note:**

    Starting with Oracle Database 12c Release 1 (12.1.0.2), the `roothas.bat` script replaces the `roothas.pl` script in the Oracle Grid Infrastructure home.

    The `roothas.bat` script stops Oracle Restart and then verifies that it is stopped.
3.  After the Oracle Restart stack is completely shut down, perform the changes to the software installed in the Grid home.
    Apply the patches using `opatch apply`.
4.  Lock the Grid home:
           DRIVE_LETTER:\Grid_home\crs\install>roothas.bat -lock
5.  Use the following command to restart the Oracle Restart stack:
           DRIVE_LETTER:\Grid_home\bin> crsctl start has

Example 6-2 Enabling Oracle ACFS on Oracle Restart Configurations

To use Oracle ACFS on Oracle Restart configurations, you must first enable Administrator access for Oracle ACFS using the following command:

    DRIVE_LETTER:\cd Grid_home\crs\install
    DRIVE_LETTER:\Grid_home\crs\install>roothas.bat -lockacfs

**See Also:**

[Oracle OPatch User's Guide for Windows and UNIX](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/ntdbi&id=OPTCH-GUID-786E76D9-B298-4B70-A939-0CBE91220238)

**Parent topic:** [Installing and Configuring Oracle Grid Infrastructure for a Standalone Server](install-configure-oracle-grid-infrastructure-standalone-server.md)
