## Easy Connect Naming Method

The Easy Connect naming method eliminates the need to look up service names in the tnsnames.ora file or other repository for TCP/IP environments.

With Easy Connect, clients use a connect string for a simple TCP/IP address, which consists of a host name, and an optional port and service name. If you use this method, then no naming or directory system is required. See "[Example 6-1](about-connecting-to-an-oracle-rac-database-using-scans.md)" for an example.

Networking elements for the Oracle Database server and clients are preconfigured for most environments. The Easy Connect naming method is enabled by default and does not require a repository. If you use a naming method other than Easy Connect, then additional configuration of Oracle Net Services may be required.

**Parent topic:** [Oracle Net Services Configuration for Oracle RAC Databases](oracle-net-services-configuration-for-oracle-rac-databases.md)
