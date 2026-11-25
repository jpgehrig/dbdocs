## Software Upgrades and Client and Server Configurations for Oracle Database

Use these topics to understand your options for upgrading precompiler and Oracle Call Interface (OCI) applications, depending on the type of software upgrade that you are performing and your client and server configurations.

- Possible Client and Server Configurations for Oracle Database
  Select a client/server configuration to run your precompiler and OCI applications.
- Types of Software Upgrades for Oracle Database Client and Server Software
  Review to identify if a release is a major release or a maintenance release.

**Parent topic:** [Upgrading Applications After Upgrading Oracle Database](upgrading-apps-after-oracle-db-upgrade.md)

### Possible Client and Server Configurations for Oracle Database

Select a client/server configuration to run your precompiler and OCI applications.

Your precompiler and OCI applications run on the client in a client/server environment, where the Oracle Database server is the server. You can use one or more of the following client/server configurations in your environment

#### Oracle Database Client and Server on Different Computers

The client software and the server software are on different computers, and they are connected through a network. The client and server environments are separate.

#### Oracle Database Client and Server in Different Oracle Locations on the Same Computer

The client software and the server software are on the same computer, but they are installed in different Oracle home directories. Again, the client and server environments are separate.

#### Oracle Database Client and Server in the Same Oracle Location

The client software and server software are installed in the same Oracle home on the same computer. In this case, any upgrade of the server software is also an upgrade of the client software.

**See Also:**

[Oracle Database Concepts](../cncpt/application-and-networking-architecture.md) for more information about client/server environments

**Parent topic:** Software Upgrades and Client and Server Configurations for Oracle Database

### Types of Software Upgrades for Oracle Database Client and Server Software

Review to identify if a release is a major release or a maintenance release.

Two types of upgrades are possible for Oracle Database client and server software: a major release of Oracle Database, and a maintenance release for Oracle Database.

#### Oracle Database Major Release Upgrade

In a major release, the upgrade changes the first digit of the release number. For example, upgrading from Oracle Database 11g to Oracle Database 12c is a major database release upgrade.

#### Oracle Database Maintenance Release Upgrade

In a maintenance release, the upgrade changes the second digit of the release number. For example, upgrading from Oracle Database 12c Release 1 (12.1) to Oracle Database 12g release 2 (12.2) is a database maintenance release upgrade. However, Oracle can introduce new features in maintenance releases.

**Parent topic:** Software Upgrades and Client and Server Configurations for Oracle Database
