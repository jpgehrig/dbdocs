## user Commands

Use commands with the `user` keyword to delete, modify, register, and unregister users.

- rhpctl delete user
  Deletes a user from the Fleet Patching and Provisioning repository.
- rhpctl modify user
  Modifies the email address of a specific user.
- rhpctl register user
  Registers an email address for a specific user.
- rhpctl unregister user
  Unregisters an email address for a specific user.

**Parent topic:** [RHPCTL Command Reference](rhpctl-command-reference.md)

### rhpctl delete user

Deletes a user from the Fleet Patching and Provisioning repository.

#### Syntax

    rhpctl delete user -user user_name [-client cluster_name]

#### Parameters

Table A-58 rhpctl delete user Command Parameters

| Parameter                | Description                                                                                                    |
|:-------------------------|:---------------------------------------------------------------------------------------------------------------|
| `-user ``user_name`      | Specify the name of the user you want to delete from a Fleet Patching and Provisioning Client.                 |
| `-client ``cluster_name` | Optionally, you can specify the name of the client cluster from which you want to delete from a specific user. |

#### Usage Notes

- You can delete non built-in users only if that user does not own any working copies.

- If the user created an image or image series, then you can still delete the user, but the creator of the image or image series is changed to internal-user@GHS.

- If the user was the owner of an image series, then you can delete the user, but the owner of the image series will be changed to internal-user@GHS. You can still use the affected image series as normal, such that you can still provision a working copy from the affected image series, and you can still insert or delete images from the affected image series.

#### Example

The following example deletes the user named `scott` on the server cluster from the Fleet Patching and Provisioning repository:

    $ rhpctl delete user -user scott

**Parent topic:** user Commands

### rhpctl modify user

Modifies the email address of a specific user.

#### Syntax

    rhpctl modify user -user user_name -email email_address [-client client_name]

#### Parameters

Table A-59 rhpctl modify user Command Parameters

| Parameter                | Description                                                                                            |
|:-------------------------|:-------------------------------------------------------------------------------------------------------|
| `-user ``user_name`      | Specify an operating system user whose email address you want to modify.                               |
| `-email ``email_address` | Specify the email address of the operating system user in the RFC 822 format.                          |
| `-client ``client_name`  | Optionally, you can specify the name of the client cluster to which the operating system user belongs. |

**Parent topic:** user Commands

### rhpctl register user

Registers an email address for a specific user.

#### Syntax

    rhpctl register user -user user_name -email email_address [-client client_name]

#### Parameters

Table A-60 rhpctl register user Command Parameters

| Parameter                | Description                                                                                                                                                                                                                                                                                                                       |
|:-------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-user ``user_name`      | Specify an operating system user whose email address you want to register.                                                                                                                                                                                                                                                        |
| `-email ``email_address` | Specify the email address of the operating system user in the RFC 822 format.                                                                                                                                                                                                                                                     |
| `-client ``client_name`  | Optionally, if you run the command on the Fleet Patching and Provisioning Server, then you can specify the name of the client cluster to which the operating system user belongs. Otherwise, the command applies to a user on the cluster (either the Fleet Patching and Provisioning Server or Client) where the command is run. |

#### Example

An example of this command is:

    $ rhpctl register user -user scott -email scott@example.com

**Parent topic:** user Commands

### rhpctl unregister user

Unregisters an email address for a specific user.

#### Syntax

    rhpctl unregister user -user user_name [-client client_name]

#### Parameters

Table A-61 rhpctl unregister user Command Parameters

| Parameter               | Description                                                                                            |
|:------------------------|:-------------------------------------------------------------------------------------------------------|
| `-user ``user_name`     | Specify an operating system user whose email address you want to unregister.                           |
| `-client ``client_name` | Optionally, you can specify the name of the client cluster to which the operating system user belongs. |

**Parent topic:** user Commands
