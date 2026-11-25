`OracleWebEventProvider` members are listed in the following tables.

### OracleWebEventProvider Constructors

The `OracleWebEventProvider` constructor is listed in Table 7-1.

Table 7-1 OracleWebEventProvider Constructor

| Constructor                                                            | Description                                                       |
|:-----------------------------------------------------------------------|:------------------------------------------------------------------|
| [OracleWebEventProvider Constructors](WebEventProviderConstructors.md) | Instantiates a new instance of the `OracleWebEventProvider` class |

### OracleWebEventProvider Static Methods

`OracleWebEventProvider` static methods are listed in Table 7-2.

Table 7-2 OracleWebEventProvider Static Methods

| Static Methods    | Description                                 |
|:------------------|:--------------------------------------------|
| `Equals`          | Inherited from `System.Object` (Overloaded) |
| `ReferenceEquals` | Inherited from `System.Object`              |

### OracleWebEventProvider Public Properties

`OracleWebEventProvider` public properties are listed in Table 7-3.

Table 7-3 OracleWebEventProvider Public Properties

| Public Properties                                   | Description                                                                                                 |
|:----------------------------------------------------|:------------------------------------------------------------------------------------------------------------|
| `BufferMode`                                        | Inherited from `System.Web.Management.BufferedWebEventProvider`                                             |
| [CommandTimeout](WebEventProviderCommandTimeout.md) | Gets the number of seconds that the command is allowed to execute before it is terminated with an exception |
| `Description`                                       | Inherited from `System.Configuration.Provider.ProviderBase`                                                 |
| `Name`                                              | Inherited from `System.Configuration.Provider.ProviderBase`                                                 |
| `UseBuffering`                                      | Inherited from `System.Web.Management.BufferedWebEventProvider`                                             |

### OracleWebEventProvider Public Methods

`OracleWebEventProvider` public methods are listed in Table 7-4.

Table 7-4 OracleWebEventProvider Public Methods

| Public Method                                             | Description                                                                                                                        |
|:----------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------|
| [Initialize](WebEventProviderInitialize.md)               | Initializes the `OracleWebEventProvider` instance with the property values specified in the ASP.NET application configuration file |
| [ProcessEvent](WebEventProviderProcessEvent.md)           | Processes the event passed to it as an argument                                                                                    |
| [ProcessEventFlush](WebEventProviderProcessEventFlush.md) | Flushes the information passed to it as an argument                                                                                |
| [Shutdown](WebEventProviderShutdown.md)                   | Releases all resources                                                                                                             |
| `Flush`                                                   | Inherited from `System.BufferedWebEventProvider`                                                                                   |
| `Equals`(Overloaded)                                      | Inherited from `System.Object`                                                                                                     |
| `GetHashCode`                                             | Inherited from `System.Object`                                                                                                     |
| `GetType`                                                 | Inherited from `System.Object`                                                                                                     |
| `ToString`                                                | Inherited from `System.Object`                                                                                                     |

**See Also:**

- "[Oracle Providers for ASP.NET Assembly](IntroAssemblyandClassList.md)"

- [OracleWebEventProvider Class](OracleWebEventProviderClass.md)
