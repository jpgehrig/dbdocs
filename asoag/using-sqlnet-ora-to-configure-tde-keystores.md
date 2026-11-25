## 11 Using sqlnet.ora to Configure Transparent Data Encryption Keystores

Configuring TDE with `sqlnet.ora` parameters has been deprecated, but is still possible depending on your database configuration.

- About the Keystore Location in the sqlnet.ora File
  Configuring TDE with the deprecated `sqlnet.ora` parameters is possible, for example when databases that were upgraded to databases that support the new static and dynamic TDE initialization parameters.
- Configuring the sqlnet.ora File for a Software Keystore Location
  The `sqlnet.ora` file can be used to configure the keystore location for a regular file system, for multiple database access, and for use with Oracle Automatic Storage Management (ASM).
- Example: Configuring a Software Keystore for a Regular File System
  You can configure a software keystore for a regular file system.
- Example: Configuring a TDE Wallet When Multiple Databases Share the Same Host
  You can configure multiple databases to share the same host by setting the `WALLET_ROOT` parameter.
- Example: Configuring a Software Keystore for an Oracle Automatic Storage Management Disk Group
  In an Oracle Real Applications Clusters (Oracle RAC) environment, the `WALLET_ROOT` parameter points to a shared directory in Oracle Automatic Storage Management (ASM) that is accessible from all Oracle RAC instances of that database.

**Parent topic:** [Using Transparent Data Encryption](asopart1.md)

### 11.1 About the Keystore Location in the sqlnet.ora File

Configuring TDE with the deprecated `sqlnet.ora` parameters is possible, for example when databases that were upgraded to databases that support the new static and dynamic TDE initialization parameters.

After you upgrade, Oracle recommends that you reconfigure your databases to use the `WALLET_ROOT` and `TDE_CONFIGURATION` parameters to configure the keystore location. These new parameters are required for PDBs that are in isolated mode.

However, if you do want to configure the `sqlnet.ora` file instead, be aware that the instance initialization file-based approach using the `WALLET_ROOT` and `TDE_CONFIGURATION` parameters is recommended. It avoids the possibility of inconsistent configuration that can arise when using `sqlnet.ora` because each connection to the database re-reads the contents of the `sqlnet.ora` parameter file. With the instance initialization file based approach, because the `WALLET_ROOT` parameter is read only once when the database instance starts, there is no risk of inconsistency. In a multitenant environment, the use of the `WALLET_ROOT` initialization parameter initialization parameter is preferred over the use of `sqlnet.ora` because it enables each tenant PDB to perform independent management operations.

If you have not set the `WALLET_ROOT` and `TDE_CONFIGURATION` initialization parameters, then Oracle Database checks the `sqlnet.ora` file for the directory location of the keystore. This applies to whether the keystore is a software keystore, an external keystore, or an Oracle Key Vault keystore. You must edit the `sqlnet.ora` file to define a directory location for the keystore that you plan to create. Ensure that this directory exists beforehand. Preferably, this directory should be empty.

Note the following behavior when you must edit the `sqlnet.ora` file in Oracle Real Application Clusters (Oracle RAC) or a multitenant environment:

- In an Oracle RAC environment: If you are using the `srvctl` utility and if you want to include environment variables in the `sqlnet.ora` configuration file, then you must set these environment variables in both the operating system and the `srvctl` environment. Oracle recommends that you place the keystore on a shared file system, such as Oracle Automatic Storage Management (ASM) or ACFS.

- In a multitenant environment: Only united mode is supported if `sqlnet.ora` is used for TDE configuration in the multitenant environment. Isolated mode is only supported if the `WALLET_ROOT` and `TDE_CONFIGURATION` parameters are used for TDE configuration.

In the `sqlnet.ora` file, you must set the `ENCRYPTION_WALLET_LOCATION` parameter to specify the keystore location. However, be aware that `ENCRYPTION_WALLET_LOCATION` is deprecated, starting with Oracle Database release 19c in favor of using the `WALLET_ROOT` and `TDE_CONFIGURATION` initialization parameters.

By default, the `sqlnet.ora` file is located in the `$ORACLE_HOME/network/admin` location, or in the location set by the `TNS_ADMIN` environment variable. Ensure that you have properly set the `TNS_ADMIN` environment variable to point to the correct `sqlnet.ora` file. When the keystore location is not set in the `sqlnet.ora` file, then the `V$ENCRYPTION_WALLET` view displays the default location. You can check the location and status of the keystore in the `V$ENCRYPTION_WALLET` view.

**Related Topics**

- [Transparent Data Encryption Keystore Search Order](configuring-transparent-data-encryption.md)
- [SQL\*Plus User's Guide and Reference](../sqpug/SQL-Plus-quick-start.md)
- [Oracle Database Net Services Reference](../netrf/parameters-for-the-sqlnet.ora.md)

**Parent topic:** Using sqlnet.ora to Configure Transparent Data Encryption Keystores

### 11.2 Configuring the sqlnet.ora File for a Software Keystore Location

The `sqlnet.ora` file can be used to configure the keystore location for a regular file system, for multiple database access, and for use with Oracle Automatic Storage Management (ASM).

- To create a software keystore on a regular file system, use the following format when you edit the `sqlnet.ora` file:

      ENCRYPTION_WALLET_LOCATION=
       (SOURCE=
        (METHOD=FILE)
         (METHOD_DATA=
          (DIRECTORY=path_to_keystore)))

  If the `path_to_keystore` will contain an environment variable, then set this variable in the environment where the database instance is started and before you start the database. If you are using the `srvctl` utility to start the database, then set the environment variable in the `srvctl` environment as well, using the following command:

      srvctl setenv database -db database_name -env "environment_variable_name=environment_variable_value"

- To create a software keystore on a shared file system for Oracle Real Application Clusters (Oracle RAC), use the following format when you edit the `sqlnet.ora` file:

      ENCRYPTION_WALLET_LOCATION =
       (SOURCE = (METHOD = FILE)
        (METHOD_DATA =
         (DIRECTORY = +DATA/$ORACLE_UNQNAME)))

  If the `DIRECTORY` setting will include an environment variable, then set this variable in the environment where the database instance is started and before you start the database. If you are using the `srvctl` utility to start the database, then set the environment variable in the `srvctl` environment as well, using a command similar to the following, assuming the name of the Oracle RAC instance is `FINRAC`:

      srvctl setenv database -db FINRAC -t "ORACLE_UNQNAME=FINRAC, ORACLE_BASE=/u01/opt/oracle"

**Note:**

Starting with Oracle Database release 19c, the `ENCRYPTION_WALLET_LOCATION` parameter is deprecated. Instead, use the `WALLET_ROOT` static initialization parameter and the `TDE_CONFIGURATION` dynamic initialization parameter to configure the wallet location. `WALLET_ROOT` and `TDE_CONFIGURATION` can be used for a regular file system, multiple database access, and ASM.

**Parent topic:** Using sqlnet.ora to Configure Transparent Data Encryption Keystores

### 11.3 Example: Configuring a Software Keystore for a Regular File System

You can configure a software keystore for a regular file system.

The following example shows how to configure a software keystore location in the `sqlnet.ora` file for a regular file system in which the database name is `orcl`.

    ENCRYPTION_WALLET_LOCATION=
      (SOURCE=
       (METHOD=FILE)
        (METHOD_DATA=
         (DIRECTORY=/etc/ORACLE/WALLETS/orcl)))

**Note:**

Starting with Oracle Database release 19c, the `ENCRYPTION_WALLET_LOCATION` parameter is deprecated. Instead, use the `WALLET_ROOT` static initialization parameter and the `TDE_CONFIGURATION` dynamic initialization parameter to configure the wallet location.

**Related Topics**

- [Step 1: Configure the TDE Wallet Location and Type](configuring-transparent-data-encryption.md)

**Parent topic:** Using sqlnet.ora to Configure Transparent Data Encryption Keystores

### 11.4 Example: Configuring a TDE Wallet When Multiple Databases Share the Same Host

You can configure multiple databases to share the same host by setting the `WALLET_ROOT` parameter.

Because the `WALLET_ROOT` parameter is internal to an Oracle database, you only need to set the parameter to enable multiple databases to share the same host.

For example:

    ALTER SYSTEM SET WALLET_ROOT = '/etc/ORACLE/KEYSTORES/${ORACLE_SID}' SCOPE = SPFILE;

To implement clean separation of individual TDE wallets for each database, add the `ORACLE_SID` (or `ORACLE_UNQNAME` in Oracle Real Application Clusters) into the `WALLET_ROOT` parameter setting.

**Parent topic:** Using sqlnet.ora to Configure Transparent Data Encryption Keystores

### 11.5 Example: Configuring a Software Keystore for an Oracle Automatic Storage Management Disk Group

In an Oracle Real Applications Clusters (Oracle RAC) environment, the `WALLET_ROOT` parameter points to a shared directory in Oracle Automatic Storage Management (ASM) that is accessible from all Oracle RAC instances of that database.

The following example shows you how to set `WALLET_ROOT` and `TDE_CONFIGURATION` for a software keystore in ASM:

    ALTER SYSTEM SET WALLET_ROOT = '+DATA/unique_name_of_database' SCOPE = SPFILE SID = '*';

For example, if you set this value to `+DATA/FINRAC`, then the `/tde` directory is automatically generated when you create a wallet.

**Related Topics**

- [Configuring Keystores for Automatic Storage Management](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Using sqlnet.ora to Configure Transparent Data Encryption Keystores
