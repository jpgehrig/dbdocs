## Using Response Files

Use these general steps for installing and configuring Oracle products using the installer in silent or response file mode.

**Note:**

You must complete all required preinstallation tasks on a system before running the installer in silent or response file mode.

1.  Verify the Windows Registry key `HKEY_LOCAL_MACHINE\Software\Oracle` exists and that the value for `inst_loc` is the location of the Oracle Inventory directory on the local node.
    **Note:**

    Changing the value for `inst_loc` in the Windows registry is not supported after the installation of Oracle software
2.  Prepare a response file.
3.  Run the installer in silent or response file mode.
4.  If you completed a software-only installation, then perform the steps necessary to configure the Oracle product.

**Parent topic:** [Installing and Configuring Oracle Grid Infrastructure Using Response Files](installing-and-configuring-oracle-grid-infrastructure-using-response-files.md)
