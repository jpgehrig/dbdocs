The gateway converts Sybase data types to Oracle data types as follows:

Table A-1 Data Type Mapping and Restrictions

| Sybase                | Oracle          | Comment                                                              | If Oracle uses large varchar (32k) |
|:----------------------|:----------------|:---------------------------------------------------------------------|:-----------------------------------|
| `BIGINT`              | `NUMBER(19)`    |                                                                      |                                    |
| `BINARY`              | `RAW`           | \-                                                                   |                                    |
| `BIT`                 | `NUMBER(3)`     | \-                                                                   |                                    |
| `CHAR`                | `CHAR`          | \-                                                                   |                                    |
| `DATE`                | `DATE`          |                                                                      |                                    |
| `DATETIME`            | `DATE`          | \-                                                                   |                                    |
| `DECIMAL`             | `NUMBER(p[,s])` | \-                                                                   |                                    |
| `FLOAT`               | `FLOAT(53)`     | \-                                                                   |                                    |
| `IMAGE`               | `LONG RAW`      | \-                                                                   |                                    |
| `INT`                 | `NUMBER(10)`    | `NUMBER` range is `-2,147,483,647` to `2,147,483,647`                |                                    |
| `MONEY`               | `NUMBER(p[,s])` | \-                                                                   |                                    |
| `NUMERIC`             | `NUMBER(p[,s])` | \-                                                                   |                                    |
| `REAL`                | `FLOAT(24)`     | \-                                                                   |                                    |
| `SMALLDATETIME`       | `DATE`          | \-                                                                   |                                    |
| `SMALLINT`            | `NUMBER(5)`     | `NUMBER` range is` -32,767` to `32,767`                              |                                    |
| `SMALLMONEY`          | `NUMBER(p[,s])` | \-                                                                   |                                    |
| `SYSNAME`             | `VARCHAR2`      |                                                                      |                                    |
| `TEXT`                | `LONG`          | \-                                                                   |                                    |
| `TIME`                | `CHAR(15)`      |                                                                      |                                    |
| `TIMESTAMP`           | `RAW`           |                                                                      |                                    |
| `TINYINT`             | `NUMBER(3)`     | \-                                                                   |                                    |
| `UNICHAR`             | `NCHAR`         | \-                                                                   |                                    |
| `UNSIGNED` `BIGINT`   | `NUMBER(20)`    |                                                                      |                                    |
| `UNSIGNED` `INT`      | `NUMBER(10)`    |                                                                      |                                    |
| `UNSIGNED` `SMALLINT` | `NUMBER(5)`     |                                                                      |                                    |
| `UNITEXT`             | `LONG`          | if Oracle DB Character Set = Unicode. Otherwise, it is not supported |                                    |
| `UNIVARCHAR`          | `NVARCHAR`      | \-                                                                   |                                    |
| `VARBINARY`           | `RAW`           | \-                                                                   |                                    |
| `VARCHAR`             | `VARCHAR2`      | `N` \< = `4000`                                                      | `N` \<= `32767`                    |
