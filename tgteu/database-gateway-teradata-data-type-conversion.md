The gateway converts Teradata data types to Oracle data types as follows:

Table A-1 Data Type Mapping and Restrictions

| Teradata                                 | Oracle               | Criteria                                                              | If Oracle uses large varchar (32k) |
|:-----------------------------------------|:---------------------|:----------------------------------------------------------------------|:-----------------------------------|
| `BLOB`                                   | `LONG RAW`           |                                                                       |                                    |
| `BYTE`                                   | `RAW`                | \-                                                                    |                                    |
| `BYTEINT`                                | `NUMBER(3)`          | `BYTEINT` range is -128 to +127                                       |                                    |
| `CHAR`                                   | `CHAR`               | \-                                                                    |                                    |
| `CHAR CHARACTER SET UNICODE`             | `CHAR`               | \-                                                                    |                                    |
| `CLOB`                                   | `LONG`               |                                                                       |                                    |
| `DATE`                                   | `CHAR(10)`           | \-                                                                    |                                    |
| `DECIMAL`                                | `NUMBER(p[,s])`      | \-                                                                    |                                    |
| `FLOAT`                                  | `FLOAT(24)`          | with precision \<= single precision float                             |                                    |
| `FLOAT`                                  | `FLOAT(53)`          | with precision \> single precision float                              |                                    |
| `INTEGER`                                | `NUMBER(10)`         | `NUMBER` range is` -2,147,483,648` to `2,147,483,647`                 |                                    |
| `INTERVAL`                               | `CHAR`               | \-                                                                    |                                    |
| `LONG` `VARCHAR` `CHARACTER SET UNICODE` | `LONG`               | if Oracle DB Character Set = Unicode. Otherwise, it is not supported. |                                    |
| `LONG` `VARCHAR`                         | `LONG`               | if Oracle DB Character Set = Unicode. Otherwise, it is not supported  |                                    |
| `SMALLINT`                               | `NUMBER(5)`          | `NUMBER` range is `-32768` to `32767`                                 |                                    |
| `TIME`                                   | `CHAR(15)`           | \-                                                                    |                                    |
| `TIMESTAMP`                              | `DATE`               | \-                                                                    |                                    |
| `VARBYTE`                                | `RAW`                | `1` \< = `N` \< = `2000`                                              | `1` \<= `N` \<= `32767`            |
| `VARBYTE`                                | `LONG RAW`           | `2000` \< `N`                                                         | `N` \< `32767`                     |
| `VARCHAR`                                | `VARCHAR2`<br>`LONG` | `N` \< = `4000`<br>`4000` \< `N`                                      | `N` \<= `32767`<br>`32767` \< `N`  |
| `VARCHAR() CHARACTER SET UNICO`          | `NVARCHAR2`          | `N < = 2000`<br>`4000` \< `N`                                         |                                    |
