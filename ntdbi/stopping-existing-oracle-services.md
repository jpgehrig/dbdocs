## Stopping Existing Oracle Services

Learn how to stop all processes, including the listener and database, running in the Oracle home.

Consider the following before you install Oracle Restart or Oracle Database:

- If you intend to use Oracle Restart, then you must install the Oracle Restart before you install and create the database. When you perform a database installation, the database must use the same listener created during the Oracle Restart installation, thereafter you do not have to perform the steps listed in this section.

  The default listener and any additional listeners must run from the Oracle Grid Infrastructure home.

- If you have an existing Oracle Database 19c running on Oracle ASM, then stop any existing Oracle ASM instances. After you finish installing Oracle Restart, start the Oracle ASM instance again.

If you choose to create a database during the installation, then most installation types configure and start a default Oracle Net listener using TCP/IP port `1521` and the IPC key value `EXTPROC`. However, if an existing Oracle Net listener process is using the same port or key value, Oracle Universal Installer looks for the next available port (for example, `1522`) and configures and starts the new listener on this available port.

**Caution:**

If you are installing additional Oracle Database 19c products in an existing Oracle home, then stop all processes, including the listener and database, running in the Oracle home. You cannot install into an existing Oracle home other than 19c. You must complete this task to enable Oracle Universal Installer to relink certain executables and libraries.

**Parent topic:** [Configuring Users, Groups and Environments for Oracle Database](configuring-users-groups-and-environments-for-oracle-database.md)
