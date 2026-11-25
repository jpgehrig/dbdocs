## Saving a Response File

You can use the Oracle Universal Installer in interactive mode to save a response file, which you can edit and then use to complete silent mode or response file mode installations.

You can save all the installation steps into a response file during installation by clicking Save Response File on the Summary page. You can use the generated response file for a silent installation later.

When you save the response file, you can either complete the installation, or you can exit from Oracle Universal Installer on the Summary page, before it starts to copy the software to the system.

**Note:**

Oracle Universal Installer does not save passwords in the response file.

To save a response file:

1.  Ensure that the computer on which you are creating the response file has met the requirements. .

    When you run Oracle Universal Installer to save a response file, it checks the system to verify that it meets the requirements to install the software. For this reason, Oracle recommends that you complete all of the required preinstallation tasks and save the response file while completing an installation.

2.  At the command prompt, use the `cd` command to change to the directory that contains the Oracle Universal Installer `setup.exe` executable.

    **Note:**

    Windows requires Administrator privileges at the command prompt.

    On the installation DVD, `setup.exe` is located in the `database` directory. Alternatively, navigate to the directory where you downloaded or copied the installation files.

3.  Run `setup.exe`.

4.  After Oracle Universal Installer starts, enter the installation settings, to save the response file.

5.  When the installer displays the Summary screen, perform the following:

    1.  Click Save Response File and specify a file name and location for the response file. Then, click Save to save the values to the file.

    2.  Click Finish to continue with the installation.

        Click Cancel if you do not want to continue with the installation. The installation stops, but the saved response file is retained.

6.  Before you use the saved response file on another system, edit the file and make any required changes.

    Use the instructions in the file as a guide when editing it.

**Related Topics**

- [Oracle Database Client Preinstallation Tasks](oracle-database-client-preinstallation-tasks.md)

**Parent topic:** [Preparing a Response File](preparing-a-response-file.md)
