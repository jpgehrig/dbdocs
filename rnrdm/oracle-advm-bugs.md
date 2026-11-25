These are the Oracle Automatic Storage Management (Oracle ASM) Dynamic Volume Manager (Oracle ADVM) bugs in Oracle Database 19c.

- Bug 29520544

**Parent topic:** [Open Bugs Affecting All Platforms](open-bugs-for-all-platforms.md)

### Bug 29520544

Upgrading to Oracle Grid 19c or 18c can cause unnecessary disk resilvering (if using more than 1 MB of allocation units (AU)). This issue does not occur on a fresh installation of Oracle Grid 19c or 18c.

#### Workaround:

Apply the patch for 29520544 before upgrading to Oracle Grid 19c or 18c. Note that the patch can be applied on the initiating system (Oracle Grid 12c Release 1 (12.1.0.2) or Oracle Grid 12c Release 2 (12.2)) before the upgrade or the patch can be applied on the receiving system (Oracle Grid 19c or 18c) before the upgrade.

Allow resilvering to complete. This is a one-time operation. Once the resilvering completes, performance returns to normal.

**Parent topic:** Oracle ASM Dynamic Volume Manager (Oracle ADVM) Known Bugs
