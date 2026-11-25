This section supplements the generic information provided in Oracle Database Net Services Administrator's Guide to configure a listener on Windows operating systems to exclusively handle external procedures. For a higher level of security, you are instructed to start the listener for external procedures from a user account with lower privileges than the `oracle` user. For Windows operating systems, this requires that you change the user account from LocalSystem to a local, unprivileged user for the `Oracle``HOMENAME``TNSListener``extproc_listener_name service`.

**Note:**

The following instructions assume that you have performed steps 1 through 5 in the section "Modifying Configuration of External Procedures for Higher Security" and the procedure described in [Default Configuration for External Procedures](../netag/enabling-advanced-features.md) section in Oracle Database Net Services Administrator's Guide.

To change the listener account:

1.  Create a new user account and grant it Log on as a Service privilege.
    **Note:**

    Ensure that this user account does not have general access to files owned by `oracle`. Specifically, this user must not have permission to read or write to database files or to the Oracle Database server address space. In addition, this user must have read access to the `listener.ora` file, but must not have the write access.
2.  Stop service `Oracle``HOMENAME``TNSListener``extproc_listener_name`.
    If the `Oracle``HOMENAME``TNSListener``extproc_listener_name` service does not exist, issue the following command from the command prompt:

        lsnrctl start extproc_listener_name

    This creates the `Oracle``HOMENAME``TNSListener``extproc_listener_name` service. When you return to the list of services, stop this service before proceeding to the next step of this procedure.
3.  Select `Oracle``HOMENAME``TNSListener``extproc_listener_name` service in the Services dialog and then display the properties of the service.
4.  Select This Account and enter the user name and password.
5.  Start the listener by clicking Start. You must start the listener in this way because you cannot use the Listener Control utility to start the listener running as an unprivileged local user.
    **Note:**

    You can also use NET START `Oracle``HOMENAME``TNSListener``extproc_listener_name` to start the listener from the command prompt. Running the listener with lower privileges prevents you from using Listener Control utility `SET` commands to alter the configuration of this listener in file `listener.ora`. You can perform other administrative tasks on this listener with the Listener Control utility, including stopping the listener. Oracle recommends that you complete `listener.ora` file configuration before running the listener.

    **See Also:**

    - Your operating system documentation for instructions on accessing the Services dialog and stopping services

    - [Oracle Database Net Services Administrator's Guide](../netag/enabling-advanced-features.md)

**Parent topic:** [Overview of Advanced Network Configuration](overview-of-advanced-network-configuration.md)
