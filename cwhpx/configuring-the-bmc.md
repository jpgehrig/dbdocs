On each node, complete the following steps to configure the BMC to support IPMI-based node fencing.

- Configure a static IP address for the BMC.

- Set a password for the null (noname) account for the BMC.

On HP-UX, the BMC and the iLO share network configuration. They have the same IP address, the same hardware MAC address, and the same default gateway address.

If your iLO processor is already configured for network access using a static address, then you have already established the required BMC network configuration. If you have not set up a static address for the iLO, then you must set a static address, and note the address so that you can enter it into the Oracle Clusterware local registry after installation.

You must also set up a password for the null (noname) user account, as this is the single account that the BMC uses. Administration accounts in the iLO are unrelated to the BMC. For security reasons, Oracle requires that you set a password for the BMC account.

Refer to your HP-UX documentation for more information about how to configure the BMC. Ensure that the BMC is configured on each cluster member node.

**Parent topic:** [Enabling Intelligent Platform Management Interface (IPMI)](enabling-intelligent-platform-management-interface-ipmi.md)
