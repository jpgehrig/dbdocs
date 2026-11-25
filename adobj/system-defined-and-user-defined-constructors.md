There are various aspects to system-defined constructors, also known as attribute-value constructors, and user-defined constructors.

Topics:

- The Attribute-Value Constructor

- Constructors and Type Evolution

- Advantages of User-Defined Constructors

- Defining and Implementing User-Defined Constructors

- Overloaded and Hidden Constructors

- Calling User-Defined Constructors

- Constructors for SQLJ Object Types

### 8.5.1 The Attribute-Value Constructor

The system-defined constructor, also known as the attribute-value constructor, requires you to pass the constructor a value for each attribute of the type. The constructor then sets the attributes of the new object instance to those values, as shown in Example 8-6.

The keyword `NEW` preceding a call to a constructor is optional but recommended.

Example 8-6 Setting the attribute-value with the Constructor

    CREATE TYPE shape AS OBJECT (
        name VARCHAR2(30),
        area NUMBER);
    /
    CREATE TABLE building_blocks of shape;

    -- attribute-value constructor: Sets instance attributes to the specified values
    INSERT INTO building_blocks
      VALUES (
        NEW shape('my_shape', 4));

### 8.5.2 Constructors and Type Evolution

The attribute-value constructor saves you the trouble of defining your own constructors for a type. However, you must supply a value for every attribute declared in the type or the constructor call fails to compile.

This requirement can create a problem if you evolve the type later on, especially because the attribute-value constructor is implicit and not visible in the code, unlike a user-defined constructor. When you change the attributes of a type, the attribute-value constructor of the type changes, too. If you add an attribute, the updated attribute-value constructor expects a value for the new attribute; otherwise, any attribute-value constructor calls in your existing code fail.

**See Also:**

"[Type Evolution](type-evolution.md)"

### 8.5.3 Advantages of User-Defined Constructors

User-defined constructors do not need to explicitly set a value for every attribute of a type, unlike attribute-value constructors.

A user-defined constructor can have any number of arguments, of any type, and these do not need to map directly to type attributes. When you define a constructor, you can initialize the attributes to any appropriate values. For any attributes which you do not supply values, the system initialized to `NULL`.

If you evolve a type—for example, by adding an attribute—calls to user-defined constructors for the type do not need to be changed. User-defined constructors are not automatically modified when the type evolves, so their signatures remain the same. You may, however, need to change the definition of the constructor if you do not want the new attribute to be initialized to `NULL`.

### 8.5.4 Defining and Implementing User-Defined Constructors

You define user-defined constructors in the type body, like an ordinary method. You introduce the declaration and the definition with the phrase `CONSTRUCTOR FUNCTION` and end with the clause `RETURN SELF AS RESULT`.

A constructor for a type must have the same name as the type. Example 8-7 defines two constructor functions for the `shape` type. As the example shows, you can overload user-defined constructors by defining multiple versions with different signatures.

Example 8-7 Defining and Implementing User-Defined Constructors

    CREATE TYPE shape AS OBJECT (
        name VARCHAR2(30),
        area NUMBER,
        CONSTRUCTOR FUNCTION shape(SELF IN OUT NOCOPY shape, name VARCHAR2)
                                   RETURN SELF AS RESULT,
        CONSTRUCTOR FUNCTION shape(SELF IN OUT NOCOPY shape, name VARCHAR2,
                                   area NUMBER) RETURN SELF AS RESULT
    ) NOT FINAL;
    /

    CREATE TYPE BODY shape AS
        CONSTRUCTOR FUNCTION shape(SELF IN OUT NOCOPY shape, name VARCHAR2)
                                   RETURN SELF AS RESULT IS
        BEGIN
            SELF.name := name;
            SELF.area := 0;
            RETURN;
        END;
        CONSTRUCTOR FUNCTION shape(SELF IN OUT NOCOPY shape, name VARCHAR2,
                                    area NUMBER) RETURN SELF AS RESULT IS
        BEGIN
            SELF.name := name;
            SELF.area := area;
            RETURN;
        END;
    END;
    /

A user-defined constructor has an implicit first parameter `SELF`. Specifying this parameter in the declaration of a user-defined constructor is optional. If you do specify it, you must declare its mode to be `IN OUT`.

The required clause `RETURN SELF AS RESULT` ensures that the most specific type of the instance being returned is the same as the most specific type of the `SELF` argument. In the case of constructors, this is the type for which the constructor is defined. For example, if the most specific type of the `SELF` argument on a call to the `shape` constructor is `shape`, then this clause ensures that the `shape` constructor returns an instance of `shape` (not an instance of a subtype of `shape`).

When a constructor function is called, the system initializes the attributes of the `SELF` argument to `NULL`. Names of attributes subsequently initialized in the function body may be qualified with `SELF`, such as `SELF.name` in Example 8-7, to distinguish them from the names of the arguments of the constructor function, if these are the same. If the argument names are different, this qualification is not necessary.

The function body must include an explicit `return;` as shown. The return keyword must not be followed by a `return` expression. The system automatically returns the newly constructed `SELF` instance.

A user-defined constructor may be implemented in PL/SQL, C, or Java.

### 8.5.5 Overloaded and Hidden Constructors

You can overload user-defined constructors, like other type methods.

User-defined constructors are not inherited, so a user-defined constructor defined in a supertype cannot be hidden in a subtype. However, a user-defined constructor does hide, and thus supersede, the attribute-value constructor for its type if the signature of the user-defined constructor exactly matches the signature of the attribute-value constructor.

For the signatures to match, the names and types of the parameters (after the implicit `SELF` parameter) of the user-defined constructor must be the same as the names and types of the attributes of the type. The mode of the parameters (after the implicit `SELF` parameter) of the user-defined constructor must be `IN`.

If an attribute-value constructor is not hidden by a user-defined constructor that has the same name and signature, the attribute-value constructor can still be called.

Note that, if you evolve a type—for example, by adding an attribute—the signature of the attribute-value constructor of the type changes accordingly. This can cause a formerly hidden attribute-value constructor to become usable again.

### 8.5.6 Calling User-Defined Constructors

You call a user-defined constructor like any other function and you can use it anywhere you can use an ordinary function.

The `SELF` argument is passed in implicitly and may not be passed in explicitly. In other words, usages like the following are not allowed:

`NEW constructor(instance, argument_list)`

A user-defined constructor cannot occur in the `DEFAULT` clause of a `CREATE` or `ALTER` `TABLE` statement, but an attribute-value constructor can. The arguments to the attribute-value constructor must not contain references to PL/SQL functions or to other columns, including the pseudocolumns `LEVEL`, `PRIOR`, and `ROWNUM`, or to date constants that are not fully specified. The same is true for check constraint expressions: an attribute-value constructor can be used as part of check constraint expressions while creating or altering a table, but a user-defined constructor cannot.

Parentheses are required in SQL even for constructor calls that have no arguments. In PL/SQL, parentheses are optional when invoking a zero-argument constructor. They do, however, make it more obvious that the constructor call is a function call. The following PL/SQL example omits parentheses in the constructor call to create a new shape:

`shape s := NEW my_schema.shape;`

The `NEW` keyword and the schema name are optional.

Example 8-8 creates a subtype under the type created in Example 8-7 and shows examples for calling the user-defined constructors.

Example 8-8 Calling User-Defined Constructors

    -- Requires Ex. 8-8
    CREATE TYPE rectangle UNDER shape (
        len NUMBER,
        wth NUMBER,
        CONSTRUCTOR FUNCTION rectangle(SELF IN OUT NOCOPY rectangle,
            name VARCHAR2, len NUMBER, wth NUMBER) RETURN SELF as RESULT,
        CONSTRUCTOR FUNCTION rectangle(SELF IN OUT NOCOPY rectangle,
            name VARCHAR2, side NUMBER) RETURN SELF as RESULT);
    /
    SHOW ERRORS
    CREATE TYPE BODY rectangle IS
        CONSTRUCTOR FUNCTION rectangle(SELF IN OUT NOCOPY rectangle,
            name VARCHAR2, len NUMBER, wth NUMBER) RETURN  SELF AS RESULT IS
        BEGIN
            SELF.name := name;
            SELF.area := len*wth;
            SELF.len := len;
            SELF.wth := wth;
            RETURN ;
        END;
        CONSTRUCTOR FUNCTION rectangle(SELF IN OUT NOCOPY rectangle,
            name VARCHAR2, side NUMBER) RETURN  SELF AS RESULT IS
        BEGIN
            SELF.name := name;
            SELF.area := side * side;
            SELF.len := side;
            SELF.wth := side;
            RETURN ;
        END;
    END;
    /

    CREATE TABLE shape_table OF shape;
    INSERT INTO shape_table VALUES(shape('shape1'));
    INSERT INTO shape_table VALUES(shape('shape2', 20));
    INSERT INTO shape_table VALUES(rectangle('rectangle', 2, 5));
    INSERT INTO shape_table VALUES(rectangle('quadrangle', 12, 3));
    INSERT INTO shape_table VALUES(rectangle('square', 12));

The following query selects the rows in the `shape_table`:

    SELECT VALUE(s) FROM shape_table s;

    VALUE(S)(NAME, AREA)
    ---------------------------------------------
    SHAPE('shape1', 0)
    SHAPE('shape2', 20)
    RECTANGLE('rectangle', 10, 2, 5)
    RECTANGLE('quadrangle', 36, 12, 3)
    RECTANGLE('square', 144, 12, 12)

The following PL/SQL code calls the constructor:

`s shape := NEW shape('void');`

### 8.5.7 Constructors for SQLJ Object Types

A SQLJ object type is a SQL object type mapped to a Java class. A SQLJ object type has an attribute-value constructor. It can also have user-defined constructors that are mapped to constructors in the referenced Java class.

Example 8-9 Creating a SQLJ Object

    CREATE TYPE address AS OBJECT
       EXTERNAL NAME 'university.address' LANGUAGE JAVA
       USING SQLData(
         street   VARCHAR2(100) EXTERNAL NAME 'street',
         city     VARCHAR2(50)  EXTERNAL NAME 'city',
         state    VARCHAR2(50)  EXTERNAL NAME 'state',
         zipcode  NUMBER        EXTERNAL NAME 'zipcode',
        CONSTRUCTOR FUNCTION address (SELF IN OUT NOCOPY address, street VARCHAR2,
                                      city VARCHAR2, state VARCHAR2, zipcode NUMBER)
          RETURN SELF AS RESULT AS LANGUAGE JAVA
          NAME  'university.address (java.lang.String, java.lang.String,
                          java.lang.String, int) return address');
    /

A SQLJ type of a serialized representation can have only a user-defined constructor. The internal representation of an object of SQLJ type is opaque to SQL, so an attribute-value constructor is not possible for a SQLJ type.
