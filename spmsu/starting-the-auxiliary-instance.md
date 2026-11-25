The initialization parameter file that you create is used to start the auxiliary instance.

RMAN shuts down and restarts the auxiliary instance as part of the duplication. Hence, it is a good idea to create a server-side initialization parameter file for the auxiliary instance in the default location. If you do not have a server-side initialization parameter file in the default location, then you must specify the client-side initialization parameter file with the `PFILE` parameter on the `DUPLICATE` command.

**Note:**

Because the auxiliary instance does not yet have a control file, you can only start the instance in `NOMOUNT` mode. Do not create a control file or try to mount or open the auxiliary instance.

To start the auxiliary instance:

1.  Start RMAN.
        % rman
2.  Connect to the auxiliary instance as a user with the `SYSDBA` or `SYSBACKUP` privilege. The following example uses password file authentication to connect to the auxiliary instance.
        RMAN> CONNECT SYS@dupdb AS SYSDBA;

    The following example uses operating system authentication to connect to the auxiliary instance by using the `SYSBACKUP` privilege.
        RMAN> CONNECT / AS SYSBACKUP;
3.  Start the auxiliary instance in `NOMOUNT` mode.
        RMAN > STARTUP FORCE NOMOUNT;

**Parent topic:** [Preparing the Auxiliary Instance on the Destination Host](preparing-the-auxiliary-instance-destination-host.md)
