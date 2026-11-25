Security is a large arena that includes network security for the connection, access, and execution control of operating system resources or of Java virtual machine (JVM)-defined and user-defined classes. Security also includes bytecode verification of Java Archive (JAR) files imported from an external source. This chapter describes the various security support available for Java applications within Oracle Database:

- [Network Connection Security](network-connection-security.md)

- [Database Contents and Oracle JVM Security](database-contents-Oracle-JVM-security.md)

- [Database Authentication Mechanisms Available with Oracle JVM](Oracle-JVM-authentication-mechanism.md)

- [Secure Use of Runtime.exec Functionality in Oracle Database](Runtime-exe-secure-use.md)

### 10.1 Database Security in a Multitenant Environment

Oracle Multitenant Isolation is a set of security principles implemented by the Oracle Multitenant Architecture. It is designed to guard each tenant's data and the overall performance integrity of all aspects of Oracle Database, on both On-Premise Database as well as on Oracle Cloud Infrastructure.

PDB isolation is a part of the Oracle Multitenant Isolation feature, which defines what individual PDBs can perform. This release enhances the support for PDB isolation by Oracle JVM in the following ways:

#### Support for the PATH_PREFIX Clause

When the `PATH_PREFIX` clause is in effect, then Oracle JVM performs file path checking for all the file access APIs, blocking file access outside of the `PATH_PREFIX`.

#### Support for the PDB_OS_CREDENTIAL Initialization Parameter

When the `PDB_OS_CREDENTIAL` initialization parameter is in effect, and Oracle JVM forks the `runtime.exec` processes on behalf of any user of such a PDB, then such a forked process has the corresponding OS credentials associated with it.

#### Additional Flexibility in Specifying Oracle JVM OS Access Restrictions

The enhancements to the PDB isolation feature provides the following additional flexibility in specifying the Oracle JVM Operating System (OS) Access Restrictions in the PDB lockdown profiles:

#### New Role of JAVA_OS_ACCESS Lockdown Profile Feature

The existing `JAVA_OS_ACCESS` lockdown profile feature, which controls the `java.io.FilePermission` Java permission, is assigned a new, closely-related role. It now controls the file-access checks in the Oracle JVM run time. This new role blends well with its existing role of controlling the file permissions.

#### The OS_ACCESS Lockdown Feature Bundle

You can still use the existing `OS_ACCESS` Lockdown profile feature bundle to disable the file-access access in the Oracle JVM run time as long as its constituent feature `JAVA_OS_ACCESS` is not configured to enable the file-access checks of Oracle JVM.

#### Examples of Enhanced Oracle JVM OS Access Restrictions

This section describes how to take advantage of the enhanced Oracle JVM OS access restrictions:

Earlier, you used the following command to disable all OS access from Java:

    ALTER LOCKDOWN PROFILE my_profile1 DISABLE FEATURE ('OS_ACCESS');

Now, you can use the following commands to disable all OS access from Java, except file access:

        ALTER LOCKDOWN PROFILE my_profile2 DISABLE FEATURE ('OS_ACCESS');
        ALTER LOCKDOWN PROFILE my_profile2 ENABLE FEATURE ('JAVA_OS_ACCESS');

Complete Example

This is a complete example that demonstrates the following:

- Creating a new PDB with the `PATH_REFIX` clause value set
- Creating a new lockdown profile that disables all types of OS access, except for Java file operations
- Linking the new lockdown profile to the PDB
- Administering the users in the new PDB with the ability to read and write files inside the `PATH_PREFIX`

Example 10-1 Complete Example Demonstrating Oracle JVM Enhanced OS Access Restrictions

1.  Create a PDB named `cdb1_pdb5`, while you connect as the root `SYS` user and `cdb1_pdb0` is the CDB root:

        create pluggable database cdb1_pdb5 admin user admin identified by manager
        file_name_convert = ('cdb1_pdb0','cdb1_pdb5') path_prefix='/d1/pdbs/pdb5/'

2.  Create a lockdown profile and set it to disable the `OS_ACCESS` and `NETWORK_ACCESS` features, and enable the `JAVA_OS_ACCESS` feature:

            create lockdown profile java_profile;
            alter lockdown profile java_profile disable feature=('OS_ACCESS');
            alter lockdown profile java_profile disable feature=('NETWORK_ACCESS');
            alter lockdown profile java_profile  enable feature=('JAVA_OS_ACCESS');

3.  Associate the `JAVA_PROFILE` with the `pdb5` PDB:

            alter session set container = cdb1_pdb5;
            alter system set pdb_lockdown = java_profile ;

4.  Restart the database after altering the system:

            alter session set container = cdb1_pdb0; -- this is the root
            shutdown abort
            startup pfile = t_initvm1.ora
            alter pluggable database all open;
            alter session set container = cdb1_pdb5;
            grant create session, create procedure, create public synonym to admin;
            grant create table to admin;
            -- add other grants to the local PDB admin as required

5.  Grant permissions to user `ADMIN` for file access operations:

        call dbms_java.grant_permission('ADMIN', 'SYS:java.io.FilePermission',
        '/d1/pdbs/pdb5/-', 'read,write,delete');

6.  Create a regular user in `cdb1_pdb5`:

            create user juser identified by juser;
            grant create session to juser;

7.  Grant `juser` the permissions for file access operations:

            call dbms_java.grant_permission('JUSER', 'SYS:java.io.FilePermission',
        '/d1/pdbs/pdb5/file1.txt', 'read');
            call dbms_java.grant_permission('JUSER', 'SYS:java.io.FilePermission',
        '/d1/pdbs/pdb5/file2.txt', 'read,write');

#### Additional Flexibility in the Oracle JVM Networking Access Restrictions

The enhancements to the PDB isolation feature provides the following additional flexibilities in specifying the Oracle JVM Networking Access Restrictions in the PDB lockdown profiles:

#### New Role of UTL_TCP Lockdown Profile Feature

The existing `UTL_TCP` lockdown profile feature that controls the PL/SQL TCP functionality, is assigned a new, closely-related role. It now controls the TCP operations in the Oracle JVM run time. This new role blends well with its existing role of controlling the PL/SQL TCP connectivity.

#### New Role of UTL_HTTP Lockdown Profile Feature

The existing `UTL_HTTP` lockdown profile feature that controls the PL/SQL HTTP functionality, is assigned a new, closely-related role. It now controls the HTTP connectivity in the Oracle JVM run time. This new role blends well with its existing role of controlling the PL/SQL HTTP connectivity.

#### The NETWORK_ACCESS Lockdown Profile Feature Bundle

You can still use the existing `NETWORK_ACCESS` lockdown profile feature bundle to disable networking in the Oracle JVM run time as a whole.

#### Examples of Enhanced Oracle JVM Networking Access Restrictions

Earlier, the following command used to disable all networking access, including the access provided using Java:

    ALTER LOCKDOWN PROFILE my_profile1 DISABLE FEATURE ('NETWORK_ACCESS');

Following are a few examples that show how to take advantage of the enhanced Oracle JVM networking access restrictions:

Example 1

Use these commands to disable any type of networking, except the following:

- Networking done using the `UTL_HTTP` PL/SQL package
- Oracle JVM HTTP operations using the `HttpURLConnection` and `HttpsURLConnection` JDK classes

<!-- -->

        ALTER LOCKDOWN PROFILE my_profile2 DISABLE FEATURE ('NETWORK_ACCESS');
        ALTER LOCKDOWN PROFILE my_profile2 ENABLE FEATURE ('UTL_HTTP');

Example 2

Use these commands to disable any type of networking, except the following:

- Networking done using the `UTL_TCP` PL/SQL package
- Oracle JVM TCP operations including HTTP

<!-- -->

        ALTER LOCKDOWN PROFILE my_profile3 DISABLE FEATURE ('NETWORK_ACCESS');
        ALTER LOCKDOWN PROFILE my_profile3 ENABLE FEATURE ('UTL_TCP');

#### Important Notes for Database Administrators

This release further enhances the ability of CDB Database Administrators to configure safe lockdowns for PDBs that allow file access from Oracle JVM. For security and isolation, always use the `PATH_PREFIX` clause when any form of file access is allowed for PDBs.

This section summarizes the important enhancements made to the PDB isolation feature for CDB administrators:

- Earlier, disabling the `OS_ACCESS` feature in a lockdown profile meant disabling all OS access from Java, including file operations. Now, a lockdown profile can enable only the Java file operations, while other types of OS access from Java remain disabled:

          ALTER LOCKDOWN PROFILE my_profile DISABLE FEATURE ('OS_ACCESS');
          ALTER LOCKDOWN PROFILE my_profile ENABLE FEATURE ('JAVA_OS_ACCESS');

- Earlier, disabling the `NETWORK_ACCESS` feature in a lockdown profile meant disabling all network access from Java. Now, a lockdown profile can selectively enable HTTP connectivity (PL/SQL and Oracle JVM), while other types of networking remain disabled:

          ALTER LOCKDOWN PROFILE my_profile DISABLE FEATURE ('NETWORK_ACCESS');
          ALTER LOCKDOWN PROFILE my_profile ENABLE FEATURE ('UTL_HTTP');

- Earlier, disabling the `NETWORK_ACCESS` feature in a lockdown profile meant disabling all network access from Java. Now, a lockdown profile can selectively enable TCP connectivity (PL/SQL and Oracle JVM), while other types of networking remain disabled:

          ALTER LOCKDOWN PROFILE my_profile DISABLE FEATURE ('NETWORK_ACCESS');
          ALTER LOCKDOWN PROFILE my_profile ENABLE FEATURE ('UTL_TCP');

**See Also:**

- [Oracle Multitenant Isolation White Paper](https://www.oracle.com/technetwork/database/multitenant/learn-more/isolation-wp-12c-3614475.pdf)
- [ALTER LOCKDOWN PROFILE](../sqlrf/ALTER-LOCKDOWN-PROFILE.md) for description of PDB lockdown profile features
- [CREATE PLUGGABLE DATABASE](../sqlrf/CREATE-PLUGGABLE-DATABASE.md) for more information about the `PATH_PREFIX` clause
- [PDB_OS_CREDENTIAL](../refrn/PDB_OS_CREDENTIAL.md) for more information about the `PDB_OS_CREDENTIAL` initialization parameter
