You must confirm that a non-networked computer can connect to itself to ensure that you can configure client network resolution after installation. A non-networked computer is a computer that does not have a fixed network address, such as a computer using DHCP.

You can install Oracle Database on a non-networked computer. If the computer, such as a laptop, is configured for DHCP and you plan to connect the computer to the network after the Oracle Database installation, then use the `ping` command on the computer on which you want to install the database to check if the computer can connect to itself. Perform this step by first using only the host name and then using the fully qualified name, which should be in the `/etc/hosts` file.

If you connect the computer to a network after installation, then the Oracle Database instance on the computer can work with other instances on the network. The computer can use a static IP or DHCP, depending on the network to which you are connected.

When you run the `ping` command on the computer itself, the ping command should return the IP address of the computer. If the `ping` command fails, then contact your network administrator.

**Parent topic:** [Configuring Networks for Oracle Database](configuring-networks-for-oracle-database.md)
