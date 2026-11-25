## Network Requirements for the Public Network

The following is a list of requirements for the public network configuration:

- The public network connection names must be different from the private network connection names.

- Public network connection names are case-sensitive.

- The public network connection name cannot contain any multibyte language characters.

- If you use OUI to install Oracle Grid Infrastructure, then the public network connection names associated with the public network adapters for each network must be the same on all nodes.

  For example, if you have a two-node cluster, you cannot configure network adapters on `node1` with `NIC1` as the public network connection name and on `node2` have `NIC2` as the public network connection name. Public network connection names must be the same, so you must configure `NIC1` as the public network connection name on both nodes.

- For the public network, each network adapter must use high-speed network adapters and switches that support user datagram protocol (UDP), transmission control protocol and internet protocol (TCP/IP). Minimum requirement is 1 Gigabit Ethernet, 10GbE recommended.

**Parent topic:** [Network Interface Hardware Requirements](network-interface-hardware-requirements.md)
