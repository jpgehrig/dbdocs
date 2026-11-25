Symbols  A  B  C  D  E  F  G  I  J  L  M  N  O  P  Q  R  S  T  U  V  W  X  

------------------------------------------------------------------------

## Symbols

- .NET object extensions [1.3.2](key-features-object-relational-model.md)
- .NET stored procedures [1.3.2](key-features-object-relational-model.md)

------------------------------------------------------------------------

## A

- ADMIN OPTION
  - with EXECUTE ANY TYPE [7.1.3](privileges-on-object-types-and-their-methods.md)
- aggregate functions
  - See: user-defined aggregate functions
- aliases
  - required for tables [2.1.8.1](Sql-object-types-and-references.md)
- ALTER ANY TYPE privilege [7.1.1](privileges-on-object-types-and-their-methods.md)
  - See also: privileges
- ALTER TABLE [8.3.9](type-evolution.md)
  - See also: object types, evolving

  <!-- -->

  - storing XMLTypes and LOBs [8.4](storing-XMLTypes-and-LOBs-in-an-ANYDATA-column.md)
- ALTER TYPE statement [8.3.8](type-evolution.md)
  - See also: object types, evolving
- ANYDATA column
  - Storing XMLTypes and LOBs in [8.4](storing-XMLTypes-and-LOBs-in-an-ANYDATA-column.md)
- ANYDATA data type [8.6](transient-and-generic-types.md)
- ANYDATASET data type [8.6](transient-and-generic-types.md)
- ANYDATA types [8.4](storing-XMLTypes-and-LOBs-in-an-ANYDATA-column.md)
- ANYTYPE data type [8.6](transient-and-generic-types.md)
- arrays
  - size of VARRAYs [5.1.5](collection-data-types.md)
- assignment narrowing [2.3.19.3](inheritance-in-sql-object-types.md)
- assignments
  - across object types [2.3.19](inheritance-in-sql-object-types.md)
  - collections [2.3.19.4](inheritance-in-sql-object-types.md)
  - objects and REFs to objects [2.3.19.1](inheritance-in-sql-object-types.md)
- atomic nulls [2.1.1](Sql-object-types-and-references.md)
  - object types in PL/SQL [3.1.3](declaring-initializing-objects-in-plsql.md)
- attributes
  - leaf-level [2.1.5](Sql-object-types-and-references.md), [8.1.1](storage-of-objects.md)
  - modifying [8.3.7](type-evolution.md)
  - of object types [1.3.1.1](key-features-object-relational-model.md)
- attribute value constructor [2.2.4](object-methods.md)

------------------------------------------------------------------------

## B

- bind variables
  - object types [4.3](plsql.md)
- BULK COLLECT clause [5.3.3](operations-on-collection-data-types.md)

------------------------------------------------------------------------

## C

- caches
  - object cache [4.4.1](oracle-call-interface-oci.md), [4.5.1](pro-c-cpp.md), [6.3](object-views-used-in-applications.md), [7.1.5](privileges-on-object-types-and-their-methods.md)
  - object views [6.3](object-views-used-in-applications.md)
- capture avoidance rule [2.1.8.1](Sql-object-types-and-references.md)
- CARDINALITY function [5.3.5.1](operations-on-collection-data-types.md)
- CAST function [2.4.1](functions-and-operators-useful-with-objects.md)
- character length semantics
  - object types [2.1.2](Sql-object-types-and-references.md)
- COLLECT function [5.3.5.2](operations-on-collection-data-types.md)
- collections [5.1](collection-data-types.md)
  - See also: varrays, nested tables

  <!-- -->

  - assigning [2.3.19.4](inheritance-in-sql-object-types.md)
  - assignments [5.2](multilevel-collection-types.md)
  - constructing [1.3.1.10](key-features-object-relational-model.md)
  - constructor methods [5.1.3](collection-data-types.md)
  - creating [5.1.2](collection-data-types.md)
  - data types [5.1](collection-data-types.md)
  - DML on [5.3.2](operations-on-collection-data-types.md)
  - multilevel [5.2](multilevel-collection-types.md), [9.4.1](design-considerations-for-collections.md), [9.4.5.1](design-considerations-for-collections.md)
    - constructing [5.2.5](multilevel-collection-types.md)
    - creating [5.2.5](multilevel-collection-types.md)
    - creating with REFs [9.4.5](design-considerations-for-collections.md), [9.4.5.2](design-considerations-for-collections.md)
    - object views containing [6.6.2](nested-tables-and-varrays-used-in-object-views.md)
  - nested tables [5.1.7](collection-data-types.md)
  - querying [5.3.1](operations-on-collection-data-types.md), [9.4.1](design-considerations-for-collections.md)
  - substitutable elements [2.3.12.5](inheritance-in-sql-object-types.md)
  - substituting [2.3.11](inheritance-in-sql-object-types.md)
  - supported data types [1.3.1.10](key-features-object-relational-model.md)
  - variable arrays (VARRAYs) [5.1.5](collection-data-types.md)
- COLUMN_VALUE keyword [5.2.1](multilevel-collection-types.md)
- column objects [1.3.1.4](key-features-object-relational-model.md)
  - indexes on [2.1.5](Sql-object-types-and-references.md)
  - versus row objects [9.1.1](general-storage-considerations-for-objects.md)
- columns
  - column objects [1.3.1.4](key-features-object-relational-model.md)
  - hidden [8.1.3](storage-of-objects.md), [8.2.1](creating-indexes-on-typeids-or-attributes.md)
  - qualifying in queries [2.1.8](Sql-object-types-and-references.md)
- comparisons
  - methods [2.2.2.2](object-methods.md)
  - nested tables [5.3.4](operations-on-collection-data-types.md)
- compilation
  - of object types [7.2.1](type-dependencies.md)
- constraints
  - object tables [2.1.3](Sql-object-types-and-references.md)
  - on Oracle objects [9.10](constraints-on-objects.md)
  - REFs [9.3.2](design-considerations-for-REFs.md)
- constructor methods [5.1.3](collection-data-types.md)
- constructors [1.3.1.3](key-features-object-relational-model.md), [2.2.4](object-methods.md), [8.1.2](storage-of-objects.md)
  - attribute values [8.5.1](system-defined-and-user-defined-constructors.md)
  - calling user-defined [8.5.6](system-defined-and-user-defined-constructors.md)
  - literal invocation [2.2.4](object-methods.md)
  - literal invocation of [2.2.4](object-methods.md)
  - methods [2.2.4](object-methods.md)
  - overloading [8.5.4](system-defined-and-user-defined-constructors.md)
  - overriding [8.5.4](system-defined-and-user-defined-constructors.md)
  - system defined [8.5.1](system-defined-and-user-defined-constructors.md)
  - type evolution [8.5.2](system-defined-and-user-defined-constructors.md)
  - user-defined [8.5.3](system-defined-and-user-defined-constructors.md), [8.5.4](system-defined-and-user-defined-constructors.md)
  - with NEW keyword [8.5.1](system-defined-and-user-defined-constructors.md)
- CREATE INDEX statement
  - object types [2.1.5](Sql-object-types-and-references.md)
- CREATE OR REPLACE TYPE Table Dependencies [7.2.4](type-dependencies.md)
- CREATE OR REPLACE TYPE with FORCE option [7.2.4](type-dependencies.md)
- CREATE OR REPLACE TYPE with Type Dependencies [7.2.4](type-dependencies.md)
- CREATE TABLE statement
  - column object example [1.3.1.2](key-features-object-relational-model.md)
  - object table example [1.3.1.4](key-features-object-relational-model.md), [2.1.3](Sql-object-types-and-references.md)
- CREATE TRIGGER statement
  - object table example [2.1.6](Sql-object-types-and-references.md)
- CREATE TYPE privilege [7.1.1](privileges-on-object-types-and-their-methods.md)
  - See also: privileges
- CREATE TYPE statement
  - collection types [1.3.1.10](key-features-object-relational-model.md)
  - dependent types [7.2.1](type-dependencies.md)
  - example [5.1.7](collection-data-types.md)
  - nested tables [5.1.7](collection-data-types.md)
  - object types [1.3.1.1](key-features-object-relational-model.md)
  - varrays [5.1.5](collection-data-types.md)
- creating object types [1.3.1.1](key-features-object-relational-model.md)
- creating VARRAYs
  - containing references to LOBs [5.1.10](collection-data-types.md)
- CURSOR expression [2.4.2](functions-and-operators-useful-with-objects.md)

------------------------------------------------------------------------

## D

- dangling REFs [1.3.1.6.2](key-features-object-relational-model.md), [1.3.1.7](key-features-object-relational-model.md)
- database administrators (DBAs)
  - DBA role [7.1.1](privileges-on-object-types-and-their-methods.md)
- database links
  - and object types [2.1.9](Sql-object-types-and-references.md)
- data types
  - array types [5.1.5](collection-data-types.md)
  - generic [8.6](transient-and-generic-types.md)
  - nested tables [5.1.7](collection-data-types.md)
  - object types [2.1.9](Sql-object-types-and-references.md)
  - opaque [8.6](transient-and-generic-types.md)
  - transient [8.6](transient-and-generic-types.md)
- DBA role
  - user-defined types [7.1.1](privileges-on-object-types-and-their-methods.md)
- declarations
  - object in a PL/SQL block [3.1.2](declaring-initializing-objects-in-plsql.md)
- declaring objects in PL/SQL [3.1](declaring-initializing-objects-in-plsql.md)
- DEFAULT clause [5.1.3](collection-data-types.md)
- default values
  - collections [5.1.3](collection-data-types.md)
  - object types [5.1.3](collection-data-types.md)
- DELETE privilege
  - for object tables [7.1.5](privileges-on-object-types-and-their-methods.md)
- DEREF
  - dereferencing a ref with [1.3.1.7.1](key-features-object-relational-model.md)
- dereferencing [1.3.1.7](key-features-object-relational-model.md)
  - implicit [1.3.1.7](key-features-object-relational-model.md)
- DEREF function [2.4.3](functions-and-operators-useful-with-objects.md), [3.2.5](object-manipulation-in-plsql.md)
- dot notation [2.1.8](Sql-object-types-and-references.md)
  - for object attributes in PL/SQL [3.2.1](object-manipulation-in-plsql.md)
  - for object methods in PL/SQL [3.2.2](object-manipulation-in-plsql.md)
  - using with methods [2.2.2](object-methods.md)
- DROP ANY TYPE privilege [7.1.1](privileges-on-object-types-and-their-methods.md)
  - See also: privileges
- DROP TYPE statement
  - FORCE option [7.2.7](type-dependencies.md)
- dump files
  - Export and Import [4.9.1](utilities-providing-support-for-objects.md)
- dynamic method dispatch [2.3.10](inheritance-in-sql-object-types.md), [3.3](use-of-overloading-in-plsql-with-inheritance.md)
- dynamic SQL [3.4](using-dynamic-sql-with-objects.md)

------------------------------------------------------------------------

## E

- editions
  - views [1.1](about-oracle-objects.md)
- equal and not equal conditions
  - nested tables [5.3.4](operations-on-collection-data-types.md)
- equipartitioning
  - nested tables
    - partitioning [5.4](partitioning-table-that-contain-oracle-objects.md)
- evolution
  - object types [1.3.1.13](key-features-object-relational-model.md)
  - versus inheritance [9.13.1](design-consideration-tips-and-techniques.md)
- EXECUTE ANY TYPE privilege [7.1.1](privileges-on-object-types-and-their-methods.md), [7.1.3](privileges-on-object-types-and-their-methods.md)
  - See also: privileges
- EXECUTE privilege [7.1.3](privileges-on-object-types-and-their-methods.md)
  - See also: privileges

  <!-- -->

  - object types [7.1.3](privileges-on-object-types-and-their-methods.md)
- executing SQL statements at run time [3.4](using-dynamic-sql-with-objects.md)
- export object types [4.9.1](utilities-providing-support-for-objects.md)
- Export utility
  - object types [4.9.1](utilities-providing-support-for-objects.md)

------------------------------------------------------------------------

## F

- files
  - Export and Import dump file [4.9.1](utilities-providing-support-for-objects.md)
- FINAL keyword [2.3.3](inheritance-in-sql-object-types.md)
  - modifying finality [8.3.7](type-evolution.md)
- FORCE keyword [6.13.2](defining-complex-relationships-in-object-views.md)
- function-based indexes
  - on type methods [9.5.4](design-considerations-for-methods.md)

------------------------------------------------------------------------

## G

- generalized expression [2.3.5.3](inheritance-in-sql-object-types.md)
- generalized method invocation [2.3.5.3](inheritance-in-sql-object-types.md)
- generic data type [8.6](transient-and-generic-types.md)
- generic programming [8.6](transient-and-generic-types.md)
- guidelines
  - comparison methods [2.2.2.2.5](object-methods.md)

------------------------------------------------------------------------

## I

- implicit dereferencing [1.3.1.7](key-features-object-relational-model.md)
- importing object tables [4.9.1](utilities-providing-support-for-objects.md)
- import object types [4.9.1](utilities-providing-support-for-objects.md)
- Import utility
  - object types [4.9.1](utilities-providing-support-for-objects.md)
- incomplete object types [7.2.1](type-dependencies.md)
- IN condition [5.3.4.2](operations-on-collection-data-types.md)
- indexes
  - nested table [5.1.7.2](collection-data-types.md)
  - object types [2.1.5](Sql-object-types-and-references.md)
  - on REFs [2.1.5](Sql-object-types-and-references.md)
  - type-discriminant column [8.2.1](creating-indexes-on-typeids-or-attributes.md)
- index-organized tables [5.2.1](multilevel-collection-types.md)
  - storing nested tables as [5.2.1.3](multilevel-collection-types.md)
- inheritance [1.3.1.12](key-features-object-relational-model.md)
  - See: type inheritance

  <!-- -->

  - and overloading [3.3](use-of-overloading-in-plsql-with-inheritance.md)
  - multiple [2.3](inheritance-in-sql-object-types.md)
  - single [2.3](inheritance-in-sql-object-types.md)
  - versus evolution [9.13.1](design-consideration-tips-and-techniques.md)
- inheriting methods [2.3.9](inheritance-in-sql-object-types.md)
- initializing objects in PL/SQL [3.1](declaring-initializing-objects-in-plsql.md)
- inner capture [2.1.8.1](Sql-object-types-and-references.md)
- INSERT privilege
  - for object tables [7.1.5](privileges-on-object-types-and-their-methods.md)
- instances
  - objects [1.3.1.2](key-features-object-relational-model.md)
  - object type [1.3.1.1](key-features-object-relational-model.md)
- INSTANTIABLE keyword
  - CREATE TYPE [2.3.6](inheritance-in-sql-object-types.md)
  - modifying instantiability [8.3.7](type-evolution.md)
- INSTEAD OF triggers
  - nested tables [6.11.1](object-view-manipulations.md)
- invoker-rights
  - object types [9.6](reusable-code-using-invoker-rights.md)
- invoking constructors [2.2.4](object-methods.md)
- IOTs
  - See: index-based tables
- IS A SET condition [5.3.4.6](operations-on-collection-data-types.md)
- IS EMPTY condition [5.3.4.5](operations-on-collection-data-types.md)
- IS NOT A SET condition [5.3.4.6](operations-on-collection-data-types.md)
- IS OF type predicate [2.4.4](functions-and-operators-useful-with-objects.md)

------------------------------------------------------------------------

## J

- Java
  - object storage [4.7.3](java-tools-for-accessing-oracle-objects.md)
  - Oracle JDBC and Oracle objects [4.7.1](java-tools-for-accessing-oracle-objects.md)
  - with Oracle objects [4.7](java-tools-for-accessing-oracle-objects.md)
- JDBC
  - See: Oracle JDBC

------------------------------------------------------------------------

## L

- leaf-level attributes [2.1.5](Sql-object-types-and-references.md), [8.1.1](storage-of-objects.md)
  - scalar [8.1.1](storage-of-objects.md)
- left correlation [5.3.1.2](operations-on-collection-data-types.md)
- literal invocation of a method [2.2.4.3](object-methods.md)
- locators
  - returning nested tables as [8.8](how-locators-improve-the-performance-of-nested-tables.md), [9.4.4.3](design-considerations-for-collections.md), [9.4.4.3.1](design-considerations-for-collections.md)
  - using a hint [9.4.4.3.2](design-considerations-for-collections.md)
- locks
  - object level locking [4.4.1](oracle-call-interface-oci.md)

------------------------------------------------------------------------

## M

- managing
  - object types [7](managing-oracle-objects.md)
- map methods [9.2](performance-of-object-comparisons.md)
  - comparing collections [5.3.4.1](operations-on-collection-data-types.md)
  - for comparing objects [2.2.2.2.1](object-methods.md)
- materialized views [1.3.1.11](key-features-object-relational-model.md), [9.9.2](materialized-view-support-for-objects.md)
- MEMBER condition [5.3.4.4](operations-on-collection-data-types.md)
- member methods [1.3.1.3](key-features-object-relational-model.md), [2.2.2](object-methods.md)
- member procedures
  - with SELF IN OUT NOCOPY [9.5.3](design-considerations-for-methods.md)
- methods [2.2.4](object-methods.md)
  - choosing a language for [9.5.1](design-considerations-for-methods.md)
  - comparison methods [2.2.2.2](object-methods.md)
    - in a type hierarchy [2.2.2.2.6](object-methods.md)
  - constructor [1.3.1.3](key-features-object-relational-model.md)
  - constructors [1.3.1.3](key-features-object-relational-model.md), [2.2.4](object-methods.md), [8.1.2](storage-of-objects.md)
  - creating maps [2.2.2.2.2](object-methods.md)
  - dot notation [2.2.2](object-methods.md)
  - dropping [8.3.7](type-evolution.md)
  - dynamic method dispatch [2.3.10](inheritance-in-sql-object-types.md)
  - execution privilege for [7.1.2](privileges-on-object-types-and-their-methods.md)
  - final [2.3.3](inheritance-in-sql-object-types.md)
  - function-based indexes [9.5.4](design-considerations-for-methods.md)
  - guidelines for comparison [2.2.2.2.5](object-methods.md)
  - inheriting [2.3.9](inheritance-in-sql-object-types.md)
  - instantiability [2.3.6](inheritance-in-sql-object-types.md)
  - invoking [2.2.2](object-methods.md)
  - map [2.2.2.2.1](object-methods.md), [9.2](performance-of-object-comparisons.md)
  - map for comparing objects [2.2.2.2.1](object-methods.md)
  - map required for collections [5.3.4.1](operations-on-collection-data-types.md)
  - member [1.3.1.3](key-features-object-relational-model.md), [2.2.2](object-methods.md)
  - object types [1.3.1.3](key-features-object-relational-model.md), [2.2](object-methods.md)
  - order [2.2.2.2.4](object-methods.md), [9.2](performance-of-object-comparisons.md)
  - overloading [2.3.5](inheritance-in-sql-object-types.md), [2.3.9](inheritance-in-sql-object-types.md), [2.3.9.1](inheritance-in-sql-object-types.md)
  - overriding [2.3.3](inheritance-in-sql-object-types.md), [2.3.5](inheritance-in-sql-object-types.md), [2.3.9](inheritance-in-sql-object-types.md), [2.3.9.2](inheritance-in-sql-object-types.md)
  - PL/SQL [4.3](plsql.md)
  - redefining [2.3.9.2](inheritance-in-sql-object-types.md)
  - restrictions on overriding [2.3.9.3](inheritance-in-sql-object-types.md)
  - SELF parameter [2.2.2.1](object-methods.md)
  - static [1.3.1.3](key-features-object-relational-model.md), [2.2.3](object-methods.md), [9.5.2](design-considerations-for-methods.md)
- modify_opaque_type clause [8.4](storing-XMLTypes-and-LOBs-in-an-ANYDATA-column.md)
- multilevel collections
  - See: collections, multilevel

  <!-- -->

  - varray storage [5.2.2](multilevel-collection-types.md)
- multiple inheritance [2.3](inheritance-in-sql-object-types.md)
- multiple subtypes [2.3.5.6](inheritance-in-sql-object-types.md)
- MULTISET EXCEPT operator [5.3.5.3](operations-on-collection-data-types.md)
- MULTISET INTERSECT operator [5.3.5.4](operations-on-collection-data-types.md)
- multiset operations
  - with nested tables [5.3.5](operations-on-collection-data-types.md)
- MULTISET UNION operator [5.3.5.5](operations-on-collection-data-types.md)

------------------------------------------------------------------------

## N

- name resolution
  - object types [2.1.8](Sql-object-types-and-references.md)
- narrowing [2.4.8](functions-and-operators-useful-with-objects.md)
- NESTED_TABLE_GET_REFS hint [9.4.4.3.2](design-considerations-for-collections.md)
- NESTED_TABLE_ID [5.2.1](multilevel-collection-types.md)
- NESTED_TABLE_ID keyword [9.4.4.2](design-considerations-for-collections.md)
- nested tables [9.4.4](design-considerations-for-collections.md)
  - adding to an object [8.3.6](type-evolution.md)
  - comparing [5.3.4](operations-on-collection-data-types.md)
  - creating [5.1.2](collection-data-types.md)
  - creating indexes on [9.4.4.2](design-considerations-for-collections.md)
  - equal and not equal conditions [5.3.4](operations-on-collection-data-types.md)
  - in an index-organized table [5.2.1.3](multilevel-collection-types.md)
  - indexes [5.1.7.2](collection-data-types.md)
  - INSTEAD OF triggers [6.11.1](object-view-manipulations.md)
  - locators [8.8](how-locators-improve-the-performance-of-nested-tables.md), [9.4.4.3](design-considerations-for-collections.md)
  - multiset operations [5.3.5](operations-on-collection-data-types.md)
  - piecewise operations [5.3.2.2](operations-on-collection-data-types.md)
  - querying [5.3.1](operations-on-collection-data-types.md)
    - unnesting results [5.3.1.2](operations-on-collection-data-types.md)
  - returning as locators [9.4.4.3](design-considerations-for-collections.md), [9.4.4.3.1](design-considerations-for-collections.md)
  - specifying a storage name [8.3.6](type-evolution.md)
  - specifying storage in a tablespace [5.1.7.3](collection-data-types.md)
  - storage [5.2.1](multilevel-collection-types.md), [9.4.4.1](design-considerations-for-collections.md)
  - updating in views [6.11.1](object-view-manipulations.md)
- NEW keyword [2.2.4](object-methods.md)
- NLS_LENGTH_SEMANTICS initialization parameter [2.1.2](Sql-object-types-and-references.md)
- NOCOPY compiler hint
  - methods [2.2.2.1](object-methods.md)
  - performance issues [9.5.3](design-considerations-for-methods.md)
  - use with member procedures [9.5.3](design-considerations-for-methods.md)
  - use with SELF [2.2.2.1](object-methods.md), [9.5.3](design-considerations-for-methods.md)
- NOT FINAL keyword [2.3.3](inheritance-in-sql-object-types.md)
- NOT MEMBER condition [5.3.4.4](operations-on-collection-data-types.md)
- nulls
  - atomic [2.1.1](Sql-object-types-and-references.md)
  - object types [2.1.1](Sql-object-types-and-references.md)

------------------------------------------------------------------------

## O

- OBJECT_ID pseudocolumn [2.3.12.2](inheritance-in-sql-object-types.md)
- OBJECT_VALUE pseudocolumn [2.3.12.2](inheritance-in-sql-object-types.md)
- object cache
  - object views [6.3](object-views-used-in-applications.md)
  - OCI [4.4.1](oracle-call-interface-oci.md)
  - privileges [7.1.5](privileges-on-object-types-and-their-methods.md)
  - Pro\*C [4.5.1](pro-c-cpp.md)
- object constructors
  - calling in PL/SQL [3.2.2](object-manipulation-in-plsql.md)
  - passing parameters to in PL/SQL [3.2.2](object-manipulation-in-plsql.md)
- object identifier [1.3.1.5](key-features-object-relational-model.md), [6.2](defining-object-views.md)
- object identifiers
  - column and index [9.1.1.2](general-storage-considerations-for-objects.md)
  - for object types [8.1.2](storage-of-objects.md)
  - primary-key based [9.1.2.2](general-storage-considerations-for-objects.md)
  - REFs [9.1.2](general-storage-considerations-for-objects.md)
  - storage [9.1.2](general-storage-considerations-for-objects.md)
  - system-generated [9.1.2.1](general-storage-considerations-for-objects.md)
- object instances [1.3.1.1](key-features-object-relational-model.md), [1.3.1.2](key-features-object-relational-model.md)
- object methods
  - calling in PL/SQL [3.2.2](object-manipulation-in-plsql.md)
- object-relational model
  - advantages [1.2](advantages-of-objects.md)
  - comparing objects [9.2](performance-of-object-comparisons.md)
  - constraints [9.10](constraints-on-objects.md)
  - database key features [1.3.1](key-features-object-relational-model.md)
  - design considerations [9](design-considerations-for-oracle-objects.md)
  - key features [1.3](key-features-object-relational-model.md)
  - methods [1.3.1.3](key-features-object-relational-model.md), [2.2](object-methods.md)
  - programmatic environments for [4](object-support-in-oracle-programming-environments.md), [4.7](java-tools-for-accessing-oracle-objects.md)
- object replication
  - using logical standby [9.8.2](replication-support-for-objects.md)
- object tables [1.3.1.4](key-features-object-relational-model.md), [9.1.1.2](general-storage-considerations-for-objects.md)
  - constraints [2.1.3](Sql-object-types-and-references.md)
  - importing [4.9.1](utilities-providing-support-for-objects.md)
  - indexes [2.1.5](Sql-object-types-and-references.md)
  - row objects [1.3.1.4](key-features-object-relational-model.md)
  - triggers [2.1.6](Sql-object-types-and-references.md)
  - virtual object tables [6.1](why-use-object-views.md)
- object types [1.1](about-oracle-objects.md), [2.3](inheritance-in-sql-object-types.md)
  - See also: type inheritance

  <!-- -->

  - adding a nested table attribute [8.3.6](type-evolution.md)
  - advantages [1.2](advantages-of-objects.md)
  - altering a type [8.3.4](type-evolution.md), [8.3.6](type-evolution.md)
  - assignments across [2.3.19](inheritance-in-sql-object-types.md)
  - attributes of [1.3.1.1](key-features-object-relational-model.md)
  - character length semantics [2.1.2](Sql-object-types-and-references.md)
  - collection objects [6.6](nested-tables-and-varrays-used-in-object-views.md)
  - collections [5.1](collection-data-types.md)
    - nested tables [5.1.7](collection-data-types.md)
    - variable arrays (VARRAYs) [5.1.5](collection-data-types.md)
  - column objects [1.3.1.4](key-features-object-relational-model.md)
  - column objects versus row objects [9.1.1](general-storage-considerations-for-objects.md)
  - comparison methods for [2.2.2.2](object-methods.md)
  - constructor methods [1.3.1.3](key-features-object-relational-model.md), [8.1.2](storage-of-objects.md)
  - constructor methods for [2.2.4](object-methods.md)
  - creating [1.3.1.1](key-features-object-relational-model.md)
  - creating subtypes of [2.3.5.2](inheritance-in-sql-object-types.md)
  - database key features [1.3.1](key-features-object-relational-model.md)
  - declaring in a PL/SQL block [3.1.2](declaring-initializing-objects-in-plsql.md)
  - dependencies [7.2](type-dependencies.md)
  - dependents [7.2.1](type-dependencies.md), [8.3](type-evolution.md)
  - evolution [1.3.1.13](key-features-object-relational-model.md)
  - evolving [8.3](type-evolution.md), [9.13.1](design-consideration-tips-and-techniques.md)
    - design considerations [9.11](considerations-related-to-type-evolution.md)
  - example of privileges [7.1.4](privileges-on-object-types-and-their-methods.md)
  - Export and Import [4.9.1](utilities-providing-support-for-objects.md)
  - FINAL or NOT FINAL [2.3.3](inheritance-in-sql-object-types.md)
  - in columns [6.4](objects-nested-in-object-views.md)
  - incomplete [7.2](type-dependencies.md), [7.2.1](type-dependencies.md), [7.2.2](type-dependencies.md)
  - indexes on column objects [2.1.5](Sql-object-types-and-references.md)
  - indexing [8.2.1](creating-indexes-on-typeids-or-attributes.md)
  - inheritance [1.3.1.12](key-features-object-relational-model.md), [2.3](inheritance-in-sql-object-types.md)
  - initializing in PL/SQL [3.1.3](declaring-initializing-objects-in-plsql.md)
  - instances [1.3.1.1](key-features-object-relational-model.md)
  - instantiable [2.3.6](inheritance-in-sql-object-types.md)
  - invoker-rights [9.6](reusable-code-using-invoker-rights.md)
  - key features [1.3](key-features-object-relational-model.md)
  - locking in cache [4.4.1](oracle-call-interface-oci.md)
  - managing [7](managing-oracle-objects.md)
  - methods [2.2](object-methods.md), [2.2.2](object-methods.md)
  - methods in PL/SQL [4.3](plsql.md)
  - mutually dependent [7.2.1](type-dependencies.md)
  - name resolution [2.1.8](Sql-object-types-and-references.md)
  - nested tables [5.1.7](collection-data-types.md)
  - not instantiable [2.3.6](inheritance-in-sql-object-types.md)
  - nulls [2.1.1](Sql-object-types-and-references.md)
  - object references [6.8](references-created-to-view-objects.md)
  - Oracle type translator [4.5.5](pro-c-cpp.md)
  - performance tuning [7.4](performance-tuning.md)
  - privileges [7.1](privileges-on-object-types-and-their-methods.md), [7.1.1](privileges-on-object-types-and-their-methods.md)
  - recompiling [7.2.3](type-dependencies.md)
  - remote access to [2.1.9](Sql-object-types-and-references.md), [6.12](applying-the-object-model-to-remote-tables.md)
  - row objects and object identifiers [6.6](nested-tables-and-varrays-used-in-object-views.md)
  - schema privileges [7.1.2](privileges-on-object-types-and-their-methods.md)
  - specializing [1.3.1.12](key-features-object-relational-model.md)
  - SQLJ types [4.7.3](java-tools-for-accessing-oracle-objects.md)
  - storage [8.1](storage-of-objects.md)
  - substituting [2.3.11](inheritance-in-sql-object-types.md)
  - subtypes [2.3.2](inheritance-in-sql-object-types.md)
  - synonyms [7.3](synonyms-for-object-types.md)
  - table aliases [2.1.8.1](Sql-object-types-and-references.md)
  - triggers [2.1.6](Sql-object-types-and-references.md)
  - use of table aliases [2.1.8.1](Sql-object-types-and-references.md)
  - utilities [4.9](utilities-providing-support-for-objects.md)
  - variable arrays (VARRAYs) [5.1.5](collection-data-types.md)
  - views [1.3.1.11](key-features-object-relational-model.md)
- object views [1.3.1.11](key-features-object-relational-model.md), [6](applying-an-object-model-to-relational-data.md)
  - advantages of [6.1](why-use-object-views.md)
  - circular references [6.13.1](defining-complex-relationships-in-object-views.md)
  - defining REFs
    - for rows of object views [6.2](defining-object-views.md)
  - hierarchies [6.14](object-vew-hierarchies.md), [9.13.3](design-consideration-tips-and-techniques.md)
    - privileges [6.14.3](object-vew-hierarchies.md)
    - querying in [6.14.2](object-vew-hierarchies.md)
  - modeling relationships [6.10](inverse-relationships-modelled-with-object-views.md), [6.13](defining-complex-relationships-in-object-views.md)
  - multilevel collections in [6.6.2](nested-tables-and-varrays-used-in-object-views.md)
  - nested tables [6.11.1](object-view-manipulations.md)
  - null objects in [6.5](identifying-null-objects-in-object-views.md)
  - OIDs with [6.7](object-identifiers-for-object-views.md)
  - REFs to [6.8](references-created-to-view-objects.md)
  - updating through INSTEAD OF triggers [6.11](object-view-manipulations.md)
- OCCI [4.6](oracle-c-cpp-call-interface-odci.md)
- OCI
  - associative access [4.4.2](oracle-call-interface-oci.md)
  - for Oracle objects
    - building a program [4.4.5](oracle-call-interface-oci.md)
  - navigational access [4.4.3](oracle-call-interface-oci.md)
  - object cache [4.4.4](oracle-call-interface-oci.md)
  - OCIObjectFlush [6.3](object-views-used-in-applications.md)
  - OCIObjectPin [6.3](object-views-used-in-applications.md)
- ODP.NET, Oracle Developer Tools for Visual Studio [1.3.2](key-features-object-relational-model.md)
- ODT, Microsoft common language [1.3.2](key-features-object-relational-model.md)
- OIDs [9.1.2](general-storage-considerations-for-objects.md)
- opaque data type [8.6](transient-and-generic-types.md)
- opaque types and ANYDATA [8.4](storing-XMLTypes-and-LOBs-in-an-ANYDATA-column.md)
- Oracle C++ Call Interface [4.6](oracle-c-cpp-call-interface-odci.md)
- Oracle Data Provider for .NET [1.3.2](key-features-object-relational-model.md)
- Oracle JDBC
  - accessing Oracle object data [4.7.1](java-tools-for-accessing-oracle-objects.md)
- Oracle objects
  - See: object-relational model
- Oracle SQLJ
  - data mapping for Oracle objects [4.7.2](java-tools-for-accessing-oracle-objects.md)
- Oracle type translator (OTT) [4.5.5](pro-c-cpp.md)
- order methods [2.2.2.2.4](object-methods.md), [9.2](performance-of-object-comparisons.md)
- ORGANIZATION INDEX clause [5.2.1](multilevel-collection-types.md)
- OTT [4.5.5](pro-c-cpp.md)
- outer-join syntax [5.3.1.2](operations-on-collection-data-types.md), [5.3.1.5](operations-on-collection-data-types.md)
- overloading [2.3.9](inheritance-in-sql-object-types.md)
  - and inheritance [3.3](use-of-overloading-in-plsql-with-inheritance.md)
  - methods [2.3.5](inheritance-in-sql-object-types.md), [2.3.9.1](inheritance-in-sql-object-types.md)
  - user-defined constructors [8.5.4](system-defined-and-user-defined-constructors.md)
- overriding
  - methods [2.3.5](inheritance-in-sql-object-types.md)
  - user-defined constructors [8.5.4](system-defined-and-user-defined-constructors.md)
- overriding methods [2.3.9](inheritance-in-sql-object-types.md)

------------------------------------------------------------------------

## P

- parallel query
  - objects [9.12](parallel-queries-with-oracle-objects.md)
  - restrictions for Oracle objects [9.12](parallel-queries-with-oracle-objects.md)
  - view objects [9.12](parallel-queries-with-oracle-objects.md)
- partitioning [5.4](partitioning-table-that-contain-oracle-objects.md)
  - tables containing Oracle object [5.4](partitioning-table-that-contain-oracle-objects.md)
- piecewise operations on multilevel nested tables [5.3.2.2](operations-on-collection-data-types.md)
- pkREFs [8.1.6](storage-of-objects.md)
- PL/SQL
  - bind variables
    - object types [4.3](plsql.md)
  - object views [6.3](object-views-used-in-applications.md)
  - using with objects [1.3.1.3](key-features-object-relational-model.md)
- polymorphism [1.3.1.11](key-features-object-relational-model.md), [2.3.11](inheritance-in-sql-object-types.md), [9.13.2](design-consideration-tips-and-techniques.md), [9.13.3](design-consideration-tips-and-techniques.md)
  - See also: substitutability
- POWERMULTISET_BY_CARDINALITY function [5.3.5.7](operations-on-collection-data-types.md)
- POWERMULTISET function [5.3.5.6](operations-on-collection-data-types.md)
- primary-key-based REFs [8.1.6](storage-of-objects.md)
- privileges
  - acquired by role on object types [7.1.1](privileges-on-object-types-and-their-methods.md)
  - ALTER ANY TYPE on object types [7.1.1](privileges-on-object-types-and-their-methods.md)
  - checked when pinning object types [7.1.5](privileges-on-object-types-and-their-methods.md)
  - column level for object tables [7.1.5](privileges-on-object-types-and-their-methods.md)
  - DELETE on object types [7.1.5](privileges-on-object-types-and-their-methods.md)
  - DROP ANY TYPE on object types [7.1.1](privileges-on-object-types-and-their-methods.md)
  - EXECUTE ANY TYPE on object types [7.1.1](privileges-on-object-types-and-their-methods.md), [7.1.3](privileges-on-object-types-and-their-methods.md)
  - EXECUTE ANY TYPE on object types with ADMIN OPTION [7.1.3](privileges-on-object-types-and-their-methods.md)
  - EXECUTE on object types [7.1.3](privileges-on-object-types-and-their-methods.md)
  - INSERT on object types [7.1.5](privileges-on-object-types-and-their-methods.md)
  - object types in types or tables [7.1.3](privileges-on-object-types-and-their-methods.md)
  - object types with CREATE TYPE [7.1.1](privileges-on-object-types-and-their-methods.md)
  - object types with INSERT [7.1.5](privileges-on-object-types-and-their-methods.md)
  - on object types [7.1](privileges-on-object-types-and-their-methods.md), [7.1.1](privileges-on-object-types-and-their-methods.md)
  - SELECT on object types [7.1.5](privileges-on-object-types-and-their-methods.md)
  - system on object types [7.1.1](privileges-on-object-types-and-their-methods.md)
  - UNDER ANY TYPE on object types [7.1.1](privileges-on-object-types-and-their-methods.md)
  - UNDER ANY VIEW on object types [7.1.1](privileges-on-object-types-and-their-methods.md)
  - UPDATE on object types [7.1.5](privileges-on-object-types-and-their-methods.md)
- Pro\*C
  - embedded SQL with user-defined data types [4.5.1](pro-c-cpp.md)
  - object cache [4.5.1](pro-c-cpp.md)
- Pro\*C/C++
  - associative access [4.5.2](pro-c-cpp.md)
  - converting between Oracle and C types [4.5.4](pro-c-cpp.md)
  - navigational access [4.5.3](pro-c-cpp.md)
  - user-defined data types [4.4](oracle-call-interface-oci.md)
- programmatic environments
  - for Oracle objects [4](object-support-in-oracle-programming-environments.md), [4.7](java-tools-for-accessing-oracle-objects.md)

------------------------------------------------------------------------

## Q

- queries
  - set membership [9.4.4.4](design-considerations-for-collections.md)
  - unnesting [9.4.1](design-considerations-for-collections.md)
  - varrays [9.4.3](design-considerations-for-collections.md)

------------------------------------------------------------------------

## R

- recompilation
  - object types [7.2.3](type-dependencies.md)
- redefining
  - methods [2.3.9.2](inheritance-in-sql-object-types.md)
- REF attributes [2.1.7](Sql-object-types-and-references.md)
- REF columns [2.1.7](Sql-object-types-and-references.md)
- references [1.3.1.6](key-features-object-relational-model.md)
- references See REFs [1.3.1.6](key-features-object-relational-model.md)
- REF function [2.4.5](functions-and-operators-useful-with-objects.md)
  - manipulating objects in PL/SQL [3.2.5](object-manipulation-in-plsql.md)
- REFs [1.3.1.6](key-features-object-relational-model.md)
  - comparing [1.3.1.9](key-features-object-relational-model.md)
  - constraints on [2.1.7](Sql-object-types-and-references.md), [9.3.2](design-considerations-for-REFs.md)
  - constructing from object identifiers [8.1.2](storage-of-objects.md)
  - dangling [1.3.1.6.2](key-features-object-relational-model.md), [1.3.1.7](key-features-object-relational-model.md), [2.1.7](Sql-object-types-and-references.md)
  - dereferencing [3.2.5](object-manipulation-in-plsql.md)
  - dereferencing of [1.3.1.7](key-features-object-relational-model.md)
  - implicit dereferencing of [1.3.1.7](key-features-object-relational-model.md)
  - indexes on [2.1.5](Sql-object-types-and-references.md)
  - indexing [9.3.3.1](design-considerations-for-REFs.md)
  - obtaining [1.3.1.8](key-features-object-relational-model.md)
  - pinning [6.3](object-views-used-in-applications.md), [7.1.5](privileges-on-object-types-and-their-methods.md)
  - scoped [1.3.1.6.1](key-features-object-relational-model.md), [2.1.7](Sql-object-types-and-references.md), [8.1.6](storage-of-objects.md), [9.3.3](design-considerations-for-REFs.md)
  - size of [8.1.6](storage-of-objects.md)
  - storage [9.3.1](design-considerations-for-REFs.md)
  - substitutability [2.3.12.4](inheritance-in-sql-object-types.md)
  - substitutability in [2.3.11](inheritance-in-sql-object-types.md)
  - use of table aliases [2.1.8.1](Sql-object-types-and-references.md)
  - WITH ROWID option [9.3.4](design-considerations-for-REFs.md)
- remote databases
  - using with object types [2.1.9](Sql-object-types-and-references.md)
- RESOURCE role
  - user-defined types [7.1.1](privileges-on-object-types-and-their-methods.md)
- return entire result sets
  - BULK COLLECT [5.3.3](operations-on-collection-data-types.md)
- roles
  - DBA role [7.1.1](privileges-on-object-types-and-their-methods.md)
  - RESOURCE role [7.1.1](privileges-on-object-types-and-their-methods.md)
- row objects
  - storage [9.1.1.2](general-storage-considerations-for-objects.md)

------------------------------------------------------------------------

## S

- sample schemas, hr schema
- schemas
  - object data types [4.3](plsql.md)
  - object types [1.3.1.1](key-features-object-relational-model.md)
  - qualifying column names [2.1.8.1](Sql-object-types-and-references.md)
- scoped REFs [1.3.1.6.1](key-features-object-relational-model.md), [8.1.6](storage-of-objects.md)
- See also dereferencing [2.4.3](functions-and-operators-useful-with-objects.md), [3.2.5](object-manipulation-in-plsql.md)
- SELECT privilege
  - for object tables [7.1.5](privileges-on-object-types-and-their-methods.md)
- SELF parameter
  - methods [2.2.2.1](object-methods.md)
- SET function [5.3.5.8](operations-on-collection-data-types.md)
- single inheritance [2.3](inheritance-in-sql-object-types.md)
- SQL
  - support for object types [4.1](sql-and-object-types.md)
  - user-defined data types [4.1](sql-and-object-types.md)
    - OCI [4.4.1](oracle-call-interface-oci.md)
- SQLJ
  - See: Oracle SQL
- SQLJ object types [4.7](java-tools-for-accessing-oracle-objects.md), [4.7.3](java-tools-for-accessing-oracle-objects.md), [9.13.4.1](design-consideration-tips-and-techniques.md)
  - See also: object types, Oracle SQLJ

  <!-- -->

  - creating [4.7.3.1](java-tools-for-accessing-oracle-objects.md)
  - mapping Java classes [4.7.3.2](java-tools-for-accessing-oracle-objects.md)
- static dispatch [2.3.5.3](inheritance-in-sql-object-types.md)
- static methods [1.3.1.3](key-features-object-relational-model.md), [2.2.3](object-methods.md)
- storage [9.1.2](general-storage-considerations-for-objects.md)
  - column objects [9.1.1.1](general-storage-considerations-for-objects.md)
  - nested tables [8.1.7](storage-of-objects.md)
  - object tables [8.1](storage-of-objects.md)
  - REFs [8.1.6](storage-of-objects.md)
- storing nested tables [5.1.7.2](collection-data-types.md)
- Storing XMLTypes and LOBs in an ANYDATA column [8.4](storing-XMLTypes-and-LOBs-in-an-ANYDATA-column.md)
- SUBMULTISET condition [5.3.4.3](operations-on-collection-data-types.md)
- subprograms
  - overloading and inheritance [3.3](use-of-overloading-in-plsql-with-inheritance.md)
  - roles with invoker’s rights [9.7](roles-with-invokers-rights-subprograms.md)
- substitutability [2.3.11](inheritance-in-sql-object-types.md)
  - attributes [2.3.11](inheritance-in-sql-object-types.md)
  - collections [2.3.11](inheritance-in-sql-object-types.md)
  - column and row [2.3.12](inheritance-in-sql-object-types.md), [8.2.1](creating-indexes-on-typeids-or-attributes.md)
  - constraining [2.3.16](inheritance-in-sql-object-types.md)
  - dependencies [7.2.6](type-dependencies.md)
  - modifying [2.3.17](inheritance-in-sql-object-types.md)
  - narrowing [2.3.19.3](inheritance-in-sql-object-types.md)
  - OBJECT_ID [2.3.12.2](inheritance-in-sql-object-types.md)
  - OBJECT_VALUE [2.3.12.2](inheritance-in-sql-object-types.md)
  - restrictions on modifying [2.3.18](inheritance-in-sql-object-types.md)
  - turning off [2.3.15](inheritance-in-sql-object-types.md)
  - views [2.3.12](inheritance-in-sql-object-types.md)
  - views and [9.13.3](design-consideration-tips-and-techniques.md)
  - widening [2.3.19.1](inheritance-in-sql-object-types.md)
    - assignment widening [2.3.19.2](inheritance-in-sql-object-types.md)
- substitutability of object types
  - with overloading [3.3](use-of-overloading-in-plsql-with-inheritance.md)
- substitutable columns
  - dropping subtypes [2.3.14](inheritance-in-sql-object-types.md)
- subtypes
  - creating [2.3.5](inheritance-in-sql-object-types.md)
  - dropping in substitutable columns [2.3.14](inheritance-in-sql-object-types.md)
  - hierarchy [2.3](inheritance-in-sql-object-types.md)
  - indexing attributes of [8.2.2](creating-indexes-on-typeids-or-attributes.md)
  - multiple [2.3.5.6](inheritance-in-sql-object-types.md)
  - object types [2.3.2](inheritance-in-sql-object-types.md)
  - specializing [9.13.1](design-consideration-tips-and-techniques.md)
  - with supertype attribute [2.3.12.3](inheritance-in-sql-object-types.md)
- supertypes
  - attribute of subtype [2.3.12.3](inheritance-in-sql-object-types.md)
  - base in hierarchy [2.3](inheritance-in-sql-object-types.md)
- synonyms
  - object types [7.3](synonyms-for-object-types.md)
- SYS_TYPEID function [2.4.6](functions-and-operators-useful-with-objects.md), [8.2.1](creating-indexes-on-typeids-or-attributes.md)
- system privileges [7.1.1](privileges-on-object-types-and-their-methods.md)
  - See also: privileges

  <!-- -->

  - ADMIN OPTION [7.1.3](privileges-on-object-types-and-their-methods.md)
  - object types [7.1.1](privileges-on-object-types-and-their-methods.md)

------------------------------------------------------------------------

## T

- TABLE
  - function [2.4.7](functions-and-operators-useful-with-objects.md)
- Table Dependencies [7.2.4](type-dependencies.md)
- TABLE expression [5.1.7](collection-data-types.md), [5.3.1.3](operations-on-collection-data-types.md)
- TABLE expressions [5.3.1.2](operations-on-collection-data-types.md), [9.4.1](design-considerations-for-collections.md)
- TABLE expression subqueries
  - restrictions [5.3.1.2](operations-on-collection-data-types.md)
- tables
  - aliases [2.1.8.1](Sql-object-types-and-references.md)
  - constraints on object tables [2.1.3](Sql-object-types-and-references.md)
  - functions [2.4.7](functions-and-operators-useful-with-objects.md)
  - indexes on nested tables [2.1.5](Sql-object-types-and-references.md)
  - nested tables [5.1.7](collection-data-types.md)
  - object tables [1.3.1.4](key-features-object-relational-model.md)
    - virtual [6.1](why-use-object-views.md)
  - qualifying column names [2.1.8](Sql-object-types-and-references.md), [2.1.8.1](Sql-object-types-and-references.md)
- transient data type [8.6](transient-and-generic-types.md)
- TREAT function [2.3.12](inheritance-in-sql-object-types.md), [2.3.19.3](inheritance-in-sql-object-types.md), [2.4.4](functions-and-operators-useful-with-objects.md), [2.4.8](functions-and-operators-useful-with-objects.md), [8.2.2](creating-indexes-on-typeids-or-attributes.md)
- triggers
  - INSTEAD OF triggers
    - object views and [6.11](object-view-manipulations.md)
  - object types [2.1.6](Sql-object-types-and-references.md)
- type dependencies [7.2.6](type-dependencies.md)
- Type Dependencies [7.2.4](type-dependencies.md)
- type evolution [1.3.1.13](key-features-object-relational-model.md)
  - See: object types
- type hierarchies [1.3.1.12](key-features-object-relational-model.md), [2.3](inheritance-in-sql-object-types.md)
  - methods in [2.2.2.2.6](object-methods.md)
- typeids [2.4.6](functions-and-operators-useful-with-objects.md), [8.2.1](creating-indexes-on-typeids-or-attributes.md)
- type inheritance
  - See: inheritance

  <!-- -->

  - finality [2.3.3](inheritance-in-sql-object-types.md)
  - instantiability [2.3.6](inheritance-in-sql-object-types.md)
  - methods [2.3.9](inheritance-in-sql-object-types.md)
  - object types [2.3](inheritance-in-sql-object-types.md)
  - specializing subtypes [2.3.2](inheritance-in-sql-object-types.md)
- types
  - See: data types, object types

------------------------------------------------------------------------

## U

- UNDER ANY TYPE privilege [7.1.1](privileges-on-object-types-and-their-methods.md)
  - See also: privileges
- UNDER ANY VIEW privilege [7.1.1](privileges-on-object-types-and-their-methods.md)
  - See also: privileges
- UNDER keyword
  - CREATE TYPE [2.3.5](inheritance-in-sql-object-types.md)
- uninitialized object
  - how treated in PL/SQL [3.1.3](declaring-initializing-objects-in-plsql.md)
- unnesting queries [9.4.1](design-considerations-for-collections.md)
- unnesting queries to collections [5.3.1.3](operations-on-collection-data-types.md)
- unnesting queries with multilevel collections [5.3.1.5](operations-on-collection-data-types.md)
- UPDATE privilege
  - for object tables [7.1.5](privileges-on-object-types-and-their-methods.md)
- updates
  - object views [6.11](object-view-manipulations.md)
- UPGRADE..STORE AS [8.3.6](type-evolution.md)
- user-defined aggregate functions [8.7](user-defined-aggregate-functions.md)
- user-defined constructors [8.5.3](system-defined-and-user-defined-constructors.md), [8.5.4](system-defined-and-user-defined-constructors.md)
- user-defined data types [1.1](about-oracle-objects.md)
  - See: object types
- user-defined types
  - and remote databases [2.1.9](Sql-object-types-and-references.md)
- utilities supporting objects [4.9](utilities-providing-support-for-objects.md)

------------------------------------------------------------------------

## V

- validation
  - object types [8.3.7](type-evolution.md)
- VALUE function [2.4.9](functions-and-operators-useful-with-objects.md), [3.2.2](object-manipulation-in-plsql.md)
- variables
  - bind variables
    - object types [4.3](plsql.md)
  - object variables [6.3](object-views-used-in-applications.md)
- varrays [5.1.5](collection-data-types.md)
  - accessing [9.4.3](design-considerations-for-collections.md)
  - creating [5.1.2](collection-data-types.md)
  - creating VARRAYs [5.1.10](collection-data-types.md)
  - increasing the number of elements [5.1.9](collection-data-types.md)
  - querying [9.4.3](design-considerations-for-collections.md)
  - storage [5.2.2](multilevel-collection-types.md), [9.4.2](design-considerations-for-collections.md)
  - updating [9.4.3](design-considerations-for-collections.md)
- views [6.11](object-view-manipulations.md)
  - See also: object views

  <!-- -->

  - object [1.3.1.11](key-features-object-relational-model.md)
  - substitutability [2.3.12](inheritance-in-sql-object-types.md)
  - updatability [6.11](object-view-manipulations.md)

------------------------------------------------------------------------

## W

- widening
  - and substitutability [2.3.19.1](inheritance-in-sql-object-types.md), [2.3.19.2](inheritance-in-sql-object-types.md)

------------------------------------------------------------------------

## X

- XML [4.8](xml.md)
- XMLType [5.1.5](collection-data-types.md)
- XMLTypes and LOBs in an ANYDATA column [8.4](storing-XMLTypes-and-LOBs-in-an-ANYDATA-column.md)
- XMLType views [4.8](xml.md)
