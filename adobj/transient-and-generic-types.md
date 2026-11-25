Oracle database has three generic (that is, generically programmed) SQL data types that enable you to dynamically encapsulate and access type descriptions, data instances, and sets of data instances of any other SQL type, including object and collection types. You can also use these three types to create anonymous types, including anonymous collection types.

The three SQL types are implemented as opaque types. In other words, the internal structure of these types is not known to the database; their data can be queried only by implementing functions (typically 3GL routines) for the purpose. Oracle database provides both an OCI and a PL/SQL API for implementing such functions.

Of the three types, `ANYTYPE` is transient, and `ANYDATA` and `ANYDATASET` are not transient, but rather persistent. Transient types cannot be persistently stored because their structures are opaque to the database. You cannot create columns of transient types or make them attributes of persistent types.

Beginning with Oracle Database release 12c, release 12.2, transient types can be created on Active Data Guard instance if:

1.  Real Time Apply is running on Active Data Guard, and

2.  Logical Standby is not lagging far behind the Primary (typically, order of seconds).

The three generic SQL types are described in Table 8-2.

Table 8-2 Generic SQL Types

| Type             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|:-----------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `SYS.ANYTYPE`    | A type description type. A `SYS.ANYTYPE` can contain a type description of any SQL type, named or unnamed, including object types and collection types.<br>An `ANYTYPE` can contain a type description of a persistent type, but an `ANYTYPE` itself is transient: in other words, the value in an `ANYTYPE` itself is not automatically stored in the database. To create a persistent type, use a `CREATE TYPE` statement from SQL.                                                       |
| `SYS.ANYDATA`    | A self-describing data instance type. A `SYS.ANYDATA` contains an instance of a given type, with data, plus a description of the type. In this sense, a `SYS.ANYDATA` is self-describing. An `ANYDATA` can be persistently stored in the database.<br>The following cannot be stored in an `ANYDATA` column:<br>• Another opaque type except `XMLTYPE`<br>• LOB types (`BLOB`/`CLOB`/`NCLOB`)<br>• `VARRAY` types with maximum size greater than 4K<br>• Transient types                    |
| `SYS.ANYDATASET` | A self-describing data set type. A `SYS.ANYDATASET` type contains a description of a given type plus a set of data instances of that type. An `ANYDATASET` can be persistently stored in the database.<br>The following cannot be stored in an `ANYDATASET` column:<br>• Another opaque type such as `ANYDATA` or `XMLTYPE`<br>• LOB types (`BLOB`/`CLOB`/`NCLOB`)<br>• `VARRAY` types with maximum size greater than 4K<br>• ADTs that contain any of the above types<br>• Transient types |

Each of these three types can be used with any built-in type native to the database as well as with object types and collection types, both named and unnamed. The types provide a generic way to work dynamically with type descriptions, lone instances, and sets of instances of other types. Using the APIs, you can create a transient `ANYTYPE` description of any kind of type. Similarly, you can create or convert (cast) a data value of any SQL type to an `ANYDATA` and can convert an `ANYDATA` (back) to a SQL type. And similarly again with sets of values and `ANYDATASET`.

The generic types simplify working with stored procedures. You can use the generic types to encapsulate descriptions and data of standard types and pass the encapsulated information into parameters of the generic types. In the body of the procedure, you can detail how to handle the encapsulated data and type descriptions of whatever type.

You can also store encapsulated data of a variety of underlying types in one table column of type `ANYDATA` or `ANYDATASET`. For example, you can use `ANYDATA` with Advanced Queuing to model queues of heterogeneous types of data. You can query the data of the underlying data types like any other data.

Example 8-10 defines and executes a PL/SQL procedure that uses methods built into `SYS.ANYDATA` to access information about data stored in a `SYS.ANYDATA` table column.

Example 8-10 Using SYS.ANYDATA

    CREATE OR REPLACE TYPE dogowner AS OBJECT (
        ownerno NUMBER, ownername VARCHAR2(10) );
    /
    CREATE OR REPLACE TYPE dog AS OBJECT (
        breed VARCHAR2(10), dogname VARCHAR2(10) );
    /
    CREATE TABLE mytab ( id NUMBER, data SYS.ANYDATA );
    INSERT INTO mytab VALUES ( 1, SYS.ANYDATA.ConvertNumber (5) );
    INSERT INTO mytab VALUES ( 2, SYS.ANYDATA.ConvertObject (
        dogowner ( 5555, 'John') ) );
    commit;

    CREATE OR REPLACE procedure P IS
      CURSOR cur IS SELECT id, data FROM mytab;

      v_id mytab.id%TYPE;
      v_data mytab.data%TYPE;
      v_type SYS.ANYTYPE;
      v_typecode PLS_INTEGER;
      v_typename VARCHAR2(60);
      v_dummy PLS_INTEGER;
      v_n NUMBER;
      v_dogowner dogowner;
      non_null_anytype_for_NUMBER exception;
      unknown_typename exception;

    BEGIN
      OPEN cur;
        LOOP
          FETCH cur INTO v_id, v_data;
          EXIT WHEN cur%NOTFOUND;
          v_typecode := v_data.GetType ( v_type /* OUT */ );
          CASE v_typecode
            WHEN Dbms_Types.Typecode_NUMBER THEN
              IF v_type IS NOT NULL
                THEN RAISE non_null_anytype_for_NUMBER; END IF;
              v_dummy := v_data.GetNUMBER ( v_n /* OUT */ );
              Dbms_Output.Put_Line (
                To_Char(v_id) || ': NUMBER = ' || To_Char(v_n) );
            WHEN Dbms_Types.Typecode_Object THEN
              v_typename := v_data.GetTypeName();
              IF v_typename NOT IN ( 'HR.DOGOWNER' )
                THEN RAISE unknown_typename; END IF;
              v_dummy := v_data.GetObject ( v_dogowner /* OUT */ );
              Dbms_Output.Put_Line (
                To_Char(v_id) || ': user-defined type = ' || v_typename ||
                '(' || v_dogowner.ownerno || ', ' || v_dogowner.ownername || ' )' );
          END CASE;
        END LOOP;
        CLOSE cur;

    EXCEPTION
      WHEN non_null_anytype_for_NUMBER THEN
          RAISE_Application_Error ( -20000,
            'Paradox: the return AnyType instance FROM GetType ' ||
            'should be NULL for all but user-defined types' );
      WHEN unknown_typename THEN
          RAISE_Application_Error ( -20000,
            'Unknown user-defined type ' || v_typename ||
            ' - program written to handle only HR.DOGOWNER' );
    END;
    /

    SELECT t.data.gettypename() FROM mytab t;
    SET SERVEROUTPUT ON;
    EXEC P;

The query and the procedure P in the preceding code sample produce output like the following:

    T.DATA.GETTYPENAME()
    -------------------------------------------------------------
    SYS.NUMBER
    HR.DOGOWNER
    1: NUMBER = 5
    2: user-defined type = HR.DOGOWNER(5555, John )

Corresponding to the three generic SQL types are three OCI types that model them. Each has a set of functions for creating and accessing the respective type:

- `OCIType`: corresponds to `SYS.ANYTYPE`

- `OCIAnyData`: corresponds to `SYS.ANYDATA`

- `OCIAnyDataSet`: corresponds to `SYS.ANYDATASET`

  **See Also:**

  - [Oracle Call Interface Programmer's Guide](../lnoci/object-relational-data-types-in-oci.md) for the `OCIType`, `OCIAnyData`, and `OCIAnyDataSet` APIs and details on how to use them

  - [Oracle Database PL/SQL Packages and Types Reference](../arpls/introduction-to-oracle-supplied-plsql-packages-and-types.md) for information about the interfaces to the `ANYTYPE`, `ANYDATA`, and `ANYDATASET` types and the `DBMS_TYPES` package, which defines constants for built-in and user-defined types, for use with `ANYTYPE`, `ANYDATA`, and `ANYDATASET`
