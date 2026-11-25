## Requirements for Enabling IPMI

Review these hardware and software requirements for enabling cluster nodes to be managed with Intelligent Platform Management Interface (IPMI).

- For this release, Oracle Grid Infrastructure supports IPMI version 2.0.
- Each cluster member node requires a Baseboard Management Controller (BMC) running firmware compatible with IPMI version 2.0, which supports IPMI over local area networks (LANs), and configured for remote control using LAN.
- Each cluster member node requires an IPMI driver installed on each node.
- The cluster requires a management network for IPMI. This can be a shared network, but Oracle recommends that you configure a dedicated network.
- Each cluster member node's Ethernet port used by BMC must be connected to the IPMI management network.
- Each cluster member must be connected to the management network.
- Some server platforms put their network interfaces into a power saving mode when they are powered off. In this case, they may operate only at a lower link speed (for example, 100 megabyte (MB), instead of 1 GB). For these platforms, the network switch port to which the BMC is connected must be able to auto-negotiate down to the lower speed, or IPMI will not function properly.
- To support IPMI 2.0, you must download a third party tool, IPMIUTIL on every node of the cluster. You can download the IPMIUTIL tool from: <http://ipmiutil.sourceforge.net/>
- After you configure Oracle Grid Infrastructure on the cluster and install the IPMIUTIL utlity, you must set the path to the utility using the `crsctl set ipmi binaryloc` command on every node of the cluster. You must restart Oracle Grid Infrastructure stack for changes to take effect.

**Note:**

IPMI operates on the physical hardware platform through the network interface of the Baseboard Management Controller (BMC). Depending on your system configuration, an IPMI-initiated restart of a server can affect all virtual environments hosted on the server. Contact your hardware and OS vendor for more information.

**Parent topic:** [Enabling Intelligent Platform Management Interface (IPMI)](enabling-intelligent-platform-management-interface-ipmi.md)
