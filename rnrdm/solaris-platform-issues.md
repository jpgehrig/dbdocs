These topics contain last-minute features and changes for Oracle Solaris for Oracle Database 19c.

- Unsupported Products for Oracle Solaris
  In addition to the list of unavailable products or features in this release of Oracle Database 19c, the following product is not supported for Oracle Solaris:
- Product Support
  These are the supported products or features for Oracle Database 19c:
- Linking Applications with Oracle Client Libraries for Oracle Solaris
  You must use the dynamic Oracle client libraries to link the client code on Oracle Solaris.
- Preinstallation Requirements for Oracle Solaris
  Refer to the installation guides for the preinstallation requirements for Oracle Database 19c.
- Installation, Configuration, and Upgrade Issues for Oracle Solaris
  These topics describe information about issues that affect Oracle Database installation, configuration, and upgrade.
- Open Bugs Affecting Oracle Solaris
  There are no open bugs affecting Oracle Solaris at the time of the release.

### Unsupported Products for Oracle Solaris

In addition to the list of unavailable products or features in this release of Oracle Database 19c, the following product is not supported for Oracle Solaris:

- Net Configuration Assistant Support

<!-- -->

- Bug 21816875
  Net Configuration Assistant (NETCA) is not supported on Oracle Solaris on SPARC (32-Bit) and Oracle Solaris on x86 (32-Bit) client platforms.

**Parent topic:** Issues Affecting Oracle Solaris for Oracle Database 19c

#### Bug 21816875

Net Configuration Assistant (NETCA) is not supported on Oracle Solaris on SPARC (32-Bit) and Oracle Solaris on x86 (32-Bit) client platforms.

**Parent topic:** Unsupported Products for Oracle Solaris

### Product Support

These are the supported products or features for Oracle Database 19c:

- Oracle Solaris Support on SPARC

  Oracle Database 19c is supported on Oracle Solaris on SPARC (64-bit).

- Database Smart Flash Cache Support

  Database Smart Flash Cache is supported on Oracle Solaris.

- Oracle ACFS and Oracle ADVM Support

  Although Oracle ADVM supports raw disks in Oracle Automatic Storage Management disk groups, Oracle ADVM device special files created through raw are not supported; Oracle ADVM only supports block device special files.

  For the latest information about supported platforms and releases, see the Note 1369107.1 on My Oracle Support at [https://support.oracle.com](https://support.oracle.com/)

**Parent topic:** Issues Affecting Oracle Solaris for Oracle Database 19c

### Linking Applications with Oracle Client Libraries for Oracle Solaris

You must use the dynamic Oracle client libraries to link the client code on Oracle Solaris.

 Do not link the static Oracle client libraries.

**Parent topic:** Issues Affecting Oracle Solaris for Oracle Database 19c

### Preinstallation Requirements for Oracle Solaris

Refer to the installation guides for the preinstallation requirements for Oracle Database 19c.

**Parent topic:** Issues Affecting Oracle Solaris for Oracle Database 19c

### Installation, Configuration, and Upgrade Issues for Oracle Solaris

These topics describe information about issues that affect Oracle Database installation, configuration, and upgrade.

- Bug 21800407
- Bug 28650933
- Bug 24355490

**Parent topic:** Issues Affecting Oracle Solaris for Oracle Database 19c

#### Bug 21800407

When installing Oracle Database for English and Japanese environments, the background font incorrectly displays yellow color for the Oracle Universal Installer (OUI), Database Configuration Assistant (DBCA), and Database Upgrade Assistant (DBUA) pages.

Workaround:

Prior to installing Oracle Database, run the following command:

`export _JAVA_OPTIONS='-Dsun.java2d.xrender=false'`

**Parent topic:** Installation, Configuration, and Upgrade Issues for Oracle Solaris

#### Bug 28650933

Installing and using Oracle Secure Backup 12.2 on Oracle Solaris 11.4 may fail if the library `libnls.so` is not available in standard system library paths, since the Oracle Secure Backup libraries depend on `libnls.so`.

Workaround:

Upgrade the Oracle Solaris OS version to Oracle Solaris 11.4.6.4.0. and then install Oracle Secure Backup 12.2. Alternate workaround is to copy the file `/usr/ib/64/libnls.so.1` from an Oracle Solaris 11.3 machine to the `/usr/lib/64` path in the Oracle Solaris 11.4 machine where Oracle Secure Backup 12.2 needs to be installed.

**Parent topic:** Installation, Configuration, and Upgrade Issues for Oracle Solaris

#### Bug 24355490

When installing or upgrading an Oracle Grid Infrastructure home on Oracle Solaris 10, if the desired software location resides under a soft link, then the Oracle Grid Infrastructure installer incorrectly sets the physical path as the software location.

Workaround:

Perform the following steps:

1.  Set the Oracle Grid Infrastructure installer specifying the complete path to the desired Oracle home path:

    `Complete Oracle home path``/gridSetup.sh`

2.  Proceed with the Oracle Grid Infrastructure installation.

**Parent topic:** Installation, Configuration, and Upgrade Issues for Oracle Solaris

### Open Bugs Affecting Oracle Solaris

There are no open bugs affecting Oracle Solaris at the time of the release.

**Parent topic:** Issues Affecting Oracle Solaris for Oracle Database 19c
