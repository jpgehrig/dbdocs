Review this procedure to configure IPMI in the iLO processor on HP platforms, and to set a password for the null (noname user).

1.  Log in to the iLO web interface, and configure the required network settings for the iLO and BMC under Administration, then Network Settings to obtain the IP address, and to check the netmask and default gateway.
2.  Start a terminal session from a device with network connectivity to the BMC of the node to configure.
3.  From the terminal session, set the IPMI password for the anonymous user (noname) over the network, using an IPMI administration tool, such as ipmitool from a client or server connected to the note whose user password you want to change. F
    or example, where `ipmiaddr` is the IPMI address, and password is the password:
        % ipmitool -H ipmiaddr -U "" user set password 1 "password"

    In this example, the anonymous username is being provided explicitly using -U "" for clarity, but it is implied if the username argument is missing. This command prompts for the current password, which can be the initial null password. If the password is successfully changed, then the command prints an error similar to:` "Close session command failed."`. This message is printed because the command attempts to terminate the IPMI network session using the previous password.
4.  After you configure the BMC on each cluster member node, and complete Oracle Grid Infrastructure installation, you must store the IPMI administrator credentials and the BMC static IP address in the Oracle Local Registry (OLR) on each cluster member node. Use crsctl to do this. However, when you store the IPMI credentials in the OLR, you must have the anonymous user specified explicitly, or a parsing error will be reported:
        % crsctl set css ipmiadmin ""

    When prompted, provide the password you set with the IPMI administrator tool.

**Parent topic:** [Enabling Intelligent Platform Management Interface (IPMI)](enabling-intelligent-platform-management-interface-ipmi.md)
