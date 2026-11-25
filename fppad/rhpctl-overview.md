## RHPCTL Overview

RHPCTL is a command-line utility with which you perform Oracle Fleet Patching and Provisioning operations and manage Oracle Fleet Patching and Provisioning Servers and Clients.

RHPCTL uses the following syntax:

    rhpctl command object [parameters]

In RHPCTL syntax:

- `command` is a verb such as `add`, `delete`, or `query`

- `object` (also known as a noun) is the object on which RHPCTL performs the command, such as client or image.

- `parameters` extend the use of a preceding command combination to include additional parameters for the command. Specify parameters as `-keyword value`. If the `value` field contains a comma-delimited list, then do not use spaces between the items in the list.

You can use RHPCTL commands to perform several Oracle Fleet Patching and Provisioning operations, including:

- Oracle Fleet Patching and Provisioning Client operations, such as creating an Oracle Fleet Patching and Provisioning Client configuration.

- Role operations, such as adding and deleting roles, and granting and revoking roles for users.

- Site operations, such as obtaining configuration information for Oracle Fleet Patching and Provisioning Servers.

- Image operations, such as adding, deleting, and importing images.

- Image series operations, such as adding and deleting image series.

- Working copy operations, such as adding and deleting working copies.

**Parent topic:** [RHPCTL Command Reference](fleet-patching-provisioning-commands.md)
