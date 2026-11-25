Oracle recommends configuring the Windows Firewall if the following conditions are true.

Configure the Windows Firewall if:

- Oracle server-side components are installed.

  These components include Oracle Database, network listeners, and any web servers or services.

- The computer handles connections from other computers over a network.

  If no other computers connect to the computer with the Oracle software, then no postinstallation configuration steps are required and the Oracle software functions as expected.

- The Windows Firewall is enabled.

  If the Windows Firewall is not enabled, then no postinstallation configuration steps are required.

If all of the conditions are met, then you must configure the Windows Firewall either by opening specific static TCP ports in the firewall or by creating exceptions for specific executables so that they are able to receive connection requests on any ports they choose. Postinstallation configuration for the Windows Firewall can be done by one of following methods:

- From the Control Panel, select Windows Firewall and then select Exceptions.

- Or enter `netsh firewall add...` at the command line.

Alternatively, Windows informs you if a foreground application is attempting to listen on a port, and it prompts you to create an exception for that executable. If you choose to do so, then the effect is the same as creating an exception for the executable either in the Control Panel or from the command line.

**Note:**

Windows Server 2008 and later operating systems do not provide any information about applications attempting to listen on a port. Instead, a security audit event is logged to signal that an application is blocked.

- [About Backing Up a Database](backing-up-a-database.md)
  The technique for backing up a database depends on the archiving mode of the database and whether you are making a component-based or a volume-based backup.

**Parent topic:** [Overview of Windows Firewall](overview-of-windows-firewall.md)
