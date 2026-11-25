Oracle Database QoS Management provides a command line utility named QOSCTL to help you manage users.

This utility is installed on each node of the cluster but runs properly only if executed as the Oracle Clusterware administrator user on the same node on which the Oracle Database QoS Management server is running. The correct node to run the utility on can be determined by issuing the following command:

    srvctl status qosmserver

The QOSCTL utility supports the creation of Oracle Database QoS Management administrative users. The account information is stored in the local` system-jazn-data.xml` file with encrypted credentials. The account information is also stored in the Oracle Clusterware Repository (OCR) to support failover of the Oracle Database QoS Management Server.

- QOSCTL Utility Reference
  QOSCTL is a command-line utility that allows you to perform certain configuration tasks for Oracle Database QoS Management.

**Parent topic:** [Administering the Oracle Database QoS Management System](administering-oracle-database-qos-management-system.md)

### 9.8.1 QOSCTL Utility Reference

QOSCTL is a command-line utility that allows you to perform certain configuration tasks for Oracle Database QoS Management.

#### Purpose

The QOSCTL utility supports the creation of Oracle Database QoS Management administrative users.

#### File Path

The `qosctl` executable file is located in the `Grid_home``/bin` directory.

#### Security Requirements

To use the QOSCTL utility, you must be logged in as an Oracle Clusterware administrator user.

#### Displaying Help for the QOSCTL Utility

To display the help for the `qosctl` utility, use the following command:

    qosctl -help

#### Syntax

The following code example shows the general format of QOSCTL commands:

    qosctl qos_admin_user command

In place of the `qos_admin_user` argument, you would put the user name of an Oracle Database QoS Management administrative user. Do not include the password. When you have submitted the command for execution, you are prompted for the password associated with the specified `qos_admin_user`.

When configuring the initial accounts for your Oracle Database QoS Management system, the command uses operating system authentication.

#### Commands

Table 9-1 Summary of Commands for the QOSCTL Utility

| Command Syntax                  | Description                                                                                                                                                                                                                                                                                                                                                             |
|:--------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-activatepolicy` `policy_name` | Sets the current policy. This command enables you to change policies through a CRON or scheduling job.<br>Policy names that include spaces must be encapsulated in double-quotes.                                                                                                                                                                                       |
| `-updatepolicyset`              | Discovers and adds new databases with their respective services, and adds performance classes for each service to the existing policy set.                                                                                                                                                                                                                              |
| `-adduser` `username`           | Adds the specified user and prompts for a password. This user is automatically granted the role required to use the Oracle Database QoS Management application and execute any of these commands.                                                                                                                                                                       |
| `-li``stusers`                  | Lists the users that are authorized to run the Oracle Database QoS Management application                                                                                                                                                                                                                                                                               |
| `-``remuser` `username`         | Removes the specified user account and all associated permissions<br>Note: This command is not recoverable. Use caution, because you can delete your own account.                                                                                                                                                                                                       |
| `-``setpasswd` `username`       | Updates the password of a specified user. The QOSCTL utility prompts you for the current password for the user. You must supply the correct value for the old password to change the password for a user.<br>If the password for a user has been forgotten or lost, then you should remove the user account and create a new account for the user, with a new password. |
| `-``help`                       | Displays the syntax for QOSCTL commands.                                                                                                                                                                                                                                                                                                                                |

**Parent topic:** Creating Administrative Users for Oracle Database QoS Management
