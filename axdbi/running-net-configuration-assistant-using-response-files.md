You can run NETCA in silent mode to configure and start an Oracle Net Listener on the system, and configure naming methods and Oracle Net service names.

To run Oracle Net Configuration Assistant (NETCA) in silent mode, you must copy and edit a response file template. Oracle provides a response file template named `netca.rsp` in the `$ORACLE_HOME/assistants/netca` directory.

To run Net Configuration Assistant using a response file:

1.  Copy the `netca.rsp` response file template from the response file directory to a directory on your system:
        $ cp $ORACLE_HOME/assistants/netca/netca.rsp local_directory
2.  Open the response file in a text editor:
        $ vi /local_directory/netca.rsp
3.  Follow the instructions in the file to edit it.
    **Note:**

    Net Configuration Assistant fails if you do not correctly configure the response file.
4.  Log in as the Oracle software owner user, and set the `ORACLE_HOME` environment variable to specify the correct Oracle home directory.
5.  Enter a command similar to the following to run Net Configuration Assistant in silent mode:
        $ $ORACLE_HOME/bin/netca -silent -responsefile /local_directory/netca.rsp

    In this command:

    - The `/silent` option indicates to run Net Configuration Assistant in silent mode.

    - local_directory is the full path of the directory where you copied the `netca.rsp` response file template.

**Parent topic:** [Running Configuration Assistants Using Response Files](running-configuration-assistants-using-response-files.md)
