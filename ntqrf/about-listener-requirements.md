In Oracle Database, the listener is set to start automatically at system restart.

You can verify the listener status by choosing the Windows Control Panel, then Administrative Tools, and then viewing the status of Services.

Oracle usually recommends that you only have a single net listener service running on a Windows computer at any one time. This single listener can support multiple databases. If you must have two different net listener services running on a Windows computer at the same time, ensure that they are configured to listen on different TCP/IP port numbers.

If the same IP address and port are used for different listeners, then you expect that the second and subsequent listeners fail to bind, instead, Windows allows them all to listen on the same IP address and port, resulting in an unexpected behavior of the listeners. This is a suspected Windows operating system problem with TCP/IP and has been reported to Microsoft.

- [Running Oracle Net Services](running-oracle-net-services.md)
  Oracle Net Services such as Oracle Listener, CMADMIN, and CMAN Proxy Listener run under the specified Oracle Home User account (Windows User Account) specified during the installation.

**Parent topic:** [Oracle Net Services Configuration on Windows](net-services-configuration-on-windows.md)
