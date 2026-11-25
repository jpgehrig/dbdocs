## Installing Oracle Database on Nonnetworked Computers

You can install Oracle Database on non-networked computers.

If the computer, such as a laptop, is configured for DHCP and you plan to connect the computer to the network after the Oracle Database installation.

Perform these steps before you install Oracle Database on the non-networked computer:

1.  Install a loopback adapter on the computer.

    The loopback adapter and the local IP address simulate a networked computer. If you connect the computer to the network, Oracle Database still uses the local IP address and host name.

2.  Ping the computer from itself, using only the host name and using the fully qualified name, which is in the `DRIVE_LETTER:``\system32\drivers\etc\hosts` file.

    For example, if you installed a loopback adapter on a computer called `mycomputer` on the `us.example.com` domain, check the following:

        DRIVE_LETTER:\>ping mycomputer                Ping itself using just the hostname.

        Reply from 10.10.10.10                    Returns local IP.
        DRIVE_LETTER:\>ping mycomputer.us.example.com   Ping using a fully qualified name.
        Reply from 10.10.10.10                    Returns local IP.

    **Note:**

    When you ping a computer from itself, the `ping` command must return the local IP address (the IP address of the loopback adapter).

    If the `ping` command fails, contact your network administrator.

If you connect the computer to a network after installation, the Oracle Database instance on your computer can work with other instances on the network. Remember that you must have installed a loopback adapter on your computer. Your computer can use a static IP or DHCP, depending on the network to which you are connected.

**Parent topic:** [Configuring Networks for Oracle Database](configuring-networks-for-oracle-database.md)
