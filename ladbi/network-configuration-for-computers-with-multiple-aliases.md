## Network Configuration for Computers with Multiple Aliases

You must set the `ORACLE_HOSTNAME` environment variable to install Oracle Database on a multialias computer. A multialias computer is one to which multiple aliases resolve.

A computer with multiple aliases is a computer that is registered with the naming service under a single IP address, but which resolves multiple aliases to that address. The naming service resolves any of those aliases to the same computer. Before installing Oracle Database on such a computer, set the Oracle installation owner environment variable `ORACLE_HOSTNAME` to the computer whose host name you want to use.

**Parent topic:** [Configuring Networks for Oracle Database](configuring-networks-for-oracle-database.md)
