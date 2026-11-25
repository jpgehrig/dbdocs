## Changes in This Release for Oracle Database Advanced Security Guide

This preface contains:

- Changes in Oracle Database Advanced Security 19c
- Updates to Oracle Advanced Database Security 19c

### Changes in Oracle Database Advanced Security 19c

The following are changes in Oracle Database Advanced Security Guide for Oracle Database 19c.

- Improved Key Management Support for Encrypting Oracle-Managed Tablespaces
  In this release, closing a TDE keystore is now allowed even when the Oracle-managed tablespaces (`SYSTEM`, `SYSAUX`, `TEMP`, and `UNDO` tablespaces) are encrypted.
- Transparent Online Conversion Support for Auto-Renaming in Non-Oracle-Managed Files Mode
  Starting with this release, online tablespace encryption no longer requires you to specify the `FILE_NAME_CONVERT` clause in the `ALTER TABLESPACE ENCRYPT` SQL statement. The file names will retain their original names.
- Support for More Algorithms for Offline Tablespace Encryption
  In previous releases, only the `AES128` encryption algorithm was supported for offline tablespace encryption. In addition to `AES128`, this release introduces support for the `AES192` and `AES256` encryption algorithms, as well as `ARIA`, `GOST`, and `3DES` encryption algorithms for offline tablespace encryption.

**Parent topic:** Changes in This Release for Oracle Database Advanced Security Guide

#### Improved Key Management Support for Encrypting Oracle-Managed Tablespaces

In this release, closing a TDE keystore is now allowed even when the Oracle-managed tablespaces (`SYSTEM`, `SYSAUX`, `TEMP`, and `UNDO` tablespaces) are encrypted.

Internal operations on these tablespaces when they are encrypted continue to be unaffected even when the TDE keystore is in the `CLOSED` state.

Closing the TDE keystore has no effect on queries of an encrypted `SYSTEM`, `SYSAUX`, `TEMP`, or `UNDO` tablespace, unlike queries of a user-created tablespace, which continue to return an `ORA-28365 wallet is not open` error when the TDE keystore is closed.

User-initiated operations such as decrypt on any encrypted Oracle-managed tablespace still require the TDE keystore to be in the `OPEN` state.

**Related Topics**

- [Impact of a Closed TDE Keystore on Encrypted Tablespaces](configuring-transparent-data-encryption.md)

**Parent topic:** Changes in Oracle Database Advanced Security 19c

#### Transparent Online Conversion Support for Auto-Renaming in Non-Oracle-Managed Files Mode

Starting with this release, online tablespace encryption no longer requires you to specify the `FILE_NAME_CONVERT` clause in the `ALTER TABLESPACE ENCRYPT` SQL statement. The file names will retain their original names.

This enhancement helps to prevent you from having to rename files back to the original name afterward, sometimes missing files.

**Related Topics**

- [Encrypting an Existing Tablespace with Online Conversion](configuring-transparent-data-encryption.md)

**Parent topic:** Changes in Oracle Database Advanced Security 19c

#### Support for More Algorithms for Offline Tablespace Encryption

In previous releases, only the `AES128` encryption algorithm was supported for offline tablespace encryption. In addition to `AES128`, this release introduces support for the `AES192` and `AES256` encryption algorithms, as well as `ARIA`, `GOST`, and `3DES` encryption algorithms for offline tablespace encryption.

This enhancement benefits scenarios in which you have concerns about auxiliary space usage required by online tablespace encryption.

**Related Topics**

- [About Encryption Conversion for Tablespaces and Databases](configuring-transparent-data-encryption.md)
- [Supported Encryption and Integrity Algorithms](introduction-to-transparent-data-encryption.md)

**Parent topic:** Changes in Oracle Database Advanced Security 19c

### Updates to Oracle Advanced Database Security 19c

Oracle Advanced Database Security release 19c has one update from the last update of release 19c.

- Oracle Data Guard Redo Decryption for Hybrid Disaster Recovery Configurations
  Available for Oracle Database release 19.16, Oracle Data Guard enables you to decrypt redo operations in hybrid cloud disaster recovery configurations where the Cloud database is encrypted with TDE and the on-premises database is not.

**Parent topic:** Changes in This Release for Oracle Database Advanced Security Guide

#### Oracle Data Guard Redo Decryption for Hybrid Disaster Recovery Configurations

Available for Oracle Database release 19.16, Oracle Data Guard enables you to decrypt redo operations in hybrid cloud disaster recovery configurations where the Cloud database is encrypted with TDE and the on-premises database is not.

Hybrid disaster recovery is often considered a quick-stepping stone to cloud adoption. By enabling the ability to quickly configure disaster recovery even in cases where on-premises databases might not already be encrypted with TDE, the steps required to configure hybrid disaster recovery environments are reduced while still ensuring that redo data is still encrypted during the transportation process.

To enable this feature, Oracle Database introduces the `TABLESPACE_ENCRYPTION` initialization parameter, which enables you to control the automatic encryption of tablespaces in both the primary and standby databases, for on-premises and Oracle Cloud Infrastructure (OCI) environments. For example, an on-premises database can be unencrypted and an OCI database can be encrypted.

**Related Topics**

- [Encryption of Tablespaces in an Oracle Data Guard Environment](using-transparent-data-encryption-with-other-oracle-features.md)

**Parent topic:** Updates to Oracle Advanced Database Security 19c
