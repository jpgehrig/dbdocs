You can execute user-defined functions in a remote non-Oracle database.

For example:

    SELECT getdeptforemp@Remote_DB(7782) FROM dual;

In this example, a `SELECT` statement was issued that executes a user-defined function in the remote database that returns department information for employee 7782.

When the remote function resides in an Oracle database, the Oracle database automatically ensures that the remote function does not update any database state (such as updating rows in a database or updating the PL/SQL package state). The gateway cannot verify this when the remote function resides in a non-Oracle database. Therefore, you are responsible for ensuring that the user-defined functions do not update the state in any database. Ensuring no updates to the database is required to guarantee read consistency.

As a security measure, you must specify the functions that you want to execute remotely and their owners in the `HS_CALL_NAME` parameter in the gateway-specific initialization parameter file. For example:

    HS_CALL_NAME = "owner1.A1, owner2.A2 "

`owner1` and `owner2` are the remote function owner names. `A1` and `A2` are the remote function names. You do not need to specify the remote function owner in the SQL statement. By default, the remote function needs to reside in the schema that the Database Gateway connects to. If this is not the case, then you must specify the owner of the remote function in the SQL statement.

Some other examples of executing user-defined remote functions are as follows:

- A remote function in a subquery

  The function uses the `employee_id` column data to retrieve the `department_id` from the `EMPLOYEES` table in the remote database. The outer query then determines all department numbers in the remote database that match the returned list.

      SELECT * FROM departments@remotedb
        WHERE department_id IN
           (SELECT
            getdeptforemp@remotedb (employee_id)
            FROM employees@remotedb);

<!-- -->

- Applying a local function to the result of a user-defined remote function

  This query returns the maximum salary of all employees on the remote database.

      SELECT max (getsalforemp@remotedb (employee_id))
         FROM employees@remotedb;

<!-- -->

- A DML statement

  The statement uses the output from a user-defined query in the remote database to update the salary column with new salary information.

      UPDDATE employee_history
         SET salary = emp_changed_salary@remote_db;

In these examples, the Oracle database passes the function name and owner to the Database Gateway. The user-defined function is executed on the remote database.

**Parent topic:** [Using Heterogeneous Services Agents](using-heterogeneous-services-agents.md)
