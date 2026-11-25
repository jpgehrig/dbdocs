Use these examples to understand how you can modify your own Oracle Database upgrade configuration file for AutoUpgrade.

These examples are for an upgrade from an Oracle Database 12c Release 2 (12.2) non-CDB named DB12 to an Oracle Database 19c PDB named PDB3 in the target Oracle Database 19c CDB named CDB2. To understand details of how the global and local parameters are used, refer to the parameter references.

**Caution:**

Because this upgrade is a conversion from a non-CDB to a PDB, AutoUpgrade cannot create a guaranteed restore point that enables you to restore the non-CDB. To ensure your ability to recover from an issue, either back up your earlier release database, or convert the CDB to a PDB in your earlier release Oracle Database, and then upgrade and convert the earlier release PDB to the later release.

Example 2-7 AutoUpgrade Configuration File for Upgrade and Convert with Separate Backup Solution for Source Database

In this example, the configuration file directs AutoUpgrade to upgrade and convert the non-CDB Oracle Database 12c named DB12 to a PDB named PDB3 on the Oracle Database 21c CDB named CDB2.

    global.autoupg_log_dir=/home/oracle/logs
    upg1.source_home=/u01/app/oracle/product/12
    upg1.target_home=/u01/app/oracle/product/21
    upg1.sid=DB12
    upg1.target_cdb=CDB2
    upg1.target_pdb_name=PDB3

Example 2-8 AutoUpgrade Using `target_pdb_copy_option`

In this example, the parameter `upg1.target_pdb_copy_option` is used to have AutoUpgrade make a copy of the Oracle Database 12c (12.2.0.1) release to a PDB named PDB3, plugged into the Oracle Database 19c CDB1. AutoUpgrade then moves PDB3 from `/u02/oradata/CDB1/pdb3` to `/u02/oradata/CDB2/pdb3`.

    global.autoupg_log_dir=/home/oracle/logs

    upg1.source_home=/u01/app/oracle/product/12.2.0.1
    upg1.target_home=/u01/app/oracle/product/19
    upg1.sid=CDB1
    upg1.pdb=PDB3
    upg1.target_cdb=CDB2
    upg1.target_pdb_copy_option=file_name_convert=('CDB1', 'CDB2')

**Parent topic:** [Preparing to Upgrade Oracle Database](preparing-to-upgrade.md)
