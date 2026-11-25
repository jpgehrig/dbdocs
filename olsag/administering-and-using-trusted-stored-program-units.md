You can use trusted stored program units to enhance system security.

- About Trusted Stored Program Units
  Oracle Database stored procedures, functions, and packages are sets of PL/SQL statements stored in a database in compiled form.
- How a Trusted Stored Program Unit Runs
  A trusted stored program unit runs using its own privileges, and the caller's labels.
- Example: Trusted Stored Program Unit
  A trusted stored program unit with the `READ` privilege can read all unprotected data and all data protected by this policy.
- Creating and Compiling Trusted Stored Program Units
  You can create and compile trusted stored program units for use in Oracle Label Security.
- How Setting and Returning Label Information Works
  The `SA_UTL` package has functions to return information about current values of session security attributes using numeric label values.

**Parent topic:** [Administering an Oracle Label Security Application](part3.md)

### 12.1 About Trusted Stored Program Units

Oracle Database stored procedures, functions, and packages are sets of PL/SQL statements stored in a database in compiled form.

The single difference between functions and procedures is that functions return a value and procedures do not. Trusted stored program units are like any other stored program units in Oracle Database: the underlying logic is the same.

A package is a set of procedures and functions, together with the cursors and variables they use, stored as a unit. There are two parts to a package, the package specification and the package body. The package specification declares the external definition of the public procedures, functions, and variables that the package contains. The package body contains the actual text of the procedures and functions, as well as any private procedures and variables.

A trusted stored program unit is a stored procedure, function, or package that has been granted one or more Oracle Label Security privileges. Trusted stored program units are typically used to let users perform privileged operations in a controlled manner, or update data at several labels. This is the optimal approach to permit users to access data beyond their authorization.

Trusted stored program units provide fine-grained control over the use of privileges. Although you can potentially grant privileges to many users, the granting of privileges should be done with great discretion because it might violate the security policy established for your application. Rather than assigning privileges to users, you can identify any application operations requiring privileges, and implement them as trusted program units. When you grant privileges to these stored program units, you effectively restrict the Oracle Label Security privileges required by users. This approach employs the principle of least privilege.

For example, if a user with the label `CONFIDENTIAL` needs to insert data into `SENSITIVE` rows, then you can grant the `WRITEUP` privilege to a trusted stored program to which the user has access. In this way, the user can perform the task by means of the trusted stored program, while staying at the `CONFIDENTIAL` level.

The trusted program unit performs all the actions on behalf of the user. You can thus effectively encapsulate the security policy into a module that can be verified to make sure that it is valid.

**Parent topic:** Administering and Using Trusted Stored Program Units

### 12.2 How a Trusted Stored Program Unit Runs

A trusted stored program unit runs using its own privileges, and the caller's labels.

In this way, the trusted stored program unit can perform privileged operations on the set of rows constrained by the user's labels.

Oracle Database system and object privileges are intended to be bundled into roles. Users are then granted roles as necessary. By contrast, Oracle Label Security privileges can only be assigned to users or to stored program units. These trusted stored program units provide a more manageable mechanism than roles to control the use of Oracle Label Security privileges.

**Parent topic:** Administering and Using Trusted Stored Program Units

### 12.3 Example: Trusted Stored Program Unit

A trusted stored program unit with the `READ` privilege can read all unprotected data and all data protected by this policy.

Consider, for example, a user who is responsible for creating purchasing forecast reports. The user must perform a summation operation on the amount of all purchases. Regardless of whether or not user's own labels authorize access to the individual purchase orders. The syntax for creating the summation procedure in this example is as follows:

    CREATE FUNCTION sum_purchases RETURN NUMBER IS
      psum NUMBER;
    BEGIN
      SELECT SUM(amount) INTO psum
      FROM purchase_orders;
    RETURN psum;
    END sum_purchases;

In this way, the program unit can gather information the end user is not able to gather, and can make it available by means of a summation.

Note that to run `SUM_PURCHASES`, the user would need to be granted the standard Oracle Database `EXECUTE` object privilege upon this procedure.

**Related Topics**

- [Access Controls and Privileges](access-controls-and-privileges.md)

**Parent topic:** Administering and Using Trusted Stored Program Units

### 12.4 Creating and Compiling Trusted Stored Program Units

You can create and compile trusted stored program units for use in Oracle Label Security.

- Creation of Trusted Stored Program Units
  You can create a trusted stored program unit in the same way that you create a standard procedure, function, or package.
- Privileges for Trusted Stored Program Units
  An Oracle Label Security administrator can verify the correctness of a stored program unit code before granting the privileges to it.
- Recompiling of Trusted Stored Program Units
  Recompiling a trusted stored program unit, either automatically or manually (using `ALTER` `PROCEDURE`), does not affect its Oracle Label Security privileges.
- Re-creation of Trusted Stored Program Units
  Oracle Label Security privileges are revoked if you perform a `CREATE` or `REPLACE` operation on a trusted stored program unit.
- Execution of Trusted Stored Program Units
  Under Oracle Label Security all the standard Oracle Database controls on procedure call (regarding access to tables and schemas) are still in force.

**Parent topic:** Administering and Using Trusted Stored Program Units

#### 12.4.1 Creation of Trusted Stored Program Units

You can create a trusted stored program unit in the same way that you create a standard procedure, function, or package.

To do this, you can use the `CREATE` `PROCEDURE`, `CREATE` `FUNCTION`, or `CREATE` `PACKAGE` and `CREATE` `PACKAGE` `BODY` statements.

The program unit becomes trusted when you grant it Oracle Label Security privileges.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/CREATE-PROCEDURE.md)

**Parent topic:** Creating and Compiling Trusted Stored Program Units

#### 12.4.2 Privileges for Trusted Stored Program Units

An Oracle Label Security administrator can verify the correctness of a stored program unit code before granting the privileges to it.

Typically another user, such as a developer, creates the stored program unit. Whenever the trusted stored program unit is re-created or replaced, Oracle Label security removes its privileges. The Oracle Label Security administrator must then verify the code again and grant the privileges once again.

The Oracle Label Security administrator should review the program unit code carefully and evaluate the privileges that are to be granted to it. For example, procedures in trusted packages should not perform privileged database operations and then write result or status information into a public variable of the package. In this way, you can make sure that no violations of your site's Oracle Label Security policy can occur.

**Related Topics**

- [SA_USER_ADMIN.SET_PROG_PRIVS](oracle-label-security-pl-sql-packages.md)

**Parent topic:** Creating and Compiling Trusted Stored Program Units

#### 12.4.3 Recompiling of Trusted Stored Program Units

Recompiling a trusted stored program unit, either automatically or manually (using `ALTER` `PROCEDURE`), does not affect its Oracle Label Security privileges.

You must, however, grant the `EXECUTE` privilege on the program unit again after recompiling.

**Parent topic:** Creating and Compiling Trusted Stored Program Units

#### 12.4.4 Re-creation of Trusted Stored Program Units

Oracle Label Security privileges are revoked if you perform a `CREATE` or `REPLACE` operation on a trusted stored program unit.

This limits the potential for misuse of a procedure's Oracle Label Security privileges.

Note that the procedure, function, or package can still run even if the Oracle Label Security privileges have been removed.

If you re-create a procedure, function, or package, then you should carefully review its text. When you are certain that the re-created program unit does not violate your site's Oracle Label Security policy, you can then grant it the required privileges again.

In a development environment where trusted stored program units must frequently be replaced (for example, during the first few months of a live system), it is advisable to create a script that can grant the proper Oracle Label Security privileges, as required.

**Parent topic:** Creating and Compiling Trusted Stored Program Units

#### 12.4.5 Execution of Trusted Stored Program Units

Under Oracle Label Security all the standard Oracle Database controls on procedure call (regarding access to tables and schemas) are still in force.

Oracle Label Security complements these security mechanisms by controlling access to rows.

When a trusted stored program unit is carried out, the policy privileges in force are a union of the invoking user's privileges and the program unit's privileges. Whether a trusted stored program unit calls another trusted program unit or a non-trusted program unit, the program unit called runs with the same privileges as the original program unit.

If a sequence of non-trusted and trusted stored program units is carried out, the first trusted program unit will determine the privileges of the entire calling sequence from that point on. Consider the following sequence:

- Procedure A (non-trusted)
- Procedure B with `WRITEUP`
- Procedure C with `WRITEDOWN`
- Procedure D (non-trusted)

Here, Procedures B, C, and D all runs with the `WRITEUP` privilege, because B was the first trusted procedure in the sequence. When the sequence ends, the privilege pertaining to Procedure B is no longer in force for subsequent procedures.

**Note:**

Unhandled exceptions raised in trusted program units are caught by Oracle Label Security. This means that error messages may not be displayed to the user. For this reason, you should always thoroughly test and debug any program units before granting them privileges.

**Parent topic:** Creating and Compiling Trusted Stored Program Units

### 12.5 How Setting and Returning Label Information Works

The `SA_UTL` package has functions to return information about current values of session security attributes using numeric label values.

Although these functions can be used in program units that are not trusted, they are primarily for use in trusted stored program units.

Note that these are public functions; you do not need the `policy_``DBA` role to use them. In addition, each of the functions has a parallel `SA_SESSION` function that returns the same labels in character string format.

**Related Topics**

- [Duties of Oracle Label Security Administrators](introduction-to-oracle-label-security.md)

**Parent topic:** Administering and Using Trusted Stored Program Units
