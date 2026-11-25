This section describes compatibility, upgrading, downgrading, and installation topics for Oracle Database 19c.

- Core Dump ORA-00600 \[8153\] Error Encountered After Database Upgrade
  This topic describes the `ORA-00600` error that can occur after a database upgrade.
- Upgrading from Oracle Database 11g Release 2 (11.2.0.4) to 19c to Oracle Database Results in Errors During Upgrade
  This topic describes the `ORA-08102` error that can occur when upgrading from Oracle Database 11g release 2 (11.2.0.4) to Oracle Database 19c.
- Plugging in an Oracle Database 12.1 Non-CDB to an Oracle Database 12.2 Local Undo CDB
  This topic describes undo tablespaces are not plugged in when going from Oracle Database release 12.1 to release 12.2.

**Parent topic:** [Issues Affecting All Platforms for Oracle Database 19c](issues-all-platforms.md)

### Core Dump ORA-00600 \[8153\] Error Encountered After Database Upgrade

This topic describes the `ORA-00600` error that can occur after a database upgrade.

A core dump `ORA-00600 [8153]` error is encountered after the database is upgraded to Oracle Database 12c release 2 (12.2) or to Oracle Database 19c and then downgraded back to its original release (reference Bug 20898997).

Always apply the patch for this bug before upgrading the database to Oracle Database 12c release 2 (12.2) or to Oracle Database 19c.

**Parent topic:** Compatibility, Upgrading, Downgrading, and Installation

### Upgrading from Oracle Database 11g Release 2 (11.2.0.4) to 19c to Oracle Database Results in Errors During Upgrade

This topic describes the `ORA-08102` error that can occur when upgrading from Oracle Database 11g release 2 (11.2.0.4) to Oracle Database 19c.

In some cases, when altering table `WRH$_SEG_STAT` to add some columns, you may encounter the `ORA-08102` error (reference Bug 28668676). For example:

    ALTER TABLE WRH$_SEG_STAT ADD (im_membytes NUMBER DEFAULT 0);
    ALTER TABLE WRH$_SEG_STAT ADD (im_membytes NUMBER DEFAULT 0)
    *
    ERROR at line 1:
    ORA-08102: index key not found, obj# 16200, file 2, block 4765 (2)

Download `c18.sql` and `c1202000.sql` from the bug and restart the upgrade process.

**Parent topic:** Compatibility, Upgrading, Downgrading, and Installation

### Plugging in an Oracle Database 12.1 Non-CDB to an Oracle Database 12.2 Local Undo CDB

This topic describes undo tablespaces are not plugged in when going from Oracle Database release 12.1 to release 12.2.

When trying to plug in an Oracle Database 12c Release 1 (12.1) non-CDB to an Oracle Database 12c Release 2 (12.2) or higher CDB and local undo is enabled, undo tablespaces are not plugged in.

#### Workaround:

None.

**Parent topic:** Compatibility, Upgrading, Downgrading, and Installation
