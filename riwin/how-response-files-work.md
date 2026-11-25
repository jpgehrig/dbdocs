## How Response Files Work

Response files can assist you with installing an Oracle product multiple times on multiple computers.

When you start the installer, you can use a response file to automate the installation and configuration of Oracle software, either fully or partially. The installer uses the values contained in the response file to provide answers to some or all installation prompts.

Typically, the installer runs in interactive mode, which means that it prompts you to provide information in graphical user interface (GUI) screens. When you use response files to provide this information, you run the installer from a command prompt using either of the following modes:

- Silent mode

  If you include responses for all of the prompts in the response file and specify the `-silent` option when starting the installer, then it runs in silent mode. During a silent mode installation, the installer does not display any screens. Instead, it displays progress information in the terminal that you used to start it.

- Response file mode

  If you include responses for some or all of the prompts in the response file and omit the `-silent` option, then the installer runs in response file mode. During a response file mode installation, the installer displays all the screens, screens for which you specify information in the response file, and also screens for which you did not specify the required information in the response file.

You define the settings for a silent or response file installation by entering values for the variables listed in the response file. For example, to specify the Oracle home name, supply the appropriate value for the `ORACLE_HOME` variable:

    ORACLE_HOME=C:\app\oracle\product\19.0.0\dbhome_1

Another way of specifying the response file variable settings is to pass them as command line arguments when you run the installer. For example:

     -silent directory_path

In this command, directory_path is the path of the database directory on the DVD, or the path of the directory on the hard drive.

Ensure that you enclose the variable and its setting in double-quotes.

- [Deciding to Use Silent Mode or Response File Mode](deciding-to-use-silent-mode-or-response-file-mode.md)
  There are several reasons for running the installer in silent mode or response file mode.
- [Creating a Database Using Oracle ASM for Database Files in Silent Mode](creating-a-db-using-oracle-asm-for-db-files-in-silent-mode.md)
  Creating an Oracle Real Application Clusters (Oracle RAC) database that uses Oracle Automatic Storage Management (Oracle ASM) for storage is a multi-step process.
- [Using Response Files](general-procedure-for-using-response-files.md)
  Use these general steps for installing and configuring Oracle products using the installer in silent or response file mode.

**Parent topic:** [Using Scripts or Response Files to Create Oracle RAC Databases](using-scripts-or-response-files-to-create-oracle-rac-databases.md)
