## 1 Host Preparation for Oracle RAC on Podman

Use these instructions to deploy Oracle Real Application Clusters (Oracle RAC) on Podman

In this publication, the Linux server hosting the Podman containers is referred to as the **Podman host,** or just the **Host**. The Podman hosts running the Oracle RAC, Oracle Grid Infrastructure, and Oracle Automatic Storage Management (Oracle ASM) are collectively referred to as the Podman Oracle RAC Container, or just the Oracle RAC Container.

- Prerequisites for Oracle RAC on Podman
  Before beginning to deploy Oracle Real Application Clusters (Oracle RAC) on Podman container images, ensure that you are prepared for the installation, and that your system meets software and storage requirements.

### Prerequisites for Oracle RAC on Podman

Before beginning to deploy Oracle Real Application Clusters (Oracle RAC) on Podman container images, ensure that you are prepared for the installation, and that your system meets software and storage requirements.

- Preparing to Install Oracle RAC on Podman Containers
  To use these instructions, you should have background knowledge of the technology and operating system.
- Software and Storage Requirements for Oracle RAC on Podman
  Review which Oracle software releases are supported for deployment with Oracle RAC on Podman, and what storage options you can use.

**Parent topic:** Host Preparation for Oracle RAC on Podman

#### Preparing to Install Oracle RAC on Podman Containers

To use these instructions, you should have background knowledge of the technology and operating system.

You should be familiar with the following technologies:

- Linux
- Podman
- Oracle Real Application Clusters (Oracle RAC) installation
- Oracle Grid Infrastructure installation
- Oracle Automatic Storage Management (Oracle ASM)

Installation on Podman follows the standard Linux installation procedure. However, because Podman is closely integrated with the host operating system, some of the environment setup steps are slightly different. Refer to the Podman documentation for an explanation of the Podman architecture, including namespaces, and resources for which you cannot use a namespace. This guide focuses on what is different. For information about standard steps and details of configuration, refer to Oracle Grid Infrastructure Installation and Upgrade Guide for Linux. Review the Oracle Grid Infrastructure Installation Checklist before starting the installation.

**Related Topics**

- [Oracle Grid Infrastructure Installation Checklist](../cwlin/oracle-grid-infrastructure-installation-checklist.md)

**Parent topic:** Prerequisites for Oracle RAC on Podman

#### Software and Storage Requirements for Oracle RAC on Podman

Review which Oracle software releases are supported for deployment with Oracle RAC on Podman, and what storage options you can use.

In this guide, Oracle Real Application Clusters (Oracle RAC) on Podman is deployed on Oracle Database 19c. Podman deployment is supported with the following 19c releases:

##### Software Requirements for Linux x86-64

- Oracle Grid Infrastructure Release 19c (19.3), updated with Release Update (RU) 19.16, or later release updates
- Oracle Database Release 19c (19.3) updated with RU 19.16 or later release updates
- Podman 4.0.2 or later
- Oracle Linux 8 Container image (`oraclelinux:8`)
- Oracle Linux for Podman host on Oracle Linux 8.5 (Linux-x86-64) or later updates

Unbreakable Enterprise Kernel 6 (UEKR6), and its release updates.

Unbreakable Enterprise Kernel 7 (UEKR7), and its release updates.

In this example, we use Oracle Linux 8.5 (Linux-x86-64) with the Unbreakable Enterprise Kernel 6: `5.4.17-2136.300.7.el8uek.x86_64`.

##### Software Requirements for Linux ARM

- Oracle Grid Infrastructure Release 19.19 or later release updates
- Oracle Database Release 19.19 or later release updates
- Podman 4.0.2 or later
- Oracle Linux 8 Container image (`oraclelinux:8`)
- Oracle Linux for Podman host on Oracle Linux 8.7 (`Linux-aarch64`) or later updates

Unbreakable Enterprise Kernel 7 (UEKR7), minimum `5.15.0-100.96.32.el8uek.aarch64` and its release updates

##### Storage Requirements

Database storage for Oracle RAC on Podman must use Oracle Automatic Storage Management (Oracle ASM) configured either on block storage, or on a network file system (NFS).

**Caution:**

For Podman deployment, Oracle Advanced Cluster File System (Oracle ACFS) and Oracle ASM Filter Driver (Oracle ASMFD) are not supported

**Parent topic:** Prerequisites for Oracle RAC on Podman
