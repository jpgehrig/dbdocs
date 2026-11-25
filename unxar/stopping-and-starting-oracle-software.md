This chapter describes how to identify Oracle Database processes, and provides basic information about how to stop and restart them. It also describes how to set up automatic startup and shutdown of the Oracle Database. It contains the following sections:

- Stopping and Starting Oracle Processes

- Automating Shutdown and Startup

**Note:**

When using Oracle Restart, you can use Service Control Utility (SRVCTL), a command-line interface, to manage Oracle processes (database instance, listener, Oracle ASM instance). With SRVCTL, you can manage the Oracle Restart configuration, see the status of processes managed by Oracle Restart, and start or stop processes such as Oracle Database. SRVCTL is enhanced to support Oracle Clusterware, and single instance Oracle databases with Oracle Restart.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/configuring-automatic-restart-of-an-oracle-database.md) and [Oracle Real Application Clusters Administration and Deployment Guide](../racad/server-control-utility-reference.md) for more information about SRVCTL commands.

### 2.1 Stopping and Starting Oracle Processes

This section describes how to stop and start Oracle processes. It contains the following topics:

- Stopping and Starting Oracle Database and Oracle Automatic Storage Management Instances

- Stopping and Starting Oracle Restart

#### 2.1.1 Stopping and Starting Oracle Database and Oracle Automatic Storage Management Instances

This section describes how to stop and start Oracle Database and Oracle Automatic Storage Management instances and contains the following topics:

- Stopping an Oracle Database or Oracle Automatic Storage Management Instance

- Restarting an Oracle Database or Oracle Automatic Storage Management Instance

##### 2.1.1.1 Stopping an Oracle Database or Oracle Automatic Storage Management Instance

**Caution:**

Do not stop an Oracle Automatic Storage Management instance until you have stopped all Oracle Database instances that use Oracle Automatic Storage Management instance to manage their storage.

To stop an Oracle Database or Oracle Automatic Storage Management instance:

1.  Run the following commands to identify the SID and Oracle home directory for the instance that must be shut down:
    On Oracle Solaris:

        $ cat /var/opt/oracle/oratab

    On other operating systems:

        $ cat /etc/oratab

    The `oratab` file contains lines similar to the following, which identify the `SID` and corresponding Oracle home directory for each database or Oracle Automatic Storage Management instance on the system:

        $ORACLE_SID:$ORACLE_HOME:<N/Y>

    **Note:**

    Oracle recommends that you use the plus sign (+) as the first character in the `SID` of Oracle Automatic Storage Management instances.
2.  Run the `oraenv` or `coraenv` script, depending on the default shell, to set the environment variables for the instance that must be shut down:
    - Bourne, Bash, or Korn shell:

          $ . /usr/local/bin/oraenv

    - C shell:

          % source /usr/local/bin/coraenv

    When prompted, specify the `SID` for the instance.
3.  Run the following commands to shut down the instance:
        $ sqlplus
        SQL> CONNECT SYS AS SYSDBA
        Enter password: sys_password
        SQL> SHUTDOWN NORMAL

    After the instance shuts down, you can quit SQL\*Plus.

##### 2.1.1.2 Restarting an Oracle Database or Oracle Automatic Storage Management Instance

**Caution:**

If the database instance uses Oracle Automatic Storage Management for storage management, then you must start the Oracle Automatic Storage Management instance before you start the database instance.

To restart an Oracle Database or Oracle Automatic Storage Management instance:

1.  Repeat steps 1 and 2, if required, to set the `ORACLE_SID` and `ORACLE_HOME` environment variables to identify the SID and Oracle home directory for the instance you want to start.
2.  Run the following commands to start the instance:
        $ sqlplus
        SQL> CONNECT SYS AS SYSDBA
        Enter password: sys_password
        SQL> STARTUP

    After the instance starts, you can exit from SQL\*Plus.

#### 2.1.2 Stopping and Starting Oracle Restart

To stop or start Oracle Restart, run the following command:

- Start: This option is used to start Oracle Restart

  Syntax and Options:

      crsctl start has

- Stop: This option is used to stop Oracle Restart

  Syntax and Options:

      crsctl stop has

  **See Also:**

  [Oracle Database Administrator's Guide](../admin/configuring-automatic-restart-of-an-oracle-database.md) for more information about the `srvctl` commands

### 2.2 About Automating Database Shutdown and Startup

Oracle recommends that you configure the system to automatically start Oracle Database when the system starts, and to automatically shut it down when the system shuts down. Automating database startup and shutdown guards against incorrect database shutdown.

To automate database startup and shutdown, use the `dbstart` and `dbshut` scripts, which are located in the `$ORACLE_HOME/bin` directory. The scripts refer to the same entries in the `oratab` file, which are applied on the same set of databases. You cannot, for example, have the `dbstart` script automatically start `sid1`, `sid2`, and `sid3`, and have the `dbshut` script shut down only `sid1`. However, you can specify that the `dbshut` script shuts down a set of databases while the `dbstart` script is not used at all. To do this, include a `dbshut` entry in the system shutdown file, but do not include the `dbstart` entry in the system startup files.

**See Also:**

The `init` command in the operating system documentation for more information about system startup and shutdown procedures

#### 2.2.1 Automating Database Startup and Shutdown

To automate database startup and shutdown by using the `dbstart` and `dbshut` scripts:

1.  Log in as the `root` user.
2.  Edit the `oratab` file for the platform.
    To open the file, use one of the following commands:

    - On Oracle Solaris:

          # vi /var/opt/oracle/oratab

    - On IBM AIX on POWER Systems (64-Bit) and Linux:

          # vi /etc/oratab

    Database entries in the `oratab` file are displayed in the following format:

        $ORACLE_SID:$ORACLE_HOME:<N|Y>

    In this example, the values `Y` and `N` specify whether you want the scripts to start or shut down the database, respectively. For each database for which you want to automate shutdown and startup, first determine the instance identifier (SID) for that database, which is identified by the SID in the first field. Then, change the last field for each to `Y`.

    You can set `dbstart` to autostart a single-instance database which uses an Automatic Storage Management installation auto-started by Oracle Clusterware. This is the default behavior for an Automatic Storage Management cluster. To do this, you must change the `oratab` entry of the database and the Automatic Storage Management installation to use a third field with the value `W` and `N`, respectively. These values specify that `dbstart` auto-starts the database only after the Automatic Storage Management instance is started.

    **Note:**

    If you add new database instances to the system and automate the startup for them, then you must edit the entries for those instances in the `oratab` file.
3.  Change directory to one of the following, depending on the operating system:
    | Platform                          | Initialization File Directory |
    |:----------------------------------|:------------------------------|
    | Linux and Oracle Solaris          | `/etc/init.d`                 |
    | IBM AIX on POWER Systems (64-Bit) | `/etc`                        |
4.  Create a file called `dbora`, and copy the following lines into this file:
    **Note:**

    Change the value of the `ORA_HOME` environment variable to specify the Oracle home directory for the installation. Change the value of the `ORA_OWNER` environment variable to the user name of the owner of the database installed in the Oracle home directory (typically, `oracle`).

        #! /bin/sh
        # description: Oracle auto start-stop script.
        #
        # Set ORA_HOME to be equivalent to the $ORACLE_HOME
        # from which you wish to execute dbstart and dbshut;
        #
        # Set ORA_OWNER to the user id of the owner of the
        # Oracle database in ORACLE_HOME.

        ORA_HOME=<Type your ORACLE_HOME in full path here>
        ORA_OWNER=<Type your Oracle account name here>

        case "$1" in
        'start')
            # Start the Oracle databases:
            # The following command assumes that the oracle login
            # will not prompt the user for any values
            # Remove "&" if you don't want startup as a background process.
            su - $ORA_OWNER -c "$ORA_HOME/bin/dbstart $ORA_HOME" &
            touch /var/lock/subsys/dbora
            ;;

        'stop')
            # Stop the Oracle databases:
            # The following command assumes that the oracle login
            # will not prompt the user for any values
            su - $ORA_OWNER -c "$ORA_HOME/bin/dbshut $ORA_HOME" &
            rm -f /var/lock/subsys/dbora
            ;;
        esac

    **Note:**

    This script can only stop Oracle Net listener for which a password has not been set. In addition, if the listener name is not the default name, `LISTENER`, then you must specify the listener name in the `stop` and `start` commands:

        $ORACLE_HOME/bin/lsnrctl {start|stop} listener_name
5.  Change the group of the `dbora` file to the OSDBA group (typically `dba`), and set the permissions to 750:
        # chgrp dba dbora
        # chmod 750 dbora
6.  Create symbolic links to the `dbora` script in the appropriate run-level script directories, as follows:
    | Platform                          | Symbolic Links Commands                                                                                                                                              |
    |:----------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Oracle Solaris                    | `# ln -s /etc/init.d/dbora /etc/rc0.d/K01dbora`<br>`# ln -s /etc/init.d/dbora /etc/rc3.d/S99dbora`                                                                   |
    | Linux                             | `# ln -s /etc/init.d/dbora /etc/rc.d/rc0.d/K01dbora`<br>`# ln -s /etc/init.d/dbora /etc/rc.d/rc3.d/S99dbora`<br>`# ln -s /etc/init.d/dbora /etc/rc.d/rc5.d/S99dbora` |
    | IBM AIX on POWER Systems (64-Bit) | `# ln -s /etc/dbora /etc/rc.d/rc2.d/S99dbora`<br>`# ln -s /etc/dbora /etc/rc.d/rc0.d/K01dbora`                                                                       |
