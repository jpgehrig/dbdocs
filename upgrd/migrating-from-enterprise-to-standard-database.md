## Migrating from Enterprise Edition to Standard Edition of Oracle Database

Converting from Enterprise Edition to Standard Edition requires exporting and importing data, using the Export utility.

To properly convert from an Enterprise Edition database to a Standard Edition database, you must perform an Export/Import operation. If you only install Standard Edition software, then some data dictionary objects become invalid. These invalid objects create problems when maintaining the database.

The Export/Import operation does not introduce data dictionary objects specific to the Enterprise Edition, because the `SYS` schema objects are not exported. After the Import in the Standard Edition database, you are only required to drop user schemas related to Enterprise Edition features.

**Parent topic:** [About Converting Databases During Upgrades](converting-databases-upgrades.md)
