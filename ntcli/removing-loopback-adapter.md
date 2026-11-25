## Removing a Loopback Adapter

Use this procedure to remove a Loopback Adapter or a Microsoft KM-TEST Loopback Adapter on different Windows versions.

To remove a Loopback Adapter on Microsoft Windows 7 or to remove Microsoft KM-Test Loopback Adapter on Microsoft Windows 8.1, Microsoft Windows Server 2012, Microsoft Windows Server 2012 R2, and Microsoft Windows Server 2016, perform the following steps:

1.  Display System in the Windows Control Panel.
2.  In the Hardware tab, click Device Manager.
3.  For Microsoft Windows 7, in the Device Manager window, expand Network adapters. You must see Microsoft Loopback Adapter. For Microsoft Windows 8.1 and later releases, you must see Microsoft KM-TEST Loopback Adapter.
4.  For Microsoft Windows 7, right-click Microsoft Loopback Adapter and select Uninstall. For Microsoft Windows 8.1 and later releases, right-click Microsoft KM-TEST Loopback Adapter and select Uninstall.
5.  Click OK.
6.  Restart the computer.
7.  Remove the line from the `DRIVE_LETTER:``\WINDOWS\system32\drivers\etc\hosts` file, added after the localhost line while installing the loopback adapter on other Windows operating systems.

**Parent topic:** [Installing a Loopback Adapter](loopback-adapter.md)
