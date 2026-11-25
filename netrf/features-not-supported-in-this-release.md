## A Features Not Supported in this Release

This appendix describes features no longer supported by Oracle Net Services.

- Overview of Unsupported Features
  This section describes the features and the configuration file that are no longer being supported in Oracle Database.
- Unsupported Parameters
  This section describes the unsupported or obsolete parameters.
- Unsupported Control Utility Commands
  This section describes the control utility commands not supported by this release.
- Unsupported or Deprecated Protocols
  This section describes the protocols not supported or deprecated since Oracle Database 12c.

**Parent topic:** [Appendices](appendixes.md)

### A.1 Overview of Unsupported Features

This section describes the features and the configuration file that are no longer being supported in Oracle Database.

- Oracle Net Connection Pooling
  In Oracle Database 12c Release 2 (12.2), Oracle Net connection pooling is no longer supported
- Oracle Names
  Oracle Names is not supported in this release.
- Oracle Net Listener Password
  In Oracle Database 12c Release 2 (12.2), the Oracle Net Listener password feature is no longer supported.

**Parent topic:** Features Not Supported in this Release

#### A.1.1 Oracle Net Connection Pooling

In Oracle Database 12c Release 2 (12.2), Oracle Net connection pooling is no longer supported

##### Deprecation of Oracle Net Connection Pooling

It was deprecated in Oracle Database 11g release. Refer to My Oracle Support note 1469466.1.

**Parent topic:** Overview of Unsupported Features

#### A.1.2 Oracle Names

Oracle Names is not supported in this release.

##### Naming Method

Oracle Names has not been supported as a naming method since Oracle Database 11g. You must migrate to directory naming.

**Parent topic:** Overview of Unsupported Features

#### A.1.3 Oracle Net Listener Password

In Oracle Database 12c Release 2 (12.2), the Oracle Net Listener password feature is no longer supported.

##### Oracle Net Listener Password Support

In Oracle Database 12c Release 2 (12.2), the Oracle Net Listener password feature is no longer supported. This does not cause a loss of security because authentication is enforced through local operating system authentication.

**Parent topic:** Overview of Unsupported Features

### A.2 Unsupported Parameters

This section describes the unsupported or obsolete parameters.

Table A-1 Unsupported Networking Parameters

| File         | Parameter                      | Description                                                                                                                                                                                       | Last Supported Release |
|:-------------|:-------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------|
| `sqlnet.ora` | `SQLNET.KERBEROS5_CONF_MIT`    | This parameter was used to specify that MIT Kerberos configuration format was used. Starting with Oracle Database 12c Release 2 (12.2), only the current MIT Kerberos configuration is supported. | 11.2                   |
| `sqlnet.ora` | `SQLNET.ALLOWED_LOGON_VERSION` | This parameter has been divided into `SQLNET.ALLOWED_LOGON_VERSION_CLIENT` and `SQLNET.ALLOWED_LOGON_VERSION_SERVER`.                                                                             | 11.2                   |

**Parent topic:** Features Not Supported in this Release

### A.3 Unsupported Control Utility Commands

This section describes the control utility commands not supported by this release.

Table A-2 Unsupported Network Control Utility Commands

| Control Utility              | Commands     | Description                          | Last Supported Release |
|:-----------------------------|:-------------|:-------------------------------------|:-----------------------|
| Oracle Names Control Utility | All commands | Oracle Names is no longer supported. | 9.2                    |

**Parent topic:** Features Not Supported in this Release

### A.4 Unsupported or Deprecated Protocols

This section describes the protocols not supported or deprecated since Oracle Database 12c.

Table A-3 Unsupported Protocols

| Protocol                                                 | Description                                                                                                                                                                                                                                                               | Last Supported Release |
|:---------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------|
| NT LAN Manager (NTLM) protocol for domain authentication | NTLM domain authentication has been deprecated from the Oracle Windows adapter. Only Kerberos authentication is used for the NTS adapter.<br>NTLM is still used for local user authentication, as well as in the case in which the database service runs as a local user. | 11.2                   |

**Parent topic:** Features Not Supported in this Release
