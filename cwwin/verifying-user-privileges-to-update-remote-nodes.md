## Verifying User Privileges to Update Remote Nodes

You must ensure that operations that are performed on multiple nodes can be performed during installation of the Oracle Grid Infrastructure software.

For the installation to be successful, you must use the same user name and password on each node in a cluster or use a domain user. You must explicitly grant membership in the local Administrators group to the installation user on all of the nodes in your cluster.

1.  Determine if User Account Control (UAC) remote restrictions have been disabled for the local installation user. If you are using a domain user for installation, then skip this step.
    Check the value of the `LocalAccountTokenFilterPolicy` registry entry for the registry key `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`. The value should be set to 1. If this registry entry does not exist, then, do the following:
    1.  Click Start, click Run, type `regedit`, and then press Enter.
    2.  Navigate to the registry key `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`.
    3.  On the Edit menu, select New, and then click DWORD Value.
    4.  Type `LocalAccountTokenFilterPolicy` and then press Enter.
    5.  Right-click `LocalAccountTokenFilterPolicy`, then click Modify.
    6.  In the Value data box, type 1, then click OK.
    7.  Exit the registry editor.

    By setting the value of `LocalAccountTokenFilterPolicy` to 1, a user who is a member of the local administrators group on the target remote computer establishes a remote administrative connection with an elevated token, enabling the user to perform administrative tasks. If you do not disable the UAC remote restrictions for administrative users, then when installing Oracle Grid Infrastructure on multiple nodes you might encounter the following error:
        INS-40937 The following hostnames are invalid
2.  Before running OUI, from the node where you intend to run the installer, verify that the user account you are using for the installation is configured as a member of the Administrators group on each node in the cluster.
    Enter the following command for each node that is a part of the cluster where nodename is the node name:
        net use \\nodename\C$
3.  If you will be using other disk drives in addition to the `C:` drive, then repeat the `net use` command for every node in the cluster, substituting the drive letter for each drive you plan to use.
4.  Verify the installation user is configured to update the Windows registry on each node in the cluster.
    1.  Run `regedit` from the Run menu or the command prompt.
    2.  From the File menu select Connect Network Registry.
    3.  In the 'Enter the object name…' edit box enter the name of a remote node in the cluster, then click OK.
    4.  Wait for the node to appear in the registry tree.

If the remote node does not appear in the registry tree or you are prompted to fill in a username and password, then you must resolve the permissions issue at the operating system level before proceeding with the Oracle Grid Infrastructure installation.

**See Also:**

[Oracle Database Administrator’s Reference for Microsoft Windows](../ntqrf/overview-of-ntfs-file-system-and-windows-registry-permissions.md) for information about NTFS file system and Windows registry permissions

**Parent topic:** [Configuring User Accounts](configuring-user-accounts.md)
