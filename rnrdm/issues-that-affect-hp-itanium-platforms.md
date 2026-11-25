These topics contain last-minute features and changes for HP-UX Itanium for Oracle Database 19c.

- Unsupported Products for HP-UX Itanium
  In addition to the list of unavailable products or features in this release of Oracle Database 19c, the following products and features are not supported:
- Product Support
  There are no supported products or features for Oracle Database 19c on HP-UX Itanium at this time.
- Linking Applications with Oracle Client Libraries for HP-UX Itanium
  You must use the dynamic Oracle client libraries to link the client code on HP-UX Itanium.
- Preinstallation Requirements for HP-UX Itanium
  Refer to the installation guides for the preinstallation requirements for Oracle Database 19c.
- Installation, Configuration, and Upgrade Issues for HP-UX Itanium
  This topic describes information about issues that affect Oracle Database installation, configuration, and upgrade.

### Unsupported Products for HP-UX Itanium

In addition to the list of unavailable products or features in this release of Oracle Database 19c, the following products and features are not supported:

- Database Smart Flash Cache Support

- Oracle ASM Filter Driver Support

**Parent topic:** Issues Affecting HP-UX Itanium for Oracle Database 19c

### Product Support

There are no supported products or features for Oracle Database 19c on HP-UX Itanium at this time.

**Parent topic:** Issues Affecting HP-UX Itanium for Oracle Database 19c

### Linking Applications with Oracle Client Libraries for HP-UX Itanium

You must use the dynamic Oracle client libraries to link the client code on HP-UX Itanium.

Do not link the static Oracle client libraries.

**Parent topic:** Issues Affecting HP-UX Itanium for Oracle Database 19c

### Preinstallation Requirements for HP-UX Itanium

Refer to the installation guides for the preinstallation requirements for Oracle Database 19c.

**Parent topic:** Issues Affecting HP-UX Itanium for Oracle Database 19c

### Installation, Configuration, and Upgrade Issues for HP-UX Itanium

This topic describes information about issues that affect Oracle Database installation, configuration, and upgrade.

- Bug 27367949
- Bug 28340043
- Bug 29198896

**Parent topic:** Issues Affecting HP-UX Itanium for Oracle Database 19c

#### Bug 27367949

In some Oracle Database installation scenarios, Database Upgrade Assistant (DBUA) reports a prerequirement checks failure, and returns the following error:

    Oracle OLAP API UPGRADED 18.1.0.0.0 00:00:18
    Upgrade Datapatch Error: prereq checks failed!
    Upgrade Datapatch 00:00:37

Further `catupgrd_datapatch_normal.log` returns the following error:

    Connecting to database...OK
    Gathering database info...done
    Bootstrapping registry and package to current versions...done
    Error: prereq checks failed!
    verify_queryable_inventory returned ORA-20001: Latest xml inventory is not loaded into table
    Prereq check failed, exiting without installing any patches.

Workaround:

Start DBUA as a user with the same group ID as that of the Oracle user that owns the Oracle Database 18c Oracle home.

For example, if the user `asmadmin` is the group owner of the Oracle home on your system, change the user primary group to the `asmadmin` group using `newgrp`:

    bash-4.3$ ls -l $ORACLE_HOME/bin/oracle
    -rwsr-s--x 1 oracle asmadmin 1133380232 Feb 14 00:36 bin/oracle
    bash-4.3$ newgrp asmadmin
    bash-4.3$ $ORACLE_HOME/bin/dbua

**Parent topic:** Installation, Configuration, and Upgrade Issues for HP-UX Itanium

#### Bug 28340043

In some Oracle Database installation scenarios, creating database using Database Configuration Assistant (DBCA) results in `INVALID JAVAVM` component or database upgrade using Database Upgrade Assistant (DBUA) reports a prerequirement checks failure and returns the following error:

    Oracle OLAP API UPGRADED 18.1.0.0.0 00:00:18
    Upgrade Datapatch Error: prereq checks failed!
    Upgrade Datapatch 00:00:37

Further `catupgrd_datapatch_normal.log` returns the following error:

    Connecting to database...OK
    Gathering database info...done
    Bootstrapping registry and package to current versions...done
    Error: prereq checks failed!
    verify_queryable_inventory returned ORA-20001: Latest xml inventory is not loaded into table
    Prereq check failed, exiting without installing any patches.

Workaround:

Start DBCA or DBUA as a user with the same group ID as that of the Oracle user that owns the Oracle Database 18c Oracle home.

For example, if the user `asmadmin` is the group owner of the Oracle home on your system, change the user primary group to the `asmadmin` group using `newgrp`:

    bash-4.3$ ls -l $ORACLE_HOME/bin/oracle
    -rwsr-s--x 1 oracle asmadmin 1133380232 Feb 14 00:36 bin/oracle
    bash-4.3$ newgrp asmadmin
    bash-4.3$ $ORACLE_HOME/bin/dbua

**Parent topic:** Installation, Configuration, and Upgrade Issues for HP-UX Itanium

#### Bug 29198896

While duplicating Oracle Database as standby using Database Configuration Assistant (DBCA), internally, RMAN DUPLICATE tries to copy the password file from Oracle Automatic Storage Management (Oracle ASM) to Non-ASM or vice-versa. The password file is copied, but the clone password file is not readable and returns the following error:

      “ORA-01017: invalid username/password; logon denied” on clone instance reconnection"

Workaround:

If the source instance password file is on Oracle ASM, then define the clone instance password on Oracle ASM only, and when the source password file is on Non-ASM files system, then keep the clone instance password file on Non-ASM file system.

**Parent topic:** Installation, Configuration, and Upgrade Issues for HP-UX Itanium
