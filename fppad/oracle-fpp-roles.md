## Oracle Fleet Patching and Provisioning Roles

An administrator assigns roles to Oracle Fleet Patching and Provisioning users with access-level permissions defined for each role.

Users on Oracle Fleet Patching and Provisioning Clients are also assigned specific roles. Oracle Fleet Patching and Provisioning includes basic built-in and composite built-in roles.

### Basic Built-In Roles

The basic built-in roles and their functions are:

- GH_ROLE_ADMIN: An administrative role for everything related to roles. Users assigned this role are able to run `rhpctl ``verb`` role` commands.

- GH_SITE_ADMIN: An administrative role for everything related to Oracle Fleet Patching and Provisioning Clients. Users assigned this role are able to run `rhpctl ``verb`` client` commands.

- GH_SERIES_ADMIN: An administrative role for everything related to image series. Users assigned this role are able to run `rhpctl ``verb`` series` commands.

- GH_SERIES_CONTRIB: Users assigned this role can add images to a series using the `rhpctl insertimage series` command, or delete images from a series using the `rhpctl deleteimage series` command.

- GH_WC_ADMIN: An administrative role for everything related to working copies of gold images. Users assigned this role are able to run `rhpctl ``verb`` workingcopy` commands.

- GH_WC_OPER: A role that enables users to create a working copy of a gold image for themselves or others using the `rhpctl add workingcopy` command with the `-user` option (when creating for others). Users assigned this role do not have administrative privileges and can only administer the working copies of gold images that they create.

- GH_WC_USER: A role that enables users to create a working copy of a gold image using the `rhpctl add workingcopy` command. Users assigned this role do not have administrative privileges and can only delete working copies that they create.

- GH_IMG_ADMIN: An administrative role for everything related to images. Users assigned this role are able to run `rhpctl ``verb`` image` commands.

- GH_IMG_USER: A role that enables users to create an image using the `rhpctl add | import image` commands. Users assigned this role do not have administrative privileges and can only delete images that they create.

- GH_IMG_TESTABLE: A role that enables users to add a working copy of an image that is in the `TESTABLE` state. Users assigned this role must also be assigned either the GH_WC_ADMIN role or the GH_WC_USER role to add a working copy.

- GH_IMG_RESTRICT: A role that enables users to add a working copy from an image that is in the `RESTRICTED` state. Users assigned this role must also be assigned either the GH_WC_ADMIN role or the GH_WC_USER role to add a working copy.

- GH_IMG_PUBLISH: Users assigned this role can promote an image to another state or retract an image from the `PUBLISHED` state to either the `TESTABLE` or `RESTRICTED` state.

- GH_IMG_VISIBILITY: Users assigned this role can modify access to promoted or published images using the `rhpctl allow | disallow image` commands.

- GH_AUTHENTICATED_USER: Users assigned to this role can execute any operation in an Oracle Fleet Patching and Provisioning Client.

- GH_CLIENT_ACCESS: Any user created automatically inherits this role. The `GH_CLIENT_ACCESS` role includes the `GH_AUTHENTICATED_USER` built-in role.

### Composite Built-In Roles

The composite built-in roles and their functions are:

- GH_SA: The Oracle Grid Infrastructure user on an Oracle Fleet Patching and Provisioning Server automatically inherits this role.

  The GH_SA role includes the following basic built-in roles: GH_ROLE_ADMIN, GH_SITE_ADMIN, GH_SERIES_ADMIN, GH_SERIES_CONTRIB, GH_WC_ADMIN, GH_IMG_ADMIN, GH_IMG_TESTABLE, GH_IMG_RESTRICT, GH_IMG_PUBLISH, and GH_IMG_VISIBILITY.

- GH_CA: The Oracle Grid Infrastructure user on an Oracle Fleet Patching and Provisioning Client automatically inherits this role.

  The GH_CA role includes the following basic built-in roles: GH_SERIES_ADMIN, GH_SERIES_CONTRIB, GH_WC_ADMIN, GH_IMG_ADMIN, GH_IMG_TESTABLE, GH_IMG_RESTRICT, GH_IMG_PUBLISH, and GH_IMG_VISIBILITY.

- GH_OPER: This role includes the following built-in roles: GH_WC_OPER, GH_SERIES_ADMIN, GH_IMG_TESTABLE, GH_IMG_RESTRICT, and GH_IMG_USER. Users assigned this role can delete only images that they have created.

Consider a gold image called `G1` that is available on the Oracle Fleet Patching and Provisioning Server.

Further consider that a user, `U1`, on an Oracle Fleet Patching and Provisioning Client, `Cl1`, has the GH_WC_USER role. If `U1` requests to provision an Oracle home based on the gold image `G1`, then `U1` can do so, because of the permissions granted by the GH_WC_USER role. If `U1` requests to delete `G1`, however, then that request would be denied because the GH_WC_USER role does not have the necessary permissions.

The Oracle Fleet Patching and Provisioning Server can associate user-role mappings to the Oracle Fleet Patching and Provisioning Client. After the Oracle Fleet Patching and Provisioning Server delegates user-role mappings, the Oracle Fleet Patching and Provisioning Client can then modify user-role mappings on the Oracle Fleet Patching and Provisioning Server for all users that belong to the Oracle Fleet Patching and Provisioning Client. This is implied by the fact that only the Oracle Fleet Patching and Provisioning Server qualifies user IDs from an Oracle Fleet Patching and Provisioning Client site with the client cluster name of that site. Thus, the Oracle Fleet Patching and Provisioning Client `CL1` will not be able to update user mappings of a user on `CL2`, where `CL2` is the cluster name of a different Oracle Fleet Patching and Provisioning Client.

- [Creating Users and Assigning Roles for Fleet Patching and Provisioning Client Cluster Users](creating-users-and-assigning-roles-for-oracle-fpp-users.md)
  Oracle Fleet Patching and Provisioning (Oracle FPP) enables you to create users and assign roles to them when you create an Oracle FPP client.

**Parent topic:** [Oracle Fleet Patching and Provisioning Security Postinstallation Tasks](security-postinstallation-tasks.md)
