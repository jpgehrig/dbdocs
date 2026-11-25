## Configuring Multiple ASM Interconnects on Microsoft Windows Platforms

When using multiple network interface cards for the Oracle Automatic Storage Management (Oracle ASM) interconnect, you must enable the `weakhostsend` network parameter.

Microsoft Windows versions prior to Windows Vista use the **weak host send and receive model**. The TCP/IP stack in Windows Vista, Windows Server 2008, and later Windows operating systems, supports the **strong host send and receive model** for both IPv4 and IPv6 protocols by default. Oracle RAC nodes that use multiple network interface cards (NICs) for the ASM interconnect must enable the weak host send by specifically setting the `weakhostsend` parameter for all the private subnets.

If you do not enable the `weakhostsend` parameter, you might experience connection issues on the ASM interconnects because the interconnect packets are being blocked or discarded. It is not considered unsafe to enable `weakhostsend` because the interconnect is on a private and isolated network. Enabling the `weakhostsend` parameter allows all private NICs to send packets to multiple private subnets.

1.  Open a CMD Prompt as Administrator window.
2.  Use the following commands to configure the send behavior for both IPv4 and IPv6, on a per-interface basis, where interface1 and interface2 represent the names or interface indexes assigned to the NIC adapters on the Oracle RAC nodes.
        netsh interface [ipv4 | ipv6] set interface interface1 weakhostsend=enabled
        netsh interface [ipv4 | ipv6] set interface interface2 weakhostsend=enabled

    You can obtain the interface index of a NIC from the output of the command:

        netsh interface [ipv4 | ipv6] show interface
3.  Repeat the commands in Step 2 for all the private NICs, on each node in the cluster.

You can choose multiple interconnects either during installation or after installation using the `oifcfg setif` command.

**Parent topic:** [Configuring Networks for Oracle Grid Infrastructure and Oracle RAC](configuring-networks-for-oracle-grid-infrastructure-and-oracle-rac.md)
