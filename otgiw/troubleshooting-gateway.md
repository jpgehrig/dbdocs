This following topics contain information about troubleshooting:

- Verifying Requirements

- What to Do if an Installation Error Occurs

- Reviewing the Log of an Installation Session

- Troubleshooting Configuration Assistants

- Noninteractive Installation Response File Error Handling

- Cleaning Up After a Failed Installation

### Verifying Requirements

Before you try any of the troubleshooting steps in this appendix, do the following:

- Check the system requirements section of respective gateway installation chapters to ensure that the system meets the requirements and that you have completed all the preinstallation tasks.

- Read the release notes for the product on your platform before installing it. The release notes are available on the Oracle software installation media. You can find the latest version of the release notes on the Oracle Technology Network Web site:

      http://docs.oracle.com/

### What to Do if an Installation Error Occurs

If you encounter an error during installation then:

- Do not exit Oracle Universal Installer.

- If you clicked Next after you entered incorrect information about one of the installation screens, then click Back to return to the screen and correct the information.

- If you encounter an error while Oracle Universal Installer is copying or linking files, see Reviewing the Log of an Installation Session.

- If you encounter an error while a configuration assistant is running, see Troubleshooting Configuration Assistants.

- If you cannot resolve the problem, then remove the failed installation by following the steps listed in Cleaning Up After a Failed Installation.

### Reviewing the Log of an Installation Session

During an installation, Oracle Universal Installer records all the actions that it performs, in a log file. If you encounter problems during the installation, then review the log file for information about possible causes of the problem.

    SYSTEM_DRIVE:\Program Files\Oracle\Inventory\logs

Log file names take the form:

    installActionsdate_time.log

For example, if the installation occurred at 9:00:56 A.M. on May 14, 2009, then the log file would be named:

    installActions2009-05-14_09-00-56-am.log

**Note:**

Do not delete or manually alter the `Inventory` directory or its contents. Doing so can prevent Oracle Universal Installer from locating products that you install on your system.

### Troubleshooting Configuration Assistants

To troubleshoot an installation error that occurs when a configuration assistant is running:

- Review the installation log files listed in Reviewing the Log of an Installation Session.

- Review the specific configuration assistant log file located in the `ORACLE_BASE``\``ORACLE_HOME``\cfgtoollogs` directory. Try to fix the issue that caused the error.

- If you see the “Fatal Error. Reinstall" message, then look for the cause of the problem by reviewing the log files. Refer to Fatal Errors for further instructions.

#### Configuration Assistant Failure

Oracle configuration assistant failures are noted at the bottom of the installation screen. The configuration assistant interface displays additional information, if available. The configuration assistant execution status is stored in the `installActions``date_time``.log` file.

The execution status codes are listed in the following table:

| Status                            | Result Code |
|:----------------------------------|:------------|
| Configuration assistant succeeded | 0           |
| Configuration assistant failed    | 1           |
| Configuration assistant cancelled | -1          |

#### Fatal Errors

If you receive a fatal error while a configuration assistant is running then:

1.  Remove the failed installation as described in Cleaning Up After a Failed Installation.
2.  Correct the cause of the fatal error.
3.  Reinstall the Oracle software.

### Noninteractive Installation Response File Error Handling

To determine whether a noninteractive installation succeeded or failed, check the `installActions``date_time``.log` file, located in `SYSTEM_DRIVE``:\Program Files\Oracle\Inventory\logs`.

If necessary, then see the previous section for information about determining the location of the `Inventory` directory.

A silent installation fails if:

- You do not specify a response file.

- You specify an incorrect or incomplete response file.

- Oracle Universal Installer encounters an error, such as insufficient disk space.

Oracle Universal Installer or a configuration assistant validates the response file at run time. If the validation fails, then the noninteractive installation or configuration process ends. Oracle Universal Installer treats values for parameters that are of the wrong context, format, or type as if no value was specified in the file.

### Cleaning Up After a Failed Installation

If an installation fails, you must remove files that Oracle Universal Installer created during the attempted installation and remove the Oracle home directory. Follow the instructions in [Removing Oracle Database Gateway](removing-gateways.md) to run the `deinstall` tool to remove the gateway, remove the Oracle directory, and remove Oracle from the Registry Editor keys. Later, reinstall the software.
