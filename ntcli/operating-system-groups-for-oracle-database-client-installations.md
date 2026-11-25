## Creating Users, Groups and Environments for Oracle Database Client

Before installation, create operating system groups, users, and configure user environments.

Oracle Universal Installer creates other groups, such as, `ORA_INSTALL`, `ORA_CLIENT_LISTENERS`, `ORA_``HOMENAME``_SVCSIDS` during installation and you must not change these groups, memberships, and ACLs associated with various Oracle created groups.

The groups that are created are explained as follows:

- ORA_INSTALL: This is a system wide group for Oracle's internal use, which is automatically populated with Oracle Home users. If a database server is running on this system, it grants dupsocket privilege to the group's members to allow listeners to operate. If no database server is present, this group is not used.

- ORA_CLIENT_LISTENERS: This group is for internal Oracle use. It contains listeners installed on client homes through custom installs. If a database server is running on this system, it grants dupsocket privilege to the group's members to allow listeners to work. If no database server is present, this group is not used.

- ORA\_HOMENAME\_SVCSIDS: This group is for Oracle's internal use and is automatically populated. It contains Service SIDs for all Windows services (e.g. Oracle Services for MTS, Listener, and Connection Manager) on client homes installed through custom installs. This group is granted full control to the specific client Oracle Home and client Oracle Base.

- ORA_DBA and ORA\_HOMENAME\_DBA: If the system is only used for clients, membership provides start/stop privileges to Oracle Windows services running from client homes. `ORA_DBA` members are granted start/stop privileges for all Oracle Windows services on the system, while membership in `ORA_``HOMENAME``_DBA` gives start/stop privileges to Oracle Windows services running from the specific home.

**Parent topic:** [Oracle Database Client Preinstallation Tasks](oracle-database-client-preinstallation-tasks.md)
