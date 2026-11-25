## Changes in Oracle Database

The following are changes in Oracle Database SecureFiles and Large Objects Developer's Guide for Oracle Database.

- New Features

- Deprecated Features

- Desupported Features

<!-- -->

- New Features
- Deprecated Features
- Desupported Features

### New Features

#### New Features for 19c Release

- Oracle Database allows configuring signature-based security for large object (LOB) locators using the LOB_SIGNATURE_ENABLE initialization parameter

  [Managing LOB Signatures](managing-LOBs.md) for more information.

#### New Features for 18c Release

- Oracle Database allows `LOB`s and `LOB` related functionality to be used with Oracle Database In-Memory.

  [Oracle Database In-Memory Guide](../inmem/in-memory-column-store-architecture.md) for more information.

- Oracle Database extends Exadata support for `LOB`s to Compressed `LOB`s.

  [ENABLE or DISABLE STORAGE IN ROW Clause](LOB-storage-with-applications.md)

- Oracle Database has improved the performance of multiple persistent and temporary `LOB` operations.

**Parent topic:** Changes in Oracle Database

### Deprecated Features

#### List of deprecated features in Oracle® Database SecureFiles and Large Objects 18c

Oracle Multimedia is deprecated in Oracle Database Release 18c, and may be desupported in a future release. Oracle recommends that you stop using deprecated features as soon as possible.

#### List of deprecated features in Oracle® Database SecureFiles and Large Objects 12c, Release 2 (12.2)

The following list of features is deprecated in Oracle Database 12c Release 2 (12.2), and may be desupported in a future release.

- `DBMS_LOB.LOADFROMFILE` Procedure.

  Use `DBMS_LOB.LoadClobFromFile` or `DBMS_LOB.LoadBlobFromFile` instead.

- LOB Buffering subsystem APIs

  The following functions are deprecated beginning with Oracle 12c Release 2 (12.2):

  - [OCILobEnableBuffering()](../lnoci/deprecated-oci-functions.md)

  - [OCILobDisableBuffering()](../lnoci/deprecated-oci-functions.md)

  - [OCILobFlushBuffer()](../lnoci/deprecated-oci-functions.md)

  In place of using these LOB buffering functions, use the LOB prefetch feature described in [Prefetching of LOB Data, Length, and Chuck Size](../lnoci/lobs-and-bfile-operations.md).

- `DBMS_XSLPROCESSOR.CLOB2FILE` procedure.

  Use [`DBMS_LOB.CLOB2FILE`](../arpls/DBMS_LOB.md) procedure instead.

- `DBMS_LOB.LOADFROMFILE` Procedure.

  Use `DBMS_LOB.LoadClobFromFile` or `DBMS_LOB.LoadBlobFromFile` instead.

- `DBMS_XSLPROCESSOR.CLOB2FILE` procedure.

  Use [`DBMS_LOB.CLOB2FILE`](../arpls/DBMS_LOB.md) procedure instead.

#### Security Update for Native Encryption

Oracle provides a patch that you can download to address necessary security enhancements that affect native network encryption environments in Oracle Database release 11.2 and later.

This patch is available in My Oracle Support note [2118136.2](https://support.oracle.com/CSP/main/article?cmd=show&amp;type=NOT&amp;id=2118136.2).

The supported algorithms that have been improved are as follows:

- Encryption algorithms: AES128, AES192 and AES256
- Checksumming algorithms: SHA1, SHA256, SHA384, and SHA512

Algorithms that are deprecated and should not be used are as follows:

- Encryption algorithms: DES, DES40, 3DES112, 3DES168, RC4_40, RC4_56, RC4_128, and RC4_256
- Checksumming algorithm: MD5

If your site requires the use of network native encryption, then you must download the patch that is described in My Oracle Support note [2118136.2](https://support.oracle.com/CSP/main/article?cmd=show&amp;type=NOT&amp;id=2118136.2). To enable a smooth transition for your Oracle Database installation, this patch provides two parameters that enable you to disable the weaker algorithms and start using the stronger algorithms. You will need to install this patch on both servers and clients in your Oracle Database installation.

An alternative to network native encryption is Transport Layer Security (TLS), which provides protection against person-in-the-middle attacks.

**See Also:**

- [Choosing Between Native Network Encryption and Transport Layer Security](../dbseg/configuring-network-data-encryption-and-integrity.md) in Oracle Database Security Guide
- [Improving Native Network Encryption Security](../dbseg/configuring-network-data-encryption-and-integrity.md) in Oracle Database Security Guide

**Parent topic:** Changes in Oracle Database

### Desupported Features

#### List of desupported features in Oracle® Database SecureFiles and Large Objects 19c

Oracle Multimedia has been desupported in its entirety. Oracle recommends that you store multimedia content in SecureFiles LOBs and use third-party products.

**See Also:**

[Oracle Database Upgrade Guide](../upgrd/oracle-database-changes-deprecations-desupports.md) for more information.

#### List of desupported features in Oracle® Database SecureFiles and Large Objects 18c

The following functions related to LOB Buffering subsystem APIs are desupported in its entirety:

- [OCILobEnableBuffering()](../lnoci/deprecated-oci-functions.md)

- [OCILobDisableBuffering()](../lnoci/deprecated-oci-functions.md)

- [OCILobFlushBuffer()](../lnoci/deprecated-oci-functions.md)

#### List of desupported features in Oracle® Database SecureFiles and Large Objects 12c, Release (2) 12.2

- Desupport of Advanced Replication

  The Oracle Database Advanced Replication feature is desupported in its entirety.

  **See Also:**

  - [Oracle Database Upgrade Guide](../upgrd/oracle-database-changes-deprecations-desupports.md) for more information.

**Parent topic:** Changes in Oracle Database
