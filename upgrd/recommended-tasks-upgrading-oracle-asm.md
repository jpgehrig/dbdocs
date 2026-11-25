## Recommended Tasks After Upgrading Oracle ASM

After you have upgraded Oracle ASM, Oracle recommends that you perform tasks such as resetting the Oracle ASM passwords and configuring disk groups.

- Create a Shared Password File In the ASM Diskgroup
  If you advance the COMPATIBLE.ASM disk group attribute, then create a shared password file.
- Reset Oracle ASM Passwords to Enforce Case-Sensitivity
  To take advantage of enforced case-sensitive passwords, you must reset the passwords of existing users during the database upgrade procedure.
- Advancing the Oracle ASM and Oracle Database Disk Group Compatibility
  You can advance the Oracle Database and the Oracle ASM disk group compatibility settings across software versions.
- Set Up Oracle ASM Preferred Read Failure Groups
  Oracle ASM administrators can specify some disks as preferred read disks for read I/O operations.

**Related Topics**

- [Add New Features as Appropriate](recommended-and-best-practices-complete-upgrading-oracle-database.md)
- [Develop New Administrative Procedures as Needed](recommended-and-best-practices-complete-upgrading-oracle-database.md)

**Parent topic:** [Post-Upgrade Tasks for Oracle Database](post-upgrade-tasks-oracle-database.md)

### Create a Shared Password File In the ASM Diskgroup

If you advance the COMPATIBLE.ASM disk group attribute, then create a shared password file.

If you advanced the COMPATIBLE.ASM disk group attribute to 12.1 or later, then you are required to create a shared password file in the ASM diskgroup.

**See Also:**

[Oracle Automatic Storage Management Administrator's Guide](../ostmg/authenticate-access-asm-instance.md) for complete information about managing a shared password file in a disk group

**Parent topic:** Recommended Tasks After Upgrading Oracle ASM

### Reset Oracle ASM Passwords to Enforce Case-Sensitivity

To take advantage of enforced case-sensitive passwords, you must reset the passwords of existing users during the database upgrade procedure.

In releases earlier than Oracle Database 11g Release 1 (11.1), passwords are not case sensitive. You can enforce case sensitivity for passwords. For example, the password `hPP5620qr` fails if it is entered as `hpp5620QR` or `hPp5620Qr`.

For new Oracle ASM instances, there are no additional tasks or management requirements. For upgraded Oracle ASM instances, each user password must be reset with an `ALTER` `USER` statement.

**Note:**

If the default Oracle Database security settings are in place, then passwords must be at least eight characters, and passwords such as `welcome` and `oracle` are not allowed. See [Oracle Database Security Guide](../dbseg/keeping-your-oracle-database-secure.md) for more information.

**Parent topic:** Recommended Tasks After Upgrading Oracle ASM

### Advancing the Oracle ASM and Oracle Database Disk Group Compatibility

You can advance the Oracle Database and the Oracle ASM disk group compatibility settings across software versions.

**Caution:**

If you advance the `COMPATIBLE.RDBMS` attribute, then you cannot revert to the previous setting. Before advancing the `COMPATIBLE.RDBMS` attribute, ensure that the values for the `COMPATIBLE` initialization parameter for all of the databases that use the disk group are set to at least the new setting for `COMPATIBLE.RDBMS` before you advance the attribute value.

Advancing compatibility enables new features only available in the new release. However, doing so makes the disk group incompatible with older releases of the software. Advancing the on disk compatibility is an irreversible operation.

Use the `compatible.rdbms` and `compatible.asm` attributes to specify the minimum software release required by the database instance and the Oracle ASM instance, respectively, to access the disk group. For example, the following `ALTER DISKGROUP` statement advances the Oracle ASM compatibility of the disk group `asmdg2`:

    ALTER DISKGROUP asmdg2 SET ATTRIBUTE 'compatible.asm' = '12.2'

In this case, the disk group can be managed only by Oracle ASM software of release 12.2 or later, while any database client of release 11.2 or later can use the disk group.

**Parent topic:** Recommended Tasks After Upgrading Oracle ASM

### Set Up Oracle ASM Preferred Read Failure Groups

Oracle ASM administrators can specify some disks as preferred read disks for read I/O operations.

**Note:**

The `ASM_PREFERRED_READ_FAILURE_GROUPS` initialization parameter is deprecated in Oracle Automatic Storage Management 12c release 2 (12.2.0.1). Starting with Oracle Automatic Storage Management (Oracle ASM) 12c release 2 (12.2.0.1), specifying the preferred read failure groups is done automatically, so the use of the` ASM_PREFERRED_READ_FAILURE_GROUPS` initialization parameter is no longer required. Use the `PREFERRED_READ.ENABLED` disk group attribute to control the preferred read functionality.

**Parent topic:** Recommended Tasks After Upgrading Oracle ASM
