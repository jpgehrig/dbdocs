## Changing the First Node for Install and Upgrade

If the first node becomes inaccessible, you can force another node to be the first node for installation or upgrade.

- Installation: If `gridconfig.bat` fails to complete on the first node, run the following command on another node using the `-force` option:
      Grid_home\crs\config\gridconfig.bat -force -first
- Upgrade: If `gridconfig.bat` fails to complete on the first node, run the following command on another node using the `-force` option:
      Grid_home\crs\config\gridconfig.bat -upgrade -force -first

**Parent topic:** [Performing Rolling Upgrades of Oracle Grid Infrastructure](performing-rolling-upgrades-of-oracle-grid-infrastructure.md)
