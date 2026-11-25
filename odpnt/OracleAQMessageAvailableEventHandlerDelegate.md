The `OracleAQMessageAvailableEventHandler` delegate represents the signature of the method that handles the `OracleAQQueue.MessageAvailable` event.

### Declaration

    // C#
    public delegate void OracleAQMessageAvailableEventHandler (object
      sender,OracleAQMessageAvailableEventArg eventArgs);

### Parameters

- `sender`

  The source of the event.

- `eventArgs`

  The `OracleAQMessageAvailableEventArgs` object that contains the event data.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- "[MessageAvailable Event](AQQueueMessageAvailableEvent.md)"
