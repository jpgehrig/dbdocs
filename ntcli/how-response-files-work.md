## How Response Files Work

Response files can assist you with installing an Oracle product multiple times on multiple computers.

When you start Oracle Universal Installer (OUI), you can use a response file to automate the installation and configuration of Oracle software, either fully or partially. OUI uses the values contained in the response file to provide answers to some or all installation prompts.

Typically, the installer runs in interactive mode, which means that it prompts you to provide information in graphical user interface (GUI) screens. When you use response files to provide this information, you run Oracle Universal Installer at a command prompt using either of the following modes:

- Silent mode: If you include responses for all of the prompts in the response file and specify the -silent option when starting the installer, then it runs in silent mode. During a silent mode installation, the installer does not display any screens. Instead, it displays progress information in the terminal that you used to start it.

- Response file mode: If you include responses for some or all of the prompts in the response file and omit the -silent option, then the installer runs in response file mode. During a response file mode installation, the installer displays all the screens, screens for which you specify information in the response file, and also screens for which you did not specify the required information in the response file. To use the response file mode, run `setup.exe` without the `-silent` parameter, but include the response file or any other parameters that apply.

Define the settings for a silent or response file installation by entering values for the variables listed in the response file. For instance, to specify the Oracle home, provide the appropriate value for the `ORACLE_HOME` variable, as in the following example:

    ORACLE_HOME="C:\app\product"

Another way of specifying the response file variable settings is to pass them as command-line arguments when you run Oracle Universal Installer. For example:

    DRIVE_LETTER:\setup.exe_location> setup -silent "ORACLE_HOME=C:\app\product" ...

This method supports only the Oracle Home User passwords.

- [Reasons for Using Silent Mode or Response File Mode](reasons-for-using-silent-mode-or-response-file-mode.md)
  Review this section for use cases for running the installer in silent mode or response file mode.
- [Using Response Files](using-response-files.md)
  Review this information to use response files.

**Related Topics**

- [My Oracle Support](https://support.oracle.com/)

**Parent topic:** [Installing and Configuring Oracle Database Using Response Files](installing-and-configuring-oracle-database-client-using-response-files.md)
