## Configuring the IPMI Management Network

You can configure the Baseboard Management Controller (BMC) for Dynamic Host Configuration Protocol (DHCP), or for static IP addresses.

Oracle recommends that you configure the BMC for dynamic IP address assignment using DHCP. To use this option, you must have a DHCP server configured to assign the BMC IP addresses.

**Note:**

If you configure Intelligent Platform Management Interface (IPMI), and you use Grid Naming Services (GNS), then you still must configure separate addresses for the IPMI interfaces. Because the IPMI adapter is not seen directly by the host, the IPMI adapter is not visible to GNS as an address on the host.

**Parent topic:** [Enabling Intelligent Platform Management Interface (IPMI)](enabling-intelligent-platform-management-interface-ipmi.md)
