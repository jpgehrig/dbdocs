Review to find the default, minimum, and maximum values for the COMPATIBLE initialization parameter for Oracle Database 19c.

### Default and Minimum COMPATIBLE Parameter Values

The COMPATIBLE parameter should not be changed for an RU or an RUR, either for CDB or Non-CDB instances. The following table lists the default and minimum values for the COMPATIBLE parameter in Oracle Database 19c, compared to earlier releases supported for direct upgrade:

### COMPATIBLE Initialization Parameter Set Too Low for Direct Upgrade to Oracle Database 19c

If the `COMPATIBLE` parameter on your source Oracle Database is set to a value too low for upgrade to Oracle Database 19c, then you must raise the `COMPATIBLE` setting on the source Oracle Database release to at least the minimum value supported for Oracle Database 19c upgrades. The minimum `COMPATIBLE` setting for Oracle Database is 11.2.0.

For example: if your source Oracle Database release is Oracle Database release is Oracle Database 11g Release 2 (11.2.0.4), but the compatible parameter is set to 10.0.0 (`COMPATIBLE = 10.0.0`), then you must change the compatible parameter to at least the minimum supported value for upgrade before you start the upgrade (`COMPATIBLE = 11.2.0`).

**Note:**

After you change the `COMPATIBLE` parameter, you must restart the database.

Table 1-1 The COMPATIBLE Initialization Parameter

| Oracle Database Release              | Default Value | Minimum Value |
|:-------------------------------------|:--------------|:--------------|
| Oracle Database 19c                  | `19.0.0`      | `11.2.0`      |
| Oracle Database 12c Release 2 (12.2) | `12.2.0`      | `11.2.0`      |
| Oracle Database 12c Release 1 (12.1) | `12.0.0`      | `11.0.0`      |
| Oracle Database 11g Release 2 (11.2) | `11.2.0`      | `10.0.0`      |

**Parent topic:** [Checking Compatibility Before Upgrading Oracle Database](getting-started.md)
