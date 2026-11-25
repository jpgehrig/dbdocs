## Downgrading Oracle Clusterware to an Earlier Release

After a successful or a failed upgrade, you can restore Oracle Clusterware to the previous release.

Downgrading Oracle Clusterware restores the Oracle Clusterware configuration to the state it was in before the Oracle Grid Infrastructure 19c upgrade. Any configuration changes you performed during or after the Oracle Grid Infrastructure 19c upgrade are removed and cannot be recovered.

To restore Oracle Clusterware to the previous release, use the downgrade procedure for the release to which you want to downgrade.

**Note:**

- Starting with Oracle Grid Infrastructure 12c Release 2 (12.2), you can downgrade the cluster nodes in any sequence. You can downgrade all cluster nodes except one, in parallel. You must downgrade the last node after you downgrade all other nodes.

- When downgrading after a failed upgrade, if the `rootcrs.sh` or `rootcrs.bat` file does not exist on a node, then instead of executing the script, use the command `perl rootcrs.pl` . Use the Perl interpreter located in the Oracle Home directory.

<!-- -->

- [Downgrading Oracle Clusterware to 18c](downgrading-oracle-clusterware-to-18c.md)
  Downgrade procedures for downgrading all Oracle Grid Infrastructure cluster types to 18c after successful or failed upgrade.
- [Downgrading Oracle Clusterware to 12c Release 2 (12.2)](downgrading-oracle-clusterware-to-12c-release-2-12-2.md)
  Downgrade procedures for downgrading all Oracle Grid Infrastructure cluster types to 12c Release 2 (12.2) after successful or failed upgrade.
- [Downgrading to Oracle Grid Infrastructure 12c Release 1 (12.1.0.2)](downgrading-to-oracle-grid-infrastructure-12c-release-1-12-1.md)
  Use this procedure to downgrade to Oracle Grid Infrastructure 12c release 1 (12.1.0.2).
- [Downgrading to Oracle Grid Infrastructure 11g Release 2 (11.2)](downgrading-to-oracle-grid-infrastructure-11g-release-2-11-2.md)
  Use this procedure to downgrade to Oracle Grid Infrastructure 11g Release 2 (11.2).

**Parent topic:** [Upgrading Oracle Grid Infrastructure](upgrading-oracle-grid-infrastructure.md)
