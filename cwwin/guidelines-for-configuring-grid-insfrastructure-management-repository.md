## Guidelines for the Grid Infrastructure Management Repository

Consider these guidelines while configuring the Grid Infrastructure Management Repository (GIMR) for your deployment.

- Starting with Oracle Grid Infrastructure 19c, configuring the GIMR is optional for Oracle Standalone Cluster deployments. The Oracle Standalone Cluster locally hosts the GIMR on an Oracle ASM disk group or a shared file system; this GIMR is a multitenant database with a single pluggable database (PDB).

- Configuring the GIMR is optional for only new installations and does not apply to existing installations.

- If you have a GIMR in your current deployment, then the GIMR is upgraded with Oracle Grid Infrastructure 19c. However, if you do not have a GIMR in your current deployment, then you cannot add the GIMR as part of upgrade to Oracle Grid Infrastructure 19c.

  For deployments where there is no GIMR, you can add a GIMR after installing Oracle Grid Infrastructure 19c or after upgrading to Oracle Grid Infrastructure 19c.

**Parent topic:** [About the Grid Infrastructure Management Repository](about-grid-insfrastructure-management-repository.md)
