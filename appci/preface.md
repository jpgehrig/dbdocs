The Oracle Database Gateway for APPC provides Oracle applications with seamless access to IBM mainframe data and services through Remote Procedure Call (RPC) processing.

The UNIX platforms supported by this gateway release are:

- IBM AIX on POWER Systems (64-Bit)

- Linux x86-64

- Oracle Solaris on SPARC (64-Bit)

Refer to the [Oracle Database Installation Guide](../install-and-upgrade.md) and to the certification matrix on the My Oracle Support Web site for the most up-to-date list of certified hardware platforms and operating system versions. The My Oracle Support Web site is available at

[`https://support.oracle.com`](https://support.oracle.com)

### Intended Audience

Read this guide if you are responsible for tasks such as:

- Determining hardware and software requirements.

- Installing, configuring, or administering an Oracle Database Gateway for APPC.

- Developing applications that access remote host databases through the gateway using either the SNA communication protocol or the TCP/IP for IMS Connect communication protocol.

- Determining security requirements.

- Determining and resolving problems.

Before using this guide to administer the gateway, you should understand the fundamentals of the operating system for your platform and Oracle Database Gateways.

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info> or visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs> if you are hearing impaired.

### Related Documents

The Oracle Database Gateway for APPC Installation and Configuration Guide for IBM AIX on POWER Systems (64-Bit), Linux x86-64, Oracle Solaris on SPARC (64-Bit), and HP-UX Itanium is included as part of your product shipment. Also included is:

- [Oracle Database Gateway for APPC User's Guide](../appug/index.md)

You might also need Oracle database and Oracle Net documentation. The following is a useful list of the Oracle publications that might be referenced in this guide:

- [Oracle Database Installation Guide](../install-and-upgrade.md)

- [Oracle Database Administrator's Guide](../admin/index.md)

- [Oracle Database Development Guide](../adfns/index.md)

- [Oracle Database Concepts](../cncpt/index.md)

- [Oracle Database Error Messages](../errmg/index.md)

- [Oracle Database Net Services Administrator's Guide](../netag/index.md)

- [Oracle Database PL/SQL Language Reference](../lnpls/index.md)

- [Oracle Database Net Services Administrator's Guide](../netag/index.md)

- [Oracle Database Heterogeneous Connectivity User's Guide](../heter/index.md)

- [Oracle Call Interface Programmer's Guide](../lnoci/index.md)

In addition to your Oracle documentation, ensure that you have appropriate documentation for your platform, for your operating system and for your communications packages. You may find IMS Connect Guide and Reference IBM documentation useful.

**Note:**

For other Operating System and SNA communication package and TCP/IP package references, refer to the appropriate vendor documentation for your system

### Conventions

The following text conventions are used in this document:

| Convention  | Meaning                                                                                                                                |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| boldface    | Boldface type indicates graphical user interface elements associated with an action, or terms defined in text or the glossary.         |
| italic      | Italic type indicates book titles, emphasis, or placeholder variables for which you supply particular values.                          |
| `monospace` | Monospace type indicates commands within a paragraph, URLs, code in examples, text that appears on the screen, or text that you enter. |

### Command Syntax

UNIX command syntax appears in `monospace` font. The dollar character (\$), number sign (#), or percent character (%) are UNIX command prompts. Do not enter them as part of the command. The following command syntax conventions are used in this guide:

| Convention       | Description                                                                                                                                                                                                                                                                                                 |
|:-----------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| backslash \\     | A backslash is the UNIX command continuation character. It is used in command examples that are too long to fit on a single line. Enter the command as displayed (with a backslash) or enter it on a single line without a backslash:<br>`dd if=/dev/rdsk/c0t1d0s6 of=/dev/rst0 bs=10b \ `<br>`count=10000` |
| braces { }       | Braces indicate required items:<br>`.DEFINE {macro1}`                                                                                                                                                                                                                                                       |
| brackets \[ \]   | Brackets indicate optional items:<br>`cvtcrt termname [outfile]`                                                                                                                                                                                                                                            |
| ellipses ...     | Ellipses indicate an arbitrary number of similar items:<br>`CHKVAL fieldname value1 value2 ... valueN`                                                                                                                                                                                                      |
| italics          | Italic type indicates a variable. Substitute a value for the variable:<br>`library_name`                                                                                                                                                                                                                    |
| vertical line \| | A vertical line indicates a choice within braces or brackets:<br>`FILE filesize [K|M]`                                                                                                                                                                                                                      |
