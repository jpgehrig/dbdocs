This property specifies the Oracle user-defined type name if the parameter is a user-defined data type.

### Declaration

    // C#
    public string UdtTypeName {get; set;}

### Property Value

Name of the Oracle UDT.

### Remarks

The `UdtTypeName` property corresponds to the user-defined type name of the parameter. This property must always be specified if the parameter is a user-defined type. Note that when a custom object is provided as an input parameter value, it is converted to the Oracle UDT that is specified by the custom type mapping on the connection used to execute the command.The Oracle UDT specified by the custom type mapping and by the `OracleParamter.UdtTypeName` property differs if the application binds a custom object that represents a subtype of the parameter type.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameter Class](OracleParameterClass.md)

- [OracleParameter Members](ParameterMembers.md)
