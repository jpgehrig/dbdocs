On each node, complete the following steps to configure the BMC to support IPMI-based node fencing:

- Enable IPMI over LAN, so that the BMC can be controlled over the management network.

- Configure a static IP address for the BMC.

- Establish an administrator user account and password for the BMC

- Configure the BMC for VLAN tags, if you plan to use the BMC on a tagged VLAN.

The configuration tool you use does not matter, but these conditions must be met for the BMC to function properly. The utility `ipmitool` is provided as part of the Oracle Solaris distribution. You can use `ipmitool` to configure IPMI parameters, but be aware that setting parameters using `ipmitool` also sets the corresponding parameters for the service processor.

Refer to the documentation for the configuration option you select for details about configuring the BMC.

**Note:**

Problems in the initial revisions of Oracle Solaris software and firmware prevented IPMI support from working properly. Ensure you have the latest firmware for your platform and the following Oracle Solaris patches (or later versions), available from the following URL:

[`http://www.oracle.com/technetwork/systems/patches/firmware/index.html`](http://www.oracle.com/technetwork/systems/patches/firmware/index.html)

- 137585-05 IPMItool patch

- 137594-02 BMC driver patch

**Parent topic:** [Enabling Intelligent Platform Management Interface (IPMI)](enabling-intelligent-platform-management-interface-ipmi.md)
