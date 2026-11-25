## Network Requirements for Each Node

Verify that servers where you install Oracle Grid Infrastructure meet the minimum network requirements for installation.

- The host name of each node must use only the characters a-z, A-Z, 0-9, and the dash or minus sign (-). Host names using underscores (\_) are not supported.

- Each node must have at least two network adapters or network interface cards (NICs): one for the public network interface, and one for the private network interface, or the interconnect. Each network adapter has a network connection name.

  **Note:**

  Do not use the names PUBLIC and PRIVATE (all caps) for the public or private (interconnect) network connection names.

- Network adapters must be at least 1 GbE, with 10 GbE recommended.

- If you plan to use Oracle ASM running in a different cluster for storage, then you must either have a third network adapter for accessing the ASM network, or use the same network adapter that is used for the private network interface.

**Parent topic:** [Network Interface Hardware Requirements](network-interface-hardware-requirements.md)
