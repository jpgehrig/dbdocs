## 8.3 Subprogram Invocations

A subprogram invocation has this form:

    subprogram_name [ ( [ parameter [, parameter]... ] ) ]

If the subprogram has no parameters, or specifies a default value for every parameter, you can either omit the parameter list or specify an empty parameter list.

A procedure invocation is a PL/SQL statement. For example:

    raise_salary(employee_id, amount);

A function invocation is an expression. For example:

    new_salary := get_salary(employee_id);
    IF salary_ok(new_salary, new_title) THEN ...

**See Also:**

"[Subprogram Parameters](subprogram-parameters.md)" for more information about specifying parameters in subprogram invocations
