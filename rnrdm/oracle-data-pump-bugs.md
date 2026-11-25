These are the Oracle Data Pump bugs in Oracle Database 19c.

- Bug 27092988

**Parent topic:** [Open Bugs Affecting All Platforms](open-bugs-for-all-platforms.md)

### Bug 27092988

In releases prior to Oracle Database 19c, the Oracle Data Pump always enabled secure roles that were granted to the user running the data pump. Starting in Oracle Database 19c, the data pump no longer enables these roles by default. There is a new parameter, `ENABLE_SECURE_ROLES`, to control whether those roles should be enabled for the data pump job.

#### Workaround:

None.

**Parent topic:** Oracle Data Pump Known Bugs
