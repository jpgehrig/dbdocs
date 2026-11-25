Heterogeneous Services components consist of generic code and must be configured to work with many different non-Oracle systems.

Each gateway has configuration information stored in the driver module. The information is uploaded to the Oracle database server immediately after the connection to the gateway is established. The configuration information includes:

- Data Dictionary Translation Views
  Data dictionary translations are views on non-Oracle data dictionary tables.
- Heterogeneous Services Initialization Parameters
  Heterogeneous Services initialization parameters serve two functions described here.
- Capabilities
  Capabilities tell Heterogeneous Services about the limitations of the non-Oracle system (such as what types of SQL statements are supported) and how to map Oracle data types and SQL expressions to their equivalents in the non-Oracle system.

**Parent topic:** [The Role of the Heterogeneous Services Component](heterogeneous-services-role.md)

### Data Dictionary Translation Views

Data dictionary translations are views on non-Oracle data dictionary tables.

These views help Heterogeneous Services translate references to Oracle data dictionary tables into queries that can retrieve the equivalent information from the non-Oracle data dictionary.

**Parent topic:** Heterogeneous Services Configuration Information

### Heterogeneous Services Initialization Parameters

Heterogeneous Services initialization parameters serve two functions described here.

- They give you a means of fine-tuning the gateway to optimize performance and memory utilization for the gateway and the Heterogeneous Services component.

- They enable you to inform the gateway (and, thereby, Heterogeneous Services) how the non-Oracle system is configured (for example, the language used by the non-Oracle system). Initialization parameters provide information to Heterogeneous Services about the configurable properties of the non-Oracle system.

You can examine the Heterogeneous Services initialization parameters for a session by querying the view `V$HS_PARAMETER`. You can set initialization parameters in gateway initialization files.

**Parent topic:** Heterogeneous Services Configuration Information

### Capabilities

Capabilities tell Heterogeneous Services about the limitations of the non-Oracle system (such as what types of SQL statements are supported) and how to map Oracle data types and SQL expressions to their equivalents in the non-Oracle system.

Capabilities tell Heterogeneous Services about the non-configurable properties of the non-Oracle system. You cannot modify capabilities.

**Parent topic:** Heterogeneous Services Configuration Information
