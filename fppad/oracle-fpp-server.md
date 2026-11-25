## Oracle Fleet Patching and Provisioning Server

The Oracle Fleet Patching and Provisioning Server (FPPS) is a highly available software provisioning system that uses Oracle Automatic Storage Management (Oracle ASM), Oracle Automatic Storage Management Cluster File System (Oracle ACFS), Grid Naming Service (GNS), and other components.

The Oracle Fleet Patching and Provisioning Server primarily acts as a central server for provisioning Oracle homes, making them available to Oracle Fleet Patching and Provisioning Client and clientless targets.

Features of the Oracle Fleet Patching and Provisioning Server:

- Efficiently stores gold images and image series for the managed homes, including separate binaries, and metadata related to users, roles, and permissions.

- Stores working copies and Oracle Fleet Patching and Provisioning Client information.

- Provides a list of available homes to clients and clientless targets upon request.

- Patch a software home once and then deploy the home to any Oracle Fleet Patching and Provisioning Client or any clientless target, instead of patching every site.

- Provides the ability to report on existing deployments.

- Deploys homes on physical servers and virtual machines.

- Notifies subscribers of changes to image series.

- Maintains an audit log of all RHPCTL commands run.

**Parent topic:** [Fleet Patching and Provisioning Architecture](oracle-fpp-architecture.md)
