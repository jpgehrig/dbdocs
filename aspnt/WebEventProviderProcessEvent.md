This method processes the event passed to it as an argument.

### Declaration

    // C#
    public override void ProcessEvent(WebBaseEvent eventRaised);

### Parameters

- `eventRaised`

  The `WebBaseEvent` object to be processed.

### Remarks

This method is called by ASP.NET applications to start event processing. If buffering is enabled, then the event is added to the buffer of events, otherwise, the event information is directly written into Oracle Database.

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleWebEventProvider Class](OracleWebEventProviderClass.md)

- [OracleWebEventProvider Members](OracleWebEventProviderMembers.md)
