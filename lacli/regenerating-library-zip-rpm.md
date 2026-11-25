## Patching Oracle Instant Client Shared Libraries

Learn how to patch Oracle Instant Client shared libraries on top of a complete Oracle Database Client installation.

You must rebuild your Oracle Instant Client packages and libraries as part of the patching process.

**Note:**

Patching Oracle Instant Client is not supported on Linux for Arm (aarch64).

- Patching Oracle Instant Client
  Perform the following steps to patch Oracle Instant Client.
- About Rebuilding Oracle Instant Client Packages and Libraries
  Separate `makefile` targets are used to create the data shared libraries, zip files, and RPM files either individually or all together.
- Regenerating Data Shared Libraries
  Learn how to regenerate the Oracle Instant Client data shared libraries `libociei.so` and `libociicus.so`.
- Regenerating Zip Files and RPM Files
  Learn how to regenerate the zip files and RPM files for the various Oracle Instant Client packages.

**Parent topic:** [Installing Oracle Instant Client](installing-instant-client.md)

### Patching Oracle Instant Client

Perform the following steps to patch Oracle Instant Client.

1.  Complete a full Oracle Database Client Administration installation based on Oracle home for patching.
2.  Apply the patch to your full Oracle Database Client Administration installation using the `OPatch` utility.
3.  Regenerate the data shared libraries, zip files, and RPM files.
    See Regenerating Data Shared Libraries and Regenerating Zip Files and RPM Files.
4.  Copy the data shared libraries, zip files, and RPM files to the target system and unzip them to the Oracle Instant Client directory.

The `OPatch` utility stores the patching information of the ORACLE_HOME installation in `libclntsh.so`. You can retrieve this patching information using the `genezi -v` command.

If the Oracle Instant Client deployment system does not have the `genezi` utility, copy it from the `$ORACLE_HOME/bin` directory.

**Related Topics**

- [Patching Using OPatch](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lacli&id=OPTCH-GUID-013C991A-BAAB-47CC-9915-F7A39A0BEF87)

**Parent topic:** Patching Oracle Instant Client Shared Libraries

### About Rebuilding Oracle Instant Client Packages and Libraries

Separate `makefile` targets are used to create the data shared libraries, zip files, and RPM files either individually or all together.

Regenerating the data shared libraries requires both a compiler and a linker, which may not be available on all installations.

The regenerated Oracle Instant Client binaries contain only the Oracle Instant Client files installed in the Oracle Client Administrator Home from which you regenerate the libraries and files. Hence, error messages, character set encodings, and time zone files that are available in the regeneration environment are the only ones that are packaged in the data shared libraries. Error messages, character set encodings, and time zone files depend on which national languages were selected for the installation of the Oracle Client Administrator Home.

**Note:**

Regeneration of data shared libraries, zip files, and RPM files is not available on Microsoft Windows.

**Parent topic:** Patching Oracle Instant Client Shared Libraries

### Regenerating Data Shared Libraries

Learn how to regenerate the Oracle Instant Client data shared libraries `libociei.so` and `libociicus.so`.

You can regenerate the Oracle Call Interface (OCI) Oracle Instant Client data shared libraries `libociei.so` and `libociicus.so` using the following commands in an Administrator install of a full Oracle Database Client:

1.  Set ORACLE_HOME to the software install directory. For example:
        $ export ORACLE_HOME=/home/user/product/19.0.0/client_1/
2.  Set LD_LIBRARY_PATH to the library directory. For example:
        $ export LD_LIBRARY_PATH=$ORACLE_HOME/lib
3.  Create the following directory:
        $ mkdir -p $ORACLE_HOME/rdbms/install/instantclient/light
4.  Under Oracle home directory, go to the `/rdbms/lib` directory.
        $ cd $ORACLE_HOME/rdbms/lib
5.  To regenerate `libociei.so`:
        $ make -f ins_rdbms.mk igenlibociei

    The generated file will be in `$ORACLE_HOME/instantclient/libociei.so`
6.  To regenerate `libociicus.so`:
        $ make -f ins_rdbms.mk igenlibociicus

    The generated file will be in `$ORACLE_HOME/instantclient/light/libociicus.so`
7.  To regenerate both `libociei.so` and `libociicus.so`:
        $ make -f ins_rdbms.mk igenliboci

**Parent topic:** Patching Oracle Instant Client Shared Libraries

### Regenerating Zip Files and RPM Files

Learn how to regenerate the zip files and RPM files for the various Oracle Instant Client packages.

Before you regenerate the zip files and RPM files, install the `rpm-build` package.

For Oracle Linux 7:

    $ sudo yum install rpm-build

For Oracle Linux 8 and later:

    $ sudo dnf install rpm-build

Table 6-8 Commands to Regenerate the Zip Files and RPM Files

| Package Name | Commands                                                                   |
|:-------------|:---------------------------------------------------------------------------|
| All Packages | `$ cd $ORACLE_HOME/rdbms/lib`<br>`$ make -f ins_rdbms.mk ic_all_zip`       |
| Basic        | `$ cd $ORACLE_HOME/rdbms/lib`<br>`$ make -f ins_rdbms.mk ic_basic_zip`     |
| Basic Light  | `$ cd $ORACLE_HOME/rdbms/lib`<br>`$ make -f ins_rdbms.mk ic_basiclite_zip` |
| JDBC         | `$ cd $ORACLE_HOME/rdbms/lib`<br>`$ make -f ins_rdbms.mk ic_jdbc_zip`      |
| ODBC         | `$ cd $ORACLE_HOME/rdbms/lib`<br>`$ make -f ins_rdbms.mk ic_odbc_zip`      |
| SQL\*Plus    | `$ cd $ORACLE_HOME/rdbms/lib`<br>`$ make -f ins_rdbms.mk ic_sqlplus_zip`   |
| Tools        | `$ cd $ORACLE_HOME/rdbms/lib`<br>`$ make -f ins_rdbms.mk ic_tools_zip`     |
| SDK          | `$ cd $ORACLE_HOME/rdbms/lib`<br>`$ make -f ins_rdbms.mk ic_sdk_zip`       |
| Precompilers | `$ cd $ORACLE_HOME/rdbms/lib`<br>`$ make -f ins_rdbms.mk ic_precomp_zip`   |

The new zip files and RPM files are generated under the `$ORACLE_HOME/rdbms/install/instantclient` directory.

**Parent topic:** Patching Oracle Instant Client Shared Libraries
