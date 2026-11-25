To create generic object types that can be used in any schema, you must define the type to use invoker rights, through the `AUTHID` `CURRENT_USER` option of `CREATE` `OR` `REPLACE` `TYPE`.

**Note:**

For information on controlling invoker's rights privileges, see [Oracle Database Security Guide.](../dbseg/managing-security-for-definers-rights-and-invokers-rights.md)

In general, use invoker rights when both of the following conditions are true:

- There are type methods that access and manipulate data.

- Users who did not define these type methods must use them.

For example, you can grant user `OE` execute privileges on type `atype` created by HR in "[Static Methods](design-considerations-for-methods.md)", and then create table `atab` based on the type:

    GRANT EXECUTE ON atype TO oe;
    CONNECT oe;
    Enter password: password
    CREATE TABLE atab OF HR.atype ;

Now, suppose user `OE` tries to use `atype` in the following statement:

    BEGIN -- follwing call raises an error, insufficient privileges
      HR.atype.newa(1, 'atab', 'OE');
    END;
    /

This statement raises an error because the definer of the type (`HR`) does not have the privileges required to perform the insert in the `newa` procedure. You can avoid this error by defining `atype` using invoker rights. Here, you first drop the `atab` table in both schemas and re-create `atype` using invoker rights:

    DROP TABLE atab;
    CONNECT hr;
    Enter password: password

    DROP TABLE atab;
    DROP TYPE atype FORCE;
    COMMIT;

    CREATE TYPE atype AUTHID CURRENT_USER AS OBJECT(
       a1 NUMBER,
       STATIC PROCEDURE newa(p1 NUMBER, tabname VARCHAR2, schname VARCHAR2));
    /
    CREATE TYPE BODY atype AS
      STATIC PROCEDURE newa(p1 NUMBER, tabname VARCHAR2, schname VARCHAR2)
       IS
         sqlstmt VARCHAR2(100);
       BEGIN
          sqlstmt := 'INSERT INTO '||schname||'.'||tabname|| '
                      VALUES (HR.atype(:1))';
          EXECUTE IMMEDIATE sqlstmt USING p1;
       END;
    END;
    /

Now, if user `OE` tries to use `atype` again, the statement executes successfully:

    GRANT EXECUTE ON atype TO oe;
    CONNECT oe;
    Enter password: password
    CREATE TABLE atab OF HR.atype;

    BEGIN
      HR.atype.newa(1, 'atab', 'OE');
    END;
    /
    DROP TABLE atab;
    CONNECT hr;
    Enter password: password

    DROP TYPE atype FORCE;

The statement is successful this time because the procedure is executed under the privileges of the invoker (`OE`), not the definer (`HR`).

In a type hierarchy, a subtype has the same rights model as its immediate supertype. That is, it implicitly inherits the rights model of the supertype and cannot explicitly specify one. Furthermore, if the supertype was declared with definer rights, the subtype must reside in the same schema as the supertype. These rules allow invoker-rights type hierarchies to span schemas. However, type hierarchies that use a definer-rights model must reside within a single schema. For example:

    CREATE TYPE deftype1 AS OBJECT (...); --Definer-rights type
    CREATE TYPE subtype1 UNDER deftype1 (...); --subtype in same schema as supertype
    CREATE TYPE schema2.subtype2 UNDER deftype1 (...); --ERROR
    CREATE TYPE invtype1 AUTHID CURRENT_USER AS OBJECT (...); --Invoker-rights type
    CREATE TYPE schema2.subtype2 UNDER invtype1 (...); --LEGAL
