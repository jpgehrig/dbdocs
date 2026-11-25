## Configuring the BMC

Configure BMC on each node for remote control using LAN for IPMI-based node fencing to function properly.

You can configure BMC from the BIOS prompt, using a distribution-specific management utility, or you can configure BMC using publicly available utilities, such as the following:

IPMItool, which is available for Linux:

<http://ipmitool.sourceforge.net>

IPMIutil, which is available for Linux:

<http://ipmiutil.sourceforge.net>

Refer to the documentation for the configuration tool you select for details about using the tool to configure the BMC.

When you configure the BMC on each node, you must complete the following:

1.  Enable IPMI over LAN, so that the BMC can be controlled over the management network.
2.  Enable dynamic IP addressing using DHCP or GNS, or configure a static IP address for the BMC.
3.  Establish an administrator user account and password for the BMC.
4.  Configure the BMC for VLAN tags, if you will use the BMC on a tagged VLAN.

The configuration tool you use does not matter, but these conditions must be met for the BMC to function properly.

**Parent topic:** [Enabling Intelligent Platform Management Interface (IPMI)](enabling-intelligent-platform-management-interface-ipmi.md)
