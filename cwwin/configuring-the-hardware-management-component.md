## Configuring the Hardware Management Component

Hardware management is installed using the Add/Remove Windows Components Wizard.

1.  Press Start, then select Control Panel.
2.  Select Add or Remove Programs.
3.  Click Add/Remove Windows Components.
4.  Select (but do not check) Management and Monitoring Tools and click the Details button to display the detailed components selection window.
5.  Select the Hardware Management option.
    If a BMC is detected through the system management BIOS (SMBIOS) Table Type 38h, then a dialog box will be displayed instructing you to remove any third-party drivers. If no third-party IPMI drivers are installed or they have been removed from the system, then click OK to continue.
    **Note:**

    The Microsoft driver is incompatible with other drivers. Any third-party drivers must be removed
6.  Click OK to select the Hardware Management Component, and then click Next.
    Hardware Management (including Windows Remote Management, or WinRM) will be installed.

After the driver and hardware management have been installed, the BMC should be visible in the Windows Device Manager under System devices with the label "Microsoft Generic IPMI Compliant Device". If the BMC is not automatically detected by the plug and play system, then the device must be created manually.

To create the IPMI device, run the following command:

    rundll32 ipmisetp.dll,AddTheDevice

**Parent topic:** [Configuring the IPMI Driver](configuring-the-ipmi-driver.md)
