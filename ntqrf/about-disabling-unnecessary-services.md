After you have significantly reduced the file cache, you can retrieve additional physical memory for Oracle Database by disabling services not needed for core operating system functionality.

Unnecessary services include:

- License Logging Service

- Plug and Play

- Remote Access Autodial Manager

- Remote Access Connection Manager

- Remote Access Server

- Telephony Service

Consult with your systems administrator to identify other unnecessary services.

Do not disable any of the following services:

- Alerter

- Computer Browser

- EventLog

- Messenger

- `OracleService``SID`

- `Oracle``HOMENAME``TNSListener`

- Remote Procedure Call (RPC) Service

- Server

- Spooler

- TCP/IP NetBS Helper

- Workstation

**Related Topics**

- [About Configuring Windows Server to Be an Application Server](about-configuring-windows-server-to-be-an-application-server.md)

**See Also:**

Your operating system documentation for instructions on disabling unnecessary services

**Parent topic:** [Tuning Windows to Optimize Oracle Database](tuning-windows-to-optimize-oracle-database.md)
