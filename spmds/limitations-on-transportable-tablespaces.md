This section lists the limitations on transportable tablespace.

Be aware of the following limitations for transportable tablespaces:

- The general limitations described in "[General Limitations on Transporting Data](general-limitations-on-transporting-data.md)" apply to transportable tablespaces.

- When transporting a tablespace set, objects with underlying objects (such as materialized views) or contained objects (such as partitioned tables) are not transportable unless all of the underlying or contained objects are in the tablespace set.

- Transportable tablespaces cannot transport tables with `TIMESTAMP` `WITH` `TIMEZONE` (TSTZ) data across platforms with different time zone file versions. The transportable tablespace operation skips these tables. You can export and import these tables conventionally.

  See [Oracle Database Utilities](../sutil/oracle-data-pump-overview.md) for more information.

- You cannot include administrative tablespaces, such as `SYSTEM` and `SYSAUX` in a transportable tablespace set.

**Parent topic:** [Migrating Data Using Transportable Tablespaces](transportable-tablespaces.md)
