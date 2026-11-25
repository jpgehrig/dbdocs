To run an external procedure, you must call the PL/SQL program unit (that is, the alias for the external function) that registered the external procedure.

These calls can appear in any of the following:

- Anonymous blocks

- Standalone and packaged subprograms

- Methods of an object type

- Database triggers

- SQL statements (calls to packaged functions only)

In “Registering an External Procedure”, PL/SQL function `PLS_MAX` registered external procedure `find_max`. Follow these steps to run `find_max`:

1.  Call PL/SQL function `PLS_MAX` from a PL/SQL routine named `UseIt`:
        SET SERVER OUTPUT ON
        CREATE OR REPLACE PROCEDURE UseIt AS
                    a integer;
                    b integer;
                    c integer;
        BEGIN
                    a := 1;
                    b := 2;
                    c := PLS_MAX(a,b);
                    dbms_output.put_line('The maximum of '||a||' and '||b||' is  '||c);
        END;
2.  Run the routine:
        SQL> EXECUTE UseIt;

**Related Topics**

- [Registering an External Procedure](registering-an-external-procedure.md)

**Parent topic:** [About Building External Procedures](about-building-external-procedures.md)
