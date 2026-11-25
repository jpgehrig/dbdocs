The following topics guide you through the basic concepts and preinstallation steps for Oracle Database Gateway for WebSphere MQ.

### Preinstallation Tasks

The preinstallation tasks for the Oracle Database Gateway for WebSphere MQ are divided into the following parts.

#### WebSphere MQ Software

This topic explains how to check for WebSphere MQ software.

Perform the following steps to check for WebSphere MQ software:

1.  Determine where the WebSphere MQ queue manager runs.
    - Local system

      If the WebSphere MQ queue manager runs on a local system, then the queue manager runs on the same system where you intend to install the gateway product set.

    - Remote system

      If the WebSphere MQ queue manager runs on a remote system, then the queue manager runs on a different system, not the system where you intend to install the gateway product set.
2.  Verify that the WebSphere MQ software is already installed. If the WebSphere MQ server software is installed on a different system than the gateway, then the WebSphere MQ client software must be installed on the gateway system.
3.  Identify the name of the WebSphere MQ queue manager.
4.  Identify the WebSphere MQ client channel definition.

If the queue manager is installed on a different system than the gateway, then the WebSphere MQ client software is used to access the remote queue manager. A channel definition is required for this configuration.

#### Setting Environment Variables

Before installing Oracle Database Gateway for WebSphere MQ on UNIX platforms, set the appropriate environment variables.

**Note:**

Verify that the values that you assign to the environment variables, which are listed in this topic, are less than 42 characters long. Longer values might generate errors such as "Word too long" during installation.

##### ORACLE_HOME

`ORACLE_HOME` is the root directory in which Oracle software is installed.

Oracle Database Gateway for WebSphere MQ cannot share the same Oracle home directory with other Oracle products. If you have installed other Oracle products, then Oracle Database Gateway for WebSphere MQ must be installed in a different `ORACLE_HOME` directory.

**Note:**

Do not install Oracle Database Gateway for WebSphere MQ in an `ORACLE_HOME` directory containing other Oracle products, including the database. Such an installation could overwrite shared components, causing the products to malfunction.

**Related Topics**

- Preventing Conflicts Between ORACLE_HOME Directories

###### Preventing Conflicts Between ORACLE_HOME Directories

To prevent a conflict between the software in an existing `ORACLE_HOME` directory and Oracle Database Gateway for WebSphere MQ, you must remove all references to the existing `ORACLE_HOME` directory.

The following steps describe removing these references.

1.  Unset your existing `ORACLE_HOME` variable using one of the following commands.
    - C shell:

          prompt> unsetenv ORACLE_HOME

    - Bourne/Korn shell:

          prompt> export ORACLE_HOME=
2.  Edit the following environment variables so that they do not use the existing `ORACLE_HOME` value:

Table 4-1 Setting Environment Variables for a New ORACLE_HOME Directory 

| Environment Variable | Platforms                                                |
|:---------------------|:---------------------------------------------------------|
| `PATH`               | Linux, AIX-based Systems, HP-UX Itanium, and Sun Solaris |
| `CLASSPATH`          | Linux, AIX-based Systems, HP-UX Itanium, and Sun Solaris |
| `LD_LIBRARY_PATH`    | Linux and Sun Solaris                                    |
| `LIBPATH`            | AIX-based Systems                                        |
| `SHLIB_PATH`         | HP-UX Itanium                                            |

**Note:**

Verify that the C compiler is in your `PATH` before you start the installation.

###### Setting ORACLE_HOME

This topic explain how to set the `ORACLE_HOME` environment variable.

Set the `ORACLE_HOME` environment variable by using one of the following commands:

- C shell

      prompt> setenv ORACLE_HOME fullpath

- Bourne/Korn shell

      prompt> ORACLE_HOME=fullpath
      prompt> export ORACLE_HOME

##### ORACLE_SID

`ORACLE_SID` is used for the SID of the gateway.

###### Setting ORACLE_SID

This topic explains how to set the `ORACLE_SID` environment variable.

Set the `ORACLE_SID` environment variable by using one of the following commands:

- C shell

      prompt> setenv ORACLE_SID dg4mqs

  or

      prompt> setenv ORACLE_SID dg4mqc

- Bourne/Korn shell

      prompt> ORACLE_SID=dg4mqs
      promtp> export ORACLE_SID

  or

      prompt> ORACLE_SID=dg4mqc
      promtp> export ORACLE_SID

##### DISPLAY

Setting the `DISPLAY` environment variable enables you to run Oracle Universal Installer remotely from a local work station.

On the system where you run Oracle Universal Installer, set the `DISPLAY` environment variable to specify the system name or IP address of your local workstation.

If you get an Xlib error when starting Oracle Universal Installer such as "Failed to connect to server", "Connection refused by server", or "Can't open display", then run the commands on your local workstations as follows:

###### On Server where the Installer is Running

This topic shows examples for using `DISPLAY` on a server where the installer is running.

- C shell

      prompt> setenv DISPLAY hostname:0.0

- Borne or Korn shell

      prompt> export DISPLAY=hostname:0.0
      prompt> export DISPLAY

###### In Session on Your Workstation

This topic shows examples of in session on the workstation.

- C shell

      prompt> xhost +server_name

- Borne or Korn shell

      prompt> xhost +server_name

##### TMP

During installation, Oracle Universal Installer uses a temporary directory for swap space.

This directory must meet the hardware requirements. The installation might fail if you do not have sufficient space. Oracle Universal Installer checks for the `TMP` environment variable to locate the temporary directory. If this environment variable does not exist, then the installer uses the `/tmp` directory.

The following example demonstrates how to set the `TMP` environment variable.

- C shell

      prompt> setenv TMP full path

- Bourne/Korn shell

      prompt> TMP=full path
      prompt> export TMP

**Related Topics**

- [Hardware Requirements for Oracle Database Gateway for WebSphere MQ](database-gateway-webspheremq-system-requirements.md)

#### Using Windows User Account as Oracle Home User

With Windows, you log in to a user with Administrator privileges to install the Oracle Database software. You can also specify an Oracle Home User (based on a low-privileged, non-administrative user account) during installation.

The following are the Windows User Accounts:

- Windows Local User account

- Windows Domain User account

- Windows Managed Services Account (MSA)

- Windows Built-in Account

**See Also:**

"Using Oracle Home User on Windows" in [Oracle Database Platform Guide for Microsoft Windows](../ntqrf/managing-oracle-home-user.md)

### About Oracle Universal Installer

Oracle Database Gateway for WebSphere MQ uses Oracle Universal Installer to configure environment variables and install components.

Oracle Universal Installer guides you through each step of the installation process, so you can choose configuration options for a customized product.

The Oracle Universal Installer includes features that perform the following tasks:

- Explore and provide installation options for products

- Detect preset environment variables and configuration settings

- Set environment variables and configuration during installation

- Uninstall products

#### oraInventory Directory

The Oracle Universal Installer creates the `oraInventory` directory the first time it is run on your system.

The `oraInventory` directory keeps an inventory of the products that Oracle Universal Installer installs on your system as well as other installation information. If you have previously installed Oracle products, then you might already have an `oraInventory` directory.

- When a UNIX group name is specified, it grants that group the permission to write to the `oraInventory` directory.  If another group attempts to run Oracle Universal Installer, then they must have permission to write to the `oraInventory` directory. If they do not have permission the installation fails.

- The user running the Oracle Universal Installer must have permission to write to the `oraInventory` directory and all its files. This is required to run the installer.

- The location of `oraInventory` is defined in `/etc/oratab/oraInst.loc `for HP-UX Inanium and AIX-Based Systems and` C:\Program Files\Oracle\Inventory\` for Microsoft Windows.

- The location of `oraInventory` is defined in `/var/opt/oraInst.loc` for` `Sun Solaris.

- The latest log file is `oraInventory_location/logs/installActions.log` On UNIX based systems and `C:\Program Files\Oracle\Inventory\logs\installActions.log` for Microsoft Windows. Log file names of previous installation sessions are in the following format: `installActions``datetime``.log`.

- Do not delete or manually alter the `oraInventory` directory or its contents. Doing this can prevent the Oracle Universal Installer from locating the products that you have installed on your system.

#### Starting Oracle Universal Installer

This topic explains how to start Oracle Universal Installer.

On UNIX based systems, perform the following steps to launch Oracle Universal Installer, which installs Oracle Database Gateway for WebSphere MQ:

1.  Stop all Oracle processes and services (for example, the Oracle database).

2.  Run Oracle Universal Installer.

    **Note:**

    Be sure you are not logged in as the `root` user when you start Oracle Universal Installer. If you are, only the `root` user will have permissions to manage Oracle Database Gateway for WebSphere MQ.

    1.  Log in as the Oracle Database Gateway for WebSphere MQ user.

    2.  Start Oracle Universal Installer by entering:

            prompt> mount_point/runInstaller

On Microsoft Windows, perform the following steps to launch Oracle Universal Installer, which installs Oracle Database Gateway for WebSphere MQ:

1.  Start your system and select MS((nbsp))Windows from the operating system Loader option. Log in to your MS((nbsp))Windows system as a member of the Administrators group.

2.  If you are installing the gateway for the first time, ensure there is sufficient space on the disk where you are installing the gateway.

3.  Before installing the software, stop all Oracle NT Services that are running:

    1.  From the Start menu, go to Setting, then Control Panel, and then click Services. A list of all NT services is displayed.

    2.  Select an Oracle NT service (these services begin with Oracle).

    3.  Click Stop.

    4.  Continue to select and stop all Oracle NT services until all active Oracle NT Services are stopped.

4.  Load the installation media and start the Oracle Universal Installer.

This launches Oracle Universal Installer using which you can install Oracle Database Gateway for WebSphere MQ.

**Related Topics**

- [Hardware Requirements for Oracle Database Gateway for WebSphere MQ](database-gateway-webspheremq-system-requirements.md)
