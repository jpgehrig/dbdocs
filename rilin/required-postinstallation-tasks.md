## Required Postinstallation Tasks

Download and apply required patches for your software release after completing your initial installation.

- [Downloading Release Update Patches](downloading-and-installing-patch-updates.md)
  Download and install Release Updates (RU) and Monthly Recommended Patches (MRPs) patches for your Oracle software after you complete installation.
- [Setting External Jobs Ownership for HP-UX Installations](setting-external-jobs-ownership-for-hp-ux-installations.md)
  On HP-UX platforms only, set external jobs ownership to a low-privilege user.
- [Setting the Oracle User Environment Variables](setting-the-oracle-user-environment-variables.md)
  On each node, in the installation owner user profile file, set the environment variables `ORACLE_BASE` and `ORACLE_HOME`, and `ORACLE_SID`; also add `ORACLE_HOME/bin` to the path environment variable.
- [Recompile Invalid Objects in the Database](recompiling-all-invalid-objects.md)
  After you install, patch, or upgrade a database, recompile invalid objects on the CDB and PDBs with a recompilation driver script.
- [Configuring Services on Oracle RAC and Oracle RAC One Node CDBs](configuring-services-on-oracle-rac-and-oracle-rac-one-node-cdbs.md)
  During installation, if you select a multitenant container database (CDB), and configure pluggable databases (PDBs), then you must add services to the PDBs after installation.
- [Copying Oracle ASM Password File For Oracle RAC One Node Database](copying-oracle-asm-password-file-for-oracle-rac-one-node-database.md)
  After installing Oracle RAC One Node database, copy the Oracle ASM password file, if configured, to all candidate nodes configured for fail over, unless you use shared password files stored in Oracle ASM.

**Parent topic:** [Oracle Real Application Clusters Postinstallation Procedures](oracle-real-application-clusters-postinstallation-procedures.md)
