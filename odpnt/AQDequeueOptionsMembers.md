`OracleAQDequeueOptions` members are listed in the following tables.

### OracleAQDequeueOptions Constructor

The `OracleAQDequeueOptions` constructor is listed in Table 12-4.

Table 12-4 OracleAQDequeueOptions Constructor

| Constructor                                                          | Description                                                       |
|:---------------------------------------------------------------------|:------------------------------------------------------------------|
| [OracleAQDequeueOptions Constructor](AQDequeueOptionsConstructor.md) | Instantiates a new instance of the `OracleAQDequeueOptions` class |

### OracleAQDequeueOptions Properties

`OracleAQDequeueOptions` properties are listed in Table 12-5.

Table 12-5 OracleAQDequeueOptions Properties

| Property                                                        | Description                                                                                                |
|:----------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------|
| [ConsumerName](AQDequeueOptionsConsumerName.md)                 | Specifies the consumer name for which to dequeue the message                                               |
| [Correlation](AQDequeueOptionsCorrelation.md)                   | Specifies the correlation identifier of the message to be dequeued                                         |
| [DeliveryMode](AQDequeueOptionsDeliveryMode.md)                 | Specifies the expected delivery mode of the message being dequeued                                         |
| [DequeueMode](AQDequeueOptionsDequeueMode.md)                   | Specifies the locking behavior associated with the dequeue operation                                       |
| [MessageId](AQDequeueOptionsMessageId.md)                       | Specifies the message identifier of the message to be dequeued                                             |
| [NavigationMode](AQDequeueOptionsNavigationMode.md)             | Specifies the position of the message that will be retrieved                                               |
| [ProviderSpecificType](AQDequeueOptionsProviderSpecificType.md) | Specifies whether the payload of a dequeued message is provided as an ODP.NET specific type or a .NET type |
| [Visibility](AQDequeueOptionsVisibility.md)                     | Specifies whether or not the new message is dequeued as part of the current transaction                    |
| [Wait](AQDequeueOptionsWait.md)                                 | Specifies the wait time, in seconds, for a message that matches the search criteria                        |

### OracleAQDequeueOptions Public Methods

`OracleAQDequeueOptions` public methods are listed in Table 12-6.

Table 12-6 OracleAQDequeueOptions Public Methods

| Public Method                     | Description                                           |
|:----------------------------------|:------------------------------------------------------|
| [Clone](AQDequeueOptionsClone.md) | Creates a copy of an `OracleAQDequeueOptions` object. |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQDequeueOptions Class](OracleAQDequeueOptionsClass.md)
