The Oracle Database Gateway for APPC provides Oracle applications with seamless access to IBM mainframe data and services through Remote Procedure Call (RPC) processing.

Refer to the [Oracle Database Installation Guide](../install-and-upgrade.md) for Microsoft Windows and to the certification matrix on My Oracle Support for the most up-to-date list of certified hardware platforms and operating system versions. The My Oracle Support Web site can be found at:

[`https://support.oracle.com`](https://support.oracle.com)

### Audience

Read this guide if you are responsible for tasks such as:

- determining hardware and software requirements

- installing, configuring, or administering an Oracle Database Gateway for APPC

- developing applications that access remote host databases through the gateway using either the SNA communication protocol or the TCP/IP for IMS Connect communication protocol.

- determining security requirements

- determining and resolving problems

Before using this guide to administer the gateway, you should understand the fundamentals of the Windows operating system, SNA Server, the Database Gateways, PL/SQL and the Oracle database .

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info> or visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs> if you are hearing impaired.

### Related Documents

The Oracle Database Gateway for APPC Installation and Configuration Guide for Microsoft Windows is included as a part of your product shipment. Also included is:

- [Oracle Database Gateway for APPC User's Guide](../appug/index.md)

You might also need Oracle database and Oracle Net documentation. The following is a useful list of the Oracle publications that may be referenced in this book:

- [Oracle Database Installation Guide for Microsoft Windows](../ntdbi/index.md)

- [Oracle Database Administrator's Guide](../admin/index.md)

- [Oracle Database Development Guide](../adfns/index.md)

- [Oracle Database Concepts](../cncpt/index.md)

- [Oracle Database Error Messages](../errmg/index.md)

- [Oracle Database Net Services Administrator's Guide](../netag/index.md)

- [Oracle Database PL/SQL Language Reference](../lnpls/index.md)

- [Oracle Call Interface Programmer's Guide](../lnoci/index.md)

In addition to the Oracle documentation, ensure that you have required documentation for your platform, for your operating system, and for your communications packages.

The following IBM documentation may be useful:

- IMS Connect Guide and Reference

The title of the IBM publication was accurate at the time of the publication of this guide. Titles and structure of these documents are subject to change. For other operating system, SNA communication package, and TCP/IP package references, refer to the appropriate vendor documentation for your system.

### Conventions

Examples of input and output for the gateway and Oracle environment are shown in a special font:

    C:\> mkdir \ORACLE\your_name

All output is shown as it appears. For input, the list of conventions and their meanings are as follows:

- `example tex`t: Words or phrases, such as `mkdir` and `ORACLE`, must be entered exactly as spelled and in the letter case shown. In this example, `mkdir` must be entered in lowercase letters and `ORACLE` in uppercase letters.

- italic text: Italicized uppercase or lowercase, such as your_name, indicates that you must substitute a word or phrase, such as the actual directory name.

- `BOLD text` or `bold italic TEXT`: Bold words or phrases refer to a file or directory structure, such as a directory, path, or file ID.

- ... : Ellipses indicate that the preceding item can be repeated. You can enter an arbitrary number of similar items.

- { }: Curly braces indicate that one of the enclosed arguments is required. Do not enter the braces themselves.

- \|: Vertical lines separate choices.

- \[ \]: Square brackets enclose optional clauses from which you can choose one or none. Do not enter the brackets themselves.

Other punctuation, such as commas, quotation marks or the pipe symbol (\|) must be entered as shown unless otherwise specified. Directory names, file IDs and so on appear in the required letter case in examples. The same convention is used when these names appear in text, and the names are highlighted in bold. The use of italics indicates that those portions of a file ID that appear in italics can vary.

Gateway commands, file IDs reserved words, MS-DOS commands, keywords and environment variables appear in uppercase in examples and text. Reserved words must always be entered as shown; they have reserved meanings within the Oracle system.

#### SQL\*Plus Prompts

The SQL\*Plus prompt, `SQL>`, appears in SQL statement and SQL\*Plus command examples. Enter your response at the prompt. Do not enter the text of the prompt, `SQL>`, in your response.

#### MS-DOS Prompts

The MS-DOS prompt, `C:\>`, appears in MS-DOS command examples. Enter your response at the prompt. Do not enter the text of the prompt, `C:\>`, in your response.

#### PGAU Prompts

The PGAU prompt, `PGAU>`, appears in PGAU command examples. Enter your response at the prompt. Do not enter the text of the prompt, `PGAU>`, in your response.

#### Directory Names

Throughout this document, there are references to the directories in which product-related files reside. `%ORACLE_HOME%` is used to represent the Oracle home directory. This is the default location for Oracle products. If you have installed into a location other than `%ORACLE_HOME%`, replace all references to `%ORACLE_HOME%` with the drive and path specification you have used.
