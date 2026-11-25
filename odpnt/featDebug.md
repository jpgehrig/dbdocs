ODP.NET provides debug tracing support, which allows logging of all the ODP.NET activities into a trace file. Different levels of tracing are available.

The provider can record the following information:

- Entry and exit information for the ODP.NET public methods

- User-provided SQL statements as well as SQL statements modified by the provider

- Connection pooling statistics such as enlistment and delistment

- Thread ID (entry and exit)

- HA Events and Load Balancing information

- Distributed Transactions

- Self-tuning information

- User-mode dumps upon unmanaged exceptions

To enable ODP.NET for tracing, `TraceFileLocation`, `TraceLevel`, and `TraceOption` must be set appropriately either in the Windows Registry or in an XML configuration file. ODP.NET, Managed and Unmanaged Drivers support the XML configuration file. Windows Registry settings are available for ODP.NET, Unmanaged Driver only.

In ODAC 12c Release 4, ODP.NET now uses new directories to write trace files to by default.

- ODP.NET, Managed Driver: `<Windows user temporary folder>``\ODP.NET\managed\trace`

- ODP.NET, Unmanaged Driver: \<Windows user temporary folder\>`\ODP.NET\unmanaged\trace`

The Windows user temporary folder is determined by your local Windows settings, such as your Windows `TMP` or `TEMP` environment variable. Typically, it can be `C:\temp` or `C:\Users\``<user name>``\AppData\Local\Temp`. ODP.NET will create an entry in the Windows event log where the trace was created anytime it creates a trace file. ODP.NET Core does not support writing to the Windows event log.

For ODP.NET, Unmanaged Driver specifically, `TraceFileLocation` is now supported similar to ODP.NET, Managed Driver. `TraceFileLocation` defines the directory where the trace files will be created. Neither `TraceFileName` nor `TraceFileLocation` will be created by default in the Windows Registry.

**See Also:**

"[Configuring Oracle Data Provider for .NET](InstallConfig.md)" for further details
