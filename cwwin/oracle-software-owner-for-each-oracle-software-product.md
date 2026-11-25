## Oracle Software Owner for Each Oracle Software Product

Oracle recommends that you use appropriate operating system groups and users for all installations where you specify separate Oracle Home Users:

You can choose from the following operating system groups and users, as per your configuration:

Separate Oracle Installation users for each Oracle software product (typically, `oracle`, for the Oracle Database software, and `grid` for the Oracle Grid Infrastructure software.

An Oracle installation user must have Administrator privilege to install Oracle sofware on the system. This user owns the Oracle binaries of the Oracle Grid Infrastructure software, and you can also use this same user as the Oracle Installation user for the Oracle Database or Oracle RAC binaries.

The Oracle Installation user for Oracle Database software has full administrative privileges for Oracle instances and is added to the `ORA_DBA`, `ORA_ASMDBA`, `ORA_``HOMENAME``_SYSBACKUP`, `ORA_``HOMENAME``_SYSDG`, `ORA_``HOMENAME``_SYSKM`, and `ORA_``HOMENAME``_SYSRAC` groups. Oracle Home users are added to the `ORA_``HOMENAME``_DBA` group for the Oracle home created during the installation. The `ORA_OPER` and `ORA_``HOMENAME``_OPER` groups are created, but no users are added to these groups during installation.

**Related Topics**

- [Oracle Database Security Guide](../dbseg/configuring-authentication.md)

**Parent topic:** [Standard Administration and Job Role Separation User Groups](standard-administration-and-job-role-separation-user-groups.md)
