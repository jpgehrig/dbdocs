## Running Oracle Universal Installer Using a Response File

After creating the response file, run Oracle Universal Installer at the command line, specifying the response file you created, to perform the installation.

The Oracle Universal Installer executables, `setup.bat` and `gridSetup.bat`, provide several options. For help information on the full set of these options, run the `gridSetup.bat` or `setup.bat` command with the `-help` option. For example:

- For Oracle Database:

      db_home> setup.bat -help

- For Oracle Grid Infrastructure:

      Grid_home> gridSetup.bat -help

The help information appears in your session window after a short period of time.

To run the installer using a response file, perform the following steps:

1.  Complete the preinstallation tasks for a normal installation.
2.  Log in as an Administrator user or the user that installed the software.
3.  To start the installer in silent or response file mode, enter a command similar to the following:
    - For Oracle Database:

          C:\> directory_path\setup.bat [-silent] [-noconfig] \
               -responseFile response_filename

    - For Oracle Grid Infrastructure:

          C:\> directory_path\gridSetup.bat [-silent] [-noconfig] \
               -responseFile response_filename

    **Note:**

    Do not specify a relative path to the response file. If you specify a relative path, then the installer fails.
    In this example:

    - `directory_path` is the path of the DVD or the path of the directory on the hard drive where you have copied the installation software.

    - `-silent` runs the installer in silent mode.

    - `-noconfig` suppresses running the configuration assistants during installation, and a software-only installation is performed instead.

    - `response_filename` is the full path and file name of the installation response file that you configured.

**Parent topic:** [Using Scripts or Response Files to Create Oracle RAC Databases](using-scripts-or-response-files-to-create-oracle-rac-databases.md)
