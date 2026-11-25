## About the Oracle Installation User

The Oracle Installation User can be either a local user or a domain user.

To install the Oracle Grid Infrastructure or Oracle Database software, you must use either a local or domain user. In either case, the **Oracle Installation User** must be an explicit member of the Administrators group on all nodes of the cluster.

If you use a local user account for installing Oracle Grid Infrastructure or Oracle Real Application Clusters (Oracle RAC), then:

- The user account must exist on all nodes in the cluster.

- The user name and password must be the same on all nodes.

- OUI displays a warning message.

If you use a domain user account for installing Oracle Grid Infrastructure or Oracle Real Application Clusters (Oracle RAC), then:

- The domain user must be explicitly declared as a member of the local Administrators group on each node in the cluster. It is not sufficient if the domain user has inherited membership from another group.

- The user performing the installation must be in the same domain on each node. For example, you cannot have the `DBADMIN\dba1` user on the first node and the `RACDBA\dba1` user on the second node.

- A local user of the same name cannot exist on any of the nodes. For example if you use `RACDBA\dba1` as the installation user, none of the nodes can have a local `NODE1\dba1` user account.

**Parent topic:** [Creating Installation Groups and Users for Oracle Grid Infrastructure and Oracle RAC](creating-installation-groups-and-users-for-grid-and-rac.md)
