Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Tree
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev](../cursor/package-tree.md)
-

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

# Hierarchy For Package oracle.olapi.data.source

Package Hierarchies:

- [All Packages](../../../../overview-tree.md)

## Class Hierarchy

- java.lang.Object
  - oracle.olapi.data.source.[Assignment](Assignment.md)
  - oracle.olapi.data.source.[BuildProperties](BuildProperties.md)
  - oracle.olapi.data.source.[BuildResult](BuildResult.md)
  - oracle.olapi.data.source.[CursorSpecification](CursorSpecification.md) (implements oracle.olapi.data.source.[CursorInfoSpecification](CursorInfoSpecification.md))
    - oracle.olapi.data.source.[CompoundCursorSpecification](CompoundCursorSpecification.md) (implements oracle.olapi.data.source.[CompoundCursorInfoSpecification](CompoundCursorInfoSpecification.md))
    - oracle.olapi.data.source.[ValueCursorSpecification](ValueCursorSpecification.md) (implements oracle.olapi.data.source.[ValueCursorInfoSpecification](ValueCursorInfoSpecification.md))
  - oracle.olapi.data.source.[CursorSpecificationVisitor](CursorSpecificationVisitor.md)
  - oracle.olapi.data.source.[CustomModel](CustomModel.md) (implements oracle.olapi.data.source.[Model](Model.md))
  - oracle.olapi.data.source.[DataProvider](DataProvider.md)
  - oracle.olapi.data.source.[FundamentalMetadataObject](FundamentalMetadataObject.md) (implements oracle.olapi.metadata.[MetadataObject](../../metadata/MetadataObject.md))
  - oracle.olapi.data.source.[FundamentalMetadataProvider](FundamentalMetadataProvider.md) (implements oracle.olapi.metadata.[MetadataProvider](../../metadata/MetadataProvider.md))
  - oracle.olapi.data.source.[Parameter](Parameter.md)
    - oracle.olapi.data.source.[BooleanParameter](BooleanParameter.md)
    - oracle.olapi.data.source.[DateParameter](DateParameter.md)
    - oracle.olapi.data.source.[NumberParameter](NumberParameter.md)
    - oracle.olapi.data.source.[StringParameter](StringParameter.md)
  - oracle.olapi.data.source.[ParameterVisitor](ParameterVisitor.md)
  - oracle.olapi.data.source.[Qualification](Qualification.md)
    - oracle.olapi.data.source.[LiteralQualification](LiteralQualification.md)
  - oracle.olapi.data.source.[Source](Source.md) (implements oracle.olapi.data.cursor.[SourceIdentifier](../cursor/SourceIdentifier.md))
    - oracle.olapi.data.source.[BooleanSource](BooleanSource.md)
    - oracle.olapi.data.source.[DateSource](DateSource.md)
    - oracle.olapi.data.source.[NumberSource](NumberSource.md)
    - oracle.olapi.data.source.[StringSource](StringSource.md)
  - oracle.olapi.data.source.[SourceDefinition](SourceDefinition.md)
    - oracle.olapi.data.source.[DynamicDefinition](DynamicDefinition.md)
  - oracle.olapi.data.source.[Template](Template.md)
  - java.lang.Throwable (implements java.io.Serializable)
    - java.lang.Exception
      - java.lang.RuntimeException
        - oracle.olapi.[OLAPIRuntimeException](../../OLAPIRuntimeException.md) (implements oracle.olapi.[HasLocalizedMessage](../../HasLocalizedMessage.md))
          - oracle.olapi.data.source.[BuildWarningsException](BuildWarningsException.md)
          - oracle.olapi.data.source.[CursorLockException](CursorLockException.md)
          - oracle.olapi.data.source.[DataProviderMismatchException](DataProviderMismatchException.md)
          - oracle.olapi.data.source.[IncorrectDataValueException](IncorrectDataValueException.md)
          - oracle.olapi.data.source.[ServerVersionException](ServerVersionException.md)
          - oracle.olapi.data.source.[UnmatchedInputsException](UnmatchedInputsException.md)

## Interface Hierarchy

- oracle.olapi.data.source.[CursorInfoSpecification](CursorInfoSpecification.md)
  - oracle.olapi.data.source.[CompoundCursorInfoSpecification](CompoundCursorInfoSpecification.md)
  - oracle.olapi.data.source.[ValueCursorInfoSpecification](ValueCursorInfoSpecification.md)
- oracle.olapi.data.cursor.[CursorManager](../cursor/CursorManager.md)
  - oracle.olapi.data.source.[SpecifiedCursorManager](SpecifiedCursorManager.md)
- oracle.olapi.data.source.[Model](Model.md)
- oracle.olapi.data.source.[SourceGenerator](SourceGenerator.md)
- oracle.olapi.data.source.[SQLCursorManager](SQLCursorManager.md)

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Tree
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev](../cursor/package-tree.md)
-

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)
