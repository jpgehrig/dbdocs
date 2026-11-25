## Preparing to Upgrade an Existing Oracle Clusterware Installation

If you have an existing Oracle Clusterware installation, then you upgrade your existing cluster by performing an out-of-place upgrade. You cannot perform an in-place upgrade.

The following topics list the steps you can perform before you upgrade Oracle Grid Infrastructure:

- [Upgrade Checklist for Oracle Grid Infrastructure](preugrade-oracle-grid-infrastructure-checklist.md)
  Review this checklist before upgrading an existing Oracle Grid Infrastructure. A cluster is being upgraded until all cluster member nodes are running the new installations, and the new clusterware becomes the active version.
- [Checks to Complete Before Upgrading Oracle Grid Infrastructure](checks-to-complete-before-upgrading-oracle-clusterware.md)
  Complete the following tasks before upgrading Oracle Grid Infrastructure.
- [Moving Oracle Clusterware Files from NFS to Oracle ASM](moving-oracle-clusterware-files-from-nfs-to-oracle-asm.md)
  You can move Oracle Cluster Registry (OCR) and voting files from Network File System (NFS) to Oracle Automatic Storage Management (Oracle ASM) disk groups.
- [Running the Oracle ORAchk Upgrade Readiness Assessment](running-the-oracle-raccheck-upgrade-readiness-assessment.md)
  Download and run the Oracle ORAchk Upgrade Readiness Assessment before upgrading Oracle Grid Infrastructure.
- [Using CVU to Validate Readiness for Oracle Clusterware Upgrades](using-cvu-to-validate-readiness-for-oracle-clusterware-upgrades.md)
  Oracle recommends that you use Cluster Verification Utility (CVU) to help to ensure that your upgrade is successful.
- [Using Dry-Run Upgrade Mode to Check System Upgrade Readiness](using-dry-run-upgrade-mode-to-validate-readiness-for-oracle-grid-infrastructure.md)
  Use dry-run upgrade mode of Oracle Grid Infrastructure installation wizard, `gridSetup.sh`, to check readiness for Oracle Clusterware upgrades.

**Parent topic:** [Upgrading Oracle Grid Infrastructure](upgrading-oracle-grid-infrastructure.md)
