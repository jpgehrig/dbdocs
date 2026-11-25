Dynamic SQL is a feature of PL/SQL that enables you to enter SQL information, such as a table name, the full text of a SQL statement, or variable information at run-time.

Topics:

- Using Dynamic SQL with Object Types and Collections

- Calling Package Procedures wtih Object Types and Collections

**See Also:**

[Oracle Database PL/SQL Language Reference](../lnpls/dynamic-sql.md)

### 3.4.1 Using Dynamic SQL with Object Types and Collections

You can use dynamic SQL with object types and collections.

Example 3-11 illustrates the use of objects and collections with dynamic SQL. First, the example defines the object type `person_typ` and the `VARRAY` type `hobbies_var`, then it defines the package, `teams`, that uses these types.

You need `AUTHID` `CURRENT_USER` to execute dynamic package methods; otherwise, these methods raise an insufficient privileges error when you run Example 3-12, which is an anonymous block that calls the procedures in package `TEAMS`.

Example 3-11 A Package that Uses Dynamic SQL for Object Types and Collections

    CREATE OR REPLACE TYPE person_typ AS OBJECT (name VARCHAR2(25), age NUMBER);
    /
    CREATE TYPE hobbies_var AS VARRAY(10) OF VARCHAR2(25);
    /
    CREATE OR REPLACE PACKAGE teams

       AUTHID CURRENT_USER AS
       PROCEDURE create_table (tab_name VARCHAR2);
       PROCEDURE insert_row (tab_name VARCHAR2, p person_typ, h hobbies_var);
       PROCEDURE print_table (tab_name VARCHAR2);
    END;
    /
    CREATE OR REPLACE PACKAGE BODY teams AS
       PROCEDURE create_table (tab_name VARCHAR2) IS
       BEGIN
          EXECUTE IMMEDIATE 'CREATE TABLE ' || tab_name ||
                            ' (pers person_typ, hobbs hobbies_var)';
       END;
       PROCEDURE insert_row (
          tab_name VARCHAR2,
          p person_typ,
          h hobbies_var) IS
       BEGIN
          EXECUTE IMMEDIATE 'INSERT INTO ' || tab_name ||
             ' VALUES (:1, :2)' USING p, h;
       END;
       PROCEDURE print_table (tab_name VARCHAR2) IS
          TYPE  refcurtyp IS REF CURSOR;
          v_cur refcurtyp;
          p     person_typ;
          h     hobbies_var;
       BEGIN
          OPEN v_cur FOR 'SELECT pers, hobbs FROM ' || tab_name;
          LOOP
             FETCH v_cur INTO p, h;
             EXIT WHEN v_cur%NOTFOUND;
             -- print attributes of 'p' and elements of 'h'
             DBMS_OUTPUT.PUT_LINE('Name: ' || p.name || ' - Age: ' || p.age);
             FOR i IN h.FIRST..h.LAST
             LOOP
               DBMS_OUTPUT.PUT_LINE('Hobby(' || i || '): ' || h(i));
             END LOOP;
          END LOOP;
          CLOSE v_cur;
       END;
    END;
    /

### 3.4.2 Calling Package Procedures with Object Types and Collections

You can call package procedures with object types and collections.

From an anonymous block,Example 3-12, you might call the procedures in package `TEAMS `as shown in Example 3-11

Example 3-12 Calling Procedures from the TEAMS Package

    DECLARE
       team_name VARCHAR2(15);
    BEGIN
       team_name := 'Notables';
       TEAMS.create_table(team_name);
       TEAMS.insert_row(team_name, person_typ('John', 31),
          hobbies_var('skiing', 'coin collecting', 'tennis'));
       TEAMS.insert_row(team_name, person_typ('Mary', 28),
          hobbies_var('golf', 'quilting', 'rock climbing', 'fencing'));
       TEAMS.print_table(team_name);
    END;
    /
