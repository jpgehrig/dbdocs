For Oracle Clusterware, you must configure the ILOM/BMC for static IP addresses.

On Oracle Solaris platforms, the BMC shares configuration information with the Integrated Lights Out Manager service processor (ILOM). Configuring the BMC with dynamic addresses (DHCP) is not supported on Oracle Solaris.

**Note:**

If you configure IPMI, and you use Grid Naming Service (GNS) you still must configure separate addresses for the IPMI interfaces. As the IPMI adapter is not seen directly by the host, the IPMI adapter is not visible to GNS as an address on the host.

**Parent topic:** [Enabling Intelligent Platform Management Interface (IPMI)](enabling-intelligent-platform-management-interface-ipmi.md)
