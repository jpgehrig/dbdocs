Overloading allows you to substitute a subtype value for a formal parameter that is a supertype. This capability is known as substitutability.

The following rules are about overloading and substitutability.

### Rules of Substitution

If more than one instance of an overloaded procedure matches the procedure call, the following substitution rules determine which procedure, if any, is called:

- If the signatures of the overloaded procedures only differ in that some parameters are object types from the same supertype-subtype hierarchy, the closest match is used. The closest match is one where all the parameters are at least as close as any other overloaded instance, as determined by the depth of inheritance between the subtype and supertype, and at least one parameter is closer.

- If instances of two overloaded methods match, and some argument types are closer in one overloaded procedure while others are closer in the second procedure, a semantic error occurs.

- If some parameters differ in their position within the object type hierarchy, and other parameters are of different data types so that an implicit conversion would be necessary, then a semantic error occurs.

### 3.3.1 Resolving PL/SQL Functions with Inheritance

Resolving PL/SQL functions with inheritance follows the rules of substitution.

Example 3-9 creates a type hierarchy that has three levels starting with `super_t`. There is a package with two overloaded instances of a function that are the same except for the position of the argument type in the type hierarchy. The invocation declares a variable of type `final_t`, and then calls the overloaded function.

The instance of the function that executes is the one that accepts a `sub_t` parameter, because `sub_t` is closer to `final_t` than `super_t` in the hierarchy. This follows the rules of substitution.

Note that because determining which instance to call happens at compile time, the fact that the argument passed in was also a `final_t` is ignored. If the declaration was `v` `super_t` `:=` `final_t(1,2,3)`, the overloaded function with the argument `super_t` would be called.

Example 3-9 Resolving PL/SQL Functions With Inheritance

    CREATE OR REPLACE TYPE super_t AS OBJECT
      (n NUMBER) NOT final;
    /
    CREATE OR REPLACE TYPE sub_t UNDER super_t
      (n2 NUMBER) NOT final;
    /
    CREATE OR REPLACE TYPE final_t UNDER sub_t
      (n3 NUMBER);
    /
    CREATE OR REPLACE PACKAGE p IS
       FUNCTION func (arg super_t) RETURN NUMBER;
       FUNCTION func (arg sub_t) RETURN NUMBER;
    END;
    /
    CREATE OR REPLACE PACKAGE BODY p IS
       FUNCTION func (arg super_t) RETURN NUMBER IS BEGIN RETURN 1; END;
       FUNCTION func (arg sub_t) RETURN NUMBER IS BEGIN RETURN 2; END;
    END;
    /

    DECLARE
      v final_t := final_t(1,2,3);
    BEGIN
      DBMS_OUTPUT.PUT_LINE(p.func(v));  -- prints 2
    END;
    /

**See Also:**

See Use of Overloading in PL/SQL with Inheritance

### 3.3.2 Resolving PL/SQL Functions with Inheritance Dynamically

Dynamically resolving PL/SQL functions with inheritance follows the rules of substitution.

See Use of Overloading in PL/SQL with Inheritance

In Example 3-10, determining which instance to call happens at run time because the functions are overriding member functions of the type hierarchy. This is dynamic method dispatch, described in "[Dynamic Method Dispatch](inheritance-in-sql-object-types.md)".

Though `v` is an instance of `super_t`, because the value of `final_t` is assigned to `v`, the `sub_t` instance of the function is called, following the rules of substitution.

Example 3-10 Resolving PL/SQL Functions With Inheritance Dynamically

    -- Perform the following drop commands if you created these objects in Ex. 3-9
    -- DROP PACKAGE p;
    -- DROP TYPE final_t;
    -- DROP TYPE _sub_t;
    -- DROP TYPE super_t FORCE;
    CREATE OR REPLACE TYPE super_t AS OBJECT
      (n NUMBER, MEMBER FUNCTION func RETURN NUMBER) NOT final;
    /
    CREATE OR REPLACE TYPE BODY super_t AS
     MEMBER FUNCTION func RETURN NUMBER IS BEGIN RETURN 1; END; END;
    /
    CREATE TYPE sub_t UNDER super_t
      (n2 NUMBER,
       OVERRIDING MEMBER FUNCTION func RETURN NUMBER) NOT final;
    /
    CREATE OR REPLACE TYPE BODY sub_t AS
     OVERRIDING MEMBER FUNCTION func RETURN NUMBER IS BEGIN RETURN 2; END; END;
    /
    CREATE OR REPLACE TYPE final_t UNDER sub_t
      (n3 NUMBER);
    /

    DECLARE
      v super_t := final_t(1,2,3);
    BEGIN
      DBMS_OUTPUT.PUT_LINE('answer:'|| v.func); -- prints 2
    END;
    /
