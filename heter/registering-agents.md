Registration is an operation through which Oracle stores information about an agent in the data dictionary.

Agents do not have to be registered. If an agent is not registered, Oracle stores information about the agent in memory instead of in the data dictionary. When a session involving an agent terminates, this information ceases to be available.

Self-registration is an operation in which a database administrator sets an initialization parameter that lets the agent automatically upload information into the data dictionary. Self-registration occurs when the `HS_AUTOREGISTER` initialization parameter is set to `TRUE` (default).

**Note:**

`HS_AUTOREGISTER` is an Oracle Database initialization parameter that you set in the `init.ora` file; it is not a Heterogeneous Services initialization parameter that is set in the gateway initialization file.

- Enabling Agent Self-Registration
  To ensure correct operation when using heterogeneous database links, agent self-registration automates updates to Heterogeneous Services (HS) configuration data that describe agents on remote hosts.
- Disabling Agent Self-Registration
  Set the `HS_AUTOREGISTER` initialization parameter to `FALSE` to disable agent self-registration.

**Parent topic:** [Using Heterogeneous Services Agents](using-heterogeneous-services-agents.md)

### Enabling Agent Self-Registration

To ensure correct operation when using heterogeneous database links, agent self-registration automates updates to Heterogeneous Services (HS) configuration data that describe agents on remote hosts.

Agent self-registration is the default behavior. If you do not want to use the agent self-registration feature, set the `HS_AUTOREGISTER` initialization parameter to `FALSE`.

Both Oracle Database and the agent rely on three types of information to configure and control the operation of the Heterogeneous Services connection. These three sets of information are collectively called HS configuration data:

Table 4-1 Agent Self-Registration

| Heterogeneous Services Configuration Data        | Description                                                                                                        |
|:-------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------|
| Heterogeneous Services initialization parameters | Provide control over various connection-specific details of operation.                                             |
| Capability definitions                           | Identify details like SQL language features supported by the non-Oracle data source.                               |
| Data dictionary translations                     | Map references to Oracle data dictionary tables and views into equivalents specific to the non-Oracle data source. |

- Using Agent Self-Registration to Avoid Configuration Mismatches
  Heterogeneous Services (HS) configuration data is stored in the data dictionary of the Oracle database server.
- Understanding Agent Self-Registration
  These sections describe Heterogeneous Services agent self-registration.
- Specifying HS_AUTOREGISTER
  The `HS_AUTOREGISTER` Oracle database server initialization parameter enables or disables automatic self-registration of Heterogeneous Services agents.

**Related Topics**

- Specifying HS_AUTOREGISTER

**Parent topic:** Registering Agents

#### Using Agent Self-Registration to Avoid Configuration Mismatches

Heterogeneous Services (HS) configuration data is stored in the data dictionary of the Oracle database server.

Because the agent can be remote and can therefore be administered separately, several circumstances can lead to configuration mismatches between servers and agents. For example:

- An agent can be newly installed on a separate computer so that the Oracle database server has no Heterogeneous Services data dictionary content to represent the agent's Heterogeneous Services configuration data.

- An Oracle database server can be newly installed and lack the necessary Heterogeneous Services configuration data for existing agents and non-Oracle data stores.

- A non-Oracle instance can be upgraded from an older version to a newer version, requiring modification of the Heterogeneous Services configuration data.

- A Heterogeneous Services agent at a remote site can be upgraded to a new version or patched, requiring modification of the Heterogeneous Services configuration data.

- A database administrator (DBA) at the non-Oracle site can change the agent setup, possibly for tuning or testing purposes, in a manner which affects Heterogeneous Services configuration data.

Agent self-registration permits successful operation of Heterogeneous Services in all these scenarios. Specifically, agent self-registration enhances interoperability between any Oracle Database and any Heterogeneous Services agent (if each is version 8.0.3 or higher). The basic mechanism for this functionality is the ability to upload Heterogeneous Services configuration data from agents to servers.

Self-registration provides automatic updating of Heterogeneous Services configuration data residing in the Oracle database data dictionary. This update ensures that the agent self-registration uploads need to be done only once, on the initial use of a previously unregistered agent. Instance information is uploaded on each connection, not stored in the server data dictionary.

**Parent topic:** Enabling Agent Self-Registration

#### Understanding Agent Self-Registration

These sections describe Heterogeneous Services agent self-registration.

The Heterogeneous Services agent self-registration feature performs the following tasks:

- Identifies the agent and the non-Oracle data store to the Oracle database server

- Permits agents to define Heterogeneous Services initialization parameters for use both by the agent and connected Oracle database servers

- Uploads capability definitions and data dictionary translations, if available, from a Heterogeneous Services agent during connection initialization

  **Note:**

  The upload of class information occurs only when the class is undefined in the server data dictionary. Similarly, instance information is uploaded only if the instance is undefined in the server data dictionary.

The information required for agent self-registration is accessed in the server data dictionary by using the agent-supplied `FDS_CLASS` and `FDS_CLASS_VERSION` names.

- FDS_CLASS and FDS_CLASS_VERSION
  Oracle Database or third-party vendors define `FDS_CLASS` and `FDS_CLASS_VERSION` for each individual Heterogeneous Services agent and version.
- FDS_INST_NAME
  Instance-specific information can be stored in the server data dictionary. The instance name, `FDS_INST_NAME`, is configured by the database administrator (DBA) who administers the agent.

**Related Topics**

- [Heterogeneous Services Data Dictionary Views](heterogeneous-services-data-dictionary-views.md)

**Parent topic:** Enabling Agent Self-Registration

##### FDS_CLASS and FDS_CLASS_VERSION

Oracle Database or third-party vendors define `FDS_CLASS` and `FDS_CLASS_VERSION` for each individual Heterogeneous Services agent and version.

Heterogeneous Services concatenates these names to form `FDS_CLASS_NAME`, which is used as a primary key to access class information in the server data dictionary.

`FDS_CLASS` should specify the type of non-Oracle data store to be accessed and `FDS_CLASS_VERSION` should specify a version number for both the non-Oracle data store and the agent that connects to it. When any component of an agent changes, `FDS_CLASS_VERSION` must also change to uniquely identify the new release. This information is uploaded when you initialize each connection.

**Parent topic:** Understanding Agent Self-Registration

##### FDS_INST_NAME

Instance-specific information can be stored in the server data dictionary. The instance name, `FDS_INST_NAME`, is configured by the database administrator (DBA) who administers the agent.

How the DBA performs this configuration depends on the specific agent in use.

The Oracle database server uses `FDS_INST_NAME` to look up instance-specific configuration information in its data dictionary. Oracle uses the value as a primary key for columns of the same name in these views:

- `FDS_INST_INIT`

- `FDS_INST_CAPS`

- `FDS_INST_DD`

Server data dictionary accesses that use `FDS_INST_NAME` also use `FDS_CLASS_NAME` to uniquely identify configuration information rows. For example, if you port a database from class Sybase816 to class Sybase817, both databases can simultaneously operate with instance name `SCOTT` and use separate sets of configuration information.

Unlike class information, instance information is not automatically self-registered in the server data dictionary:

- If available, instance information is always uploaded by the agent. However, it is never stored in the server data dictionary. Instead, the information is kept in memory and it is only valid for that connection.

- If the server data dictionary contains instance information, it represents the DBA's defined setup details which correspond to the instance configuration. Data dictionary defined instance information takes precedence over class information. However, uploaded instance information takes precedence over data dictionary defined instance information.

**Parent topic:** Understanding Agent Self-Registration

#### Specifying HS_AUTOREGISTER

The `HS_AUTOREGISTER` Oracle database server initialization parameter enables or disables automatic self-registration of Heterogeneous Services agents.

Note that this parameter is specified in the Oracle initialization parameter file, not the agent initialization file. For example, you can set the parameter as follows:

    HS_AUTOREGISTER = TRUE

When set to `TRUE`, the agent uploads information describing a previously unknown agent class or a new agent version into the server's data dictionary.

Oracle recommends that you use the default value for this parameter (`TRUE`), which ensures that the server's data dictionary content always correctly represents definitions of class capabilities and data dictionary translations as used in Heterogeneous Services connections.

**See Also:**

[Oracle Database Reference ](../refrn/HS_AUTOREGISTER.md)for a description of this parameter.

**Parent topic:** Enabling Agent Self-Registration

### Disabling Agent Self-Registration

Set the `HS_AUTOREGISTER` initialization parameter to `FALSE` to disable agent self-registration.

To disable agent self-registration, set the `HS_AUTOREGISTER` initialization parameter as follows:

    HS_AUTOREGISTER = FALSE

Disabling agent self-registration means that agent information is not stored in the data dictionary. Consequently, the Heterogeneous Services data dictionary views are not useful sources of information. Nevertheless, the Oracle server still requires information about the class and instance of each agent. If agent self-registration is disabled, the server stores this information in local memory.

**Parent topic:** Registering Agents
