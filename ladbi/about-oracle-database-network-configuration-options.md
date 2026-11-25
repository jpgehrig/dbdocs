## About Oracle Database Network Configuration Options

You can enable database clients to connect to servers associated with multiple IP addresses, and you can install Oracle Database on servers with no network connections, and set up database services after installation.

Typically, the computer on which you want to install Oracle Database is a server running a single database instance, with a single host name that is resolvable on a network. Oracle Universal Installer uses the host name and Oracle Database instance information to set up network services automatically. The database provides database services to clients using a connect descriptor that resolves to the host name where the database instance is running.

However, you can configure Oracle Database on servers with the following nonstandard configurations:

- **Multihomed Computers**: Servers with multiple Oracle Database installations

- **Multiple Alias Computers**: Servers with multiple aliases, so that more than one host name resolves to the computer

- **Non-Networked computers**: Servers that do not have network connectivity at the time of installation

**Parent topic:** [Configuring Networks for Oracle Database](configuring-networks-for-oracle-database.md)
