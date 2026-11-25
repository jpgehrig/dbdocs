## Creating Users and Assigning Roles for Fleet Patching and Provisioning Client Cluster Users

Oracle Fleet Patching and Provisioning (Oracle FPP) enables you to create users and assign roles to them when you create an Oracle FPP client.

When you create a Fleet Patching and Provisioning Client with the `rhpctl add client` command, you can use the `-maproles` parameter to create users and assign roles to them. You can associate multiple users with roles, or you can assign a single user multiple roles with this command.

After the client has been created, you can add and remove roles for users using the `rhpctl grant role` command and the `rhpctl revoke role`, respectively.

**Parent topic:** [Oracle Fleet Patching and Provisioning Roles](oracle-fpp-roles.md)
