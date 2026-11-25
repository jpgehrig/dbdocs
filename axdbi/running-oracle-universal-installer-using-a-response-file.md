After creating the response file, run Oracle Universal Installer at the command line, specifying the response file you created, to perform the installation.

Run Oracle Universal Installer at the command line, specifying the response file you created. The Oracle Universal Installer executables, `runInstaller` and `gridSetup.sh`, provide several options. For help information on the full set of these options, run the `gridSetup.sh` or `runInstaller` command with the `-help` option. For example:

- For Oracle Database:

      $ $ORACLE_HOME/runInstaller -help

- For Oracle Grid Infrastructure:

      $ /u01/app/oracle/product/19.0.0/grid/gridSetup.sh -help

The help information appears in a window after some time.

To run the installer using a response file:

1.  Complete the preinstallation tasks for a normal installation.

2.  Log in as the software installation owner user.

3.  If you are completing a response file mode installation, then set the operating system `DISPLAY` environment variable for the user running the installation.

    **Note:**

    You do not have to set the `DISPLAY` environment variable if you are completing a silent mode installation.

4.  To start the installer in silent or response file mode, enter a command similar to the following:

    - For Oracle Database:

          $ $ORACLE_HOME/runInstaller [-silent] \
           -responseFile responsefilename

    - For Oracle Grid Infrastructure:

          $ /u01/app/oracle/product/19.0.0/grid/gridSetup.sh [-silent] \
           -responseFile responsefilename

    **Note:**

    Do not specify a relative path to the response file. If you specify a relative path, then the installer fails.

    In this example:

    - `-silent` runs the installer in silent mode.

    - responsefilename is the full path and file name of the installation response file that you configured.

5.  If this is the first time you are installing Oracle software on your system, then Oracle Universal Installer prompts you to run the `orainstRoot.sh` script.

    Log in as the `root` user and run the `orainstRoot.sh` script:

        $ su root
        password:
        # /u01/app/oraInventory/orainstRoot.sh

    **Note:**

    You do not have to manually create the `oraInst.loc` file. Running the `orainstRoot.sh `script is sufficient as it specifies the location of the Oracle Inventory directory.

6.  When the installation completes, log in as the `root` user and run the `root.sh` script. For example:

        $ su root
        password:
        # $ORACLE_HOME/root.sh

**Parent topic:** [Response Files](installing-and-configuring-oracle-database-using-response-files.md)
