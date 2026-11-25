Skip navigation links

- [Overview](../../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Package](../cursor/package-summary.md)
- [Next Package](../../metadata/package-summary.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

# Package oracle.olapi.data.source

Contains classes that construct a query of the data in an Oracle Database.

See: Description

- **Interface Summary**

  | Interface                                                             | Description                                                                                                                                                                                                 |
  |-----------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [CompoundCursorInfoSpecification](CompoundCursorInfoSpecification.md) | A `CursorInfoSpecification` for a `Cursor` for a `Source` that has one or more outputs.                                                                                                                     |
  | [CursorInfoSpecification](CursorInfoSpecification.md)                 | An interface that specifies characteristics of a `Cursor`.                                                                                                                                                  |
  | [Model](Model.md)                                                     | An interface for an object that represents a set of assignments that apply to a `Source` that has one or more inputs.                                                                                       |
  | [SourceGenerator](SourceGenerator.md)                                 | An interface for an object that produces a `Source` for a `Template`.                                                                                                                                       |
  | [SpecifiedCursorManager](SpecifiedCursorManager.md)                   | A `CursorManager` that specifies methods for determining whether the `SpecifiedCursorManager` is open and for getting and setting the input `Source` objects associated with this `SpecifiedCursorManager`. |
  | [SQLCursorManager](SQLCursorManager.md)                               | An interface for an object that gets the SQL statement that the Oracle OLAP SQL Generator generates for a `Source` that specifies a query.                                                                  |
  | [ValueCursorInfoSpecification](ValueCursorInfoSpecification.md)       | A `CursorInfoSpecification` for a `Cursor` for a `Source` that does not have any outputs.                                                                                                                   |

- **Class Summary**

  | Class                                                         | Description                                                                                                                                                                                      |
  |---------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [Assignment](Assignment.md)                                   | An object that belongs to a `Model` and that represents a calculation, a set of `Source` elements, and a precedence.                                                                             |
  | [BooleanParameter](BooleanParameter.md)                       | A `Parameter` that specifies a `boolean` value that you use in creating a query.                                                                                                                 |
  | [BooleanSource](BooleanSource.md)                             | A `Source` whose elements have `boolean` values.                                                                                                                                                 |
  | [BuildProperties](BuildProperties.md)                         | Contains properties that affect a `BuildProcess`.                                                                                                                                                |
  | [BuildResult](BuildResult.md)                                 | A container for an integer that identifies a build process in the `CUBE_BUILD_LOG` table.                                                                                                        |
  | [CompoundCursorSpecification](CompoundCursorSpecification.md) | A `CursorSpecification` for a `Source` that has one or more outputs.                                                                                                                             |
  | [CursorSpecification](CursorSpecification.md)                 | The base class for an object that specifies characteristics of a `Cursor` for a `Source`.                                                                                                        |
  | [CursorSpecificationVisitor](CursorSpecificationVisitor.md)   | A visitor object that can execute operations on `CursorSpecification` objects.                                                                                                                   |
  | [CustomModel](CustomModel.md)                                 | A `Model` that an application can explicitly create.                                                                                                                                             |
  | [DataProvider](DataProvider.md)                               | Creates user sessions for a connection to Oracle OLAP and creates objects that an application uses in getting metadata objects, in specifying queries, and in retrieving data from a data store. |
  | [DateParameter](DateParameter.md)                             | A `Parameter` that specifies a `Date` value that you use in creating a query.                                                                                                                    |
  | [DateSource](DateSource.md)                                   | A `Source` whose elements have `Date` objects as values.                                                                                                                                         |
  | [DynamicDefinition](DynamicDefinition.md)                     | A proxy for the `SourceDefinition` of the `Source` returned by the `SourceGenerator` for a `Template`.                                                                                           |
  | [FundamentalMetadataObject](FundamentalMetadataObject.md)     | An object that represents a data type, function, or function parameter used by the Oracle OLAP Java API.                                                                                         |
  | [FundamentalMetadataProvider](FundamentalMetadataProvider.md) | Provides `FundamentalMetadataObject` objects that represent OLAP Java API data types.                                                                                                            |
  | [LiteralQualification](LiteralQualification.md)               | A `Qualification` that specifies a literal value, such as an `Integer`, `Boolean`, or `String` literal, that identifies an element of a `Source` for an `Assignment` of a `Model`.               |
  | [NumberParameter](NumberParameter.md)                         | A `Parameter` that specifies a number value that you use in creating a query.                                                                                                                    |
  | [NumberSource](NumberSource.md)                               | A `Source` whose elements have numeric values, which are `double`, `float`, `int`, or `short` values, or some combination of those values.                                                       |
  | [Parameter](Parameter.md)                                     | An object that specifies a value that you use in creating a query.                                                                                                                               |
  | [ParameterVisitor](ParameterVisitor.md)                       | A visitor object that can execute operations on `Parameter` objects.                                                                                                                             |
  | [Qualification](Qualification.md)                             | An object that specifies a `Source` and an element of that `Source` for an `Assignment` of a `Model`.                                                                                            |
  | [Source](Source.md)                                           | The base class of the Oracle OLAP query model.                                                                                                                                                   |
  | [SourceDefinition](SourceDefinition.md)                       | Contains information about the origins of the `Source` with which it is associated.                                                                                                              |
  | [StringParameter](StringParameter.md)                         | A `Parameter` that specifies a `String` value that you use in creating a query.                                                                                                                  |
  | [StringSource](StringSource.md)                               | A `Source` that has elements that have `String` objects as values.                                                                                                                               |
  | [Template](Template.md)                                       | The basis for creating a `Source` that an application can dynamically change.                                                                                                                    |
  | [ValueCursorSpecification](ValueCursorSpecification.md)       | A `CursorSpecification` for the values of a `Source`.                                                                                                                                            |

- **Exception Summary**

  | Exception                                                         | Description                                                                                                                                                                               |
  |-------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [BuildWarningsException](BuildWarningsException.md)               | Indicates that the attempt to build succeeded, but that there are warning messages.                                                                                                       |
  | [CursorLockException](CursorLockException.md)                     | Indicates that the application cannot modify the state of a `Template` at the moment because the state is locked, which can mean that the state is being modified in another transaction. |
  | [DataProviderMismatchException](DataProviderMismatchException.md) | Indicates an attempt to combine `Source` objects associated with different `DataProvider` objects.                                                                                        |
  | [IncorrectDataValueException](IncorrectDataValueException.md)     | Indicates that the data value is incorrect for the attempted operation.                                                                                                                   |
  | [ServerVersionException](ServerVersionException.md)               | Indicates that the version of Oracle OLAP on the server does not match the version specified by the client application.                                                                   |
  | [UnmatchedInputsException](UnmatchedInputsException.md)           | Indicates that an input of a `Source` does not have a matching `Source`.                                                                                                                  |

## Package oracle.olapi.data.source Description

Contains classes that construct a query of the data in an Oracle Database.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Package](../cursor/package-summary.md)
- [Next Package](../../metadata/package-summary.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)
