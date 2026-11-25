## Disabling Windows Media Sensing

Windows Media Sensing must be disabled for the private network adapters.

To disable Windows Media Sensing for TCP/IP, you must set the value of the `DisableDHCPMediaSense` parameter to 1 on each node. Because you must modify the Windows registry to disable Media Sensing, you should first backup the registry and confirm that you can restore it, using the methods described in your Windows documentation.

1.  Backup the Windows registry.
2.  Use Registry Editor to view the following key in the registry:
        HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Tcpip\Parameters
3.  Add a new DWORD value to the Parameters subkey:
        Value Name: DisableDHCPMediaSense
        Value: 1
4.  Exit the Registry Editor and restart the computer.
5.  Repeat steps 1 through 4 on each node in your cluster.

**Parent topic:** [Network Configuration Tasks for Windows Server Deployments](network-configuration-tasks-for-windows-server-deployments.md)
