## Specifying a Connection by Using the Easy Connect Naming Method

You can specify a connection address to an Oracle Database directly from a client application, without having to configure a `tnsnames` setting for the Instant Client.

This method is convenient in that you do not have to create and manage a `tnsnames.ora` file. However, your application users must specify the host name and port number when they want to log in to your application.

For example, suppose you are running SQL\*Plus on the client computer and want to connect to the sales_us database, which is located on a server whose host name is shobeen and port number is 1521. If you launch SQL\*Plus from the command line, then log in as follows:

`sqlplus system/admin@//shobeen:1521/sales_us`

Similarly, in your application code, you can use Oracle Call Interface net naming methods to create the Instant Client-to-Oracle Database connection. For example, the following formats in the OCIServerAttach() call specify the connection information:

- Specify a SQL connect URL string using the following format:

  `//``host``[``:port``][/``service_name``]`

  For example:

  `//shobeen:1521/sales_us`

- Alternatively, specify the SQL connect information as an Oracle Net keyword-value pair. For example:

  `“(DESCRIPTION=(ADDRESS=(PROTOCOL=tcp) (HOST=shobeen) (PORT=1521))`

  `(CONNECT_DATA=(SERVICE_NAME=sales_us)))”`

**Parent topic:** [Connecting Instant Client or Instant Client Light to an Oracle Database](connecting-instant-client-to-an-oracle-db.md)
