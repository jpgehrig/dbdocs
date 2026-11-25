Learn about running system privilege authentication tasks on the Oracle Database server.

Perform the following steps:

1.  Add your administrator user names to this group. The client logs in using one of these user names so that it is granted the required system privilege.
    **See Also:**

    Your operating system documentation for instructions on managing users and groups
2.  Ensure that parameter `SQLNET.AUTHENTICATN_SERVICES` in file `sqlnet.ora` contains `nts`.

**Parent topic:** [Overview of Manually Granting Administrator, Operator, and Task-Specific Privileges for Databases](overview-of-manually-granting-administrator-operator-and-task-specific-privileges-for-databases.md)
