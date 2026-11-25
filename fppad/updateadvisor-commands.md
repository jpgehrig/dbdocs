## updateadvisor Commands

Use commands with the `updateadvisor` keyword to manage the user registered for the Oracle Update Advisor.

- rhpctl manage updateadvisor
  Registers the specified user for the Oracle Update Advisor. You can also use this command to unregister an already registered user.

**Parent topic:** [RHPCTL Command Reference](rhpctl-command-reference.md)

### rhpctl manage updateadvisor

Registers the specified user for the Oracle Update Advisor. You can also use this command to unregister an already registered user.

**Note:**

You can register only one user on each Oracle FPP Server to use Oracle Update Advisor.

#### Syntax

    rhpctl manage updateadvisor {-registeruser -ssousername sso_username [-csinumber customer_support_ID]
    [-proxyserver proxy_server -proxyport port_number [-proxyuser proxy_user]]
    [-endpoint endpoint_url] | -unregisteruser}

#### Parameters

Table A-47 rhpctl manage updateadvisor Command Parameters

| Parameter                          | Description                                                                                                                                                                                                                                                                        |
|:-----------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-registeruser`                    | Use this flag to register a user for the Oracle Update Advisor.                                                                                                                                                                                                                    |
| `-ssousername ``sso_username`      | Specify a Single sign-on (SSO) user name of the user that you want to register for the Oracle Update Advisor.                                                                                                                                                                      |
| `-csinumber ``customer_support_ID` | Optionally, specify the Customer Support Identifier (CSI) of the user that you are registering.<br>Note: The CSI is a unique identifier assigned to customers with an Oracle support contract. If you do not specify a CSI, then you can not download the recommended gold images. |
| `-proxyserver ``proxy_server`      | Specify the name or IP address of the proxy server.                                                                                                                                                                                                                                |
| `-proxyport ``port_number`         | Specify the port number to connect to the proxy server.                                                                                                                                                                                                                            |
| `-proxyuser ``proxy_user`          | Specify the proxy server user name.                                                                                                                                                                                                                                                |
| `-endpoint ``endpoint_url`         | Specify the Oracle Update Advisor endpoint URL.                                                                                                                                                                                                                                    |
| `-unregisteruser`                  | Use this flag to unregister an already registered user from the Oracle Update Advisor.                                                                                                                                                                                             |

#### Examples

To register a user for Oracle Update Advisor:

    $ rhpctl manage updateadvisor -user abc.xyz@example.com -csinumber 18890944

To unregister a user from the Oracle Update Advisor:

    $ rhpctl manage updateadvisor -unregisteruser

**Parent topic:** updateadvisor Commands
