## credentials Commands

Use commands with the `credentials` keyword to add credentials to and delete credentials from the Oracle Cluster Registry (OCR).

- rhpctl add credentials
  Adds credentials to the Oracle Cluster Registry (OCR).
- rhpctl delete credentials
  Deletes credentials from the Oracle Cluster Registry (OCR).

**Parent topic:** [RHPCTL Command Reference](rhpctl-command-reference.md)

### rhpctl add credentials

Adds credentials to the Oracle Cluster Registry (OCR).

#### Syntax

    rhpctl add credentials -cred cred_name {-root | -sudouser sudo_user_name
      -sudopath sudo_binary_location}

#### Parameters

Table A-8 rhpctl add credentials Command Parameters

| Parameter                                                               | Description                                                                                                                                                   |
|:------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-cred ``cred_name`                                                     | Specify a credential name to associate the user and password credentials to access a remote node.                                                             |
| `-root | -sudouser ``sudo_user_name`` -sudopath ``sudo_binary_location` | You must choose either to provide `root` access to access a remote node or a `sudo` user name and path to the `sudo` binary to perform super user operations. |

#### Usage Notes

After you add credentials they can be used in the `-cred` cred_name parameter of other commands to avoid those commands prompting for a password.

**Parent topic:** credentials Commands

### rhpctl delete credentials

Deletes credentials from the Oracle Cluster Registry (OCR).

#### Syntax

    rhpctl delete credentials -cred cred_name

#### Usage Notes

Specify only the name of the credentials you want to delete.

**Parent topic:** credentials Commands
