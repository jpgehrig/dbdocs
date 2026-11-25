## Network Interface Configuration Options for Performance

The precise configuration you choose for your network depends on the size and use of the cluster you want to configure, and the level of availability you require.

If you access Oracle ASM remotely, or a certified Network-attached Storage (NAS) is used for Oracle RAC and this storage is connected through Ethernet-based networks, then you must have a third network interface for data communications. Failing to provide three separate network interfaces in this case can cause performance and stability problems under heavy system loads.

**Parent topic:** [Network Interface Hardware Requirements](network-interface-hardware-requirements.md)
