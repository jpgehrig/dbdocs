This appendix contains the following topics:

- Reserved Words and Keywords

- Oracle Reserved Namespaces

### A.1 Reserved Words and Keywords

Some words are reserved by Oracle. That is, they have a special meaning to Oracle and cannot be redefined. For this reason, you cannot use them to name database objects such as columns, tables, or indexes. To view the lists of the Oracle reserved words for SQL and PL/SQL, see the [Oracle Database SQL Language Reference](../sqlrf/index.md) and the [Oracle Database PL/SQL Language Reference](../lnpls/index.md).

Pro\*C/C++ keywords, like C or C++ keywords, should not be used as variables in your program. Otherwise, an error will be generated. An error may result if they are used as the name of a database object such as a column. Here are the keywords used in Pro\*C/C++:

| Keywords                        | Keywords                      | Keywords                 |
|:--------------------------------|:------------------------------|:-------------------------|
| all                             | allocate                      | alter                    |
| analyze                         | and                           | any                      |
| append                          | arraylen                      | as                       |
| asc                             | assign                        | at                       |
| audit                           | authorization                 | avg                      |
| begin                           | between                       | bind                     |
| both                            | break                         | buffer                   |
| buffering                       | by                            | call                     |
| cast                            | char                          | character                |
| character_set_name              | charf                         | charz                    |
| check                           | chunksize                     | close                    |
| collection                      | comment                       | commit                   |
| connect                         | constraint                    | constraints              |
| context                         | continue                      | convbufsz                |
| copy                            | count                         | create                   |
| current                         | currval                       | cursor                   |
| data                            | database                      | date                     |
| dateformat                      | datelang                      | datetime_interval_code   |
| datetime_interval_precision     | day                           | deallocate               |
| dec                             | decimal                       | declare                  |
| default                         | define                        | delete                   |
| deref                           | desc                          | describe                 |
| descriptor                      | directory                     | disable                  |
| display                         | distinct                      | do                       |
| double                          | drop                          | eject                    |
| else                            | enable                        | end                      |
| endif                           | end-exec                      | erase                    |
| escape                          | exec                          | execute                  |
| exists                          | explain                       | extract                  |
| fetch                           | file                          | fileexists               |
| filename                        | first                         | float                    |
| flush                           | for                           | force                    |
| found                           | free                          | from                     |
| function                        | get                           | global                   |
| go                              | goto                          | grant                    |
| group                           | having                        | hold                     |
| host_stride_length              | hour                          | iaf                      |
| identified                      | ifdef                         | ifndef                   |
| immediate                       | in                            | include                  |
| indicator                       | indicator_stride_length       | input                    |
| insert                          | integer                       | internal_length          |
| intersect                       | interval                      | into                     |
| is                              | isopen                        | istemporary              |
| last                            | leading                       | length                   |
| level                           | like                          | list                     |
| load                            | lob                           | local                    |
| lock                            | long                          | max                      |
| message                         | min                           | minus                    |
| minute                          | mode                          | month                    |
| multiset                        | name                          | national_character       |
| nchar                           | nchar_cs                      | next                     |
| nextval                         | noaudit                       | not                      |
| notfound                        | nowait                        | null                     |
| nullable                        | number                        | numeric                  |
| nvarchar                        | nvarchar2                     | object                   |
| ocibfilelocator                 | ocibloblocator                | ocicloblocator           |
| ocidate                         | ociextproccontext             | ocinumber                |
| ociraw                          | ocirowid                      | ocistring                |
| octet_length                    | of                            | one                      |
| only                            | open                          | option                   |
| or                              | oracle                        | order                    |
| output                          | overlaps                      | overpunch                |
| package                         | partition                     | perform                  |
| precision                       | prepare                       | prior                    |
| procedure                       | put                           | raw                      |
| read                            | real                          | ref                      |
| reference                       | register                      | release                  |
| rename                          | replace                       | return                   |
| returned_length                 | returned_octet_length         | returning                |
| revoke                          | role                          | rollback                 |
| rowid                           | rownum                        | savepoint                |
| scale                           | second                        | section                  |
| select                          | set                           | skip1                    |
| skip2                           | skip3                         | smallint                 |
| some                            | sql                           | sql-context              |
| sql-cursor                      | sqlerror                      | sqlwarning               |
| start                           | statement                     | stddev                   |
| stop                            | string                        | sum                      |
| sysdate                         | sysdba                        | sysoper                  |
| table                           | temporary                     | threads                  |
| time                            | timestamp                     | timezone_hour            |
| timezone_minute                 | to                            | tools                    |
| title                           | trailing                      | transaction              |
| trigger                         | trim                          | truncate                 |
| type                            | uid                           | ulong_varchar            |
| union                           | unique                        | unsigned                 |
| user_defined_type_name          | user_defined_type_name_length | user_defined_type_schema |
| user_defined_type_schema_length | user_defined_type_version     | update                   |
| use                             | user                          | using                    |
| validate                        | value                         | values                   |
| var                             | varchar                       | varchar2                 |
| variables                       | variance                      | varnum                   |
| varraw                          | view                          | whenever                 |
| where                           | with                          | work                     |
| write                           | year                          | zone                     |

### A.2 Oracle Reserved Namespaces

The following table contains a list of namespaces that are reserved by Oracle. The initial characters of function names in Oracle libraries are restricted to the character strings in this list. Because of potential name conflicts, do not use function names that begin with these characters. For example, the Oracle Net Transparent Network Service functions all begin with the characters `NS`, so you need to avoid naming functions that begin with `NS`.

Table A-1 Oracle Reserved Namespaces

| Namespace                                                        | Library                                                                                                                                                                                                                                                                                                                        |
|:-----------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| XA                                                               | external functions for XA applications only                                                                                                                                                                                                                                                                                    |
| SQ                                                               | external SQLLIB functions used by Oracle Precompiler and SQL\*Module applications                                                                                                                                                                                                                                              |
| O, OCI                                                           | external OCI functions internal OCI functions                                                                                                                                                                                                                                                                                  |
| UPI, KP                                                          | function names from the Oracle UPI layer                                                                                                                                                                                                                                                                                       |
| NA<br>NC<br>ND<br>NL<br>NM<br>NR<br>NS<br>NT<br>NZ<br>OSN<br>TTC | Oracle Net Native services product<br>Oracle Net RPC project<br>Oracle Net Directory<br>Oracle Net Network Library layer<br>Oracle Net Net Management Project<br>Oracle Net Interchange<br>Oracle Net Transparent Network Service<br>Oracle Net Drivers<br>Oracle Net Security Service<br>Oracle Net V1<br>Oracle Net Two task |
| GEN, L, ORA                                                      | Core library functions                                                                                                                                                                                                                                                                                                         |
| LI, LM, LX                                                       | function names from the Oracle Globalization Support layer                                                                                                                                                                                                                                                                     |
| S                                                                | function names from system-dependent libraries                                                                                                                                                                                                                                                                                 |

The list in the table is not a comprehensive list of all functions within the Oracle reserved namespaces. For a complete list of functions within a particular namespace, refer to the document that corresponds to the appropriate Oracle library.
