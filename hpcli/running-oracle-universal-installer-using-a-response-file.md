After creating the response file, run Oracle Univeral Installer at the command line, specifying the response file you created, to perform the installation.

Run Oracle Universal Installer at the command line, specifying the response file you created. The Oracle Universal Installer executable, `runInstaller`, provides several options. For help information on the full set of these options, run the `runInstaller` command with the `-help` option. For example:

    $ directory_path/runInstaller -help

The help information appears in a window after some time.

To run the installer using a response file:

1.  Complete the preinstallation tasks as for a normal installation

2.  Log in as the software installation owner user.

3.  If you are completing a response file mode installation, then set the operating system `DISPLAY` environment variable for the user running the installation.

    **Note:**

    You do not have to set the `DISPLAY` environment variable if you are completing a silent mode installation.

4.  To start the installer in silent or response file mode, enter a command similar to the following:

        $ /directory_path/runInstaller [-silent] [-noconfig] \
         -responseFile responsefilename

    **Note:**

    Do not specify a relative path to the response file. If you specify a relative path, then the installer fails.

    In this example:

    - directory_pathis the path of the directory where you have copied the installation binaries.

    - `-silent` runs the installer in silent mode.

    - `-noconfig` suppresses running the configuration assistants during installation, and a software-only installation is performed instead.

    - `responsefilename` is the full path and file name of the installation response file that you configured.

5.  If this is the first time you are installing Oracle software on your system, then Oracle Universal Installer prompts you to run the orainstRoot.sh script.

    Log in as the `root` user and run the `orainstRoot.sh` script:

        $ su root
        password:
        # /u01/app/oraInventory/orainstRoot.sh

    **Note:**

    You do not have to manually create the `oraInst.loc` file. Running the `orainstRoot.sh` script is sufficient as it specifies the location of the Oracle Inventory directory.

6.  When the installation completes, log in as the `root` user and run the `root.sh` script. For example

        $ su root
        password:
        # /oracle_home_path/root.sh

**Parent topic:** [Installing and Configuring Oracle Database Using Response Files](installing-and-configuring-oracle-database-using-response-files.md)
