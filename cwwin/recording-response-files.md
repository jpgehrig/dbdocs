## Recording Response Files

You can use the installer in interactive mode to record response files, which you can then edit and use to complete silent mode or response file mode installations.

This method is useful for Advanced or software-only installations. You can save all the installation steps into a response file during installation by clicking Save Response File on the Summary page. You can use the generated response file for a silent installation later.

When you record the response file, you can either complete the installation, or you can exit from the installer on the Summary page, before the installer starts to copy the software to the local disk.

If you use record mode during a response file mode installation, then the installer records the variable values that were specified in the original source response file into the new response file.

**Note:**

You cannot save passwords while recording the response file.

1.  Complete preinstallation tasks for a standard installation.
    When you run the installer to record a response file, it checks the system to verify that it meets the requirements to install the software. For this reason, Oracle recommends that you complete all of the required preinstallation tasks and record the response file while completing an installation.
2.  Log in as the Oracle Installation User. Ensure that the Oracle Installation User has permissions to create or write to the Grid home path that you specify during installation.
3.  Start the installer. On each installation screen, specify the required information.
4.  When the installer displays the Summary screen, perform the following steps:
    1.  Click Save Response File. In the pop up window, specify a file name and location to save the values for the response file, then click Save.
    2.  Click Finish to continue with the installation.
        Click Cancel if you do not want to continue with the installation. The installation stops, but the recorded response file is retained.
        **Note:**

        Your response file name must end with the `.rsp` suffix.
5.  Before you use the saved response file on another system, edit the file and make any required changes. Use the instructions in the file as a guide when editing it.

**Parent topic:** [Preparing Response Files](preparing-response-files.md)
