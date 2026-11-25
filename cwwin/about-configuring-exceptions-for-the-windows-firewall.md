## About Configuring Exceptions for the Windows Firewall

You must configure exceptions for the Windows Firewall to allow successful incoming connections to the Oracle software.

If the Windows Firewall feature is enabled on one or more nodes in your cluster, then virtually all transmission control protocol (TCP) network ports are blocked to incoming connections. Any Oracle product that listens for incoming connections on a TCP port does not receive any of those connection requests, and the clients making those connections report errors unless you configure exceptions for the Windows Firewall.

You must configure exceptions for the Windows Firewall if your system meets all of the following conditions:

- Oracle server-side components are installed on a computer running a supported version of Microsoft Windows. The list of components includes the Oracle Database, Oracle Grid Infrastructure, Oracle Real Application Clusters (Oracle RAC), network listeners, or any web servers or services.

- The Windows computer accepts connections from other computers over the network. If no other computers connect to the Windows computer to access the Oracle software, then no post-installation configuration steps are required and the Oracle software functions as expected.

- The Windows computer is configured to run the Windows Firewall. If the Windows Firewall is not enabled, then no post-installation configuration steps are required.

Use one of the following methods to configure the firewall:

- Start the Windows Firewall application, select the Exceptions tab and then click either Add Program or Add Port to create exceptions for the Oracle software.

- From the command prompt, run the `netsh firewall add...` command.

  A notification appears that a foreground application is attempting to listen on a port, and you are prompted to create an exception for that executable file. If you choose to create the exception in this way, the effect is the same as creating an exception for the executable file either through Control Panel or from the command line.

**Parent topic:** [Configuring Exceptions for the Windows Firewall](configuring-exceptions-for-the-windows-firewall.md)
