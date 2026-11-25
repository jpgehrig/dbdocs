You must create an Oracle Context to use net directory naming features with Active Directory.

Oracle Context is the top-level Oracle entry in the Active Directory tree. It contains Oracle Database service and Oracle Net service name object information.

- You can create only one Oracle Context for each Windows server domain (administrative context).

- You must have the necessary permissions to create domain and enterprise objects to create the Oracle Context in Active Directory with Oracle Net Configuration Assistant.

- Use Oracle Net Configuration Assistant to create your Oracle Context. You can create the Oracle Context during or after Oracle Database Custom installation.

**See Also:**

- [Oracle Database Installation Guide for Microsoft Windows](../ntdbi/installing-oracle-database.md) for installation procedures

- [Oracle Database Net Services Administrator's Guide](../netag/part-II-config-and-admin-of-oracle-net-services.md) for configuration procedures

<!-- -->

- [Running Oracle Network Configuration Assistant](running-oracle-network-configuration-assistant.md)
  Oracle Net Configuration Assistant is a graphical, wizard-based tool used to configure and manage Oracle Network configurations.

**Parent topic:** [Overview of Requirements for Using Oracle Database with Active Directory](overview-of-requirements-for-using-oracle-database-with-active-directory.md)
