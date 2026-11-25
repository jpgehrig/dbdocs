The following topics describe the system requirements of the gateway.

- Hardware Requirements

- Software Requirements

### Hardware Requirements

The hardware requirements for this release of the gateway on Microsoft Windows are described in the following sections.

#### Processor Requirements

Refer to the [Oracle Database Installation Guide for Microsoft Windows](../ntdbi/index.md) and to the certification matrix on My Oracle Support for the most up-to-date list of certified hardware platforms and operating system version requirements to operate the gateway for your system. The My Oracle Support Web site can be found at:

<https://support.oracle.com>

The Oracle Database Gateway for APPC requires an Intel or 100% compatible personal computer based on a Pentium processor that can run Microsoft Windows 2000 and higher.

#### Memory Requirements

For most installations, Oracle recommends a minimum of 256 MB of real memory for the system running the Oracle Database Gateway for APPC.

Each concurrent use of the gateway requires a minimum of 10 MB.

The following factors affect the virtual memory requirements of the gateway server process:

- number of concurrent gateway connections opened by each user;

- number of data items being transferred between the gateway and the RTP;

- additional factors such as configured network buffer size;

- the Oracle Net protocol adapters that were included during the gateway installation.

#### Network Attachment Requirements

The gateway requires any network attachment supported by either the SNA Server for your platform or the TCP/IP Networking Facility for TCP/IP communication.

However, if you are using solely the new TCP/IP support for IMS Connect feature, you will not need an SNA package. The Windows operating system comes with TCP/IP installed, you will need to configure it.

#### Disk Space Requirements

The gateway disk space requirement is a minimum of 700 MB.

### Software Requirements

The system software configuration described in these requirements is supported by Oracle, provided that the underlying system software products are supported by their respective vendors. Verify the latest support status with your system software vendors.

#### Operating System Requirements

Refer to the [Oracle Database Installation Guide for Microsoft Windows ](../ntdbi/index.md)and to the certification matrix on My Oracle Support for the most up-to-date list of certified operating system version requirements to operate the gateway for your Windows Intel system. The My Oracle Support Web site can be found at:

[`https://support.oracle.com`](https://support.oracle.com)

#### Communication Protocol Requirements

A Microsoft Host Integration Server 2000 is required, or IBM Communication Server V6.1.1 (or higher) for Windows. In this document, either of these communications servers will be referred to generically as SNA Server.

**Note:**

If you choose to use TCP/IP support for IMS Connect as your communications protocol, then you will not need to use an SNA Server. Your operating system comes with a TCP/IP protocol automatically installed. If you choose to use the TCP/IP protocol, you will need to configure it to work properly with the gateway then instructions for doing so are located in [Gateway Configuration Using TCP/IP Communication Protocol](configure-appc-gateway-using-tcp-ip.md).

#### Oracle Database Requirements

The Microsoft Windows platform requires that the Oracle database be up to date with the latest patch set for supported Oracle database releases.

#### Oracle Networking Product Requirements

Oracle Net is automatically installed on the system where the Oracle database is installed and on the system where the gateway is installed. Refer to [Configuring Your Oracle Network](appc-gateway-configure-oracle-network.md) in this guide for configuration information. Additionally, you may refer to the [Oracle Database Net Services Administrator's Guide](../netag/index.md).

#### IBM Mainframe Requirements

In addition to the other software requirements of the gateway and your particular platform, the following list outlines other requirements necessary on the IBM mainframe:

##### OLTP for SNA

The OLTP must support mapped APPC conversations. If the OLTP transaction programs to be executed through the gateway perform database updates, then the APPC verbs `CONFIRM`, `CONFIRMED`, and `SEND_ERR` must be supported by the OLTP. These verbs implement APPC `SYNCLEVEL 1`.

All resources controlled by an OLTP that can be updated by transaction programs invoked through the gateway must be defined as recoverable resources to the OLTP and host system if `COMMIT`/`ROLLBACK` capability is required for those resources. For example, a VSAM file updated by a CICS transaction must be defined to CICS as a recoverable file for `COMMIT`/`ROLLBACK` to control the updates.

The gateway is compatible with all supported releases of SNA-enabled products such as CICS, IMS/TM, and z/OS.

Important: For a list of known restrictions, read the "[Known Restrictions](appc-gateway-release-information.md)" section[Known Restrictions](appc-gateway-release-information.md) before proceeding with installation of the gateway.

##### OLTP for TCP/IP

IMS/TM: Release 7.1 or later is required, as well as any APARs (patches) listed in the IBM IMS Connect Guide and Reference.

IMS Connect: Release 1.2 or higher is required.
