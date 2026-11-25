This method releases all resources.

### Declaration

    // C#
    public override void Shutdown();

### Remarks

This method is called by ASP.NET applications when the provider is unloaded. All the buffered events are first flushed into Oracle Database before the provider proceeds with shutdown.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleWebEventProvider Class](OracleWebEventProviderClass.md)

- [OracleWebEventProvider Members](OracleWebEventProviderMembers.md)
