You must set scripts to point to the new Oracle home location.

After you upgrade Oracle Database to a new release, you must ensure that your `oratab` file and any client scripts that set the value of `ORACLE_HOME` point to the new Oracle home that is created for the new Oracle Database release. DBUA automatically points `oratab` to the new Oracle home. However, you must check client scripts regardless of the method you use to upgrade.

If you upgrade your database manually, then you must log in as the Oracle installation owner for the new Oracle Database release, and update the `oratab` file manually. The location of the `oratab` file can vary, depending on your operating system.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/getting-started-with-database-administration.md) for information about setting operating system environment variables

My Oracle Support: Find or Create Oratab File (Doc ID 394251.1)

<https://support.oracle.com/rs?type=doc&id=394251.1>

**Parent topic:** [Required Tasks to Complete After Upgrading Oracle Database](required-tasks-to-complete-after-upgrade.md)
