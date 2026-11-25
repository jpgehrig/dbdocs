## Creating a Database Using Oracle ASM for Database Files in Silent Mode

Creating an Oracle Real Application Clusters (Oracle RAC) database that uses Oracle Automatic Storage Management (Oracle ASM) for storage is a multi-step process.

Before you create a database that uses Oracle ASM, you must run the `root.bat` script. For this reason, you cannot create a database using Oracle ASM as the storage option for database files during a silent-mode installation.

**Note:**

This limitation applies only to databases that use Oracle Automatic Storage Management as the storage option for database files. You can create a database that uses the file system option during a silent-mode installation.

1.  Complete a software-only installation of Oracle RAC using silent-mode.
2.  Run Oracle Database Configuration Assistant (DBCA) in silent mode.

**See Also:**

"[Performing a Software-Only Installation of Oracle Database](Chunk456916531.md)"

**Parent topic:** [How Response Files Work](how-response-files-work.md)
