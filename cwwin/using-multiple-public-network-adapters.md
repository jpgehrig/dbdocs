## Using Multiple Public Network Adapters

You can configure multiple network adapters for the public network interface.

Oracle recommends that you do not identify multiple public network connection names during Oracle Grid Infrastructure installation.

1.  Use a third-party technology for your platform to aggregate the multiple public network adapters before you start installation.
2.  During installation, select the single network connection name for the combined network adapters as the public interface.

If you configure two network adapters as public network adapters in the cluster without using an aggregation technology, the failure of one public network adapter on a node does not result in automatic VIP failover to the other public network adapter.

**Parent topic:** [Network Interface Hardware Requirements](network-interface-hardware-requirements.md)
