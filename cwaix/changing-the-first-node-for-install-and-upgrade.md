If the first node becomes inaccessible, you can force another node to be the first node for installation or upgrade.

During installation, if `root.sh` fails to complete on the first node, run the following command on another node using the `-force` option:

    root.sh -force -first

For upgrade:

    rootupgrade.sh -force -first

**Parent topic:** [Performing Rolling Upgrade of Oracle Grid Infrastructure](performing-rolling-upgrade-of-oracle-grid-infrastructure.md)
