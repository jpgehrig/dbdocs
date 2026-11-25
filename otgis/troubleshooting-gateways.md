The following topics contain information about troubleshooting:

- Verify Requirements

- What to Do if an Installation Error Occurs

- Reviewing the Log of an Installation Session

- Troubleshooting Configuration Assistants

- Silent-Mode Response File Error Handling

- Cleaning Up After a Failed Installation

### B.1 Verify Requirements

Before performing any of the troubleshooting steps in this appendix, ensure that the system meets the requirements and that you have completed all of the pre-installation tasks specified in respective topics.

#### Read the Release Notes

Read the release notes for the product before installing it. The latest version of the release notes is also available on the OTN Web site:

    http://docs.oracle.com

### B.2 What to Do if an Installation Error Occurs

If you encounter an error during installation:

- Do not exit Oracle Universal Installer.

- If you clicked Next after you entered incorrect information about one of the installation screens, then click Back to return to the screen and correct the information.

- If you encounter an error while Oracle Universal Installer is copying or linking files, see Reviewing the Log of an Installation Session.

- If you encounter an error while a configuration assistant is running, see Troubleshooting Configuration Assistants.

- If you cannot resolve the problem, then remove the failed installation by following the steps listed in Cleaning Up After a Failed Installation.

### B.3 Reviewing the Log of an Installation Session

During an installation, Oracle Universal Installer records all the actions that it performs, in a log file. If you encounter problems during the installation, then review the log file for information about possible causes of the problem.

To view the log file, follow these steps:

1.  If necessary, enter the following command to determine the location of the `oraInventory` directory:
    For AIX and Linux:

        $ cat /etc/oraInst.loc

    For Solaris SPARC:

        # more /var/opt/oracle/oraInst.loc

    The `inventory_loc` parameter in this file specifies the location of the `oraInventory` directory.
2.  Enter the following command to change directory to Oracle Universal Installer log file directory, where `orainventory_location` is the location of the `oraInventory` directory:
        $ cd /orainventory_location/logs
3.  Enter the following command to determine the name of the log file:
        $ ls -ltr

    This command lists the files in the order of creation, with the most recent file shown last. Installer log files have names similar to the following, where `date_time` indicates the date and time that the installation started:

        installActionsdate_time.log
4.  To view the most recent entries in the log file, where information about a problem is most likely to appear, enter a command similar to the following:
        $ tail -50 installActionsdate_time.log | more

    This command displays the last 50 lines in the log file.
5.  If the error displayed by Oracle Universal Installer or listed in the log file indicates a relinking problem, refer to the following file for more information:
        $ORACLE_HOME/install/make.log

### B.4 Troubleshooting Configuration Assistants

To troubleshoot an installation error that occurs when a configuration assistant is running:

- Review the installation log files listed in Reviewing the Log of an Installation Session.

- Review the specific configuration assistant log file located in the `$ORACLE_HOME/cfgtoollogs` directory. Try to fix the issue that caused the error.

- If you see the "Fatal Error. Reinstall" message, look for the cause of the problem by reviewing the log files. Refer to Fatal Errors for further instructions.

#### B.4.1 Configuration Assistant Failure

Oracle configuration assistant failures are noted at the bottom of the installation screen. The configuration assistant interface displays additional information, if available. The configuration assistant execution status is stored in the following file:

    oraInventory_location/logs/installActionsdate_time.log

The execution status codes are listed in the following table:

| Status                            | Result Code |
|:----------------------------------|:------------|
| Configuration assistant succeeded | 0           |
| Configuration assistant failed    | 1           |
| Configuration assistant cancelled | -1          |

#### B.4.2 Fatal Errors

If you receive a fatal error while a configuration assistant is running then:

1.  Remove the failed installation as described in Cleaning Up After a Failed Installation.
2.  Correct the cause of the fatal error.
3.  Reinstall the Oracle software.

### B.5 Silent-Mode Response File Error Handling

To determine whether a silent-mode installation succeeds or fails, refer to the following log file:

    /oraInventory_location/logs/silentInstalldate_time.log

If necessary, refer to the previous section for information about determining the location of the `oraInventory` directory.

A silent installation fails if:

- You do not specify a response file

- You specify an incorrect or incomplete response file

- Oracle Universal Installer encounters an error, such as insufficient disk space

Oracle Universal Installer or configuration assistant validates the response file at run time. If the validation fails, then the silent-mode installation or configuration process ends. Oracle Universal Installer treats values for parameters that are of the wrong context, format, or type as if no value was specified in the file.

### B.6 Cleaning Up After a Failed Installation

If an installation fails, you must remove files that Oracle Universal Installer created during the attempted installation and remove the Oracle home directory. Perform the following steps to remove the files:

1.  Start Oracle Universal Installer as described in [Running the Oracle Universal Installer](overview-of-gateways.md).
2.  Click Deinstall Products on the Welcome window or click Installed Products on any Installer window.
    The Inventory window appears, listing installed products.
3.  Select the Oracle home that contains the products that you want to remove, then click Remove.
4.  Manually remove the Oracle home directory created during the failed installation.
5.  Reinstall the Oracle software.
