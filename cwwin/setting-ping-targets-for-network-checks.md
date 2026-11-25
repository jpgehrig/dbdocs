## Setting Ping Targets for Network Checks

Receive notification about the status of public networks by setting the `Ping_Targets` parameter during the Oracle Grid Infrastructure installation.

In certain environments, for example, in a virtual machine, the network link status is not correctly returned when the network cable is disconnected. You can receive notification about public network status in these environments by setting the `Ping_Targets` parameter during the Oracle Grid Infrastructure installation. You should use this parameter for addresses outside the cluster, like a switch or router.

- Run the installer:
      C:\..> setup.exe oracle_install_crs_Ping_Targets=Host1|IP1,Host2|IP2

  For example:

      C:\..> setup.exe oracle_install_crs_Ping_Targets=192.0.2.1,192.0.2.2

The `ping` utility contacts the comma-separated list of host names or IP addresses Host1/IP1,Host2/IP2 to determine whether the public network is available. If none of the hosts respond, then the network is considered to be offline.

**Parent topic:** [Installing Oracle Grid Infrastructure for a Cluster](installing-oracle-grid-infrastructure-for-a-cluster.md)
