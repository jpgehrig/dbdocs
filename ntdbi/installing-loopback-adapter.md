## Installing a Loopback Adapter

Use this procedure to install a Loopback Adapter or a Microsoft KM-TEST Loopback Adapter on different Windows versions.

The Microsoft Loopback Adapter in Microsoft Windows 7 is renamed to Microsoft KM-TEST Loopback Adapter in Microsoft Windows 8.1 and later releases. 

To install a Loopback Adapter on Microsoft Windows 7 or to install Microsoft KM-Test Loopback Adapter on Microsoft Windows 8.1, Microsoft Windows Server 2012, Microsoft Windows Server 2012 R2, and Microsoft Windows Server 2016 perform the following steps:

1.  Click Start and enter `hdwwiz` in the Search box. Click hdwwiz to start the Add Hardware wizard.

    For Microsoft Windows 8.1 and later releases, open the Windows Control Panel and double-click Add Hardware to start the Add Hardware wizard.

2.  In the Welcome window, click Next.

3.  In the The wizard can help you install other hardware window, select Install the hardware that I manually select from a list, and click Next.

4.  From the list of hardware types, select the type of hardware you are installing, select Network adapters, and click Next.

5.  In the Select Network Adapter window, make the following selections:

    - Manufacturer: Select Microsoft.

    - Network Adapter: Select Microsoft Loopback Adapter for Microsoft Windows 7 and Microsoft KM-TEST Loopback Adapter for Microsoft Windows Server 8.1 and later releases.

6.  Click Next.

7.  In the The wizard is ready to install your hardware window, click Next.

8.  In the Completing the Add Hardware Wizard window, click Finish.

9.  Click Manage Network Connections. This displays the Network Connections Control Panel item.

10. Right-click the connection that was just created. This is usually named "Local Area Connection 2". Choose Properties.

11. On the General tab, select Internet Protocol (TCP/IP), and click Properties.

12. In the Properties dialog box, click Use the following IP address and do the following:

    1.  IP Address: Enter a non-routable IP for the loopback adapter. Oracle recommends the following non-routable addresses:

        - `192.168.``x`.`x` (`x` is any value between 0 and 255)

        - `10.10.10.10`

    2.  Subnet mask: Enter `255.255.255.0`.

    3.  Record the values you entered, which you need later in this procedure.

    4.  Leave all other fields empty.

    5.  Click OK.

13. Click Close.

14. Close Network Connections.

15. Restart the computer.

16. Add a line to the `DRIVE_LETTER``: \WINDOWS\system32\drivers\etc\hosts` file with the following format, after the `localhost` line:

        IP_address   hostname.domainname   hostname

    where:

    - `IP_address` is the non-routable IP address.

    - `hostname` is the name of the computer.

    - `domainname` is the name of the domain.

    For example:

        10.10.10.10   mycomputer.us.example.com   mycomputer

17. Check the network configuration:

    1.  Open System in the Control Panel, and verify that Full computer name displays the host name and the domain name, for example, `sales.us.example.com`.

    2.  Click Change. In Computer name, you must see the host name, and in Full computer name, you must see the host name and domain name. Using the previous example, the host name must be `sales` and the domain must be `us.example.com`.

    3.  Click More. In Primary DNS suffix of this computer, you must see the domain name, for example, `us.example.com`.

**Parent topic:** [Installing a Loopback Adapter](loopback-adapter.md)
