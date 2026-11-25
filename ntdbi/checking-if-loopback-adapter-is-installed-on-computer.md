## Checking if a Loopback Adapter is Installed on Your Computer

Review this section to verify if a loopback adapter is installed on your computer by running the `ipconfig /all` command.

To check if a loopback adapter is installed on your computer, run the `ipconfig /all` command:

    DRIVE_LETTER:\>ipconfig /all

**Note:**

Loopback Adapter installed on the computer must be the Primary Network Adapter.

If there is a loopback adapter installed, you see a section that lists the values for the loopback adapter. For example:

    Ethernet adapter Local Area Connection 2:
    Connection-specific DNS Suffix  . :
    Description . . . . . . . . . . . : Microsoft Loopback Adapter
    Physical Address. . . . . . . . . : 02-00-4C-4F-4F-50
    DHCP Enabled. . . . . . . . . . . : No
    IP Address. . . . . . . . . . . . : 10.10.10.10
    Subnet Mask . . . . . . . . . . . : 255.255.0.0

**Parent topic:** [Installing a Loopback Adapter](loopback-adapter.md)
