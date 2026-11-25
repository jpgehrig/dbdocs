## Using Response Files

Use these general steps for installing and configuring Oracle products using the installer in silent or response file mode.

**Note:**

You must complete all required preinstallation tasks on a system before running the installer in silent or response file mode.

1.  Verify the Windows Registry key `HKEY_LOCAL_MACHINE\Software\Oracle` exists and that the value for `inst_loc` is the location of the Oracle Inventory directory on the local node.
    To install Oracle RAC, you must first have installed Oracle Grid Infrastructure on your cluster nodes. The Oracle Inventory directory was created and added to the Windows registry during the installation of Oracle Grid Infrastructure. If the `inst_loc` key does not exist in the Windows registry, then install Oracle Grid Infrastructure for a cluster before continuing.

    **Note:**

    Changing the value for `inst_loc` in the Windows registry is not supported after the installation of Oracle software
2.  Prepare a response file.
3.  Run the installer in silent or response file mode.
4.  If you completed a software-only installation, then run Oracle Database Configuration Assistant (DBCA) in silent or response file mode.

**Parent topic:** [How Response Files Work](how-response-files-work.md)
