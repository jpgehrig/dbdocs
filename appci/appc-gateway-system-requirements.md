The following topics describe the system requirements of the gateway.

- Hardware Requirements

- Software Requirements

Refer to the [Oracle Database Installation Guide](../ladbi/oracle-database-installation-checklist.md) and to the certification matrix on My Oracle Support for the most up-to-date list of certified hardware platforms and operating system version requirements to operate the gateway for your system. The My Oracle Support Web site can be found at:

<https://support.oracle.com>

### Hardware Requirements

The hardware requirements for this release of the gateway on your platform are described in the following sections:

Table 3-1 lists the minimum hardware requirements for Oracle Database Gateway for APPC.

Table 3-1 Hardware requirements for Oracle Database Gateway for APPC

| Hardware Items       | Required for IBM AIX on POWER Systems (64-Bit) | Required for Linux x86 64 bit | Required for Oracle Solaris on SPARC (64-Bit)  | Required for HP-UX Itanium        |
|:---------------------|:-----------------------------------------------|:------------------------------|:-----------------------------------------------|:----------------------------------|
| Temporary Disk Space | 400 MB                                         | 400 MB                        | 400 MB                                         | 400 MB                            |
| Disk Space           | 1.5 GB                                         | 750 MB                        | 750 MB                                         | 1.5 GB                            |
| Physical Memory\*    | 512 MB                                         | 512 MB                        | 512 MB                                         | 512 MB                            |
| Swap Space           | 1 GB                                           | 1 GB                          | 1 GB                                           | 1 GB                              |
| Processor            | IBM RS/6000 AIX-Based System Processor         | x86_64                        | Sun Solaris Operating System (SPARC) Processor | HP Itanium processor for hp-ux 11 |

The following factors affect the virtual memory requirements of the gateway server process:

- Number of concurrent gateway connections open by each user

- Number of data items being transferred between the gateway and the remote transaction program

- The Oracle Net protocol adapters that were included during the gateway installation

- Additional factors, such as configured network buffer size

#### Network Attachment Requirements

The gateway requires any network attachment supported by either the SNA communication package for your platform or the TCP/IP Networking Facility for TCP/IP communication.

However, if you are using only the new TCP/IP support for IMS Connect feature, you will not need an SNA package. Your operating system comes with TCP/IP installed.

### Software Requirements

The system software configuration described in this section is supported by Oracle, provided that the underlying system software products are supported by their respective vendors. Verify the latest support status with your system software vendors.

Topics:

- Operating System Requirements

- Communication Protocol Requirements

- Oracle Database Requirements

- Oracle Networking Product Requirements

- IBM Mainframe Requirements

#### Operating System Requirements

Refer to the [Oracle Database Installation Guide](../install-and-upgrade.md) and to the certification matrix on My Oracle Support for the most up-to-date list of certified operating system version requirements to operate the gateway for your Linux 64-bit systems, AIX-Based, or Solaris system. The My Oracle Support Web site is available at

[`https://support.oracle.com`](https://support.oracle.com)

#### Communication Protocol Requirements

Each operating system uses specific communications servers, as described in this section.

**Note:**

If you choose to use TCP/IP support for IMS Connect as communication protocol, then you do not need to use an SNA communication package from the following list. Each operating system comes with a TCP/IP protocol automatically installed. If you choose to use the TCP/IP protocol, then you need to configure it to work properly with the gateway. Refer to [Gateway Configuration Using TCP/IP Communication Protocol](config-appc-gateway-using-tcp-ip.md).

##### Communications Protocols for Linux for Intel Pentium-based 32-bit Systems

Communications protocols for Linux for Intel Pentium-based 32-bit System IBM Communications Server V6.0.1.1 for Linux or higher, or the TCP/IP communication software that comes with your operating system.

##### Communications Protocols for AIX-based Systems

SNA Server for AIX version 6.01 or higher, or the TCP/IP communications software that comes with your operating system.

##### Communications Protocols for Solaris

SNAP-IX version 6 or higher, or the TCP/IP communications software that comes with your operating system.

#### Oracle Database Requirements

All UNIX platforms require that the Oracle database, that is to act as the Oracle database be up to date with the latest patchset for supported Oracle database releases.

#### Oracle Networking Product Requirements

Oracle Net is automatically installed on the system where Oracle database is installed and on the system where the gateway is installed. Refer to [Configuring Your Oracle Network](appc-gateway-config-oracle-network.md) in this guide for detailed configuration information. Additionally, you might refer to the [Oracle Database Net Services Administrator's Guide](../netag/index.md).

#### IBM Mainframe Requirements

In addition to the other software requirements of the gateway and the platform being used, the following list outlines other requirements necessary on the IBM mainframe:

- OLTP for SNA

  The OLTP must support mapped APPC conversations. If the OLTP transaction programs to be executed through the gateway perform database updates, then the APPC verbs `CONFIRM`, `CONFIRMED`, and `SEND_ERR` must be supported by the OLTP. These verbs implement APPC `SYNCLEVEL 1`.

  All resources controlled by an OLTP that can be updated by transaction programs invoked through the gateway must be defined as recoverable resources to the OLTP and host system if `COMMIT`/`ROLLBACK` capability is required for those resources. For example, a VSAM file updated by a CICS transaction must be defined to CICS as a recoverable file for `COMMIT`/`ROLLBACK` to control the updates.

  The gateway is compatible with all supported releases of SNA-enabled products such as CICS, IMS/TM, IDMS and z/OS.

  **Note:**

  For a list of known restrictions, read the "[Known Restrictions](appc-gateway-release-info.md)" section before proceeding with the installation of the gateway.

- OLTP for TCP/IP

  IMS/TM: Release 7.1 or later is required, as well as any APARs (patches) listed in the IBM IMS Connect Guide and Reference.

  IMS Connect: Release 1.2 or higher is required.
