Oracle recommends that you remove write permissions from users who are not Oracle Database DBAs or system administrators in the `HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE` directory of the Windows registry.

To remove write permissions:

1.  Open the registry.
2.  Go to `HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE`.
3.  Select Permissions from the Edit menu.
    The Permissions for Oracle dialog box appears.
4.  Remove write privileges from any users who are not Oracle Database DBAs or system administrators. Note that the `SYSTEM` account must have Full Control, because some Oracle Database services run as `SYSTEM`.
5.  Ensure that user accounts that must run Oracle applications have read privileges.
6.  Select OK.
7.  Exit the registry.

**Parent topic:** [Overview of NTFS File System and Windows Registry Permissions](overview-of-ntfs-file-system-and-windows-registry-permissions.md)
