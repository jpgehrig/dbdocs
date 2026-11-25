This chapter discusses how the Oracle SQLJ implementation supports user-defined SQL types. There is also a small section at the end regarding Oracle OPAQUE types.

The chapter consists of the following sections:

- Oracle Objects and Collections

- Custom Java Classes

- User-Defined Types

- Strongly Typed Objects and References in SQLJ Executable Statements

- Strongly Typed Collections in SQLJ Executable Statements

- Serialized Java Objects

- Weakly Typed Objects\_ References\_ and Collections

- Oracle OPAQUE Types

### 7.1 Oracle Objects and Collections

This section provides some background conceptual information about Oracle Database 12c Release 2 (12.2) objects and collections.

**See Also:**

[Oracle Database SQL Language Reference ](../sqlrf/Database-Objects.md)and [Oracle Database Development Guide](../adfns/sql-data-types.md).

This section covers the following topics:

- Overview of Objects and Collections

- Oracle Object Fundamentals

- Oracle Collection Fundamentals

- Object and Collection Data Types

#### 7.1.1 Overview of Objects and Collections

The Oracle SQLJ implementation supports user-defined SQL object types, which are composite data structures, related SQL object reference types, and user-defined SQL collection types. Oracle objects and collections are composite data structures consisting of individual data elements.

The Oracle SQLJ implementation supports either strongly typed or weakly typed Java representations of object types, reference types, and collection types to use in iterators or host expressions. Strongly typed representations use a custom Java class that maps to a particular object type, reference type, or collection type and must implement either the Java Database Connectivity (JDBC) 2.0 standard `java.sql.SQLData` interface, for object types only, or the Oracle `oracle.sql.ORAData` interface.

The term strongly typed is used where a particular Java type is associated with a particular SQL named type or user-defined type. For example, if there is a `PERSON` type, then a corresponding `Person` Java class will be associated with it.

Weakly typed representations use `oracle.sql.STRUCT` for objects, `oracle.sql.REF` for object references, or `oracle.sql.ARRAY` for collections. Alternatively, you can use standard `java.sql.Struct`, `java.sql.Ref`, or `java.sql.Array` objects in a weakly typed scenario.

The term weakly typed is used where a Java type is used in a generic way and can map to multiple SQL named types. The Java class or interface has no special information particular to any SQL type. This is the case for the `oracle.sql.STRUCT`, `oracle.sql.REF`, and `oracle.sql.ARRAY` types and the `java.sql.Struct`, `java.sql.Ref`, and `java.sql.Array` types.

Note that using Oracle extensions in your code requires the following:

- Use one of Oracle JDBC drivers.

- Use default Oracle-specific code generation or, for ISO code generation, customize the profiles appropriately. For Oracle-specific generated code, no profiles are produced so customization is not applicable. Oracle JDBC application programming interfaces (APIs) are called directly through the generated Java code.

  **Note:**

  Oracle recommends the use of the default customizer, `oracle.sqlj.runtime.util.OraCustomizer`.

- Use Oracle SQLJ run time when your application runs. Oracle SQLJ run time and an Oracle JDBC driver are required whenever you use Oracle customizer, even if you do not actually use Oracle extensions in your code.

For Oracle-specific semantics-checking, you must use an appropriate checker. The default checker, `oracle.sqlj.checker.OracleChecker`, acts as a front end and will run the appropriate checker based on your environment. This will be one of the Oracle specific checkers if you are using an Oracle JDBC driver.

**Note:**

Oracle-specific types for Oracle objects and collections are included in the `oracle.sql` package.

**See Also:**

"[Connection Options](translator-command-line-and-options.md)" and "[Semantics-Checking and Offline-Parsing Options](translator-command-line-and-options.md)"

##### Custom Java Class Usage Notes

- This chapter primarily discusses the use of custom Java classes with user-defined types. However, classes implementing `ORAData` can be used for other Oracle SQL types as well. A class implementing `ORAData` can be used to perform any kind of desired processing or conversion in the course of transferring data between SQL and Java.

  **See Also:**

  "Additional Uses for ORAData Implementations"

- The `SQLData` interface is intended only for custom object classes. The `ORAData` interface can be used for any custom Java class.

##### Terminology Notes

- User-defined SQL object types and user-defined SQL collection types are referred to as user-defined types (UDTs).

- Custom Java classes for objects, references, and collections are referred to as custom object classes, custom reference classes, and custom collection classes, respectively.

**See Also:**

[Oracle Database Object-Relational Developer's Guide](../adobj/introduction-to-oracle-objects.md) for general information about Oracle object features and functionality

#### 7.1.2 Oracle Object Fundamentals

The Oracle SQL objects are composite data structures that group related data items, such as facts about each employee, into a single data unit. An object type is functionally similar to a Java class. You can populate and use any number of individual objects of a given object type, just as you can instantiate and use individual objects of a Java class.

For example, you can define an object type `EMPLOYEE` that has the attributes `name` of type `CHAR`, `address` of type `CHAR`, `phonenumber` of type `CHAR`, and `employeenumber` of type `NUMBER`.

Oracle objects can also have methods, or stored procedures, associated with the object type. These methods can be either static methods or instance methods and can be implemented either in PL/SQL or Java. Their signatures can include any number of input, output, or input-output parameters. All this depends on how they are initially defined

#### 7.1.3 Oracle Collection Fundamentals

There are two categories of Oracle SQL collections:

- Variable-length arrays (VARRAY types)

- Nested tables (TABLE types)

Both categories are one-dimensional, although the elements can be complex object types. VARRAY types are used for one-dimensional arrays, and nested table types are used for single-column tables within an outer table. A variable of any VARRAY type can be referred to as a VARRAY. A variable of any nested table type can be referred to as a nested table.

A VARRAY, as with any array, is an ordered set of data elements, with each element having an index and all elements being of the same data type. The size of a VARRAY refers to the maximum number of elements. Oracle VARRAYs, as indicated by their name, are of variable size, but the maximum size of any particular VARRAY type must be specified when the VARRAY type is declared.

A nested table is an unordered set of elements. Nested table elements within a table can themselves be queried in SQL. A nested table, as with any table, is not created with any particular number of rows. This is determined dynamically.

**Note:**

The elements in a VARRAY or the rows in a nested table can be of a user-defined object type, and VARRAY and nested table types can be used for attributes in a user-defined object type. Oracle Database 12c Release 2 (12.2) supports nesting of collection types. The elements of a VARRAY or rows of a nested table can be of another VARRAY or nested table type, or these elements can be of a user-defined object type that has VARRAY or nested table attributes.

#### 7.1.4 Object and Collection Data Types

In Oracle Database 12c Release 2 (12.2), user-defined object and collection definitions function as SQL data type definitions. You can use these data types, as with any other data type, in defining table columns, SQL object attributes, and stored procedure or function parameters. In addition, once you have defined an object type, the related object reference type can be used as any other SQL reference type.

For example, consider the `EMPLOYEE` Oracle object described in the preceding section. Once you have defined this object, it becomes an Oracle data type. You can have a table column of type `EMPLOYEE` just as you can have a table column of type `NUMBER`. Each row in an `EMPLOYEE` column contains a complete `EMPLOYEE` object. You can also have a column type of `REF EMPLOYEE`, consisting of references to `EMPLOYEE` objects.

Similarly, you can define a variable-length array `MYVARR` as `VARRAY(10)` of `NUMBER` and a nested table `NTBL` of `CHAR(20)`. The `MYVARR` and `NTBL` collection types become Oracle data types, and you can have table columns of either type. Each row of a `MYVARR` column consists of an array of up to 10 numbers. Each row of an `NTBL` column consists of 20 characters.

### 7.2 Custom Java Classes

Custom Java classes are first-class types that you can use to read from and write to user-defined SQL types transparently. The purpose of custom Java classes is to provide a way to convert data between SQL and Java and make the data accessible, particularly in supporting objects and collections or if you want to perform custom data conversions.

It is generally advisable to provide custom Java classes for all user-defined types that you use in a SQLJ application. Oracle JDBC driver will use instances of these classes in converting data, which is more convenient and less error-prone than using the weakly typed `oracle.sql.STRUCT`, `oracle.sql.REF`, and `oracle.sql.ARRAY` classes.

To be used in SQLJ iterators or host expressions, a custom Java class must implement either the `oracle.sql.ORAData` and `oracle.sql.ORADataFactory` interfaces or the standard `java.sql.SQLData` interface. This section provides an overview of these interfaces and custom Java class functionality, covering the following topics:

- Custom Java Class Interface Specifications

- Custom Java Class Support for Object Methods

- Custom Java Class Requirements

- Compiling Custom Java Classes

- Reading and Writing Custom Data

- Additional Uses for ORAData Implementations

#### 7.2.1 Custom Java Class Interface Specifications

This section discusses specifications of the `ORAData` and `ORADataFactory` interfaces and the standard `SQLData` interface.

Oracle Database 12c Release 2 (12.2) includes a set of APIs for Oracle-specific custom Java class functionality for user-defined types: `oracle.sql.ORAData` and `oracle.sql.ORADataFactory`.

##### ORAData and ORADataFactory Specifications

Oracle provides the `oracle.sql.ORAData` interface and the related `oracle.sql.ORADataFactory` interface to use in mapping and converting Oracle object types, reference types, and collection types to custom Java classes.

Data is sent or retrieved in the form of an `oracle.sql.Datum` object, with the underlying data being in the format of the appropriate `oracle.sql.Datum` subclass, such as `oracle.sql.STRUCT`. This data is still in its SQL format. The `oracle.sql.Datum` object is just a wrapper.

**See Also:**

[Oracle Database JDBC Developer’s Guide](../jjdbc/Oracle-object-types.md)

The `ORAData` interface specifies a `toDatum()` method for data conversion from Java format to SQL format. This method takes as input your connection object and converts data to the appropriate `oracle.sql.*` representation. The connection object is necessary so that the JDBC driver can perform appropriate type checking and type conversions at run time. The `ORAData` and `toDatum()` specification is as follows:

    interface oracle.sql.ORAData
    {
       oracle.sql.Datum toDatum(java.sql.Connection c) throws SQLException;
    }

The `ORADataFactory` interface specifies a `create()` method that constructs instances of your custom Java class, converting from SQL format to Java format. This method takes as input a `Datum` object containing the data and a type code, such as `OracleTypes.RAW`, indicating the SQL type of the underlying data. It returns an object of your custom Java class, which implements the `ORAData` interface. This object receives its data from the `Datum` object that was input. The `ORADataFactory` and `create()` specification is as follows:

    interface oracle.sql.ORADataFactory
    {
       oracle.sql.ORAData create(oracle.sql.Datum d, int sqlType)
                          throws SQLException;
    }

To complete the relationship between the `ORAData` and `ORADataFactory` interfaces, you must implement a static `getORADataFactory()` method in any custom Java class that implements the `ORAData` interface. This method returns an object that implements the `ORADataFactory` interface and that, therefore, can be used to create instances of your custom Java class. This returned object can itself be an instance of your custom Java class, and its `create()` method is used by Oracle JDBC driver to produce further instances of your custom Java class, as necessary.

##### SQLData Specification

Standard JDBC 2.0 supplies the `java.sql.SQLData` interface to use in mapping and converting structured object types to Java classes. This interface is intended for mapping structured object types only, not object references, collections or arrays, or other SQL types.

The `SQLData` interface is a JDBC 2.0 standard, specifying a `readSQL()` method to read data into a Java object and a `writeSQL()` method to write to the database from a Java object.

For additional information about standard `SQLData` functionality, refer to the Sun Microsystems JDBC 2.0 or later API specification.

#### 7.2.2 Custom Java Class Support for Object Methods

Methods of Oracle objects can be invoked from custom Java class wrappers. Whether the underlying stored procedure is written in PL/SQL or is written in Java and published to SQL is invisible to the user.

A Java wrapper method used to invoke a server method requires a connection to communicate with the server. The connection object can be provided as an explicit parameter or can be associated in some other way. For example, as an attribute of your custom Java class. If the connection object used by the wrapper method is a nonstatic attribute, then the wrapper method must be an instance method of the custom Java class in order to have access to the connection.

There are also issues regarding output and input-output parameters in methods of Oracle objects. If a stored procedure, that is, a SQL object method, modifies the internal state of one of its arguments, then the actual argument passed to the stored procedure is modified. In Java this is not possible. When a JDBC output parameter is returned from a stored procedure call, it must be stored in a newly created object. The original object identity is lost.

One way to return an output or input-output parameter to the caller is to pass the parameter as an element of an array. If the parameter is input-output, then the wrapper method takes the array element as input. After processing, the wrapper assigns the output to the array element.

#### 7.2.3 Custom Java Class Requirements

Custom Java classes must satisfy certain requirements to be recognized by Oracle SQLJ translator as valid host variable types and to enable type-checking by the translator.

**Note:**

Custom Java classes for user-defined types are often referred to in this manual as "wrapper classes".

##### Oracle Requirements for Classes Implementing ORAData

Oracle requirements for `ORAData` implementations are primarily the same for any kind of custom Java class, but vary slightly depending on whether the class is for mapping to objects, object references, collections, or some other SQL type.

These requirements are as follows:

- The class implements the `oracle.sql.ORAData` interface.

- The class implements the `getORADataFactory()` method that returns an `oracle.sql.ORADataFactory` object. The method signature is as follows:

      public static oracle.sql.ORADataFactory getORADataFactory();

- The class has a `String` constant, `_SQL_TYPECODE`, initialized to the `oracle.jdbc.OracleTypes` type code of the `Datum` subclass instance that `toDatum()` returns. The type code is:

  - For custom object classes:

        public static final int _SQL_TYPECODE = OracleTypes.STRUCT;

  - For custom reference classes:

        public static final int _SQL_TYPECODE = OracleTypes.REF;

  - For custom collection classes:

        public static final int _SQL_TYPECODE = OracleTypes.ARRAY;

  For other uses, some other type code might be appropriate. For example, for using a custom Java class to serialize and deserialize Java objects into or out of `RAW` fields, a `_SQL_TYPECODE` of `OracleTypes.RAW` is used.

  **Note:**

  The `OracleTypes` class simply defines a type code, which is an integer constant, for each Oracle data type. For standard SQL types, the `OracleTypes` entry is identical to the entry in the standard `java.sql.Types` type definitions class.

  **See Also:**

  "Serialized Java Objects"

- For custom Java classes with `_SQL_TYPECODE` of `STRUCT`, `REF`, or `ARRAY`, that is, for custom Java classes that represent objects, object references, or collections, the class has a constant that indicates the relevant user-defined type name. This is as follows:

  - Custom object classes and custom collection classes must have a `String` constant, `_SQL_NAME`, initialized to the SQL name you declared for the user-defined type, as follows:

        public static final String _SQL_NAME = UDT name;

    For example, the custom object class for a user-defined `PERSON` object will have the constant:

        public static final String _SQL_NAME = "PERSON";

    The same can be specified along with the schema, if appropriate, as follows:

        public static final String _SQL_NAME = "HR.PERSON";

    The custom collection class for a collection of `PERSON` objects, which you have declared as `PERSON_ARRAY`, will have the constant:

        public static final String _SQL_NAME = "PERSON_ARRAY";

  - Custom reference classes must have a `String` constant, `_SQL_BASETYPE`, initialized to the SQL name you declared for the user-defined type being referenced, as follows:

        public static final String _SQL_BASETYPE = UDT name;

    The custom reference class for `PERSON` references will have the constant:

        public static final String _SQL_BASETYPE = "PERSON";

    For other `ORAData` uses, specifying a UDT name is not applicable.

Keep in mind the following usage notes:

- A collection type name reflects the collection type, not the base type. For example, if you have declared a VARRAY or nested table type, `PERSON_ARRAY`, for `PERSON` objects, then the name of the collection type that you specify for the `_SQL_NAME` entry is `PERSON_ARRAY`, not `PERSON`.

- When specifying the SQL type in a `_SQL_NAME` field, if the SQL type was declared in a case-sensitive way (in quotes), then you must specify the SQL name exactly as it was declared, such as `CaseSensitive` or `HR.CaseSensitive`.

##### Requirements for Classes Implementing SQLData

The ISO SQLJ standard outlines requirements for type map definitions for classes implementing the `SQLData` interface. Alternatively, `SQLData` wrapper classes can identify associated SQL object types through the `public static final` fields.

Be aware of the following important points:

- Whether you use a type map or use alternative (nonstandard) `public static final` fields to specify mappings, you must be consistent in your approach. Either use a type map that specifies all relevant mappings so that you do not require the `public static final` fields, or do not use a type map at all and specify all mappings through the `public static final` fields.

- `SQLData`, unlike `ORAData`, is for mapping structured object types only. It is not for object references, collections or arrays, or any other SQL types. If you are not using `ORAData`, then your only choices for mapping object references and collections are the weak `java.sql.Ref` and `java.sql.Array` types, respectively, or `oracle.sql.REF` and `oracle.sql.ARRAY`.

- `SQLData` implementations require a Java Development Kit (JDK) 1.4.x or 1.5.x environment.

- When specifying the mapping from a SQL type to a Java type, if the SQL type was declared in a case-sensitive way, then you must specify the SQL name exactly as it was declared, such as `CaseSensitive` or `HR.CaseSensitive`.

##### Mapping Specified in Type Map Resource

First, consider the mapping representation according to the ISO SQLJ standard. Assume that `Address`, `pack.Person`, and `pack.Manager.InnerPM`, where `InnerPM` is an inner class of `Manager`, are three wrapper classes that implement `java.sql.SQLData`.

Then, you need to consider the following:

- You must use these classes only in statements that use explicit connection context instances of a declared connection context type. For example, assuming that this type is called `SDContext`:

      Address               a =...;
      pack.Person           p =...;
      pack.Manager.InnerPM pm =...;
      SDContext ctx = new SDContext(url,user,pwd,false);
      #sql [ctx] { ... :a ... :p ... :pm ... };

- The connection context type must have been declared using the `with` attribute `typeMap` that specifies an associated class implementing `java.util.PropertyResourceBundle`. In the preceding example, `SDContext` may be declared as follows:

      #sql public static context SDContext with (typeMap="SDMap");

- The type map resource must provide the mapping from SQL object types to corresponding Java classes that implement the `java.sql.SQLData` interface. This mapping is specified with entries of the following form:

      class.java_class_name=STRUCT sql_type_name

  The `STRUCT` keyword can also be omitted. In the example, the `SDMap.properties` resource file may contain the following entries:

      class.Address=STRUCT HR.ADDRESS
      class.pack.Person=PERSON
      class.pack.Manager$InnerPM=STRUCT PRODUCT_MANAGER

  Although the period (.) separates package and class name, you must use the dollar sign (\$) to separate an inner class name.

**Note:**

If you used the default Oracle-specific code generation in this example, then any iterator that is used for a statement whose context type is `SDContext` must also have been declared with the same associated type map, `SDMap`, such as in the following example:

    #sql public static iterator SDIter with (typeMap="SDMap");
    ...
    SDContext sdctx = ...
    SDIter sditer;
    #sql [sdctx] sditer = { SELECT ...};

This is to ensure that proper code is generated for the iterator class.

This mechanism of specifying mappings in a type map resource is more complicated than the nonstandard alternative. Also, it is not possible to associate a type map resource with the default connection context. The advantage is that all the mapping information is placed in a single location, the type map resource. This means that the type mapping in an already compiled application can be easily adjusted at a later time, for example, to accommodate new SQL types and Java wrappers in an expanding SQL-Java type hierarchy.

Be aware of the following:

- You must employ the SQLJ `runtime12` or `runtime12ee` library to use this feature. Type maps are represented as `java.util.Map` objects. These are exposed in the SQLJ run-time API and, therefore, cannot be supported by the generic run-time library.

- You must use Oracle SQLJ run time and Oracle-specific code generation or profile customization if your `SQLData` wrapper classes occur as `OUT` or `INOUT` parameters in SQLJ statements. This is because the SQL type of such parameters is required for `registerOutParameter()` by Oracle JDBC driver. Also, for `OUT` parameter type registration, the SQL type is "frozen in" by the type map in effect during translation.

- The SQLJ type map is independent of any JDBC type map you may be using on the underlying connection. Thus, you must be careful when you are mixing SQLJ and JDBC code if both use `SQLData` wrappers. However, you can easily extract the type map in effect on a given SQLJ connection context:

      ctx.getTypeMap();

##### Mapping Specified in Static Field of Wrapper Class

A class that implements `SQLData` can satisfy the following nonstandard requirement:

- The Java class declares the `String` constant `_SQL_NAME`, which defines the name of the SQL type that is being wrapped by the Java class. In the example, the `Address` class would have the following field declaration:

      public static final String _SQL_NAME="HR.ADDRESS";

  The following declaration would be in `pack.Person`:

      public static final String _SQL_NAME="PERSON";

  And the `pack.Manager.InnerPM` class would have the following:

      public static final String _SQL_NAME="PRODUCT_MANAGER";

**Note:**

- If a class that implements the `_SQL_NAME` field is used in a SQLJ statement with an explicit connection context type and associated type map, then that type map is used and the `_SQL_NAME` field is ignored. This simplifies migration of existing SQLJ programs to the ISO SQLJ standard.

- The static SQL-Java type correspondence specified in the `_SQL_NAME` field is independent from any JDBC type map you may be using on the underlying connection. Thus, you must be careful when you are mixing SQLJ and JDBC code if both use `SQLData` wrappers.

#### 7.2.4 Compiling Custom Java Classes

You can include any `.java` files for your custom Java classes, whether `ORAData` or `SQLData` implementations, on the SQLJ command line together with the `.sqlj` files for your application. However, this is not necessary if the SQLJ `-checksource` flag is set to `true`, which is the default, and your classpath includes the directory where the custom Java source is located.

**Note:**

This discussion assumes you are creating `.java` files for your custom objects and collections, not `.sqlj` files. Any `.sqlj` files must be included in the SQLJ command line.

For example, if `ObjectDemo.sqlj` uses the `ADDRESS` and `PERSON` Oracle object types and you have produced custom Java classes for these objects, then you can run SQLJ as follows.

- If `-checksource=true` and the classpath includes the custom Java source location:

      % sqlj ObjectDemo.sqlj

- If `-checksource=false` (this is a single wraparound line):

      % sqlj ObjectDemo.sqlj Address.java AddressRef.java Person.java PersonRef.java

You also have the choice of using your Java compiler to compile custom `.java` source files directly. If you do this, then you must do it prior to translating `.sqlj` files.

**Note:**

Because `ORAData` implementations rely on Oracle-specific features, SQLJ will report numerous portability warnings if you do not use the `-warn=noportable` translator portability setting, which is the default.

#### 7.2.5 Reading and Writing Custom Data

Through the use of custom Java class instances, the Oracle SQLJ and JDBC implementations allow you to read and write user-defined types as though they are built-in types. Exactly how this is accomplished is transparent to the user.

For the mechanics of how data is read and written, for both `ORAData` implementations and `SQLData` implementations, refer to the[ Oracle Database JDBC Developer's Guide](../jjdbc/Oracle-object-types.md).

#### 7.2.6 Additional Uses for ORAData Implementations

To this point, discussion of custom Java classes has been for use as one of the following.

- Wrappers for SQL objects: custom object classes, for use with `oracle.sql.STRUCT` instances

- Wrappers for SQL references: custom reference classes, for use with `oracle.sql.REF` instances

- Wrappers for SQL collections: custom collection classes, for use with `oracle.sql.ARRAY` instances

It might be useful, however, to provide custom Java classes to wrap other `oracle.sql.*` types as well, for customized conversions or processing. You can accomplish this with classes that implement `ORAData`, but not `SQLData`, as in the following examples:

- Perform encryption and decryption or validation of data.

- Perform logging of values that have been read or are being written.

- Parse character columns, such as character fields containing URL information, into smaller components.

- Map character strings into numeric constants.

- Map data into more desirable Java formats, such as mapping a `DATE` field to `java.util.Date` format.

- Customize data representation, for example, data in a table column is in feet, but you want it represented in meters after it is selected.

- Serialize and deserialize Java objects, for example, into or out of `RAW` fields.

**Note:**

This sort of functionality is not possible through the `SQLData` interface, as `SQLData` implementations can wrap only structured object types.

**See Also:**

"Serialized Java Objects"

##### General Use of ORAData: BetterDate.java

This example shows a class that implements the `ORAData` interface to provide a customized representation of Java dates and can be used instead of `java.sql.Date`.

**Note:**

This is not a complete application. There is no `main()` method.

    import java.util.Date;
    import oracle.sql.ORAData;
    import oracle.sql.DATE;
    import oracle.sql.ORADataFactory;
    import oracle.jdbc.OracleTypes;

    // a Date class customized for user's preferences:
    //      - months are numbers 1..12, not 0..11
    //      - years are referred to through four-digit numbers, not two.

    public class BetterDate extends java.util.Date
                 implements ORAData, ORADataFactory {
      public static final int _SQL_TYPECODE = OracleTypes.DATE;

      String[]monthNames={"JAN", "FEB", "MAR", "APR", "MAY", "JUN",
                          "JUL", "AUG", "SEP", "OCT", "NOV", "DEC"};
      String[]toDigit={"0", "1", "2", "3", "4", "5", "6", "7", "8", "9"};

      static final BetterDate _BetterDateFactory = new BetterDate();

      public static ORADataFactory getORADataFactory() { return _BetterDateFactory;}

      // the current time...
      public BetterDate() {
        super();
      }

      public oracle.sql.Datum toDatum(java.sql.Connection conn) {
        return new DATE(toSQLDate());
      }

      public oracle.sql.ORAData create(oracle.sql.Datum dat, int intx) {
        if (dat==null) return null;
        DATE DAT = ((DATE)dat);
        java.sql.Date jsd = DAT.dateValue();
        return new BetterDate(jsd);
      }

      public java.sql.Date toSQLDate() {
        java.sql.Date retval;
        retval = new java.sql.Date(this.getYear()-1900, this.getMonth()-1,
                 this.getDate());
        return retval;
      }
      public BetterDate(java.sql.Date d) {
        this(d.getYear()+1900, d.getMonth()+1, d.getDate());
      }
      private static int [] deconstructString(String s) {
        int [] retval = new int[3];
        int y,m,d; char temp; int offset;
        StringBuffer sb = new StringBuffer(s);
        temp=sb.charAt(1);
        // figure the day of month
        if (temp < '0' || temp > '9') {
          m = sb.charAt(0)-'0';
          offset=2;
        } else {
          m = (sb.charAt(0)-'0')*10 + (temp-'0');
          offset=3;
        }

        // figure the month
        temp = sb.charAt(offset+1);
        if (temp < '0' || temp > '9') {
          d = sb.charAt(offset)-'0';
          offset+=2;
        } else {
          d = (sb.charAt(offset)-'0')*10 + (temp-'0');
          offset+=3;
        }

        // figure the year, which is either in the format "yy" or "yyyy"
        // (the former assumes the current century)
        if (sb.length() <= (offset+2)) {
          y = (((new BetterDate()).getYear())/100)*100 +
              (sb.charAt(offset)- '0') * 10 +
              (sb.charAt(offset+1)- '0');
        } else {
          y = (sb.charAt(offset)- '0') * 1000 +
              (sb.charAt(offset+1)- '0') * 100 +
              (sb.charAt(offset+2)- '0') * 10 +
              (sb.charAt(offset+3)- '0');
        }
        retval[0]=y;
        retval[1]=m;
        retval[2]=d;
    //    System.out.println("Constructing date from string as: "+d+"/"+m+"/"+y);
        return retval;
      }
      private BetterDate(int [] stuff) {
        this(stuff[0], stuff[1], stuff[2]);
      }
      // takes a string in the format: "mm-dd-yyyy" or "mm/dd/yyyy" or
      // "mm-dd-yy" or "mm/dd/yy" (which assumes the current century)
      public BetterDate(String s) {
        this(BetterDate.deconstructString(s));
      }

      // years are as '1990', months from 1..12 (unlike java.util.Date!), date
      // as '1' to '31'
      public BetterDate(int year, int months, int date) {
        super(year-1900,months-1,date);
      }
      // returns "Date: dd-mon-yyyy"
      public String toString() {
        int yr = getYear();
        return getDate()+"-"+monthNames[getMonth()-1]+"-"+
          toDigit[(yr/1000)%10] +
          toDigit[(yr/100)%10] +
          toDigit[(yr/10)%10] +
          toDigit[yr%10];
    //    return "Date: " + getDate() + "-"+getMonth()+"-"+(getYear()%100);
      }
      public BetterDate addDays(int i) {
        if (i==0) return this;
        return new BetterDate(getYear(), getMonth(), getDate()+i);
      }
      public BetterDate addMonths(int i) {
        if (i==0) return this;
        int yr=getYear();
        int mon=getMonth()+i;
        int dat=getDate();
        while(mon<1) {
          --yr;mon+=12;
        }
        return new BetterDate(yr, mon,dat);
      }
      // returns year as in 1996, 2007
      public int getYear() {
        return super.getYear()+1900;
      }
      // returns month as 1..12
      public int getMonth() {
        return super.getMonth()+1;
      }
      public boolean equals(BetterDate sd) {
        return (sd.getDate() == this.getDate() &&
                sd.getMonth() == this.getMonth() &&
                sd.getYear() == this.getYear());
      }
      // subtract the two dates; return the answer in whole years
      // uses the average length of a year, which is 365 days plus
      // a leap year every 4, except 100, except 400 years =
      // = 365 97/400 = 365.2425 days = 31,556,952 seconds
      public double minusInYears(BetterDate sd) {
        // the year (as defined in the preceding text) in milliseconds
        long yearInMillis = 31556952L;
        long diff = myUTC()-sd.myUTC();
        return (((double)diff/(double)yearInMillis)/1000.0);
      }
      public long myUTC() {
        return Date.UTC(getYear()-1900, getMonth()-1, getDate(),0,0,0);
      }

      // returns <0 if this is earlier than sd
      // returns = if this == sd
      // else returns >0
      public int compare(BetterDate sd) {
        if (getYear()!=sd.getYear()) {return getYear()-sd.getYear();}
        if (getMonth()!=sd.getMonth()) {return getMonth()-sd.getMonth();}
        return getDate()-sd.getDate();
      }
    }

### 7.3 User-Defined Types

This section contains examples of creating and using user-defined object types and collection types in Oracle Database 12c Release 2 (12.2).

#### Creating Object Types

SQL commands to create object types are of the following form:

    CREATE TYPE typename AS OBJECT
    (
      attrname1    datatype1,
      attrname2    datatype2,
      ...         ...
      attrnameN    datatypeN
    );

Where `typename` is the desired name of your object type, `attrname1` through `attrnameN` are the desired attribute names, and `datatype1` through `datatypeN` are the attribute data types.

The remainder of this section provides an example of creating user-defined object types in Oracle Database 12c Release 1 (12.1).

In this example, the following items are created using SQL:

- Two object types, `PERSON` and `ADDRESS`

- A typed table for `PERSON` objects

- An `EMPLOYEES` table that includes an `ADDRESS` column and two columns of `PERSON` references

The script for creating these items is as follows:

    /*** Using user-defined types (UDTs) in SQLJ ***/
    /
    /*** Create ADDRESS UDT ***/
    CREATE TYPE ADDRESS AS OBJECT
    (
      street        VARCHAR(60),
      city          VARCHAR(30),
      state         CHAR(2),
      zip_code      CHAR(5)
    )
    /
    /*** Create PERSON UDT containing an embedded ADDRESS UDT ***/
    CREATE TYPE PERSON AS OBJECT
    (
      name    VARCHAR(30),
      ssn     NUMBER,
      addr    ADDRESS
    )
    /
    /*** Create a typed table for PERSON objects ***/
    CREATE TABLE persons OF PERSON
    /
    /*** Create a relational table with two columns that are REFs
         to PERSON objects, as well as a column which is an Address ADT. ***/
    CREATE TABLE  employees
    (
      empnumber            INTEGER PRIMARY KEY,
      person_data     REF  PERSON,
      manager         REF  PERSON,
      office_addr          ADDRESS,
      salary               NUMBER
    )
    /*** Insert some data--2 objects into the persons typed table ***/
    INSERT INTO persons VALUES (
                PERSON('Wolfgang Amadeus Mozart', 123456,
                   ADDRESS('Am Berg 100', 'Salzburg', 'AT','10424')))
    /
    INSERT INTO persons VALUES (
                PERSON('Ludwig van Beethoven', 234567,
                   ADDRESS('Rheinallee', 'Bonn', 'DE', '69234')))
    /
    /** Put a row in the employees table **/
    INSERT INTO employees (empnumber, office_addr, salary) VALUES (
                1001,
                ADDRESS('500 Oracle Parkway', 'Redwood Shores', 'CA', '94065'),
                50000)
    /
    /** Set the manager and PERSON REFs for the employee **/
    UPDATE employees
       SET manager =
           (SELECT REF(p) FROM persons p WHERE p.name = 'Wolfgang Amadeus Mozart')
    /
    UPDATE employees
       SET person_data =
           (SELECT REF(p) FROM persons p WHERE p.name = 'Ludwig van Beethoven')

**Note:**

Use of a table alias, such as `p` in the example, is a recommended general practice in the Oracle SQL implementation, especially in accessing tables with user-defined types. It is required syntax in some cases where object attributes are accessed. Even when not required, it helps in avoiding ambiguities. Refer to the[ Oracle Database SQL Language Reference ](../sqlrf/Data-Types.md)for more information about table aliases.

#### Creating Collection Types

There are two categories of collections

- Variable-length arrays (VARRAYs)

- Nested tables

SQL commands to create VARRAY types are of the following form:

    CREATE TYPE typename IS VARRAY(n) OF datatype;

The `typename` designation is the desired name of your VARRAY type, `n` is the desired maximum number of elements in the array, and `datatype` is the data type of the array elements. For example:

    CREATE TYPE myvarr IS VARRAY(10) OF INTEGER;

SQL commands to create nested table types are of the following form:

    CREATE TYPE typename AS TABLE OF datatype;

The `typename` designation is the desired name of your nested table type and `datatype` is the data type of the table elements. This can be a user-defined type as well as a standard data type. A nested table is limited to one column, although that one column type can be a complex object with multiple attributes. The nested table, as with any database table, can have any number of rows. For example:

    CREATE TYPE person_array AS TABLE OF person;

This command creates a nested table where each row consists of a `PERSON` object.

The rest of this section provides an example of creating a user-defined collection type, as well as object types, in Oracle Database 12c Release 2 (12.2).

The following items are created and populated using SQL:

- Two object types, `PARTICIPANT_T` and `MODULE_T`

- A collection type, `MODULETBL_T`, which is a nested table of `MODULE_T` objects

- A `PROJECTS` table that includes a column of `PARTICIPANT_T` references and a column of `MODULETBL_T` nested tables

- A collection type `PHONE_ARRAY`, which is a VARRAY of `VARCHAR2(30)`

- `PERSON` and `ADDRESS` objects (repeating the same definitions used earlier)

- An `EMPLOYEES` table, which includes a `PHONE_ARRAY` column

The script for creating these items is as follows:

    Rem This is a SQL*Plus script used to create schema to demonstrate collection
    Rem manipulation in SQLJ

    CREATE TYPE PARTICIPANT_T AS OBJECT (
      empno   NUMBER(4),
      ename   VARCHAR2(20),
      job     VARCHAR2(12),
      mgr     NUMBER(4),
      hiredate DATE,
      sal      NUMBER(7,2),
      deptno   NUMBER(2))
    /
    SHOW ERRORS
    CREATE TYPE MODULE_T  AS OBJECT (
      module_id  NUMBER(4),
      module_name VARCHAR2(20),
      module_owner REF PARTICIPANT_T,
      module_start_date DATE,
      module_duration NUMBER )
    /
    SHOW ERRORS
    CREATE TYPE MODULETBL_T AS TABLE OF MODULE_T;
    /
    SHOW ERRORS
    CREATE TABLE projects (
      id NUMBER(4),
      name VARCHAR(30),
      owner REF PARTICIPANT_T,
      start_date DATE,
      duration NUMBER(3),
      modules  MODULETBL_T  ) NESTED TABLE modules STORE AS modules_tab;

    SHOW ERRORS
    CREATE TYPE PHONE_ARRAY IS VARRAY (10) OF varchar2(30)
    /

    /*** Create ADDRESS UDT ***/
    CREATE TYPE ADDRESS AS OBJECT
    (
      street        VARCHAR(60),
      city          VARCHAR(30),
      state         CHAR(2),
      zip_code      CHAR(5)
    )
    /
    /*** Create PERSON UDT containing an embedded ADDRESS UDT ***/
    CREATE TYPE PERSON AS OBJECT
    (
      name    VARCHAR(30),
      ssn     NUMBER,
      addr    ADDRESS
    )
    /
    CREATE TABLE  employees
    ( empnumber            INTEGER PRIMARY KEY,
      person_data     REF  person,
      manager         REF  person,
      office_addr          address,
      salary               NUMBER,
      phone_nums           phone_array
    )
    /

### 7.4 Strongly Typed Objects and References in SQLJ Executable Statements

The Oracle SQLJ implementation is flexible in how it enables you to use host expressions and iterators in reading or writing object data through strongly typed objects or references.

For iterators, you can use custom object classes as iterator column types. Alternatively, you can have iterator columns that correspond to individual object attributes, similar to extent tables, using column types that appropriately map to the SQL data types of the attributes.

For host expressions, you can use host variables of your custom object class type or custom reference class type. Alternatively, you can use host variables that correspond to object attributes, using variable types that appropriately map to the SQL data types of the attributes.

The remainder of this section provides examples of how to manipulate Oracle objects using custom object classes, custom object class attributes, and custom reference classes for host variables and iterator columns in SQLJ executable statements.

The following two examples operate at the object level:

- Selecting Objects and Object References into Iterator Columns

- Updating an Object

The Inserting an Object Created from Individual Object Attributes example operates at the scalar-attribute level.

The Updating an Object Reference example operates through a reference.

#### 7.4.1 Selecting Objects and Object References into Iterator Columns

This example uses a custom Java class and a custom reference class as iterator column types. Presume the following definition of the `ADDRESS` Oracle object type:

    CREATE TYPE ADDRESS AS OBJECT
    (  street VARCHAR(40),
       zip NUMBER );

And the following definition of the `EMPADDRS` table, which includes an `ADDRESS` column and an `ADDRESS` reference column:

    CREATE TABLE empaddrs
    (  name VARCHAR(60),
       home ADDRESS,
       loc REF ADDRESS );

Once you create a custom Java class, `Address`, and custom reference class, `AddressRef`, corresponding to the `ADDRESS` Oracle object type, you can use `Address` and `AddressRef` in a named iterator as follows:

    #sql iterator EmpIter (String name, Address home, AddressRef loc);

    ...
    EmpIter ecur;
    #sql ecur = { SELECT name, home, loc FROM empaddrs };
    while (ecur.next()) {
       Address homeAddr = ecur.home();
       // Print out the home address.
       System.out.println ("Name: " + ecur.name() + "\n" +
                           "Home address: " + homeAddr.getStreet() + "   " +
                           homeAddr.getZip());
       // Now update the loc address zip code through the address reference.
       AddressRef homeRef = ecur.loc();
       Address location = homeRef.getValue();
       location.setZip(new BigDecimal(98765));
       homeRef.setValue(location);
       }
    ...

The `ecur.home()` method call extracts an `Address` object from the `home` column of the iterator and assigns it to the `homeAddr` local variable (for efficiency). The attributes of that object can then be accessed using standard Java dot syntax:

    homeAddr.getStreet()

Use the `getValue()` and `setValue()` methods to manipulate the location address (in this case its zip code).

#### 7.4.2 Updating an Object

This example declares and sets an input host variable of the `Address` Java type to update an `ADDRESS` object in a column of the `employees` table. Both before and after the update, the address is selected into an output host variable of the `Address` type and printed for verification.

    ...
    // Updating an object

    static void updateObject()
    {

       Address addr;
       Address new_addr;
       int empnum = 1001;

       try {
          #sql {
             SELECT office_addr
             INTO :addr
             FROM employees
             WHERE empnumber = :empnum };
          System.out.println("Current office address of employee 1001:");

          printAddressDetails(addr);

          /* Now update the street of address */

          String street ="100 Oracle Parkway";
          addr.setStreet(street);

          /* Put updated object back into the database */

          try {
             #sql {
                UPDATE employees
                SET office_addr = :addr
                WHERE empnumber = :empnum };
             System.out.println
                ("Updated employee 1001 to new address at Oracle Parkway.");

             /* Select new address to verify update */

             try {
                #sql {
                   SELECT office_addr
                   INTO :new_addr
                   FROM employees
                   WHERE empnumber = :empnum };

                System.out.println("New office address of employee 1001:");
                printAddressDetails(new_addr);

             } catch (SQLException exn) {
             System.out.println("Verification SELECT failed with "+exn); }

          } catch (SQLException exn) {
          System.out.println("UPDATE failed with "+exn); }

       } catch (SQLException exn) {
       System.out.println("SELECT failed with "+exn); }
    }
    ...

Note the use of the `setStreet()` accessor method of the `Address` object.

This example uses the `printAddressDetails()` utility. The source code for this method is as follows:

    static void printAddressDetails(Address a) throws SQLException
    {

      if (a == null)  {
        System.out.println("No Address available.");
        return;
       }

       String street = ((a.getStreet()==null) ? "NULL street" : a.getStreet()) ;
       String city = (a.getCity()==null) ? "NULL city" : a.getCity();
       String state = (a.getState()==null) ? "NULL state" : a.getState();
       String zip_code = (a.getZipCode()==null) ? "NULL zip" : a.getZipCode();

       System.out.println("Street: '" + street + "'");
       System.out.println("City:   '" + city   + "'");
       System.out.println("State:  '" + state  + "'");
       System.out.println("Zip:    '" + zip_code + "'" );
    }

#### 7.4.3 Inserting an Object Created from Individual Object Attributes

This example declares and sets input host variables corresponding to attributes of `PERSON` and nested `ADDRESS` objects, then uses these values to insert a new `PERSON` object into the `persons` table in the database.

    ...
    // Inserting an object

    static void insertObject()
    {
       String new_name   = "NEW PERSON";
       int    new_ssn    = 987654;
       String new_street = "NEW STREET";
       String new_city   = "NEW CITY";
       String new_state  = "NS";
       String new_zip    = "NZIP";
      /*
       * Insert a new PERSON object into the persons table
       */
       try {
          #sql {
             INSERT INTO persons
             VALUES (PERSON(:new_name, :new_ssn,
             ADDRESS(:new_street, :new_city, :new_state, :new_zip))) };

          System.out.println("Inserted PERSON object NEW PERSON.");

       } catch (SQLException exn) { System.out.println("INSERT failed with "+exn); }
    }
    ...

#### 7.4.4 Updating an Object Reference

This example selects a `PERSON` reference from the `persons` table and uses it to update a `PERSON` reference in the `employees` table. It uses simple input host variables to check attribute value criteria. The newly updated reference is then used in selecting the `PERSON` object to which it refers, so that information can be output to the user to verify the change.

    ...
    // Updating a REF to an object

    static void updateRef()
    {
       int empnum = 1001;
       String new_manager = "NEW PERSON";

       System.out.println("Updating manager REF.");
       try {
          #sql {
             UPDATE employees
             SET manager =
                (SELECT REF(p) FROM persons p WHERE p.name = :new_manager)
             WHERE empnumber = :empnum };

          System.out.println("Updated manager of employee 1001. Selecting back");

       } catch (SQLException exn) {
       System.out.println("UPDATE REF failed with "+exn); }

       /* Select manager back to verify the update */
       Person manager;

       try {
          #sql {
             SELECT deref(manager)
             INTO :manager
             FROM employees e
             WHERE empnumber = :empnum };

          System.out.println("Current manager of "+empnum+":");
          printPersonDetails(manager);

       } catch (SQLException exn) {
       System.out.println("SELECT REF failed with "+exn); }

    }
    ...

**Note:**

This example uses table alias syntax (`p`) as discussed previously. Also, the `REF` syntax is required in selecting a reference through the object to which it refers, and the `DEREF` syntax is required in selecting an object through a reference. Refer to the[ Oracle Database SQL Language Reference ](../sqlrf/Syntax-for-Schema-Objects-and-Parts-in-SQL-Statements.md)for more information about table aliases, `REF`, and `DEREF`.

### 7.5 Strongly Typed Collections in SQLJ Executable Statements

As with strongly typed objects and references, the Oracle SQLJ implementation supports different scenarios for reading and writing data through strongly typed collections, using either iterators or host expressions.

From the perspective of a SQLJ developer, both categories of collections, VARRAY and nested table, are treated essentially the same, but there are some differences in implementation and performance.

The Oracle SQLJ implementation supports syntax choices so that nested tables can be accessed and manipulated either apart from or together with their outer tables. In this section, manipulation of a nested table by itself will be referred to as detail-level manipulation and manipulation of a nested table together with its outer table will be referred to as master-level manipulation.

Most of this section, after a brief discussion of some syntax, focuses on examples of manipulating nested tables, given that their use is somewhat more complicated than that of VARRAYs.

**Note:**

In the Oracle SQLJ implementation, VARRAY types and nested table types can be retrieved only in their entirety. This is as opposed to the Oracle SQL implementation, where nested tables can be selectively queried.

This section covers the following topics:

- Accessing Nested Tables: TABLE syntax and CURSOR syntax

- Inserting a Row that Includes a Nested Table

- Selecting a Nested Table into a Host Expression

- Manipulating a Nested Table Using TABLE Syntax

- Selecting Data from a Nested Table Using a Nested Iterator

- Selecting a VARRAY into a Host Expression

- Inserting a Row that Includes a VARRAY

#### 7.5.1 Accessing Nested Tables: TABLE syntax and CURSOR syntax

The Oracle SQLJ implementation supports the use of nested iterators to access data in nested tables. Use the `CURSOR` keyword in the outer `SELECT` statement to encapsulate the inner `SELECT` statement. This is shown in "Selecting Data from a Nested Table Using a Nested Iterator".

Oracle also supports use of the `TABLE` keyword to manipulate the individual rows of a nested table. This keyword informs Oracle that the column value returned by a subquery is a nested table, as opposed to a scalar value. You must prefix the `TABLE` keyword to a subquery that returns a single column value or an expression that yields a nested table.

The following example shows the use of the `TABLE` syntax:

    UPDATE TABLE(SELECT a.modules FROM projects a WHERE a.id=555) b
           SET module_owner=
           (SELECT ref(p) FROM employees p WHERE p.ename= 'Smith')
           WHERE b.module_name = 'Zebra';

When you see `TABLE` used as it is here, realize that it is referring to a single nested table that has been selected from a column of an outer table.

**Note:**

This example uses table alias syntax (`a` for `projects`, `b` for the nested table, and `p` for `employees`) as discussed previously.

#### 7.5.2 Inserting a Row that Includes a Nested Table

This example shows an operation that manipulates the master level (outer table) and detail level (nested tables) simultaneously and explicitly. This inserts a row in the `projects` table, where each row includes a nested table of the `MODULETBL_T` type, which contains rows of `MODULE_T` objects.

First, the scalar values are set (`id`, `name`, `start_date`, `duration`), then the nested table values are set. This involves an extra level of abstraction, because the nested table elements are objects with multiple attributes. In setting the nested table values, each attribute value must be set for each `MODULE_T` object in the nested table. Finally, the `owner` values, initially set to `null`, are set in a separate statement.

    // Insert Nested table details along with master details

      public static void insertProject2(int id)  throws Exception
      {
        System.out.println("Inserting Project with Nested Table details..");
        try {
          #sql { INSERT INTO Projects(id,name,owner,start_date,duration, modules)
                 VALUES ( 600, 'Ruby', null, '10-MAY-98',  300,
                 moduletbl_t(module_t(6001, 'Setup ', null, '01-JAN-98', 100),
                            module_t(6002, 'BenchMark', null, '05-FEB-98',20) ,
                            module_t(6003, 'Purchase', null, '15-MAR-98', 50),
                            module_t(6004, 'Install', null, '15-MAR-98',44),
                            module_t(6005, 'Launch', null,'12-MAY-98',34))) };
        } catch ( Exception e) {
          System.out.println("Error:insertProject2");
          e.printStackTrace();
        }

        // Assign project owner to this project

        try {
          #sql { UPDATE Projects pr
              SET owner=(SELECT ref(pa) FROM participants pa WHERE pa.empno = 7698)
             WHERE pr.id=600 };
        } catch ( Exception e) {
          System.out.println("Error:insertProject2:update");
          e.printStackTrace();
        }
      }

#### 7.5.3 Selecting a Nested Table into a Host Expression

This example presents an operation that works directly at the detail level of the nested table.

      static ModuletblT mymodules=null;
      ...

      public static void getModules2(int projId)
      throws Exception
      {
        System.out.println("Display modules for project " + projId );

        try {
          #sql {SELECT modules INTO :mymodules
                               FROM projects  WHERE id=:projId };
          showArray(mymodules);
        } catch(Exception e) {
          System.out.println("Error:getModules2");
          e.printStackTrace();
        }
      }

      public static void showArray(ModuletblT a)
      {
        try {
          if ( a == null )
            System.out.println( "The array is null" );
          else {
            System.out.println( "printing ModuleTable array object of size "
                                 +a.length());
            ModuleT[] modules = a.getArray();

            for (int i=0;i<modules.length; i++) {
              ModuleT module = modules[i];
              System.out.println("module "+module.getModuleId()+
                    ", "+module.getModuleName()+
                    ", "+module.getModuleStartDate()+
                    ", "+module.getModuleDuration());
            }
          }
        }
        catch( Exception e ) {
          System.out.println("Show Array");
          e.printStackTrace();
        }
      }

#### 7.5.4 Manipulating a Nested Table Using TABLE Syntax

This example uses `TABLE` syntax to work at the detail level to access and update nested table elements directly, based on master-level criteria.

The `assignModule()` method selects a nested table of `MODULE_T` objects from the `MODULES` column of the `PROJECTS` table, then updates `MODULE_NAME` for a particular row of the nested table. Similarly, the `deleteUnownedModules()` method selects a nested table of `MODULE_T` objects, then deletes any unowned modules in the nested table, where `MODULE_OWNER` is `null`.

These methods use table alias syntax, as discussed previously. In this case, `m` is used for the nested table, and `p` is used for the `participants` table.

      /* assignModule
         Illustrates accessing the nested table using the TABLE construct
         and updating the nested table row
      */
      public static void assignModule(int projId, String moduleName,
                                      String modOwner) throws Exception
      {
        System.out.println("Update:Assign '"+moduleName+"' to '"+ modOwner+"'");

        try {
          #sql {UPDATE TABLE(SELECT modules FROM projects WHERE id=:projId) m
                SET m.module_owner=
               (SELECT ref(p) FROM participants p WHERE p.ename= :modOwner)
                WHERE m.module_name = :moduleName };
        } catch(Exception e) {
          System.out.println("Error:insertModules");
          e.printStackTrace();
        }
      }

      /* deleteUnownedModules
      // Demonstrates deletion of the Nested table element
      */

      public static void deleteUnownedModules(int projId)
      throws Exception
      {
        System.out.println("Deleting Unowned Modules for Project " + projId);
        try {
          #sql { DELETE TABLE(SELECT modules FROM projects WHERE id=:projId) m
                 WHERE m.module_owner IS NULL };
        } catch(Exception e) {
          System.out.println("Error:deleteUnownedModules");
          e.printStackTrace();
        }
      }

#### 7.5.5 Selecting Data from a Nested Table Using a Nested Iterator

SQLJ supports the use of nested iterators as a way of accessing nested tables. This requires `CURSOR` syntax, as used in the following example. The code defines a named iterator class, `ModuleIter`, then uses that class as the type for a `modules` column in another named iterator class, `ProjIter`. Inside a populated `ProjIter` instance, each `modules` item is a nested table rendered as a nested iterator.

The `CURSOR` syntax is part of the nested `SELECT` statement that populates the nested iterators. Once the data has been selected, it is output to the user through the iterator accessor methods.

This example uses required table alias syntax, as discussed previously. In this case, `a` for the `projects` table and `b` for the nested table.

    ...

    //  The Nested Table is accessed using the ModuleIter
    //  The ModuleIter is defined as Named Iterator

    #sql public static iterator ModuleIter(int moduleId ,
                                           String moduleName ,
                                           String moduleOwner);

    // Get the Project Details using the ProjIter defined as
    // Named Iterator. Notice the use of ModuleIter:

    #sql public static iterator ProjIter(int id,
                                         String name,
                                         String owner,
                                         Date start_date,
                                         ModuleIter modules);

    ...

    public static void listAllProjects() throws SQLException
    {
      System.out.println("Listing projects...");

       // Instantiate and initialize the iterators

       ProjIter projs = null;
       ModuleIter  mods = null;
       #sql projs = {SELECT a.id,
                            a.name,
                            initcap(a.owner.ename) as "owner",
                            a.start_date,
                            CURSOR (
                            SELECT b.module_id AS "moduleId",
                                   b.module_name AS "moduleName",
                                     initcap(b.module_owner.ename) AS "moduleOwner"
                            FROM TABLE(a.modules) b) AS "modules"
                     FROM projects a };

      // Display Project Details

      while (projs.next()) {
        System.out.println( "\n'" + projs.name() + "' Project Id:"
                    + projs.id() + " is owned by " +"'"+ projs.owner() +"'"
                    + " start on "
                    + projs.start_date());

        // Notice the modules from the ProjIter are assigned to the module
        // iterator variable

        mods = projs.modules();
        System.out.println ("Modules in this Project are : ");

        // Display Module details

        while(mods.next()) {
          System.out.println ("  "+ mods.moduleId() + " '"+
                                    mods.moduleName() + "' owner is '" +
                                    mods.moduleOwner()+"'" );
        }                    // end of modules
        mods.close();
      }                      // end of projects
      projs.close();
    }

#### 7.5.6 Selecting a VARRAY into a Host Expression

This section provides an example of selecting a VARRAY into a host expression. Presume the following SQL definitions:

    CREATE TYPE PHONE_ARRAY IS VARRAY (10) OF varchar2(30)
    /
    /*** Create ADDRESS UDT ***/
    CREATE TYPE ADDRESS AS OBJECT
    (
      street        VARCHAR(60),
      city          VARCHAR(30),
      state         CHAR(2),
      zip_code      CHAR(5)
    )
    /
    /*** Create PERSON UDT containing an embedded ADDRESS UDT ***/
    CREATE TYPE PERSON AS OBJECT
    (
      name    VARCHAR(30),
      ssn     NUMBER,
      addr    ADDRESS
    )
    /

    CREATE TABLE  employees
    ( empnumber            INTEGER PRIMARY KEY,
      person_data     REF  person,
      manager         REF  person,
      office_addr          address,
      salary               NUMBER,
      phone_nums           phone_array
    )
    /

And presume that you created a `PhoneArray` custom collection class to map from the `PHONE_ARRAY` SQL type.

The following method selects a row from this table, placing the data into a host variable of the `PhoneArray` type:

    private static void selectVarray() throws SQLException
    {
      PhoneArray ph;
      #sql {select phone_nums into :ph from employees where empnumber=2001};
      System.out.println(
        "there are "+ph.length()+" phone numbers in the PhoneArray.  They are:");

      String [] pharr = ph.getArray();
      for (int i=0;i<pharr.length;++i)
        System.out.println(pharr[i]);
    }

#### 7.5.7 Inserting a Row that Includes a VARRAY

This section provides an example of inserting data from a host expression into a VARRAY, using the same SQL definitions and custom collection class (`PhoneArray`) as in the previous section.

The following methods populate a `PhoneArray` instance and use it as a host variable, inserting its data into a VARRAY in the database:

    // creates a varray object of PhoneArray and inserts it into a new row
    private static void insertVarray() throws SQLException
    {
      PhoneArray phForInsert = consUpPhoneArray();
      // clean up from previous demo runs
      #sql {delete from employees where empnumber=2001};
      // insert the PhoneArray object
      #sql {insert into employees (empnumber, phone_nums)
            values(2001, :phForInsert)};
    }

    private static PhoneArray consUpPhoneArray()
    {
      String [] strarr = new String[3];
      strarr[0] = "(510) 555.1111";
      strarr[1] = "(617) 555.2222";
      strarr[2] = "(650) 555.3333";
      return new PhoneArray(strarr);
    }

### 7.6 Serialized Java Objects

When writing and reading instances of Java objects to or from the database, it is sometimes advantageous to define a SQL object type that corresponds to your Java class and use the mechanisms of mapping custom Java classes described previously. This fully permits SQL queries on your Java objects.

In some cases, however, you may want to store Java objects "as-is" and retrieve them later, using database columns of the `RAW` or `BLOB` type. There are different ways to accomplish this:

- You can map a serializable Java class to `RAW` or `BLOB` columns by using a nonstandard extension to the type map facility or by adding a type code field to the serializable class, so that instances of the serializable class can be stored as `RAW` or `BLOB`.

- You can use the `ORAData` facility to define a serializable wrapper class whose instances can be stored in `RAW` or `BLOB` columns.

Serializing in any of these ways works for any Oracle SQLJ run-time library.

This section covers the following topics:

- Serializing Java Classes to RAW and BLOB Columns

- SerializableDatum: an ORAData Implementation

- SerializableDatum in SQLJ Applications

- SerializableDatum (Complete Class)

#### 7.6.1 Serializing Java Classes to RAW and BLOB Columns

If you want to store instances of Java classes directly in `RAW` or `BLOB` columns, then you must meet certain nonstandard requirements to specify the desired SQL-Java mapping. Note that in SQLJ statements the serializable Java objects can be transparently read and written as if they were built-in types.

You have two options in specifying the SQL-Java type mapping:

- Declare a type map in the connection context declaration and use this type map to specify mappings.

- Use the `public static final` field `_SQL_TYPECODE` to specify the mapping.

##### Defining a Type Map for Serializable Classes

Consider an example where `SAddress`, `pack.SPerson`, and `pack.Manager.InnerSPM`, where `InnerSPM` is an inner class of `Manager`, are serializable Java classes. In other words, these classes implement the `java.io.Serializable` interface.

You must use the classes only in statements that use explicit connection context instances of a declared connection context type, such as `SerContext` in the following example:

    SAddress               a =...;
    pack.SPerson           p =...;
    pack.Manager.InnerSPM pm =...;
    SerContext ctx = new SerContext(url,user,pwd,false);
    #sql [ctx] { ... :a ... :OUT p ... :INOUT pm ... };

The following is required:

- The connection context type must have been declared using the `typeMap` attribute of a `with` clause to specify an associated class implementing `java.util.PropertyResourceBundle`. In the example, `SerContext` may be declared as follows.

      #sql public static context SerContext with (typeMap="SerMap");

- The type map resource must provide nonstandard mappings from `RAW` or `BLOB` columns to the serializable Java classes. This mapping is specified with entries of the following form, depending on whether the Java class is mapped to a `RAW` or a `BLOB` column:

      oracle-class.java_class_name=JAVA_OBJECT RAW
      oracle-class.java_class_name=JAVA_OBJECT BLOB

  The keyword `oracle-class` marks this as an Oracle-specific extension. In the example, the `SerMap.properties` resource file may contain the following entries:

      oracle-class.SAddress=JAVA_OBJECT RAW
      oracle-class.pack.SPerson=JAVA_OBJECT BLOB
      oracle-class.packManager$InnerSPM=JAVA_OBJECT RAW

  Although the period (.) separates package and class names, you must use the dollar sign (\$) to separate an inner class name.

Note that this Oracle-specific extension can be placed in the same type map resource as standard `SQLData` type map entries.

##### Using Fields to Determine Mapping for Serializable Classes

As an alternative to using a type map for a serializable class, you can use static fields in the serializable class to determine type mapping. You can add either of the following fields to a class that implements the `java.io.Serializable` interface, such as the `SAddress` and `SPerson` classes from the preceding example:

    public final static int _SQL_TYPECODE = oracle.jdbc.OracleTypes.RAW;

    public final static int _SQL_TYPECODE = oracle.jdbc.OracleTypes.BLOB;

**Note:**

Using the type map facility supersedes manually adding the `_SQL_TYPECODE` field to the class.

##### Limitations on Serializing Java Objects

You should be aware of the effect of serialization. If two objects, A and B, share the same object, C, then upon serialization and subsequent deserialization of A and B, each will point to its own clone of the object C. Sharing is broken.

In addition, note that for a given Java class, you can declare only one kind of serialization: either into `RAW` or into `BLOB`. The SQLJ translator can check only that the actual usage conforms to either `RAW` or `BLOB`.

`RAW` columns are limited in size. You might experience run-time errors if the actual size of the serialized Java object exceeds the size of the column.

Column size is much less restrictive for `BLOB` columns. Writing a serialized Java object to a `BLOB` column is supported by Oracle JDBC Oracle Call Interface (OCI) driver and Oracle JDBC Thin driver. Retrieving a serialized object from a `BLOB` column is supported by all Oracle JDBC drivers since Oracle9i.

Finally, treating serialized Java objects this way is an Oracle-specific extension and requires Oracle SQLJ run time as well as either the default Oracle-specific code generation (`-codegen=oracle` during translation) or, for ISO standard code generation (`-codegen=iso`), Oracle-specific profile customization.

10iProd: Note that future versions of Oracle might support SQL types that directly encapsulate Java serialized objects. These are described as JAVA_OBJECT SQL types in JDBC 2.0. At that point, you can replace each of the BLOB and RAW designations by the names of their corresponding JAVA_OBJECT SQL types, and you can drop the oracle- prefix on the entries.

**Note:**

The implementation of this particular serialization mechanism does not use JDBC type maps. The map (to `BLOB` or to `RAW`) is hardcoded in the Oracle profile customization at translation time, or is generated directly into Java code.

#### 7.6.2 SerializableDatum: an ORAData Implementation

"Additional Uses for ORAData Implementations" includes examples of situations where you might want to define a custom Java class that maps to some `oracle.sql.*` type other than `oracle.sql.STRUCT`, `oracle.sql.REF`, or `oracle.sql.ARRAY`.

An example of such a situation is if you want to serialize and deserialize Java objects into and out of `RAW` fields, with a custom Java class that maps to the `oracle.sql.RAW` type. This could apply equally to `BLOB` fields, with a custom Java class that maps to the `oracle.sql.BLOB` type.

This section presents an example of such an application, creating a class, `SerializableDatum`, that implements the `ORAData` interface and follows the general form of custom Java classes. The example starts with a step-by-step approach to the development of `SerializableDatum`, followed by the complete sample code.

**Note:**

This application uses classes from the `java.io`, `java.sql`, `oracle.sql`, and `oracle.jdbc` packages. The import statements are not shown here.

1.  Begin with a skeleton of the class.
        public class SerializableDatum implements ORAData
        {
           // Client methods for constructing and accessing the Java object

           public Datum toDatum(java.sql.Connection c) throws SQLException
           {
              // Implementation of toDatum()
           }

           public static ORADataFactory getORADataFactory()
           {
              return FACTORY;
           }

           private static final ORADataFactory FACTORY =
                   // Implementation of an ORADataFactory for SerializableDatum

           // Construction of SerializableDatum from oracle.sql.RAW

           public static final int _SQL_TYPECODE = OracleTypes.RAW;
        }

    `SerializableDatum` does not implement the `ORADataFactory` interface, but its `getORADataFactory()` method returns a static member that implements this interface.

    The `_SQL_TYPECODE` is set to `OracleTypes.RAW` because this is the data type being read from and written to the database. The SQLJ translator needs this type code information in performing online type-checking to verify compatibility between the user-defined Java type and the SQL type.
2.  Define client methods that perform the following:
    - Create a `SerializableDatum` object.

    - Populate a `SerializableDatum` object.

    - Retrieve data from a `SerializableDatum` object.

    <!-- -->

        // Client methods for constructing and accessing a SerializableDatum

        private Object m_data;
        public SerializableDatum()
        {
           m_data = null;
        }
        public void setData(Object data)
        {
           m_data = data;
        }
        public Object getData()
        {
           return m_data;
        }
3.  Implement a `toDatum()` method that serializes data from a `SerializableDatum` object to an `oracle.sql.RAW` object. The implementation of `toDatum()` must return a serialized representation of the object in the `m_data` field as an `oracle.sql.RAW` instance.
        // Implementation of toDatum()

        try {
           ByteArrayOutputStream os = new ByteArrayOutputStream();
           ObjectOutputStream oos = new ObjectOutputStream(os);
           oos.writeObject(m_data);
           oos.close();
           return new RAW(os.toByteArray());
        } catch (Exception e) {
          throw new SQLException("SerializableDatum.toDatum: "+e.toString()); }
4.  Implement data conversion from an `oracle.sql.RAW` object to a `SerializableDatum` object. This step deserializes the data.
        // Constructing SerializableDatum from oracle.sql.RAW

        private SerializableDatum(RAW raw) throws SQLException
        {
           try {
              InputStream rawStream = new ByteArrayInputStream(raw.getBytes());
              ObjectInputStream is = new ObjectInputStream(rawStream);
              m_data = is.readObject();
              is.close();
           } catch (Exception e) {
             throw new SQLException("SerializableDatum.create: "+e.toString()); }
        }
5.  Implement an `ORADataFactory`. In this case, it is implemented as an anonymous class.
        // Implementation of an ORADataFactory for SerializableDatum

        new ORADataFactory()
        {
           public ORAData create(Datum d, int sqlCode) throws SQLException
           {
              if (sqlCode != _SQL_TYPECODE)
              {
                 throw new SQLException
                           ("SerializableDatum: invalid SQL type "+sqlCode);
              }
              return (d==null) ? null : new SerializableDatum((RAW)d);
           }
        };

#### 7.6.3 SerializableDatum in SQLJ Applications

Given the `SerializableDatum` class created in the preceding section, this section shows how to use an instance of it in a SQLJ application, both as a host variable and as an iterator column.

Presume the following table definition:

    CREATE TABLE PERSONDATA (NAME VARCHAR2(20) NOT NULL, INFO RAW(2000));

##### SerializableDatum as Host Variable

The following uses a `SerializableDatum` instance as a host variable:

    ...
    SerializableDatum pinfo = new SerializableDatum();
    pinfo.setData (
       new Object[] {"Some objects", new Integer(51), new Double(1234.27) } );
    String pname = "MILLER";
    #sql { INSERT INTO persondata VALUES(:pname, :pinfo) };
    ...

##### SerializableDatum in Iterator Column

Following is an example of using `SerializableDatum` as a named iterator column:

    #sql iterator PersonIter (SerializableDatum info, String name);

    ...
    PersonIter pcur;
    #sql pcur = { SELECT * FROM persondata WHERE info IS NOT NULL };
    while (pcur.next())
    {
       System.out.println("Name:" + pcur.name() + " Info:" + pcur.info());
    }
    pcur.close();
    ...

#### 7.6.4 SerializableDatum (Complete Class)

The following is complete code for the `SerializableDatum` class, which was developed in step-by-step fashion in the preceding sections.

    import java.io.*;
    import java.sql.*;
    import oracle.sql.*;
    import oracle.jdbc.*;

    public class SerializableDatum implements ORAData
    {
    // Client methods for constructing and accessing a SerializableDatum

       private Object m_data;
       public SerializableDatum()
       {
          m_data = null;
       }
       public void setData(Object data)
       {
          m_data = data;
       }
       public Object getData()
       {
          return m_data;
       }

    // Implementation of toDatum()

       public Datum toDatum(Connection c) throws SQLException
       {

          try {
             ByteArrayOutputStream os = new ByteArrayOutputStream();
             ObjectOutputStream oos = new ObjectOutputStream(os);
             oos.writeObject(m_data);
             oos.close();
             return new RAW(os.toByteArray());
          } catch (Exception e) {
            throw new SQLException("SerializableDatum.toDatum: "+e.toString()); }
       }

       public static ORADataFactory getORADataFactory()
       {
          return FACTORY;
       }

    // Implementation of an ORADataFactory for SerializableDatum

       private static final ORADataFactory FACTORY =

          new ORADataFactory()
          {
             public ORAData create(Datum d, int sqlCode) throws SQLException
             {
                if (sqlCode != _SQL_TYPECODE)
                {
                   throw new SQLException(
                      "SerializableDatum: invalid SQL type "+sqlCode);
                }
                return (d==null) ? null : new SerializableDatum((RAW)d);
             }
          };

    // Constructing SerializableDatum from oracle.sql.RAW

       private SerializableDatum(RAW raw) throws SQLException
       {
          try {
             InputStream rawStream = new ByteArrayInputStream(raw.getBytes());
             ObjectInputStream is = new ObjectInputStream(rawStream);
             m_data = is.readObject();
             is.close();
          } catch (Exception e) {
            throw new SQLException("SerializableDatum.create: "+e.toString()); }
       }

       public static final int _SQL_TYPECODE = OracleTypes.RAW;
    }

### 7.7 Weakly Typed Objects, References, and Collections

Weakly typed objects, references, and collections are supported by SQLJ. Their use is not generally recommended, and there are some specific restrictions, but in some circumstances they can be useful. For example, you might have generic code that can use "any `STRUCT`" or "any `REF`".

This section covers the following topics:

- Support for Weakly Typed Objects\_ References\_ and Collections

- Restrictions on Weakly Typed Objects\_ References\_ and Collections

#### 7.7.1 Support for Weakly Typed Objects, References, and Collections

In using Oracle objects, references, or collections in a SQLJ application, you have the option of using generic and weakly typed `java.sql` or `oracle.sql` instances instead of the strongly typed custom object, reference, and collection classes that implement the `ORAData` interface or the strongly typed custom object classes that implement the `SQLData` interface. Note that if you use `SQLData` implementations for your custom object classes, then you will have no choice but to use weakly typed custom reference instances.

The following weak types can be used for iterator columns or host expressions in the Oracle SQLJ implementation:

- `java.sql.Struct` or `oracle.sql.STRUCT` for objects

- `java.sql.Ref` or `oracle.sql.REF` for object references

- `java.sql.Array` or `oracle.sql.ARRAY` for collections

In host expressions, they are supported as follows:

- As input host expressions

- As output host expressions in an `INTO`-list

Using these weak types is not generally recommended, however, as you would lose all the advantages of the strongly typed paradigm that SQLJ offers.

Each attribute in a `STRUCT` object or each element in an `ARRAY` object is stored in an `oracle.sql.Datum` object, with the underlying data being in the form of the appropriate `oracle.sql.*` subtype of `Datum`, such as `oracle.sql.NUMBER` or `oracle.sql.CHAR`. Attributes in a `STRUCT` object are nameless. Because of the generic nature of the `STRUCT` and `ARRAY` classes, SQLJ cannot perform type checking where objects or collections are written to or read from instances of these classes.

It is generally recommended that you use custom Java classes for objects, references, and collections.

#### 7.7.2 Restrictions on Weakly Typed Objects, References, and Collections

A weakly typed object (`Struct` or `STRUCT` instance), reference (`Ref` or `REF` instance), or collection (`Array` or `ARRAY` instance) cannot be used in host expressions in the following circumstances:

- `IN` parameter if null

- `OUT` or `INOUT` parameter in a stored procedure or function call

- `OUT` parameter in a stored function result expression

They cannot be used in these ways, because there is no way to know the underlying SQL type name, such as `Person`, which is required by Oracle JDBC driver to materialize an instance of a user-defined type in Java.

### 7.8 Oracle OPAQUE Types

Oracle OPAQUE types are abstract data types. With data implemented as simply a series of bytes, the internal representation is not exposed. Typically an OPAQUE type will be provided by Oracle, not implemented by a customer.

OPAQUE types are similar in some basic ways to object types, with similar concepts of static methods, instances, and instance methods. Typically, only the methods supplied with an OPAQUE type allow you to manipulate the state and internal byte representation. In Java, an OPAQUE type can be represented as `oracle.sql.OPAQUE` or as a custom class implementing the `oracle.sql.ORAData` interface. On the client-side, Java code can be implemented to manipulate the bytes, assuming the byte pattern is known.

A key example of an OPAQUE type is `XMLType`, provided with Oracle Database 12c Release 2 (12.2). This Oracle-provided type facilitates handling XML data natively in the database.

`SYS.XMLType` offers the following features, exposed through the Java `oracle.xdb.XMLType` class:

- It can be used as the data type of a column in a table or view. `XMLType` can store any content but is designed to optimally store XML content. An instance of it can represent an XML document in SQL.

- It has a SQL API with built-in member functions that operate on XML content. For example, you can use `XMLType` functions to create, query, extract, and index XML data stored in an Oracle Database 12c Release 1 (12.1) instance.

- It can be used in stored procedures for parameters, return values, and variables.

- Its functionality is also available through APIs provided in PL/SQL, Java, and C (OCI).

**See Also:**

[Oracle XML DB Developer's Guide](../adxdb/XML-DB-basics.md)
