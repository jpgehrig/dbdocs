## Network Configuration for Multihome Computers

You must set the `ORACLE_HOSTNAME` environment variable to install Oracle Database on a multihomed computer. A multihomed computer is associated with multiple IP addresses.

Typically, a server configured to run multiple Oracle Database Oracle homes is configured with multiple network interface cards. A host name resolves to an IP address configured for one network card for each Oracle Database. You can also set up aliases for host names. By default, during installation, Oracle Universal Installer uses the value set for the environment variable `ORACLE_HOSTNAME` set for the Oracle installation user account running the installation to find the host name. If the user environment variable `ORACLE_HOSTNAME` is not set for the Oracle user, and you are installing on a computer that has multiple network cards, then Oracle Universal Installer determines the host name from the `/etc/hosts` file and the information you provide during the installation session.

Oracle Database clients connecting to the database must be able to access the computer by using either the alias for the host name, or by using the host name associated with that instance. To verify that the client can resolve to the database using both alias and host name, use the `ping` command to check connectivity to the host name both for the database on the server (host name only), and for the fully qualified domain name (host name and domain name).

**Note:**

Clients must be able to obtain a response using the `ping` command both for the host name and for the fully qualified domain name. If either test fails, then contact your network administrator to resolve the issue.

**Parent topic:** [Configuring Networks for Oracle Database](configuring-networks-for-oracle-database.md)
