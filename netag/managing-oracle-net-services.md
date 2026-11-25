## 7 Managing Oracle Net Services

Learn about the various administration tools of Oracle Net Services, and also explore the command-line control utilities.

This involves the main administration applications, Oracle Enterprise Manager Cloud Control and Oracle Net Manager.

- Using the User Interface Tools
  Oracle Net Services provides tools to help you perform configuration and administrative tasks.
- About the OracleNetAdmins Group
  To use Oracle Net Manager, you must be a member of the `OracleNetAdmins` group or the `OracleContextAdmins` group.
- Using Listener Control Utility to Administer the Listener
  Oracle Net Services provides tools to help you start, stop, configure, and control each network component. The Listener Control utility enables you to administer the listener.
- Performing Common Network Tasks
  Learn how to perform network configuration and administration tasks, such as configuring directory server, naming methods, profiles, listener, and Oracle Connection Manager.

**Parent topic:** [Configuration and Administration of Oracle Net Services](part-II-config-and-admin-of-oracle-net-services.md)

### 7.1 Using the User Interface Tools

Oracle Net Services provides tools to help you perform configuration and administrative tasks.

- Using Oracle Enterprise Manager Cloud Control to Configure Oracle Net Services
- Using Oracle Net Manager to Configure Oracle Net Services
- Deciding When to Use Oracle Enterprise Manager Cloud Control and Oracle Net Manager
- Using Oracle Net Configuration Assistant to Configure Network Components

**Parent topic:** Managing Oracle Net Services

#### 7.1.1 Using Oracle Enterprise Manager Cloud Control to Configure Oracle Net Services

Oracle Enterprise Manager Cloud Control enables you to configure Oracle Net Services for any Oracle home across multiple file systems. It also provides common administration functions for listeners. Oracle Enterprise Manager Cloud Control provides an integrated environment for configuring and managing Oracle Net Services.

You can use Oracle Enterprise Manager Cloud Control to configure and administer the following from multiple Oracle homes:

- Listeners: Configure listeners to receive client connections.

- Naming: Define [connect identifier](glossary.md)s and map them to [connect descriptor](glossary.md)s to identify the network location of a service. Oracle Net Manager supports configuration of connect descriptors in local `tnsnames.ora` files or a centralized directory service.

- File location: Specify the file location of the Oracle Net configuration files.

<!-- -->

- Accessing the Net Services Administration Page

**See Also:**

Oracle Enterprise Manager Cloud Control documentation set and online help for information about using Oracle Enterprise Manager Cloud Control

**Parent topic:** Using the User Interface Tools

##### 7.1.1.1 Accessing the Net Services Administration Page

The following procedure describes how to access the Net Services Administration page using Oracle Enterprise Manager Cloud Control:

1.  From the Login to Database page, enter the database credentials, and then click Login.

    The Select Enterprise Manager Home page appears.

2.  Select All Targets from the Targets menu.

3.  Select Listener from the Refine Search list.

4.  Select the listener by double-clicking on the listener name.

5.  Select Net Services Administration from the Oracle Listener menu.

    The Net Services Administration page appears.

From the Net Services Administration page, you can administer the listeners, naming methods, preferences, and so on. The administration procedures are described in other chapters of this book.

**Parent topic:** Using Oracle Enterprise Manager Cloud Control to Configure Oracle Net Services

#### 7.1.2 Using Oracle Net Manager to Configure Oracle Net Services

Oracle Net Manager enables you to configure Oracle Net Services for an Oracle home on a local client or server host.

You can use Oracle Net Manager to configure the following network components:

- Listeners: Create and configure listeners to receive client connections.

- Naming: Define connect identifiers and map them to connect descriptors to identify the network location and identification of a service. Oracle Net Manager supports configuration of connect descriptors in local `tnsnames.ora` files or a centralized directory service.

- Naming methods: Configure the ways connect identifiers are resolved to connect descriptors.

- Profiles: Configure preferences for enabling and configuring Oracle Net features on the client or server.

This section introduces the features of Oracle Net Manager. However, the primary documentation for using Oracle Net Manager is online help.

- Starting Oracle Net Manager
- Navigating Oracle Net Manager
- Using Oracle Net Manager Wizards

**Parent topic:** Using the User Interface Tools

##### 7.1.2.1 Starting Oracle Net Manager

To start Oracle Net Manager, do the following

- On Linux, run `netmgr` from the `ORACLE_HOME/bin` directory.

- On Microsoft Windows, select Programs from the Start menu, and then select Oracle - HOME_NAME. Next, select Configuration and Migration Tools, and then Net Manager.

**Parent topic:** Using Oracle Net Manager to Configure Oracle Net Services

##### 7.1.2.2 Navigating Oracle Net Manager

The Oracle Net Manager interface includes a toolbar and menu options, as well as property sheets for configuring network components.

The navigator pane provides a tree view of network objects and the objects they contain, organized in a folder hierarchy. You can expand and collapse the folders to monitor or manage objects such as connect identifiers, listeners, and profiles. Click an object to make changes to it.

The following are the main folders in the navigator pane:

- Local

  Displays networking elements configured in local configuration files:

  - Net service names in the `tnsnames.ora` file

  - Listeners in the `listener.ora` file

  - Profile in the `sqlnet.ora` file

- Directory

  Displays connect identifiers configured in a directory server

**Parent topic:** Using Oracle Net Manager to Configure Oracle Net Services

##### 7.1.2.3 Using Oracle Net Manager Wizards

The Oracle Net Manager wizards provide step-by-step guidance for tasks. The wizards simplify complex tasks by guiding you through the tasks in manageable steps. The wizards are not intended to provide all configuration options. After you have completed a task with a wizard, use the other components of Oracle Net Manager to modify the configuration.

- Using the Net Service Name Wizard
- Using the Directory Server Migration Wizard

**Parent topic:** Using Oracle Net Manager to Configure Oracle Net Services

###### 7.1.2.3.1 Using the Net Service Name Wizard

The Net Service Name wizard guides you through creating a basic network service name in a directory server or a `tnsnames.ora` file.

The following procedure describes how to start the Net Service Name wizard to create network service names:

1.  In the navigator pane, select Directory or Local, and then select Service Naming.

2.  Click the plus sign (+) on the toolbar, or select Create from the Edit menu.

**See Also:**

Oracle Net Manager online help for detailed information about using the Net Service Name wizard to create a network service name

**Parent topic:** Using Oracle Net Manager Wizards

###### 7.1.2.3.2 Using the Directory Server Migration Wizard

If a `tnsnames.ora` file already exists, then its network service names can be exported to a directory server with the Directory Server Migration wizard.

The following procedure describes how to use the Directory Server Migration wizard:

1.  Select Directory from the Command menu.

2.  Select Export Net Service Names from the Oracle Net Manager menu.

**See Also:**

"[Exporting Local Naming Entries to a Directory Naming Server](configuring-naming-methods.md)"

**Parent topic:** Using Oracle Net Manager Wizards

#### 7.1.3 Deciding When to Use Oracle Enterprise Manager Cloud Control and Oracle Net Manager

Much of the functionality previously available only in Oracle Net Manager has been integrated with Oracle Enterprise Manager Cloud Control. Oracle Enterprise Manager Cloud Control provides the ability to manage configuration for multiple Oracle homes across multiple file systems. Oracle Net Manager only enables you to manage configuration for one Oracle home on a local host computer. The following are the key differences between the tools.

Oracle Enterprise Manager Cloud Control

- Configure the following features:

  \- Local naming (`tnsnames.ora` files)

  \- Directory naming

  \- Listeners

- Provide Oracle home support across multiple file system

- Provide the ability to search and sort local and directory naming entries

- Export directory naming entries to a `tnsnames.ora` file

- Perform the following administrative tasks for a selected listener:

  \- Show current status

  \- Change status

  \- Change tracing level settings

  \- Change logging settings

  \- Set connect-time failover and load balancing methods when there is more than one listener

Oracle Net Manager

- Configure the following features:

  \- Local naming (`tnsnames.ora` files)

  \- Directory naming

  \- Listeners

  \- Profiles

- Provide Oracle home support for single host

- Set connect-time failover and load balancing methods when there is more than one listener

- Set the following options for clients and servers:

  \- Tracing settings

  \- Logging settings

  \- Security, authentication and access rights

  \- Routing

**Note:**

When Automatic Diagnostic Repository (ADR) is enabled, any changes to the tracing and logging settings using Oracle Enterprise Manager Cloud Control are ignored by the system.

**Parent topic:** Using the User Interface Tools

#### 7.1.4 Using Oracle Net Configuration Assistant to Configure Network Components

[Oracle Net Configuration Assistant](glossary.md) configures basic network components during installation, including:

- Listener names and protocol addresses

- Naming methods the client uses to resolve connect identifiers to connect descriptors

- Net service names in a `tnsnames.ora` file

- Directory server usage

Oracle Net Configuration Assistant runs automatically during software installation, as described in the Oracle Database installation guide. It can also be run after installation in standalone mode to configure naming methods, the listener, network service names in the `tnsnames.ora` file, and directory server usage.

To start Oracle Net Configuration Assistant do the following:

- On Linux and UNIX, run `netca` from the `ORACLE_HOME/bin` directory.

- On Microsoft Windows, select Programs from the Start menu, and then select Oracle - HOME_NAME. Next, select Configuration and Migration Tools, and then Oracle Net Configuration Assistant.

**See Also:**

- Oracle Net Configuration Assistant online help

- [Oracle Grid Infrastructure Installation Guide ](../install-and-upgrade.md)for information on running Oracle Net Configuration Assistant in silent mode

The following are the configuration options on the Oracle Net Configuration Assistant Welcome page:

- Listener configuration – Create, modify, delete, or rename a listener.

- Naming Methods configuration – Configure the computer to resolve connect identifiers to connect descriptor with one or more of following naming methods:
  - Local naming

  - Directory naming

  - Easy Connect naming

  - External naming

- Local Net Service Name configuration

  – Create, modify, delete, rename, or test connectivity of a connect descriptor stored in a local `tnsnames.ora` file

- Directory Usage Configuration – Configure a directory server for directory-enabled features.

**Parent topic:** Using the User Interface Tools

### 7.2 About the OracleNetAdmins Group

To use Oracle Net Manager, you must be a member of the `OracleNetAdmins` group or the `OracleContextAdmins` group.

Oracle Net Configuration Assistant establishes these access rights for these groups during Oracle Context creation.

- Adding Users To the OracleNetAdmins Group
- Removing Users From the OracleNetAdmins Group
- Changing Ownership of the OracleNetAdmins Group

**Parent topic:** Managing Oracle Net Services

#### 7.2.1 Adding Users To the OracleNetAdmins Group

The following procedure describes how to add a user to the `OracleNetAdmins` group using the `ldapmodify` command:

1.  Create an [LDIF](glossary.md) (Lightweight Directory Interchange Format) file that specifies that you want to add a user to the `OracleNetAdmins` group.

    You can use the following sample LDIF file. Use the appropriate DN for `cn=OracleNetAdmins` and the user that you want to add.

        dn: cn=OracleNetAdmins,cn=OracleContext,...
        changetype: modify
        add: uniquemember
        uniquemember: DN of user being added to group

2.  Enter the following command at the command line to refresh the file:

        $ ldapmodify -h directory_host -p port -D binddn -q -f ldif_file

    In the preceding command, directory_host is the directory server host, port is the listening TCP/IP port for the directory server, binddn is the directory administrator or user DN, and ldif_file is the input file name. If the port is not specified, then the default port of 389 is used. The `-q` option prompts for a single bind password.

**Parent topic:** About the OracleNetAdmins Group

#### 7.2.2 Removing Users From the OracleNetAdmins Group

The following procedure describes how to remove a user from the `OracleNetAdmins` group with the `ldapmodify` command:

1.  Create an LDIF file that specifies that you want to delete a user to the `OracleNetAdmins` group.

    You can use the following sample LDIF file. Enter the appropriate DN for `cn=OracleNetAdmins` and the user that you want to delete.

        dn: cn=OracleNetAdmins,cn=OracleContext,...
        changetype: modify
        delete: uniquemember
        uniquemember: DN of user being deleted from group

2.  Enter the following command to delete the user:

        $ ldapmodify -h directory_host -p port -D binddn -q -f ldif_file

    In the preceding command, directory_host is the directory server host, port is the listening TCP/IP port for the directory server, binddn is the directory administrator or user DN, and ldif_file is the input file name. If the port is not specified, then the default port of 389 is used. The `-q` option prompts for a single bind password.

**Parent topic:** About the OracleNetAdmins Group

#### 7.2.3 Changing Ownership of the OracleNetAdmins Group

The following procedure describes how to add a group as an owner of an `OracleNetAdmins` group:

1.  Create an LDIF file, as follows:

    1.  Specify the group you want to add as an owner.

        You can use the following sample LDIF file. Enter the appropriate DN for `cn=OracleNetAdmins` and the DN of the group that you want to add.

            dn: cn=OracleNetAdmins,cn=OracleContext,...
                changetype: modify
                add: owner
                owner: DN of group to add

        For example, the following LDIF syntax changes the ownership from the `OracleNetAdmins` group to another group named `ExampleSecurityAdmins`. The group can be either inside or outside Oracle Context.

            dn: cn=OracleNetAdmins,cn=OracleContext,...
                 changetype: modify
                 add: owner
                 owner: cn=ExampleSecurityAdmins

    2.  (Optional) Specify the group to delete as an owner.

            dn: cn=OracleNetAdmins,cn=OracleContext,...
                changetype: modify
                delete: owner
                owner: DN of group to delete

2.  Enter the following command at the command line to refresh the file:

        $ ldapmodify -h directory_host -p port -D binddn -q -f ldif_file

    In the preceding command, directory_host is the directory server host, port is the listening TCP/IP port for the directory server, binddn is the directory administrator or user DN, and ldif_file is the input file name. If the port is not specified, then the default port of 389 is used. The `-q` option prompts for a single bind password to be entered.

**Parent topic:** About the OracleNetAdmins Group

### 7.3 Using Listener Control Utility to Administer the Listener

Oracle Net Services provides tools to help you start, stop, configure, and control each network component. The Listener Control utility enables you to administer the listener.

The utility is started by the user that owns the Oracle installation, or a member of the designated group, on the same machine where the listener is running. The basic syntax for this utility is as follows:

    lsnrctl command [listener_name]

For example, the following command starts a listener named `lsnr`:

    lsnrctl START lsnr

You can also issue Listener Control utility commands at the `LSNRCTL>` program prompt. To obtain the prompt, enter `lsnrctl` with no arguments at the operating system command line. When you run `lsnrctl`, the utility is started, and you can enter the necessary commands from the program prompt.

For example:

    lsnrctl
    LSNRCTL> START lsnr

**See Also:**

- "[Customizing Oracle Net Listener Configuration](configuring-and-administering-oracle-net-listener.md)" for additional information about the listener

- [Oracle Database Net Services Reference](../netrf/listener-control-utility.md) for additional information about the Listener Control utility

**Parent topic:** Managing Oracle Net Services

### 7.4 Performing Common Network Tasks

Learn how to perform network configuration and administration tasks, such as configuring directory server, naming methods, profiles, listener, and Oracle Connection Manager.

Configuring Directory Server for Oracle Net Usage

- Configure directory server usage.

  Tool used to perform the task: Oracle Internet Directory Configuration Assistant. See [Oracle Fusion Middleware Administering Oracle Internet Directory](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/netag&id=OIDAG-GUID-B5EE7E57-2AC3-4841-9E60-BECFDD42B6EE).

- Add users to the `OracleNetAdmins` group.

  Tool used to perform the task: `ldapmodify`. See [Who Can Add or Modify Entries in the Directory Server](managing-network-address-information.md).

- Authenticate with the directory.

  Tools used to perform the task: Oracle Enterprise Manager Cloud Control, Oracle Net Manager. See Online help in Oracle Enterprise Manager Cloud Control and [Oracle Database Enterprise User Security Administrator's Guide](../dbimi/getting-started-with-enterprise-user-security.md).

- Change Oracle Context.

  Tool used to perform the task: Oracle Net Manager. See Online help in Oracle Net Manager.

Configuring Naming Methods

- Configure the local naming method.

  Tool used to perform the task: Oracle Enterprise Manager Cloud Control, Oracle Net Manager, Oracle Net Configuration Assistant. See [Configuring the Local Naming Method](configuring-naming-methods.md).

- Configure the directory naming method.

  Tool used to perform the task: Oracle Enterprise Manager Cloud Control, Oracle Net Manager. See [Configuring the Directory Naming Method](configuring-naming-methods.md).

- Configure the Easy Connect naming method.

  Tool used to perform the task: Oracle Net Manager. See [Understanding the Easy Connect Naming Method](configuring-naming-methods.md).

- Configure external naming methods.

  Tool used to perform the task: Oracle Net Manager. See [Configuring External Naming Methods](configuring-naming-methods.md).

Migrating to Directory Naming

Export from `tnsnames.ora` files.

Tools used to perform the task: Oracle Enterprise Manager Cloud Control, Oracle Net Manager. See [Export Directory Naming Entries to the tnsnames.ora file](configuring-naming-methods.md).

Configuring Profiles

- Prioritize naming methods.

  Tool used to perform the task: Oracle Net Manager, Oracle Net Configuration Assistant. See [Prioritizing Naming Methods](configuring-profiles.md).

- Configure a default domain that is automatically appended to any unqualified network service name.

  Tool used to perform the task: Oracle Net Manager, Oracle Net Configuration Assistant. See [About the Default Domain for Clients](configuring-profiles.md).

- Route connection requests.

  Tool used to perform the task: Oracle Net Manager, Oracle Net Configuration Assistant. See [Routing Connection Requests to a Process](configuring-profiles.md).

- Configure access control.

  Tool used to perform the task: Oracle Net Manager. See [Settings for Database Access Control](configuring-profiles.md).

- Configure an authentication method.

  Tool used to perform the task: Oracle Net Manager. See [Configuring Oracle Network Security](configuring-profiles.md).

- Configure connect request timeouts.

  Tool used to perform the task: Manual configuration. See [Limiting Resource Consumption by Unauthorized Users](optimizing-performance.md).

Configuring Listeners

- Configure listening protocol addresses.

  Tool used to perform the task: Oracle Enterprise Manager Cloud Control, Oracle Net Manager, Oracle Net Configuration Assistant. See [Configuring Listening Protocol Addresses](configuring-and-administering-oracle-net-listener.md).

- Configure dynamic service registration.

  Tool used to perform the task: Automatic configuration. See [Configuring Dynamic Service Registration](configuring-and-administering-oracle-net-listener.md).

- Configure static service registration.

  Tool used to perform the task: Oracle Enterprise Manager Cloud Control, Oracle Net Manager. See [Configuring Static Service Registration](enabling-advanced-features.md).

- Configure connect request timeouts.

  Tool used to perform the task: Manual configuration. See [Limiting Resource Consumption by Unauthorized Users](optimizing-performance.md).

Administering Listeners

- Start and stop listeners.

  Tool used to perform the task: Listener Control Utility. See [Starting and Stopping a Listener](configuring-and-administering-oracle-net-listener.md).

- View registered information.

  Tool used to perform the task: Listener Control Utility. See [Monitoring Services of a Listener](configuring-and-administering-oracle-net-listener.md).

Configuring Oracle Connection Manager

- Configure session multiplexing.

  Tool used to perform the task: Manual configuration. See [Enabling Session Multiplexing for Oracle Connection Manager](configuring-oracle-connection-manager.md).

- Configure access control.

  Tool used to perform the task: Manual configuration. See [Enabling Access Control](configuring-oracle-connection-manager.md).

**Parent topic:** Managing Oracle Net Services
