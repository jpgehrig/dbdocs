## Required Postinstallation Tasks

Perform these tasks after completing your installation.

- [Determine If Any Patches Are Required For Your New Software](determine-if-any-patches-are-required-for-your-new-software.md)
  If you did not choose to download software options during installation, then after installing Oracle RAC, verify if there are any patches needed for your system.
- [Configure Exceptions for the Windows Firewall](configure-exceptions-for-the-windows-firewall.md)
  If the Windows Firewall feature is enabled on one or more nodes of your Oracle RAC cluster, then you must create exceptions for Oracle RAC applications and ports.
- [Create the OraMTS Service for Microsoft Transaction Server](create-the-oramts-service-for-microsoft-transaction-server.md)
  To enable client components to use Oracle databases as resource managers in Microsoft application coordinated transactions, create the Oracle Service for Microsoft Transaction Server (OraMTS).
- [Recompiling All Invalid Objects](recompiling-all-invalid-objects.md)
  Identify and recompile invalid objects on the CDB and PDBs using the `catcon` utility to run `utlrp.sql` after you install, patch, or upgrade a database.
- [Configuring Services on Oracle RAC with CDBs](configuring-services-on-oracle-rac-with-cdbs.md)
  During installation, if you select a multitenant container database (CDB), and configure pluggable databases (PDBs), then Oracle recommends that you add services to the PDBs after installation.

**Parent topic:** [Oracle Real Application Clusters Postinstallation Procedures](oracle-real-application-clusters-postinstallation-procedures.md)
