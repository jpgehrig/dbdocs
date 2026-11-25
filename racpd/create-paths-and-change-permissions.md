## Create Paths and Change Permissions

To create directory paths and change the permissions as needed for the cluster, complete this set of commands on the Podman host.

As `root`, run the following commands for `racnode1`:

    # podman exec racnode1 /bin/bash -c "mkdir -p /u01/app/oraInventory"
    # podman exec racnode1 /bin/bash -c "mkdir -p /u01/app/grid"
    # podman exec racnode1 /bin/bash -c "mkdir -p /u01/app/19c/grid"
    # podman exec racnode1 /bin/bash -c "chown -R grid:oinstall /u01/app/grid"
    # podman exec racnode1 /bin/bash -c "chown -R grid:oinstall /u01/app/19c/grid"
    # podman exec racnode1 /bin/bash -c "chown -R grid:oinstall /u01/app/oraInventory"
    # podman exec racnode1 /bin/bash -c "mkdir -p /u01/app/oracle"
    # podman exec racnode1 /bin/bash -c "mkdir -p /u01/app/oracle/product/19c/dbhome_1"
    # podman exec racnode1 /bin/bash -c "chown -R oracle:oinstall /u01/app/oracle"
    # podman exec racnode1 /bin/bash -c "chown -R oracle:oinstall /u01/app/oracle/product/19c/dbhome_1"

Next, repeat the commands for `racnode2`:

    # podman exec racnode2 /bin/bash -c "mkdir -p /u01/app/oraInventory"
    # podman exec racnode2 /bin/bash -c "mkdir -p /u01/app/grid"
    # podman exec racnode2 /bin/bash -c "mkdir -p /u01/app/19c/grid"
    # podman exec racnode2 /bin/bash -c "chown -R grid:oinstall /u01/app/grid"
    # podman exec racnode2 /bin/bash -c "chown -R grid:oinstall /u01/app/19c/grid"
    # podman exec racnode2 /bin/bash -c "chown -R grid:oinstall /u01/app/oraInventory"
    # podman exec racnode2 /bin/bash -c "mkdir -p /u01/app/oracle"
    # podman exec racnode2 /bin/bash -c "mkdir -p /u01/app/oracle/product/19c/dbhome_1"
    # podman exec racnode2 /bin/bash -c "chown -R oracle:oinstall /u01/app/oracle"
    # podman exec racnode2 /bin/bash -c "chown -R oracle:oinstall /u01/app/oracle/product/19c/dbhome_1"

**Parent topic:** [Set Up the Podman Containers for Oracle Grid Infrastructure Installation](set-podman-container-oracle-grid-infrastructure-installation.md)
