ODP.NET Core developers can assign application settings in .NET Configuration API, `sqlnet.ora `file, and `tnsnames.ora` file.

### .NET Configuration API

.NET Core does not support application configuration via .NET configuration files, that is, `web.config`. Instead, it uses .NET Configuration API in lieu of a configuration file. ODP.NET Core supports Configuration API via the static class, `OracleConfiguration`, for application level provider settings. The `OracleDataSourceCollection `class supports adding and deleting net services names, that is, TNS entries. The `OracleOnsServerCollection ` class supports adding to and deleting from a list of nodes where the Oracle Notification Service (ONS) daemons are talking to their remote clients.

All configurations settings through `OracleConfiguration` should be done before opening any connection in the application. Once a connection is opened, any updates to configuration properties will result in `InvalidOperationException`; with only exception of trace settings that are still allowed to change during application runtime.

Example 2-6 Code Sample

    using System;
    using Oracle.ManagedDataAccess.Client;

    namespace ODP_Core_Config_API
    {
        class odp_core_config
        {
            static void Main(string[] args)
            {
                // This sample demonstrates how to use ODP.NET Core Configuration API

                // Add connect descriptors and net service names entries.
                OracleConfiguration.OracleDataSources.Add("orclpdb", "(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=<hostname or IP>)(PORT=1521))(CONNECT_DATA=(SERVICE_NAME=<service name>)(SERVER=dedicated)))");
                OracleConfiguration.OracleDataSources.Add("orcl", "(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=<hostname or IP>)(PORT=1521))(CONNECT_DATA=(SERVICE_NAME=<service name>)(SERVER=dedicated)))");

                // Set default statement cache size to be used by all connections.
                OracleConfiguration.StatementCacheSize = 25;

                // Disable self tuning by default.
                OracleConfiguration.SelfTuning = false;

                // Bind all parameters by name.
                OracleConfiguration.BindByName = true;

                // Set default timeout to 60 seconds.
                OracleConfiguration.CommandTimeout = 60;

                // Set default fetch size as 1 MB.
                OracleConfiguration.FetchSize = 1024 * 1024;

                // Set tracing options
                OracleConfiguration.TraceOption = 1;
                OracleConfiguration.TraceFileLocation = @"D:\traces";
                // Uncomment below to generate trace files
                //OracleConfiguration.TraceLevel = 7;

                // Set network properties
                OracleConfiguration.SendBufferSize = 8192;
                OracleConfiguration.ReceiveBuffereSize = 8192;
                OracleConfiguration.DisableOOB = true;

                OracleConnection orclCon = null;

                try
                {
                    // Open a connection
                    orclCon = new OracleConnection("user id=hr; password=<password>; data source=orclpdb");
                    orclCon.Open();

                    // Execute simple select statement that returns first 10 names from EMPLOYEES table
                    OracleCommand orclCmd = orclCon.CreateCommand();
                    orclCmd.CommandText = "select first_name from employees where rownum <= 10 ";
                    OracleDataReader rdr = orclCmd.ExecuteReader();

                    while (rdr.Read())
                        Console.WriteLine("Employee Name: " + rdr.GetString(0));

                    Console.ReadLine();

                    rdr.Dispose();
                    orclCmd.Dispose();
                }
                finally
                {
                    // Close the connection
                    if (null != orclCon)
                        orclCon.Close();
                }
            }
        }
    }

### Oracle Configuration Files

ODP.NET Core supports the `sqlnet.ora` and `tnsnames.ora` parameters below. These settings can be used in conjunction with .NET Configuration API.

- `BindByName`

- `DbNotificationPort`

- `Disable_Oob` – `sqlnet.ora`

- `DRCPConnectionClass`

- `FetchSize`

- `MaxStatementCacheSize`

- `NAMES.DIRECTORY_PATH `– `sqlnet.ora`

- `NODELAY` –` sqlnet.ora`

- `RETRY_COUNT`

- `RETRY_DELAY`

- `RECEIVE_BUF_SIZE` – `sqlnet.ora` or `tnsnames.ora`

- SelfTuning

- `SEND_BUF_SIZE` –` sqlnet.ora `or `tnsnames.ora`

- `ServiceRelocationConnectionTimeout`

- `SQLNET.AUTHENTICATION_SERVICES` – `sqlnet.ora`

- `SQLNET.CRYPTO_CHECKSUM_CLIENT` – `sqlnet.ora`

- `SQLNET.CRYPTO_CHECKSUM_TYPES_CLIENT` – `sqlnet.ora`

- `StatementCacheSize`

- `SSL_SERVER_DN_MATCH` – `sqlnet.ora`

- `SSL_VERSION` – `sqlnet.ora`

- `TNS_ADMIN`

- `TraceFileLocation`

- `TraceLevel`

- `TraceOption`

- `TCP.CONNECT_TIMEOUT `– `sqlnet.ora`

- `SQLNET.ENCRYPTION_CLIENT` – `sqlnet.ora `

- `SQLNET.ENCRYPTION_TYPES_CLIENT` – `sqlnet.ora`

ODP.NET Core will look for `sqlnet.ora` and `tnsnames.ora` files in the following precedence order:

1.  Directory set in `OracleConfiguration.TnsAdmin` property

2.  Directory of the running ODP.NET Core assembly

3.  Current working directory

**See Also:**

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleDataSourceCollection Class](OracleDataSourceCollectionClass.md)
