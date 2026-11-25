## C LDAP Schema for Oracle Net Services

This appendix describes the Oracle schema object classes and attributes defined in the directory server for Oracle Net Services objects. It does not describe object classes and attributes reserved for future functionality or used by other Oracle products.

- Structural Object Classes
  The Oracle schema supports the structural object classes for Oracle Net directory naming lookups.
- Attributes
  It lists the attributes used for the object classes. This list is subject to change.

**Parent topic:** [Appendices](appendixes.md)

### C.1 Structural Object Classes

The Oracle schema supports the structural object classes for Oracle Net directory naming lookups.

Table C-1 Oracle Net Structural Object Classes

| Object Class           | Attributes                                                                                                                                                                                                      | Description                                                                                                                |
|:-----------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------|
| orclDBServer           | • orclNetDescName<br>• orclVersion                                                                                                                                                                              | Defines the attributes for database service entries.                                                                       |
| orclNetAddress         | • orclNetAddressString<br>• orclNetProtocol<br>• orclVersion                                                                                                                                                    | Specifies a listener protocol address.                                                                                     |
| orclNetAddressAux1     | • orclNetHostname                                                                                                                                                                                               | Specifies an auxiliary object class to add attributes to an orclNetAddress entry.                                          |
| orclNetAddressList     | • orclNetAddrList<br>• orclNetFailover<br>• orclNetLoadBalance<br>• orclNetSourceRoute<br>• orclVersion                                                                                                         | Specifies a list of protocol addresses.                                                                                    |
| orclNetDescription     | • orclNetAddrList<br>• orclNetInstanceName<br>• orclNetConnParamList<br>• orclNetFailover<br>• orclNetLoadBalance<br>• orclNetSdu<br>• orclNetServiceName<br>• orclNetSourceRoute<br>• orclSid<br>• orclVersion | Specifies a connect descriptor containing the protocol address of the listener and the connect information to the service. |
| orclNetDescriptionAux1 | • orclNetSendBufSize<br>• orclNetReceiveBufSize<br>• orclNetFailoverModeString<br>• orclNetInstanceRole                                                                                                         | Specifies auxiliary object class to add attributes to an orclNetDescription entry.                                         |
| orclNetDescriptionList | • orclNetDescList<br>• orclVersion                                                                                                                                                                              | Specifies a list of connect descriptors.                                                                                   |
| orclNetService         | • orclNetDescName<br>• orclVersion                                                                                                                                                                              | Defines the attributes for network service name entries.                                                                   |
| orclNetServiceAlias    | • orclNetDescName<br>• orclVersion                                                                                                                                                                              | Defines the attributes for network service alias entries.                                                                  |

**Parent topic:** LDAP Schema for Oracle Net Services

### C.2 Attributes

It lists the attributes used for the object classes. This list is subject to change.

Table C-2 LDAP Schema Attributes for Oracle Net Services

| Attribute                   | Description                                                                                                                                                                                                                   |
|:----------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `orclCommonContextMap`      | Allows the mapping of more than one default Oracle Context in the directory server.                                                                                                                                           |
| `orclNetAddrList`           | Identifies one or more listener protocol addresses.                                                                                                                                                                           |
| `orclNetAddressString`      | Defines a listener protocol address.                                                                                                                                                                                          |
| `orclNetConnParamList`      | Placeholder for connect data parameters.                                                                                                                                                                                      |
| `orclNetDescList`           | Identifies one or more connect descriptors.                                                                                                                                                                                   |
| `orclNetDescName`           | Identifies a connect descriptor or a list of connect descriptors.                                                                                                                                                             |
| `orclNetFailover`           | Turns connect-time failover on for a protocol address list.                                                                                                                                                                   |
| `orclNetFailoverModeString` | Instructs Oracle Net to fail over to a different listener if the first listener fails during runtime. Depending on the configuration, session or any `SELECT` statements that were in progress are automatically failed over. |
| `orclNetHostname`           | Specifies the host name.                                                                                                                                                                                                      |
| `orclNetInstanceName`       | Specifies the instance name to access.                                                                                                                                                                                        |
| `orclNetInstanceRole`       | Specifies a connection to the primary or secondary instance of an Oracle Real Application Clusters (Oracle RAC) configuration.                                                                                                |
| `orclNetLoadBalance`        | Turns client load balancing on for a protocol address list.                                                                                                                                                                   |
| `orclNetProtocol`           | Identifies the protocol used in the `orclAddressString` attribute.                                                                                                                                                            |
| `orclNetReceiveBufSize`     | Specifies the buffer space limit for receive operations of sessions.                                                                                                                                                          |
| `orclNetSdu`                | Specifies the session data unit (SDU) size.                                                                                                                                                                                   |
| `orclNetSendBufSize`        | Specifies the buffer space limit for send operations of sessions.                                                                                                                                                             |
| `orclNetServiceName`        | Specifies the database service name in the `CONNECT_DATA` portion.                                                                                                                                                            |
| `orclNetSourceRoute`        | Instructs Oracle Net to use each address in order until the destination is reached.                                                                                                                                           |
| `orclSid`                   | Specifies the Oracle system identifier (SID) in the `CONNECT_DATA` portion of a connection descriptor.                                                                                                                        |
| `orclVersion`               | Specifies the version of software used to create the entry.                                                                                                                                                                   |

**Parent topic:** LDAP Schema for Oracle Net Services
