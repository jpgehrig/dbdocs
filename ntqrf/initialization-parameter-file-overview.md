An initialization parameter file is an ASCII text file containing parameters.

By changing parameters and values in an initialization parameter file, you can specify, for example:

- Amount of memory Oracle Database uses

- Whether to archive filled online redo logs

- Which control files currently exist

Every database instance has a corresponding initialization parameter file and an `ORACLE_SID` registry parameter that points to the system identifier for the instance.

The initialization parameter file name takes the form `init.ora`. A single instance might have several initialization parameter files, each having some differences that affect system performance.

**Note:**

Your `init.ora` file for initialization parameters is set by Oracle Universal Installer during database installation. These parameter settings may vary depending on your hardware configuration.

- [About the Location of the Initialization Parameter File](about-the-location-of-the-initialization-parameter-file.md)
  Describes the location of the initialization parameter file.
- [About Editing The Initialization Parameter File](about-editing-the-initialization-parameter-file.md)
  To customize Oracle Database functions, you may be required to edit the initialization parameter file.
- [About Oracle Database Configuration Assistant Renaming init.ora](about-database-configuration-assistant-renaming-init-ora.md)
  When you create a database using Oracle Database Configuration Assistant (Oracle DBCA), a Server Parameter File (SPFILE) is created from the initialization parameter file, and the initialization parameter file is renamed.

**See Also:**

[Oracle Database Reference](../refrn/initialization-parameters.md) for descriptions of all initialization parameters and instructions for setting and displaying their values

**Parent topic:** [Oracle Database Specifications for Windows](oracle-database-specifications-for-windows.md)
