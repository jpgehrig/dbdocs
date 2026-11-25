This constructor instantiates a new instance of the `OracleCacheDependency` class.

### Declaration

    // C#
    public OracleCacheDependency(OracleCommand cmd);

### Parameters

- `cmd`

  The `OracleCommand` object has the command text on which the change notification is based.

### Remarks

When this constructor is invoked, the `OracleCacheDependency` object is instantiated and the `OracleCommand` object is configured for change notification. When the supplied `OracleCommand` object is executed by the application, the change notification is registered and the `OracleCacheDependency` instance is notified when changes are detected on the server side.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleCacheDependency Class](OracleCacheDependencyClass.md)

- [OracleCacheDependency Members](OracleCacheDependencyMembers.md)
