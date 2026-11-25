This method flushes the information passed to it as an argument.

### Declaration

    // C#
    public override void ProcessEventFlush(WebEventBufferFlushInfo flushEvent);

### Parameters

- `flushEvent`

  The `WebEventBufferFlushInfo` object that contains a collection of buffered Web events.

### Remarks

This method is called by ASP.NET applications to flush all events into Oracle Database.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleWebEventProvider Class](OracleWebEventProviderClass.md)

- [OracleWebEventProvider Members](OracleWebEventProviderMembers.md)
