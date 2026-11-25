Specifies the location of time zone file.

Each file contains:

- Valid time zone names

- Offset from UTC

- Abbreviation for standard time

- Abbreviation for daylight savings time

In previous releases, the default value for `ORA _TZFILE` was

    ORACLE_BASE\ORACLE_HOME\oracore\zoneinfo\timezlrg.dat

Starting with Oracle Database 11g Release 2 (11.2), the default value is

    ORACLE_HOME\oracore\zoneinfo\timezlrg_11.dat

The `timezone_``version_number``.dat` data files contain most commonly used time zones and are smaller for better database performance. The new default, `timezlrg_``version_number``.dat`, includes time zones not defined in the smaller file.

**See Also:**

[Oracle Database Globalization Support Guide](../nlspg/appendix-A-locale-data.md) for additional details about time zone files

**Parent topic:** [About HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\KEY_HOMENAME](about-hkey-local-machine.md)
