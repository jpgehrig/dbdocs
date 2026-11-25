The Procedural Gateway Data Dictionary (PG DD) is maintained in a conventional Oracle database. It is installed by a SQL\*Plus installation script (`pgddcr8.sql` in the `%ORACLE_HOME%\dg4appc\admin` directory on Microsoft Windows or `$ORACLE_HOME/dg4appc/admin` directory on UNIX based systems) and manipulated by PGAU statements and standard SQL statements.

The dictionary is divided into two sections:

- the environment dictionary

- the active dictionary

The environment dictionary is static and should not be changed. The contents of the environment dictionary support proper translation from the remote transaction's environment to the integrating server's environment, and is platform-specific. The active dictionary is updated at the user's location by the PGAU in response to definitions supplied by the user.

Topics:

- PG DD Environment Dictionary

- PG DD Active Dictionary

### PG DD Environment Dictionary

The PGAU uses some dictionary tables strictly as input. These dictionary tables define environmental parameters for PGAU. Both table and values are installed by a SQL\*Plus script at gateway installation time and are not to be modified by the installation.

The environment dictionary does not reference the active dictionary, but the active dictionary does reference environment dictionary entries.

#### Environment Dictionary Sequence Numbers

The environment dictionary requires unique identifying numbers in some columns to join environment dictionary entries together. Oracle sequence objects are therefore created by the Oracle Database Gateway for APPC to support this requirement.

Table A-1 presents the Oracle sequence objects and their descriptions.

Table A-1 Oracle Sequence Objects

| Oracle Sequence Objects | Descriptions                 |
|:------------------------|:-----------------------------|
| `pga.envrseq`           | Environment id tag           |
| `pga.compseq`           | Compiler id tag              |
| `pga.eattrseq`          | Environment Attribute id tag |
| `pga.dtypeseq`          | Datatype id tag              |
| `pga.dtattseq`          | Datatype Attribute id tag    |

#### Environment Dictionary Tables

The environment dictionary tables contain constants that describe the following components of the operating environment:

- `pga_maint`

- `pga_environments`

- `pga_env_attr`

- `pga_env_values`

- `pga_compilers`

- `pga_datatypes`

- `pga_datatype_attr`

- `pga_datatype_values`

- `pga_usage`

- `pga_modes`

##### pga_maint

The `pga_maint` table stores the PG DD maintenance information, including version number and change history, as presented in Table A-2:

Table A-2 pga_maint

| Column    | Type            | Contents                                                                                                                                                                        |
|:----------|:----------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `version` | `number(10,4)`  | PG DD version in format `VVRRFF.rrff`, where:<br>`VV `- base version;<br>`RR` - base release;<br>`FF` - base fix;<br>`rr` - port-specific release;<br>`ff `- port-specific fix. |
| `mntdate` | `date`          | Oracle date and time at which the PG DD was upgraded.                                                                                                                           |
| `change`  | `varchar2(256)` | Description of the PG DD upgrade.                                                                                                                                               |

##### pga_environments

The `pga_environments` table stores the defined environment keywords, as presented in Table A-3:

Table A-3 pga_environments

| Column | Type                     | Content                      |
|:-------|:-------------------------|:-----------------------------|
| `name` | `varchar2(16)` not null  | Environment.<br>Primary key. |
| `env#` | `number (9, 0)` not null | Env id.<br>Foreign key.      |

##### pga_env_attr

The `pga_env_attr` table stores the types of environmental attributes, as presented in Table A-4:

Table A-4 pga_env_attr

| Column    | Type                     | Content                          |
|:----------|:-------------------------|:---------------------------------|
| `name`    | `varchar2 (16)` not null | Attribute.<br>Primary key.       |
| `attr#`   | `number (9, 0)` not null | Attribute id.<br>Foreign key.    |
| `coltype` | `varchar2 (4)` not null  | Attr value type.<br>Foreign key. |

##### pga_env_values

The `pga_env_values` table stores the values for environments, as presented in Table A-5:

Table A-5 pga_env_values

| Column    | Type                     | Content                       |
|:----------|:-------------------------|:------------------------------|
| `env#`    | `number (9, 0)` not null | Env id.<br>Primary key.       |
| `attr#`   | `number (9, 0)` not null | Attribute id.<br>Primary key. |
| `numval`  | `number (9, 0)`          | Numeric attribute value.      |
| `charval` | `varchar2 (64)`          | Character attribute value.    |
| `dateval` | `date`                   | Date attribute value.         |

##### pga_compilers

The `pga_compilers` table stores the compiler environment names, as presented in Table A-6:

Table A-6 pga_compilers

| Column        | Type                     | Content                              |
|:--------------|:-------------------------|:-------------------------------------|
| `name`        | `varchar2 (16)` not null | Compiler name.<br>Primary key.       |
| `plscomp`     | `varchar2 (30)`          | PLS compiler name.<br>Secondary key. |
| `env#`        | `number (9, 0)` not null | Env id.<br>Foreign key.              |
| `comp# `      | `number (9, 0) `not null | Compiler env id.<br>Foreign key.     |
| `ddl_process` | `number (9, 0) `not null | PGADDL processor number.             |

##### pga_datatypes

The `pga_datatypes` table stores the datatype keywords, as presented in Table A-7:

Table A-7 pga_datatypes

| Column  | Type                     | Content                           |
|:--------|:-------------------------|:----------------------------------|
| `comp#` | `number (9, 0)` not null | Compiler env id.<br>Primary key.  |
| `name`  | `varchar2 (16) `not null | Datatype keyword.<br>Primary key. |
| `dt#`   | `number (9, 0)` not null | Datatype_values.<br>Foreign key.  |

##### pga_datatype_attr

The `pga_datatype_attr` table stores datatype attribute keywords, as presented in Table A-8:

Table A-8 pga_datatype_attr

| Column    | Type                     | Content                            |
|:----------|:-------------------------|:-----------------------------------|
| `name`    | `varchar2 (16) `not null | Attribute keyword.<br>Primary key. |
| `attr#`   | `number (9, 0)` not null | Attribute id.<br>Foreign key.      |
| `coltype` | `varchar2 (4)` not null  | Type of attr.<br>Foreign key.      |

##### pga_datatype_values

The `pga_datatype_values` table stores the datatype attribute values, as presented in Table A-9:

Table A-9 pga_datatype_values

| Column    | Type                     | Content                          |
|:----------|:-------------------------|:---------------------------------|
| `comp#`   | `number (9, 0)` not null | Compiler env id.<br>Primary key. |
| `dt#`     | `number (9, 0)` not null | datatype_values.<br>Foreign key. |
| `attr#`   | `number (9, 0)` not null | Attribute id.<br>Foreign key.    |
| `dag#`    | `number (9, 0)`          | Datatype attr group no.          |
| `numval`  | `number (9, 0)`          | Numeric attribute value.         |
| `charval` | `varchar2 (40)`          | Character attribute value.       |
| `dateval` | `date`                   | Date attribute value.            |

##### pga_usage

The `pga_usage` table performs a referential integrity check of `pga_data` and `pga_field` column "usage" as presented in Table A-10:

Table A-10 pga_usage

| Column | Type          | Content                                                                                                                                                                      |
|:-------|:--------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name` | `varchar2(6)` | Value for the "`usage`" field of data dictionary tables. For example:<br>'`PASS`'<br>'`SKIP`<br>'`NULL`'<br>'`ASIS`'<br>Primary key.<br>Max length =\> 4-char string length. |

##### pga_modes

The `pga_modes` table performs a referential integrity check of `pga_call_parm` column "mode", as presented in Table A-11:

Table A-11 pga_modes

| Column | Type          | Content                                                                                                                   |
|:-------|:--------------|:--------------------------------------------------------------------------------------------------------------------------|
| `name` | `varchar2(6)` | Name of valid parameter call modes. For example:<br>`IN`<br>`OUT`<br>`IN OUT`<br>`Max length => 'IN OUT' ` string length. |

### PG DD Active Dictionary

The PG DD active data dictionary is created by `pgddcr8.sql` at installation, but maintained using PGAU. The active dictionary can refer to items (by ID number) in the environment dictionary.

#### Active Dictionary Versioning

The PG DD active dictionary tables contain the descriptions of transactions and data structures. There might be more than one version of a definition. Old versions are retained indefinitely.

In PGAU dictionary operations, a definition is referred to by its "name", which can be qualified by a specific version number. If omitted, the most recent version is assumed.

#### Active Dictionary Sequence Numbers

Because the active dictionary is constantly changing, the identifying numbers needed to join active dictionary entries together must also change. To support this requirement, PG DD installation creates the following Oracle sequence objects.

Table A-12 lists the Oracle sequence objects and their descriptions:

Table A-12 Active Dictionary Oracle Sequence Object Descriptions

| Oracle Sequence Objects | Description                  |
|:------------------------|:-----------------------------|
| `pga.transeq`           | Transaction id tag           |
| `pga.tranvers`          | Transaction Version id tag   |
| `pga.tattrseq`          | Transaction Attribute id tag |
| `pga.callseq`           | APPC-Call id tag             |
| `pga.callvers`          | Call Version id tag          |
| `pga.parmseq`           | APPC-Call Parameter id tag   |
| `pga.dataseq`           | Data id tag                  |
| `pga.fieldseq`          | Data subfield id tag         |
| `pga.datavers`          | Data Version id tag          |
| `pga.dattrseq`          | Data Attribute id tag        |

#### Active Dictionary Tables

Following is a list of active dictionary tables:

- `pga_trans`

- `pga_trans_attr`

- `pga_trans_values`

- `pga_trans_calls`

- `pga_call`

- `pga_data`

- `pga_fields`

- `pga_data_attr`

- `pga_data_values`

##### pga_trans

One row exists in the `PGA_TRANS` table for each user transaction. The row is created by a PGAU `DEFINE TRANSACTION` statement and used by a PGAU `GENERATE` statement to create the PL/SQL package (TIP).

Table A-13 This 3-column table presents the column, type and content information for `PGA_TRANS`:

Table A-13 pga_trans

| Column     | Type           | Content                                                                                                                                                                                                                                                                    |
|:-----------|:---------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `tname`    | `varchar2(64)` | Transaction name as defined by the customer.<br>Primary key.<br>Max length =\> APPC TPname string length.                                                                                                                                                                  |
| `version`  | `number(9,0)`  | Version identification of this entry; it exists in the table because multiple archived or invalid entries might exist and be kept for possible future reactivation.<br>Primary key.<br>Set from an Oracle sequence object for transaction version inserted into the PG DD. |
| `updtdate` | `date`         | Audit-trail date/time record last updated.                                                                                                                                                                                                                                 |
| `updtuser` | `varchar2(30)` | Audit-trail user ID/program which last updated this record.                                                                                                                                                                                                                |
| `trans#`   | `number(9,0)`  | PGA Transaction number, used for the define call, define data and define transaction statements.<br>Foreign key.<br>`pga_trans_values(trans#)`, `pga_trans_calls(trans#)`.<br>Set from an Oracle sequence object for transaction inserted into the PG DD.                  |

##### pga_trans_attr

The `pga_trans_attr` table relates a character string defining the transaction attributes supported by PGA to `pga_trans_values` entries through an attribute id number and type.

The `pga_trans_attr` table is also used for integrity checks of transaction attributes when new transactions are being defined.

There is an entry in the `pga_trans_attr` table for each transaction attribute name. All possible transaction attribute names supported by PGA on any defined transaction are specified. There is one row for each attribute, and no duplicates are allowed.

Table A-14 This 3-column table presents the column, type and content information for `pga_trans_attr`:

Table A-14 pga_trans_attr

| Column     | Type           | Content                                                                                                                                                                                                                            |
|:-----------|:---------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name`     | `varchar2(16)` | Character string name of attribute.<br>Primary key.<br>Contains:<br>"`ENVIRONMENT`",<br>"`LUNAME`",<br>"`TPNAME`",<br>"`LOGMODE`",<br>"`SIDEPROFILE`",<br>"`SYNCLEVEL`",<br>"`NLS_LANGUAGE`",<br>"`REMOTE_MBCS`"<br>"`LOCAL_MBCS`" |
| `attr#`    | `number(9,0)`  | Attribute id assigned.<br>Foreign key.<br>pga_data_values(attr#).<br>Set from an Oracle sequence object for each supported transaction attribute inserted into the PG DD.                                                          |
| `coltype`  | `varchar2(4)`  | Type of Oracle column from which attribute value is retrieved from pga_tran_values. For example:<br>'`NUM ' => pga_tran_values(numval)`<br>'`CHAR' => pga_tran_values(charval)`<br>'`DATE' => pga_tran_values(dateval``)`          |
| `required` | `char(1)`      | If not null, required keyword for `DEFINE TRANSACTION`; if null, optional.                                                                                                                                                         |

##### pga_trans_values

The `pga_trans_values` table describes the values of transaction attributes.

A row exists to specify the value of each attribute of each transaction defined in the data dictionary.

The column, type and content information for `pga_trans_values` is presented in Table A-15:

Table A-15 pga_trans_values

| Column    | Type           | Content                                                                                                                                                            |
|:----------|:---------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `trans#`  | `number(9,0)`  | Transaction id from `pga_trans(trans#)`.<br>Primary key.<br>Set from an Oracle sequence object for transaction inserted into the PG DD.                            |
| `attr#`   | `number(9,0)`  | Attribute id from `pga_trans_attr(attr#)`,<br>Primary key.<br>Set from an Oracle sequence object for each supported transaction attribute inserted into the PG DD. |
| `numval`  | `number(9,0)`  | Attribute's numeric value, for example for a given transaction's `SYNCLEVEL` attribute `0`.                                                                        |
| `charval` | `varchar2(64)` | Attribute's character value; for example, a given transaction's `TPNAME` attribute.                                                                                |
| `dateval` | `date`         | Attribute's date value. Probably always null; included for completeness.                                                                                           |

##### pga_trans_calls

The `pga_trans_calls` table relates all calls available with any single transaction to each specific call definition through a call ID number.

An entry exists in the `pga_trans_calls` table for each PL/SQL call referenced in a transaction definition through the `CALL`(cname,...) operand. One row per transaction call; no duplicates.

The column, type and content information for `pga_trans_calls` is presented in Table A-16:

Table A-16 pga_trans_calls

| Column   | Type          | Content                                                                                                                                                                |
|:---------|:--------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `trans#` | `number(9,0)` | Transaction id number from `pga_trans(trans#)`.<br>Primary key.<br>Set from an Oracle sequence object for transaction inserted into the PG DD.                         |
| `seq#`   | `number(9,0)` | Sequence number of this call.<br>Primary key.                                                                                                                          |
| `call#`  | `number(9,0)` | Call id number in `pga_call(call#)`.<br>Foreign key.<br>Copied from `pga_call.call#` for the referenced call when this transaction definition was inserted or updated. |

##### pga_call

The pga_call table relates all calls that are available for all defined transactions, to a unique call id number and PL/SQL remote procedural call (RPC) name. One entry exists in this table for each PL/SQL call (defined in a `DEFINE CALL` statement).

One row per call, duplicates are possible when multiple transactions make identical calls. The plsrpc specification must be unique within the Oracle database which makes the calls, and rows are uniquely distinguished by call#.

The column, type and content information for pga_call are presented in Table A-17:

Table A-17 pga_call

| Column     | Type           | Content                                                                                                                                                                                                                                  |
|:-----------|:---------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `cname`    | `varchar2(48)` | Call name for PGAU reference;<br>Primary key.<br>Max length =\> COBOL name string length                                                                                                                                                 |
| `plsrpc`   | `varchar2(30)` | RPC call name for reference in PL/SQL (public procedure to be generated).<br>Max length =\> PL/SQL RPC name length                                                                                                                       |
| `updtdate` | `date`         | Audit trail date/time of record's last update.                                                                                                                                                                                           |
| `updtuser` | `varchar2(30)` | Audit trail user id/program which last updated this record.                                                                                                                                                                              |
| `version`  | `number(9,0)`  | Version identification of this entry, because multiple archived or invalid entries might exist and be kept for possible future reactivation.<br>Primary key.<br>Set from an Oracle sequence object for call version inserted into PG DD. |
| `call#`    | `number(9,0)`  | Call id number.<br>Foreign key.<br>`pga_trans_calls(call#)`, `pga_call_parm(call#)`.<br>Set from an Oracle sequence object for each call inserted into the PG DD.                                                                        |

##### pga_call_parm

The `pga_call_parm` table relates all parameters of any single transaction call to the data definitions describing each parameter.

One entry exists in the `pga_call_parm` table for each parameter on a call in the `PARMS()` operand of the PGAU `DEFINE CALL` statement. One row per parameter, duplicates allowed when multiple calls (in the `pga_call` table) refer to the same parameters.

Table A-18 This 3-column table presents the column, type and content information for `pga_call_parm`:

Table A-18 pga_call_parm

| Column  | Type          | Content                                                                                                                                                                                                                        |
|:--------|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `call#` | `number(9,0)` | Call number for the referencing call from `pga_calls`.<br>Primary key.<br>Set from an Oracle sequence object for each call inserted into the PG DD.                                                                            |
| `parm#` | `number(9,0)` | Position in the `PARMS()` argument of `DEFINE CALL` operation (1,2,3...).<br>Primary key.                                                                                                                                      |
| `cmode` | `varchar2(6)` | Call mode of this parameter; one of the values in `pga_data_modes`. For example:<br>'`IN`', '`OUT`', '`IN OUT`'<br>Max length =\> '`IN OUT`' string length                                                                     |
| `data#` | `number(9,0)` | Data definition \# in `pga_data(data#)` of this item.<br>Foreign key.<br>`pga_data(data#)`,`pga_data_values(data#)`.<br>Copied from `pga_data.data#` for the data item when this call/parm definition was inserted or updated. |

##### pga_data

The `pga_data` table defines each data item used as a parameter in a call and relates the remote host data name to its PL/SQL variables and any component subfields or clauses within each data item (if the data item is an aggregate, such as a record). Each data item might have attributes related to it through its corresponding field definition. Even atomic data items have a single row in the `pga_field` table.

One row exists in the `pga_data` table for each data item defined by a PGAU `DEFINE DATA` or `REDEFINE DATA` statement.

Table A-19 This 3-column table presents the column, type and content information for `pga_data`:

Table A-19 pga_data

| Column     | Type            | Content                                                                                                                                                                                                          |
|:-----------|:----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `comp#`    | `number(9,0)`   | Compiler id number.;<br>Foreign key.<br>(`pga_compiler(comp#)`.<br>Set from `pga_compiler`(comp#) based on the language parameter specified on the `DEFINE DATA` statement when the data definition is inserted. |
| `compopts` | `varchar2(100)` | Compiler options from the `COMPOPTS` keyword on the `DEFINE DATA` statement.                                                                                                                                     |
| `dname`    | `varchar2(255)` | Name from the DEFINE statement;<br>Primary key.<br>Max length =\> COBOL name length                                                                                                                              |
| `plsdvar`  | `varchar(30)`   | PL/SQL variable name of data item for reference in PL/SQL.<br>Max length =\> PL/SQL variable length                                                                                                              |
| `version`  | `number(9,0)`   | Version number of this entry. Set from an Oracle sequence object for data version inserted into the PGADD.                                                                                                       |
| `updtdate` | `date`          | Audit-trail date/time this control record last updated.                                                                                                                                                          |
| `updtuser` | `varchar2(30)`  | Audit-trail user id/program which last updated this record.                                                                                                                                                      |
| `usage`    | `varchar2(6)`   | Default usage of this data item: `PASS`, `SKIP`, `NULL`, `ASIS`.<br>Used primarily by PGAU `REPORT`.<br>Max length =\> 4-char string length                                                                      |
| `data#`    | `number(9,0)`   | Data definition number.<br>Foreign key.<br>(`pga_call_parm(data#)`, `(pga_field(data#)`<br>Set from an Oracle sequence object.                                                                                   |

##### pga_fields

The pga_fields table defines each field within a data item and relates the remote host data field to its PL/SQL variables or nested records. Each field item might have attributes related to it (by field#) in the `pga_data_attr` and `pga_data_values` tables.

One row exists in the pga_fields table for each atomic item, field, clause, or nested record defined by a PGAU `DEFINE DATA` statement. Several rows would exist (related by a single data# and incrementing fld#) to define an aggregate data item, one row per field or group.

Table A-20 This 3-column table presents the column, type and content information for pga_fields:

Table A-20 pga_fields

| Column     | Type            | Content                                                                                                                                                                                                                                          |
|:-----------|:----------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `data#`    | `number(9,0)`   | Data definition number.<br>Primary key.<br>(`pga_data(data#), pga_call_parm(data#)`.<br>Set from an Oracle sequence object.                                                                                                                      |
| `fname`    | `varchar2(255)` | Extracted or derived name of a field if dname defines aggregate data.<br>Max length =\> COBOL name length                                                                                                                                        |
| `plsfvar`  | `varchar2(30)`  | PL/SQL variable name of subfield in aggregate data for reference in PL/SQL. Max length =\> PL/SQL variable length                                                                                                                                |
| `updtdate` | `date`          | Audit-trail date/time this control record last updated.                                                                                                                                                                                          |
| `updtuser` | `varchar2(30)`  | Audit-trail user id/program which last updated this record.                                                                                                                                                                                      |
| `fld#`     | `number(9,0)`   | Clause or field within data definition id no.<br>Foreign key.<br>`pga_data_values(fld#)`.<br>Set from an Oracle sequence object.                                                                                                                 |
| `pos#`     | `number(9,0)`   | Relative position number of each field defined within an aggregate data item (for example, 1, 2 3, and so on) or `NULL` if data is atomic.                                                                                                       |
| `usage`    | `varchar2(6)`   | Usage of this data field:<br>'`PASS`', '`SKIP`', '`NULL`', '`ASIS`'.<br>Max length =\> 4-char string length                                                                                                                                      |
| `mask`     | `varchar2(30)`  | Datatype or Mask value. For example:<br>'`S9(4)`'<br>'`X(24)`'<br>'`VARCHAR2(24)`'<br>'`BINARY_INTEGER(16)`'<br>`NULL`<br>When `NULL`, item defined is assumed to be a COBOL group or PL/SQL nested record.<br>Max length =\> arbitrarily chosen |
| `maskopts` | `varchar2(100)` | Datatype or Mask options value. For example:<br>'`USAGE COMP-4`'<br>'`DISPLAY`'<br>`NULL`<br>Max length =\> arbitrarily chosen                                                                                                                   |

##### pga_data_attr

The `pga_data_attr` table defines all possible data attribute names allowed by PGA and relates each attribute name to a number and type, by which the value of this attribute for a specific data item can be selected from `pga_data_values`.

The `pga_data_attr` table is also used for integrity checks of data attributes when new data items are defined.

There is one entry in the `pga_data_attr` table for every possible attribute name to which any PGA supported data item might relate.

Table A-21 This 3-column table presents the column, type and content information for `pga_data_attr`:

Table A-21 pga_data_attr

| Column     | Type           | Content                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|:-----------|:---------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name`     | `varchar2(16)` | Character string name of attribute.<br>Primary key.<br>Contains:<br>`"LEVEL"`<br>`"RENAMEMF" (renames member first)`<br>`"RENAMEML" (renames member last)`<br>`"REMAPSMF" (redefines member first)`<br>`"REMAPSML" (redefines member last)`<br>`"REMAPSWM" (redefines when member)`<br>`"REMAPSWC" (redefines when char value)`<br>`"REMAPSWN" (redefines when num value)`<br>`"REPGRPFF" (occurs n)`<br>`"REPGRPVF" (odo first n)`<br>`"REPGRPVL" (odo last n)`<br>`"REPGRPVM" (odo depending member)`<br>`"REPGRPKA" (either Key Asc name)`<br>`"REPGRPKD" (either Key Desc name)`<br>`"REPGRPIX" (either index name)`<br>`"PLSTYPE"`<br>`"JUST"     (justified char data)`<br>`"SYNC"     (aligned aggregate data)`<br>`"LOCAL_LANGUAGE"`<br>`"REMOTE_LANGUAGE"`<br>`"LENGTH"   (LENGTH IS variable)`<br>`Max length => attr name string lengths ` |
| `attr#`    | `number(9,0)`  | Attribute id assigned.<br>Foreign key.<br>pga_data_values(attr#). Set from an Oracle sequence object for each supported data attribute inserted into the PG DD.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `coltype`  | `varchar2(4)`  | Type of Oracle column from which attribute value is retrieved from pga_data_values. For example:<br>'`NUM ' => pga_data_values(numval)`<br>'`CHAR'=> pga_data_values(charval``)`<br>'`DATE' => pga_data_values(dateval)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `required` | `char(1)`      | If not null, required keyword.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |

##### pga_data_values

A row exists in the `pga_data_values` table for each attribute of each data item defined by each data definition.

Table A-22 This 3-column table presents the column, type and content information for `pga_data_values`:

Table A-22 pga_data_values

| Column    | Type           | Content                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|:----------|:---------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `fld#`    | `number(9,0)`  | Data Field Definition number from pga_data(fld#). Primary key.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `attr#`   | `number(9,0)`  | Attribute id from `pga_data_attr(attr#)`.<br>Primary key.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `numval`  | `number(9,0)`  | Attribute's numeric value. For example:<br>`number for "LEVEL"`<br>`number for "REMAPSWN" (redefines)`<br>`number for "REPGRPFF" (occurs n)`<br>`number for "REPGRPVF" (odo first n)`<br>`number for "REPGRPVL" (odo last n)`<br>If a non-numeric attribute, this item is `NULL`.                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `charval` | `varchar2(40)` | Attribute's character value.<br>`fname for "RENAMEMF (renames first)`<br>`fname for "RENAMEML" (renames last)`<br>`fname for "REMAPSMF" (redefines first)`<br>`fname for "REMAPSML" (redefines last)`<br>`fname for "REMAPSWM" (redefines when)`<br>`fname for "REPGRPVM" (odo member)`<br>`string for "REMAPSWC" (redefines)`<br>`string for "REPGRPKA" (occurs key)`<br>`string for "REPGRPKD" (occurs key)`<br>`string for "REPGRPIX" (occurs index)`<br>`string for "PLSTYPE" (PL/SQL data type)`<br>`string for "JUST"`<br>`string for "SYNC"`<br>`string for "REMOTE_LANGUAGE"`<br>`fname for "LENGTH"`<br>If a non-character attribute, this item is `NULL`.<br>Max length =\> NLS_charset string length |
| `dateval` | `date`         | Attribute's date value. Always null, included for completeness.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `qual`    | `number (9,0)` | Qualified name number.<br>Foreign key.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
