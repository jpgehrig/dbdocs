The following topics describe how to install and configure Oracle products using response files.

- Introduction

- Creating the oraInst.loc File

- Preparing a Response File

- Running Oracle Universal Installer in Silent or Suppressed Mode

### A.1 Introduction

You can automate the installation and configuration of Oracle software, either fully or partially, by specifying a response file when you start Oracle Universal Installer. Oracle Universal Installer uses the values contained in the response file to provide answers to some or all of Oracle Universal Installer prompts:

- If you include responses for all of the prompts in the response file and specify the `-silent` option when starting Oracle Universal Installer, then Oracle Universal Installer runs in silent mode. During a silent-mode installation, Oracle Universal Installer does not display any screens. Instead, it displays progress information in the terminal that you used to start it.

- If you include responses for some or all of the prompts in the response file and omit the `-silent` option, then Oracle Universal Installer runs in suppressed mode. During a suppressed-mode installation, Oracle Universal Installer displays only the screens for which you did not specify all required information. You can also use variables in the response file or command-line options to suppress other installer screens, such as the Welcome screen or Summary screen, that do not prompt for information.

The following table describes several reasons why you might want to run Oracle Universal Installer in silent mode or suppressed mode:

| Mode       | Uses                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:-----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Silent     | Use silent mode if you want to:<br>• Complete an unattended installation, which you might schedule using operating system utilities such as `at`<br>• Complete several similar installations on multiple systems without user interaction<br>• Install the software on a system that does not have X Window System software installed on it<br>Oracle Universal Installer displays progress information in the terminal that you used to start it, but it does not display any of Oracle Universal Installer screens. |
| Suppressed | Use suppressed mode if you want to complete similar Oracle software installations on more than one system, providing default answers to some, but not all of Oracle Universal Installer prompts.<br>If you do not specify information required for a particular Installer screen in the response file, Oracle Universal Installer displays that screen. It suppresses screens for which you have provided all of the required information.                                                                            |

#### A.1.1 Installation Overview

To install and configure Oracle products using Oracle Universal Installer in silent or suppressed mode, follow these steps:

1.  Create the `oraInst.loc` file.
2.  Prepare a response file.
3.  Run Oracle Universal Installer in silent or suppressed mode.

These steps are described in the following sections.

### A.2 Creating the oraInst.loc File

If you plan to install Oracle products using Oracle Universal Installer in silent or suppressed mode, you must manually create the `oraInst.loc` file if it does not already exist. This file specifies the location of the Oracle Inventory directory where Oracle Universal Installer creates the inventory of Oracle products installed on the system.

**Note:**

If Oracle software has been installed previously on the system, the `oraInst.loc` file might already exist. If the file does exist, you do not need to create a file.

To create the `oraInst.loc` file, follow these steps:

1.   Switch user to root:
2.   On Solaris (SPARC), create the `/var/opt/oracle` directory if it does not exist:
        # mkdir /var/opt/oracle
3.  Change directory as follows, depending on your operating system:
    AIX:

        # cd /etc

    Solaris (SPARC):

        # cd /var/opt/oracle
4.  Enter the following commands to set the appropriate owner, group, and permissions on the `oraInst.loc` file:
        # chown oracle:oinstall oraInst.loc
        # chmod 664 oraInst.loc

### A.3 Preparing a Response File

This section describes the methods that you can use to prepare a response file for use during silent-mode or suppressed-mode installations:

- Editing a Response File Template

- Recording a Response File

#### A.3.1 Editing a Response File Template

Oracle provides response file templates for each product and installation type, and for each configuration tool. The response files for Oracle Database Gateway, `tg.rsp` and `netca.rsp` are located in the `response` directory on the media.

**Note:**

If you copied the software to a hard disk, the response files are located in the `Disk1/response` directory.

To prepare a response file:

1.  Copy the response file from the response file directory to a directory on your system:
        $ cp /directory_path/response/response_file.rsp local_directory

    In this example, `directory_path` is the CD-ROM mount point directory or the directory on the DVD. If you have copied the software to a hard drive, you can edit the file in the `response` directory if you prefer.
2.  Open the response file in a text editor:
        $ vi /local_dir/response_file.rsp
3.  Edit the file, following the instructions in the file.
    **Note:**

    Oracle Universal Installer or configuration assistant fails if you do not correctly configure the response file. Refer to [Silent-Mode Response File Error Handling](troubleshooting-gateways.md)for more information about troubleshooting a failed silent-mode installation.
4.  Change the permissions on the file to 700:
        $ chmod 700 /local_dir/response_file.rsp

#### A.3.2 Recording a Response File

This method is most useful for Custom or software-only installations.

You can use Oracle Universal Installer in interactive mode to record a response file that you can edit and then use to complete silent-mode or suppressed-mode installations. When you are recording the response file, you can either complete the installation, or you can exit from Oracle Universal Installer on the Summary page, before it starts to copy the software to the system.

To record a new response file:

1.  Complete the pre-installation tasks listed in respective topics.
    When you run Oracle Universal Installer to record a response file, it checks the system to verify that it meets the requirements to install the software. For this reason, Oracle recommends that you complete all of the required pre-installation tasks and record the response file while completing an installation.
2.  If you have not installed Oracle software on this system previously, create the `oraInst.loc` file, as described in the previous section.
3.  Ensure that the Oracle software owner user (typically `oracle`) has permissions to create or write to the Oracle home path that you will specify when you run Oracle Universal Installer.
4.  To record a response file, enter a command similar to the following to start Oracle Universal Installer:
    **Note:**

    Do not specify a relative path to the response file. If you specify a relative path, Oracle Universal Installer fails.

        $ /directory_path/runInstaller -record -destinationFile filename

    In the previous example:

    - `directory_path` is either the CD-ROM mount point directory, the path of the directory on the DVD, or the path of the `Disk1` directory on the hard drive

    - The `-record` parameter specifies that you want to record the responses that you enter in a response file

    - `filename` is the full path and file name of the response file that you want to record
5.  On each Installer screen, specify the required information.
6.  When Oracle Universal Installer displays the Summary screen, do one of the following:
    - Click Install to create the response file, then continue with the installation.

    - Click Cancel, then Yes to create the response file but exit from Oracle Universal Installer without installing the software.

    The response file is saved in the location that you specified using the `-destinationFile` option.
7.  If you did not complete the installation, delete the Oracle home directory that Oracle Universal Installer created using the path you specified on the Specify File Locations screen.
8.  Before using the recorded response file on another system, use a text editor to edit the file and make any required changes.
    Use the comments in the file as a guide when editing it.

### A.4 Running Oracle Universal Installer in Silent or Suppressed Mode

To run Oracle Universal Installer in silent or suppressed mode, follow these steps:

1.  Complete the pre-installation tasks listed in the respective topics.
2.  Log in as the Oracle software owner user (typically `oracle`).
3.  To start Oracle Universal Installer in silent or suppressed mode, enter a command similar to the following:
        $ $ /directory_path/runInstaller -silent -noconfig -responseFile filename

    **Note:**

    Do not specify a relative path to the response file. If you specify a relative path, Oracle Universal Installer fails.

    -

    In this example:

    - `directory_path` is either the installation media mount point directory, the path of the directory on the DVD, or the path of the `Disk1` directory on the hard drive.

    - `-silent` indicates that you want to run Oracle Universal Installer in silent mode.

    - `-noconfig` suppresses running the configuration assistants during installation, and a software-only installation is performed instead.

    - `filename` is the full path and file name of the installation response file that you configured.

    **Note:**

    For more information about other options for the `runInstaller` command, enter the following command:

        $ /directory_path/runInstaller -help
