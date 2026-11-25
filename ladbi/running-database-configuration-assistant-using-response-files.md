## Running Oracle DBCA Using Response Files

You can run Oracle Database Configuration Assistant (Oracle DBCA) in response file mode to configure and start an Oracle database on the system.

To run Oracle DBCA in response file mode, you must copy and edit a response file template. Oracle provides a response file template named `dbca.rsp` in the `ORACLE_HOME/assistants/dbca` directory. To run Oracle DBCA in response file mode, you must use the `-responseFile` flag in combination with the` -silent` flag. You must also use a graphical display and set the `DISPLAY` environment variable.

To run Oracle DBCA in response file mode:

1.  Copy the `dbca.rsp` response file template from the response file directory to a directory on your system:
        $ cp /directory_path/assistants/dbca/dbca.rsp local_directory

    In this example, `directory_path` is the path of the directory where you have copied the installation binaries.

    As an alternative to editing the response file template, you can also create a database by specifying all required information as command line options when you run Oracle DBCA. For information about the list of options supported, enter the following command:

        $ $ORACLE_HOME/bin/dbca -help
2.  Open the response file in a text editor:
        $ vi /local_dir/dbca.rsp
3.  Follow the instructions in the file to edit the file.
    **Note:**

    Oracle DBCA fails if you do not correctly configure the response file.
4.  Log in as the Oracle software owner user, and set the `ORACLE_HOME` environment variable to specify the correct Oracle home directory.
5.  To run Oracle DBCA in response file mode, set the `DISPLAY` environment variable.
6.  Use the following command syntax to run Oracle DBCA in silent or response file mode using a response file:
        $ORACLE_HOME/bin/dbca [-silent] -createDatabase -responseFile /local_dir/dbca.rsp

    In this example:

    - `-silent` option indicates that Oracle DBCA runs in silent mode.

    - `local_dir` is the full path of the directory where you copied the `dbca.rsp` response file template.

    During configuration, Oracle DBCA displays a window that contains the status messages and a progress bar.

**Parent topic:** [Running Configuration Assistants Using Response Files](running-configuration-assistants-using-response-files.md)
