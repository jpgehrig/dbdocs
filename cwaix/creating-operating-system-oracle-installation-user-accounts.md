Before starting installation, create Oracle software owner user accounts, and configure their environments.

Oracle software owner user accounts require resource settings and other environment configuration. To protect against accidents, Oracle recommends that you create one software installation owner account for each Oracle software program you install.

- [Creating an Oracle Software Owner User](creating-an-oracle-software-owner-user.md)
  If the Oracle software owner user (`oracle` or `grid`) does not exist, or if you require a new Oracle software owner user, then create it as described in this section.
- [Modifying Oracle Owner User Groups](modifying-oracle-owner-user-groups.md)
  If you have created an Oracle software installation owner account, but or it is not a member of the groups you want to designate as the OSDBA, OSOPER, OSDBA for ASM, ASMADMIN, or other system privileges group, then modify the group settings for that user before installation.
- [Identifying Existing User and Group IDs](identifying-existing-user-ids-group-ids.md)
  To create identical users and groups, you must identify the user ID and group IDs assigned them on the node where you created them, and then create the user and groups with the same name and ID on the other cluster nodes.
- [Creating Identical Database Users and Groups on Other Cluster Nodes](creating-users-groups-on-other-cluster-nodes.md)
  Oracle software owner users and the Oracle Inventory, OSDBA, and OSOPER groups must exist and be identical on all cluster nodes.
- [Example of Creating Minimal Groups, Users, and Paths](example-of-creating-minimal-users-roles-groups.md)
  You can create a minimal operating system authentication configuration as described in this example.
- [Example of Creating Role-allocated Groups, Users, and Paths](example-of-creating-role-allocated-groups-users-paths.md)
  Understand this example of how to create role-allocated groups and users that is compliant with an Optimal Flexible Architecture (OFA) deployment.

**Parent topic:** [Configuring Users, Groups and Environments for Oracle Grid Infrastructure and Oracle Database](configuring-users-groups-and-environments-for-oracle-grid-infrastructure-and-oracle-database.md)
