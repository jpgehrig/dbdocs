During installation of Oracle Grid Infrastructure, you have the option of either providing cluster configuration information manually, or using a cluster configuration file.

A cluster configuration file is a text file that you can create before starting `gridSetup.sh`, which provides the installer with cluster node addresses that it requires to configure the cluster.

Oracle recommends that you consider using a cluster configuration file if you intend to perform repeated installations on a test cluster, or if you intend to perform an installation on many nodes. A sample cluster configuration file is available in the directory `Grid_home``/install/response/sample.ccf`.

To create a cluster configuration file manually, start a text editor, and create a file that provides the name of the public and virtual IP addresses for each cluster member node, in the following format:

    node1 node1-vip
    node2 node2-vip
    .
    .
    .

Specify the different nodes, separating them with either spaces or colon (:).

For example:

    mynode1 mynode1-vip
    mynode2 mynode2-vip

Or, for example:

    mynode1:mynode1-vip
    mynode2:mynode2-vip

Example 8-1 Sample Cluster Configuration File

The following sample cluster configuration file is available in the directory `Grid_home``/install/response/sample.ccf`:

    #
    # Cluster nodes configuration specification file
    #
    # Format:
    # node [vip] [site-name]
    #
    # node            - Node's public host name
    # vip             - Node's virtual host name
    # site-name       - Node's assigned site
    #
    # Specify details of one node per line.
    # Lines starting with '#' will be skipped.
    #
    # (1) vip is not required for Oracle Grid Infrastructure software only
    #     installs and Oracle Member cluster for Applications
    # (2) vip should be specified as AUTO if Node Virtual host names are Dynamically
    #     assigned
    # (3) site-name should be specified only when configuring Oracle Grid Infrastructure with "Extended Cluster" option
    #
    # Examples:
    # --------
    # For installing GI software only on a cluster:
    # ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
    # node1
    # node2
    #
    # For Standalone Cluster:
    # ^^^^^^^^^^^^^^^^^^^^^^
    # node1 node1-vip
    # node2 node2-vip
    #
    # For Standalone Extended Cluster:
    # ^^^^^^^^^^^^^^^^^^^^^^
    # node1 node1-vip sitea
    # node2 node2-vip siteb
    #
    # For Domain Services Cluster:
    # ^^^^^^^^^^^^^^^^^^^^^^^^^^^
    # node1 node1-vip
    # node2 node2-vip
    #
    # For Member Cluster for Oracle Database:
    # ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
    # node1 node1-vip
    # node2 node2-vip
    #
    # For Member Cluster for Applications:
    # ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
    # node1
    # node2
    #

**Parent topic:** [Installing Oracle Grid Infrastructure](installing-oracle-grid-infrastructure.md)
