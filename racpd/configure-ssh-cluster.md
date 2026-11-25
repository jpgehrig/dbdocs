## Configure SSH for the Cluster

You must configure SSH for both the Oracle Real Application Clusters (Oracle RAC) software owner (`oracle`) and the Oracle Grid Infrastructure software owner (`grid`) before starting installation.

Configure SSH separately for `grid` and `oracle`:

Log in to Oracle RAC containers from your container host, and reset the passwords for the `grid` and `oracle` users:

    # podman exec -i -t racnode1 /bin/bash
    # passwd grid
    # passwd oracle
    # podman exec -i -t racnode2 /bin/bash
    # passwd grid
    # passwd oracle

For information about configuring SSH on cluster nodes, refer to Oracle Grid Infrastructure Installation and Upgrade Guide for Linux to see how to set up user equivalency for the `grid` and `oracle` users inside the containers.

**Parent topic:** [Set Up the Podman Containers for Oracle Grid Infrastructure Installation](set-podman-container-oracle-grid-infrastructure-installation.md)
