Oracle Grid Infrastructure for a standalone server includes Oracle Restart and Oracle Automatic Storage Management.

If you install Oracle Grid Infrastructure for a standalone server and then create your database, then the database is automatically added to the Oracle Restart configuration. Oracle Restart automatically restarts the database when required.

If you install Oracle Grid Infrastructure for a standalone server on a host computer on which a database already exists, then you must manually add the database, the listener, the Oracle ASM instance, and other components to the Oracle Restart configuration before you are able to configure automatic database restarts.

**Note:**

Oracle Grid Infrastructure for a standalone server can support multiple single-instance databases on a single host computer.

- [About Image-Based Oracle Grid Infrastructure Installation](about-image-based-oracle-grid-infrastructure-installation.md)
  Installation and configuration of Oracle Grid Infrastructure software is simplified with image-based installation.
- [Setup Wizard Installation Options for Creating Images](setup-wizard-installation-options.md)
  Before you start the setup wizards for your Oracle Database or Oracle Grid Infrastructure installation, decide if you want to use any of the available image-creation options.
- [Installing Oracle Grid Infrastructure for a Standalone Server with a New Database Installation](installing-oracle-grid-infrastructure-for-a-standalone-server-with-a-new-database-installation.md)
  Complete these steps to Install Oracle Grid Infrastructure for a standalone server and then create a database that is managed by Oracle Restart.
- [Installing Oracle Grid Infrastructure for a Standalone Server for an Existing Database](installing-oracle-grid-infrastructure-for-a-standalone-server-for-an-existing-database.md)
  Follow the high-level instructions in this section to install Oracle Grid Infrastructure for a standalone server and configure it for an existing Oracle Database.
- [Installing Oracle Grid Infrastructure for a Standalone Server Using a Software-Only Installation](installing-oracle-grid-infrastructure-for-a-standalone-server-using-a-software-only-installation.md)
  A software-only installation only installs the Oracle Grid Infrastructure for a standalone server binaries at the specified location. You must complete a few manual configuration steps to enable Oracle Restart after you install the software.
- [Testing the Oracle Automatic Storage Management Installation](testing-the-oracle-automatic-storage-management-installation.md)
  After installing Oracle Grid Infrastructure for a single instance, use the ASMCMD command-line utility to test the Oracle ASM installation.
- [Relinking Oracle Restart and Oracle ASM Binaries](modifying-oracle-grid-infrastructure-for-a-standalone-server-binaries-after-installation.md)
  Relink the Oracle Restart and Oracle ASM binaries every time you apply an operating system patch or after an operating system upgrade.
- [Configuring Oracle ASM Disk Groups Manually using Oracle ASMCA](configuring-oracle-asm-disk-groups-manually-using-oracle-asmca.md)
  After installing Oracle Grid Infrastructure for a standalone server, you can also use Oracle ASMCA to create and configure disk groups, Oracle ADVM, and Oracle ACFS.
- [Enabling Oracle ACFS on Oracle Restart Configurations](enabling-oracle-acfs-on-oracle-restart-configurations.md)
  You must enable root access to use Oracle ACFS.
- [Applying Patches During an Oracle Grid Infrastructure Installation or Upgrade](applying-patches-during-gi-install.md)
  Starting with Oracle Grid Infrastructure 18c, you can download and apply Release Updates (RUs) and one-off patches during an Oracle Grid Infrastructure installation or upgrade.
