## Local Configuration File Parameter Fixups Checklist Example

To include or exclude specific fixups for individual databases during upgrades, use the local configuration file checklist.

In this example, there is a local checklist file called `sales4_checklist.cfg`, which provides a preupgrade fixup checklist for the database `sales4`. A portion of the file contains the following settings:

    [checkname] DICTIONARY_STATS
    [stage] PRECHECKS
    [fixup_available] YES
    [runfix] YES
    [severity] RECOMMEND

You can change the default fixup for `DICTIONARY_STATS` to exclude performing a fixup for the database `sales4` by changing the `runfix` option for the check from `YES` to `NO`:

    [checkname] DICTIONARY_STATS
    [stage] PRECHECKS
    [fixup_available] YES
    [runfix] NO
    [severity] RECOMMEND

**Parent topic:** [Using AutoUpgrade for Oracle Database Upgrades](using-autoupgrade-oracle-database-upgrades.md)
