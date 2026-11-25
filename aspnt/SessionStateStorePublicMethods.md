The `OracleSessionStateStore` public methods are listed in Table 5-5.

Table 5-5 OracleSessionStateStore Public Methods

| Public Methods                                                               | Description                                                                                                     |
|:-----------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------|
| [CreateNewStoreData](SessionStateStoreCreateNewStoreData.md)                 | Creates a new `SessionStateStoreData` object for the current request                                            |
| [CreateUninitializedItem](SessionStateStoreCreateUninitializedItem.md)       | Adds a new session state item to the database                                                                   |
| [Dispose](SessionStateStoreDispose.md)                                       | Releases all the resources for this instance                                                                    |
| [EndRequest](SessionStateStoreEndRequest.md)                                 | Allows the `OracleSessionStateStore` object to perform any cleanup that may be required for the current request |
| [GetItem](SessionStateStoreGetItem.md)                                       | Returns a read-only session item from the database                                                              |
| [GetItemExclusive](SessionStateStoreGetItemExclusive.md)                     | Locks and returns a session item from the database                                                              |
| [Initialize](SessionStateStoreInitialize.md)                                 | Initializes the provider with the property values specified in the ASP.NET application configuration file       |
| [InitializeRequest](SessionStateStoreInitializeRequest.md)                   | Performs any per-request initializations that the `OracleSessionStateStore` provider requires                   |
| [ReleaseItemExclusive](SessionStateStoreReleaseItemExclusive.md)             | Releases the lock on a session item in the database, if multiple attempts to retrieve the session item fail     |
| [RemoveItem](SessionStateStoreRemoveItem.md)                                 | Removes the specified session item from the database                                                            |
| [ResetItemTimeout](SessionStateStoreResetItemTimeout.md)                     | Resets the expiration date and timeout for a session item in the database                                       |
| [SetAndReleaseItemExclusive](SessionStateStoreSetAndReleaseItemExclusive.md) | Updates the session time information in the database with the specified session item and releases the lock      |
| [SetItemExpireCallback](SessionStateStoreSetItemExpireCallback.md)           | Returns a `false` value to indicate that callbacks for expired sessions are not supported                       |

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleSessionStateStore Class](OracleSessionStateStoreClass.md)

- [OracleSessionStateStore Members](OracleSessionStateStoreMembers.md)
