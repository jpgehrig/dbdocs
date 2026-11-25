Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Package](../data/source/package-summary.md)
- [Next Package](deployment/package-summary.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

# Package oracle.olapi.metadata

Contains interfaces and classes that represent Oracle OLAP metadata objects and that provide those objects to an application.

See: Description

- **Interface Summary**

  | Interface                                           | Description                                                                                                                                                                                                                           |
  |-----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [MetadataObject](MetadataObject.md)                 | An interface that is implemented by most of the Oracle OLAP metadata objects.                                                                                                                                                         |
  | [MetadataProvider](MetadataProvider.md)             | An interface for an object that provides access to OLAP metadata objects.                                                                                                                                                             |
  | [XML11_2_ParserCallback](XML11_2_ParserCallback.md) | An extension of the `XMLParserCallback` interface that adds methods for renaming an object and for suppressing attributes of objects.                                                                                                 |
  | [XMLParserCallback](XMLParserCallback.md)           | An interface for an object that processes errors that occur as an `MdmMetadataProvider.importXML` method produces a metadata object from an XML object definition or as a `SyntaxObject.fromSyntax` method produces a `SyntaxObject`. |
  | [XMLWriterCallback](XMLWriterCallback.md)           | An interface for an object that Oracle OLAP calls to find out whether or not to exclude an attribute or an owner name from the XML that an `MdmMetadataProvider` is exporting.                                                        |

- **Class Summary**

  | Class                                                     | Description                                                                      |
  |-----------------------------------------------------------|----------------------------------------------------------------------------------|
  | [BaseMetadataObject](BaseMetadataObject.md)               | The abstract base class for Oracle OLAP metadata objects.                        |
  | [BaseMetadataProvider](BaseMetadataProvider.md)           | The base class for an object that gives access to the metadata for a data store. |
  | [InvalidMetadataObjectInfo](InvalidMetadataObjectInfo.md) | Contains information about an invalid metadata object.                           |
  | [PublicMetadataObject](PublicMetadataObject.md)           | A `BaseMetadataObject` that you can export to XML.                               |

- **Exception Summary**

  | Exception                                                                     | Description                                                                                                                                                                       |
  |-------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [DuplicateMetadataIDException](DuplicateMetadataIDException.md)               | Indicates that a `BaseMetadataObject` with the specified identification already exists.                                                                                           |
  | [InvalidMetadataException](InvalidMetadataException.md)                       | Indicates that one or more metadata objects are invalid.                                                                                                                          |
  | [MetadataFactoryException](MetadataFactoryException.md)                       | Indicates that Oracle OLAP cannot perform the requested metadata factory operation; usually, this exception occurs because the specified parameters for the method are not valid. |
  | [MetadataModificationException](MetadataModificationException.md)             | Indicates that an error occurred when Oracle OLAP attempted to change some metadata property.                                                                                     |
  | [MetadataRenameNotSupportedException](MetadataRenameNotSupportedException.md) | Indicates that Oracle OLAP does not support the renaming of existing metadata objects in the version of Oracle Database to which the application is connected.                    |
  | [MetadataUpdateNotSupportedException](MetadataUpdateNotSupportedException.md) | Indicates that Oracle OLAP does not support the updating of metadata in the version of Oracle Database to which the application is connected.                                     |

## Package oracle.olapi.metadata Description

Contains interfaces and classes that represent Oracle OLAP metadata objects and that provide those objects to an application.

Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Package](../data/source/package-summary.md)
- [Next Package](deployment/package-summary.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)
