## Logging In to a Remote System Using X Window System

Use this procedure to run Oracle Universal Installer (OUI) by logging on to a remote system where the runtime setting prohibits logging in directly to a graphical user interface (GUI).

OUI is a graphical user interface (GUI) application. On servers where the runtime settings prevent GUI applications from running, you can redirect the GUI display to a client system connecting to the server.

**Note:**

If you log in as another user (for example, `oracle` or `grid`), then repeat this procedure for that user as well.

1.  Start an X Window System session. If you are using an X Window System terminal emulator from a PC or similar system, then you may need to configure security settings to permit remote hosts to display X applications on your local system.
2.  Enter a command using the following syntax to enable remote hosts to display X applications on the local X server:
        # xhost + RemoteHost

    RemoteHost is the fully qualified remote host name. For example:

        # xhost + somehost.example.com
        somehost.example.com being added to the access control list
3.  If you are not installing the software on the local system, then use the `ssh` command to connect to the system where you want to install the software:
        # ssh -Y  RemoteHost

    RemoteHost is the fully qualified remote host name. The `-Y` flag ("yes") enables remote clients to have full access to the original server display. For example:

        # ssh -Y somehost.example.com
4.  If you are not logged in as the `root` user, and you are performing configuration steps that require `root` user privileges, then switch the user to `root`.

**Note:**

For more information about remote login using X Window System, refer to your X server documentation, or contact your X server vendor or system administrator. Depending on the X server software that you are using, you may have to complete the tasks in a different order.

**Parent topic:** [Checking and Configuring Server Hardware for Oracle Grid Infrastructure](checking-and-configuring-server-hardware-for-oracle-grid-infrastructure.md)
