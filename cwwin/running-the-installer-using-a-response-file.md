## Running Oracle Universal Installer Using a Response File

After creating the response file, run Oracle Universal Installer at the command line, specifying the response file you created, to perform the installation.

The Oracle Universal Installer executable, `setup.exe` provides several options. For help information on the full set of these options, run the `setup.exe` command with the `-help` option. For example:

- For Oracle Database:

      db_home> setup.exe -help

- For Oracle Grid Infrastructure:

      Grid_home> setup.exe -help

The help information appears in your session window after a short period of time.

To run the installer using a response file, perform the following steps:

1.  Complete the preinstallation tasks for a normal installation.
2.  Log in as an Administrator user or the user that installed the software.
3.  To start the installer in silent or response file mode, enter a command similar to the following:
    - For Oracle Database:

          C:\> db_home\setup.exe [-silent]  \
               -responseFile response_filename

    - For Oracle Grid Infrastructure:

          C:\> Grid_home\setup.exe [-silent]  \
               -responseFile response_filename

    **Note:**

    Do not specify a relative path to the response file. If you specify a relative path, then the installer fails.
    In this example:

    - `db_home` is the directory on the hard drive where you have copied the Oracle Database installation software.

    - `Grid_home` is the directory on the hard drive where you have copied the Oracle Grid Infrastructure installation software.

    - `-silent` runs the installer in silent mode.

    - `response_filename` is the full path and file name of the installation response file that you configured.

**Parent topic:** [Installing and Configuring Oracle Grid Infrastructure Using Response Files](installing-and-configuring-oracle-grid-infrastructure-using-response-files.md)
