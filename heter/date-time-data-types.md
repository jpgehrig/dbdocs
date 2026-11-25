Heterogeneous Services generic code supports Oracle date-time data types in SQL and stored procedures. Heterogeneous Services does not support these data types in data dictionary translations or queries involving data dictionary translations.

Oracle Database has five date-time data types:

- `TIMESTAMP`

- `TIMESTAMP WITH TIME ZONE`

- `TIMESTAMP WITH LOCAL TIME ZONE`

- `INTERVAL YEAR TO MONTH`

- `INTERVAL DAY TO SECOND`

Even though Heterogeneous Services generic code supports date-time data types, support for a particular gateway depends on whether or not the driver for that non-Oracle system implemented date-time support. Support, even when the driver implements it, may be partial because of the limitations of the non-Oracle system. For more information, see your gateway-specific documentation.

You must set the timestamp formats of the non-Oracle system in the gateway initialization file. The parameters to set are `HS_NLS_TIMESTAMP_FORMAT` and `HS_NLS_TIMESTAMP_TZ_FORMAT`. You should also set the local time zone for the non-Oracle system in the initialization file by setting `HS_TIME_ZONE`.

**See Also:**

[Oracle Database SQL Language Reference ](../sqlrf/Data-Types.md)for information about datetime data types.

**Parent topic:** [Features of Oracle Database Gateways](oracle-database-gateways-features.md)
