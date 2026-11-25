Learn about configuring Windows Firewall exceptions.

You must configure exceptions for the Windows Firewall if your system meets all of the following conditions:

- Oracle server-side components are installed on a Windows server operating system. The list of components includes Oracle Database, Oracle Grid infrastructure, network listeners, or any web servers or services.

- The Windows system in question accepts connections from other machines over the network. If no other machines connect to the Windows system to access the Oracle software, then no postinstallation configuration steps are required and the Oracle software functions as expected.

- The Windows system in question is configured to run the Windows Firewall. If the Windows Firewall is not enabled, then no postinstallation configuration steps are required.

If all the conditions are met, then the Windows Firewall must be configured to allow successful incoming connections to the Oracle software. To enable Oracle software to accept connection requests, Windows Firewall must be configured by either opening up the specific static TCP ports in the firewall or by creating exceptions for specific executables so they can receive the connection requests on any ports they choose. This firewall configuration can be done by one of the following methods:

- From the Start menu:

  1.  Click Run and enter firewall.cpl. This opens the Windows Firewall Control Panel applet.

  2.  Complete one of the following operating system-specific steps to allow a program through the Windows Firewall:

      - On Windows 8, Windows 8.1, Windows Server 2012, or Windows Server 2012 R2 x64, click Allow an app or feature through Windows Firewall. Click Change Settings.

      - On Windows 7 or Windows Server 2008 R2, click Allow a program or feature through Windows Firewall. Click Change Settings, Allow Another Program.

      - On Windows Server 2008, click Allow a program through Windows Firewall.

  3.  On the Exceptions tab, click Add Program to create exceptions for the Oracle software.

- From the command prompt, use the `netsh` `firewall add...` command.

When Windows notifies you that a foreground application is attempting to listen on a port, and gives you the opportunity to create an exception for that executable, if you choose to create the exception in this way, then the effect is the same as creating an exception for the executable either through Control Panel or from the command line.

**Parent topic:** [About Oracle Executables Requiring Windows Firewall Exceptions](about-oracle-executables-requiring-windows-firewall-exceptions.md)
