The following topics describe how to install and configure Oracle products using response files:

- Introduction

- Using Response Files to Install Oracle Components in Noninteractive Mode

- Customizing a Sample Response File

- Creating a New Response File

- Running Oracle Universal Installer and Specifying a Response File

### Introduction

Typically, Oracle Universal Installer runs in interactive mode, which means that it prompts you to provide information in graphical user interface (GUI) screens. Alternatively, you can run Oracle Universal Installer in noninteractive mode. Noninteractive mode is also referred to as silent mode, or silent installation.

You may want to use noninteractive mode to install Oracle Database Gateway on Microsoft Windows (64-bit) in the following scenarios:

- You need to deploy Oracle Components to multiple nodes in an unattended manner. You can schedule the noninteractive installation mode from the operating system scheduler or other job subsystem that your site normally uses.

- No interaction with the user is intended.

- A graphical facility to run Oracle Universal Installer in interactive mode is not available. (Oracle Universal Installer is always available on Microsoft Windows, but not on UNIX systems.)

This section covers the following topics on how you can use response files to run Oracle Universal Installer in noninteractive mode:

### Using Response Files to Install Oracle Components in Noninteractive Mode

To use noninteractive mode, you run Oracle Universal Installer with a response file. A response file is a text file that contains variables and values that Oracle Universal Installer uses during the installation process. Oracle provides a set of sample response files that you can customize, or you can create your own response file by recording your installation selections.

**See Also:**

Oracle Universal Installer and OPatch User's Guide for Windows and UNIX for more information about response file formats

### Customizing a Sample Response File

Oracle provides response file templates for each product and installation type, and for each configuration tool. The response files for Oracle Gateway, `tg.rsp` and `netca.rsp`, are located in the response directory on the media.

**Note:**

If you copied the software to a hard disk, then the response files are located in the `Disk1\response` directory.

To copy and modify a response file:

1.  Copy the necessary response files from the \Response directory on the installation media to your hard drive.
2.  From the Start menu, select Programs, then Oracle - HOME_NAME, then Oracle Installation Products, then Universal Installer Concepts Guide.
    Oracle Universal Installer and OPatch User's Guide for Windows and UNIX appears in HTML format.
3.  Modify the response files with any text file editor by following the instructions in both the response files and Oracle Universal Installer and OPatch User's Guide for Windows and UNIX.
4.  Run the response file by following the instructions in Running Oracle Universal Installer and Specifying a Response File.

### Creating a New Response File

When you run Oracle Universal Installer in interactive mode, you can record your installation selections into a response file. You do this by running Oracle Universal Installer in Record mode. Oracle Universal Installer generates the response file immediately after you complete the Summary page, so you do not need to actually install the gateway to create the response file.

If you want to use the Record mode during a noninteractive installation, then Oracle Universal Installer records the variable values that were specified in the original source response file into the new response file.

**Note:**

You cannot use Record mode to create a response file based on the Basic installation type.

To create a new response file:

1.  Make sure that the computer on which you are creating the response file has met the requirements described in respective gateway installation chapters.
2.  At the command prompt, use the `cd` command to change to the directory that contains the Oracle Universal Installer `setup.exe` executable.
    On the installation media, `setup.exe` is located on Disk 1. If you want to run Oracle Universal Installer from an existing gateway installation, then you can find `setup.exe` in `ORACLE_BASE``\``ORACLE_HOME``\oui\bin`.
3.  Enter the following command:
        setup -record -destinationFile response_file_name

    Replace `response_file_name` with the complete path for the new response file. For example:

        setup -record -destinationFile C:\response_files\install_oracle11g
4.  After Oracle Universal Installer launches, enter the installation settings, which will be recorded into the response file.
5.  When the Summary page appears, do one of the following:
    - Click Install to continue with the installation.

    - Click Cancel if you want to only create the response file but not continue with the installation. The installation will stop, but the settings you have entered will be recorded to the response file.

    Later, Oracle Universal Installer will save your new response file using the path and file name you specified on the command line.
6.  If necessary, make any environment-specific changes to the response file for the computer on which you will run it.
7.  Run the response file by following the instructions in the Running Oracle Universal Installer and Specifying a Response File section.

### Running Oracle Universal Installer and Specifying a Response File

You run Oracle Universal Installer at the command line, specifying a response file. The Oracle Universal Installer executable, `setup.exe`, provides several options. For help information on the full set of these options, run `setup.exe` with the `-help` option, for example:

    C:\ORACLE_BASE\ORACLE_HOME\oui\bin> setup.exe -help

To run Oracle Universal Installer and specify a response file:

1.  Start a command prompt.
2.  Go to the directory where Oracle Universal Installer is installed.
3.  From the command line, run Oracle Universal Installer with the correct response file. For example:
    `C:\ORACLE_BASE\ORACLE_HOME``\oui\bin>` `setup.exe` `[-silent]` `[-nowelcome]` `[-nowait] -responseFile` `filename`

| Where...     | Description                                                                                                                                 |
|:-------------|:--------------------------------------------------------------------------------------------------------------------------------------------|
| `filename`   | Identifies the full path of the response file                                                                                               |
| `-silent`    | Runs Oracle Universal Installer in silent mode and suppresses the Welcome screen. If you use -`silent`, then -`nowelcome` is not necessary. |
| `-nowelcome` | Suppresses the Welcome screen that appears during installation                                                                              |
| `–nowait`    | Closes the console window when the silent installation completes                                                                            |
