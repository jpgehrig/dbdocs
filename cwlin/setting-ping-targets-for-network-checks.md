## Setting Ping Targets for Network Checks

Receive notification about network status by setting the `Ping_Targets` parameter during the Oracle Grid Infrastructure installation.

For environments where the network link status is not correctly returned when the network cable is disconnected, for example, in a virtual machine, you can receive notification about network status by setting the `Ping_Targets` parameter during the Oracle Grid Infrastructure installation.

Run the installer:

    ./gridSetup.sh oracle_install_crs_Ping_Targets=Host1|IP1,Host2|IP2

The ping utility contacts the comma-separated list of host names or IP addresses `Host1|IP1,Host2|IP2` to determine whether the public network is available. If none of the hosts respond, then the network is considered to be offline. Addresses outside the cluster, like of a switch or router, should be used.

For example:

    /gridSetup.sh oracle_install_crs_Ping_Targets=192.0.2.1,192.0.2.2

**Parent topic:** [Installing Only the Oracle Grid Infrastructure Software](installing-only-the-oracle-grid-infrastructure-software.md)
