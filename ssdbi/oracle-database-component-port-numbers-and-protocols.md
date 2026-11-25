This table lists the port numbers and protocols configured for Oracle Database components during a single-instance installation. By default, the first port in the range is assigned to the component, if it is available.

Table D-1 Protocols and Default Port Numbers for Oracle Database Components

| Component                    | Description                                                                                                                                                                                                                                              | Default Port Number | Port Range                                                                                    | Protocol |
|:-----------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------|:----------------------------------------------------------------------------------------------|:---------|
| Oracle Net Services Listener | Enables Oracle client connections to the database over the Oracle Net Services protocol. You can configure it during installation. To reconfigure this port, use Net Configuration Assistant.                                                            | 1521                | Port number changes to the next available port.<br>Modifiable manually to any available port. | TCP      |
| Oracle Connection Manager    | Listening port for Oracle client connections to Oracle Connection Manager. It is not configured during installation, but can be configured manually by editing the `cman.ora` parameter file. This file is located under the `/network/admin `directory. | 1630                | 1630                                                                                          | TCP      |
| Oracle XML DB                | The Oracle XML DB HTTP port is used if web-based applications must access an Oracle database from an HTTP listener. You must configure this port manually.                                                                                               | 0                   | Configured Manually                                                                           | HTTP     |
| Oracle XML DB                | The Oracle XML DB FTP is used when applications must access an Oracle database from an FTP listener. You must configure this port manually.                                                                                                              | 0                   | Configured Manually                                                                           | FTP      |

**Related Topics**

- [Using HTTP(S) on a Standard Port](../adxdb/repository-access-using-protocols.md)
- [Using FTP on the Standard Port](../adxdb/repository-access-using-protocols.md)
- [Oracle Real Application Clusters Installation Guide for Linux and UNIX](../rilin/port-numbers-and-protocols-of-oracle-components.md)

**Parent topic:** [Managing Oracle Database Port Numbers](managing-oracle-database-port-numbers.md)
