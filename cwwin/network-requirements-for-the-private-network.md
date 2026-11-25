## Network Requirements for the Private Network

The following is a list of requirements for the private network configuration:

- The private network connection names must be different from the network connection names used for the public network.

- Each node's private interface for interconnects must be on the same subnet.

  For example, if the private interfaces have a subnet mask of 255.255.255.0, then your private network is in the range 192.168.0.0--192.168.0.255, and your private addresses must be in the range of 192.168.0.\[0-255\]. If the private interfaces have a subnet mask of 255.255.0.0, then your private addresses can be in the range of 192.168.\[0-255\].\[0-255\]

- The private network connection name cannot contain any multibyte language characters. The private network connection names are case-sensitive.

- Both IPv4 and IPv6 addresses are supported.

  You can configure a network interface to use either the IPv4 protocol, or the IPv6 protocol on a given network. If you use redundant network interfaces (bonded or teamed interfaces), then be aware that Oracle does not support configuring one interface to support IPv4 addresses and the other to support IPv6 addresses. You must configure network interfaces of a redundant interface pair with the same IP protocol.

  All the nodes in the cluster must use the same IP protocol configuration. Either all the nodes use only IPv4, or all the nodes use only IPv6. You cannot have some nodes in the cluster configured to support only IPv6 addresses, and other nodes in the cluster configured to support only IPv4 addresses.

- If you use OUI to install Oracle Grid Infrastructure, then the private network connection names associated with the private network adapters must be the same on all nodes.

  For example, if you have a two-node cluster, and `PrivNIC` is the private network connection name for `node1`, then `PrivNIC` must be the private network connection name for `node2`.

- For the private network, the network adapters must use high-speed network adapters and switches that support UDP, TCP/IP (minimum requirement is 1 Gigabit Ethernet, 10GbE recommended). Alternatively, use InfiniBand for the interconnect.

  **Note:**

  UDP or TCP is the interconnect protocol for Oracle Clusterware. You must use a switch for the interconnect. Oracle recommends that you use a dedicated switch.

  Oracle does not support token-rings or crossover cables for the interconnect.

- For the private network adapters, the endpoints of all designated network connection names must be completely reachable on the network. There should be no node that is not connected to every other node on the private network. You can test if an interconnect interface is reachable using `ping`.

**Parent topic:** [Network Interface Hardware Requirements](network-interface-hardware-requirements.md)
