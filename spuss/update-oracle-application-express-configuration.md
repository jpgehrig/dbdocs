Oracle Application Express affects upgrade procedures, depending on the Oracle Application Express release and your database installation type.

If the Oracle Database release that you upgrade includes Oracle Application Express release 3.2 or later, then you do not need to carry out additional configuration after upgrading to the new Oracle Database release. However, if Oracle Application Express is in the registry, so that Oracle Application Express is included in the upgrade, then set the open_cursors parameter to a minimum of 200.

If the Oracle Database you upgrade is an Oracle Express Edition database, then it contains an earlier release of Oracle Application Express that is tailored for the Oracle Express Edition environment. The latest Oracle Application Express release is automatically installed during the upgrade. You must complete a series of postinstallation steps to configure Oracle Application Express for use with the new Oracle Database release.

**See Also:**

- [Oracle Application Express Installation Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/spuss&id=HTMIG-GUID-802A767F-2528-4B98-AC4F-B683DF4E572B) for postinstallation tasks for Oracle Application Express

- [`http://www.oracle.com/technetwork/developer-tools/apex/overview/index.html`](http://www.oracle.com/technetwork/developer-tools/apex/overview/index.html)

**Parent topic:** [Required Tasks to Complete After Upgrading Oracle Database](required-tasks-to-complete-after-upgrade.md)
