Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Package](../parsers/package-summary.md)**
- **[Next Package](dom/package-summary.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

# **Package javax.xml.transform**

**This package defines the generic APIs for processing XML transformation, and performing a transformation from a source to a result.**

**See: Description**

- **Interface Summary**

  | Interface                         | Description                                                                                                                                                           |
  |-----------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [ErrorListener](ErrorListener.md) | To provide customized error handling, implement this interface and use the setErrorListener method to register an instance of the implmentation with the Transformer. |
  | [Result](Result.md)               | An object that implements this interface contains the information needed to build a transformation result tree.                                                       |
  | [Source](Source.md)               | An object that implements this interface contains the information needed to act as source input (XML source or transformation instructions).                          |
  | [SourceLocator](SourceLocator.md) | This interface is primarily for the purposes of reporting where an error occurred in the XML source or transformation instructions.                                   |
  | [Templates](Templates.md)         | An object that implements this interface is the runtime representation of processed transformation instructions.                                                      |
  | [URIResolver](URIResolver.md)     | An object that implements this interface that can be called by the processor to turn a URI used in document(), xsl:import, or xsl:include into a Source object.       |

- **Class Summary**

  | Class                                       | Description                                                                                                                                                     |
  |---------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [OutputKeys](OutputKeys.md)                 | Provides string constants that can be used to set output properties for a Transformer, or to retrieve output properties from a Transformer or Templates object. |
  | [Transformer](Transformer.md)               | An instace of this abstract class can transform a source tree into a result tree.                                                                               |
  | [TransformerFactory](TransformerFactory.md) | A TransformerFactory instance can be used to create Transformer and Template objects.                                                                           |

- **Exception Summary**

  | Exception                                                                 | Description                                                                                   |
  |---------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
  | [TransformerConfigurationException](TransformerConfigurationException.md) | Indicates a serious configuration error.                                                      |
  | [TransformerException](TransformerException.md)                           | This class specifies an exceptional condition that occured during the transformation process. |

- **Error Summary**

  | Error                                                                           | Description                                                                     |
  |---------------------------------------------------------------------------------|---------------------------------------------------------------------------------|
  | [TransformerFactoryConfigurationError](TransformerFactoryConfigurationError.md) | Thrown when a problem with configuration with the Transformer Factories exists. |

## **Package javax.xml.transform Description**

**This package defines the generic APIs for processing XML transformation, and performing a transformation from a source to a result.
**

**Skip navigation links**

- **[Overview](../../../overview-summary.md)**
- **Package**
- **Class**
- **[Tree](package-tree.md)**
- **[Deprecated](../../../deprecated-list.md)**
- **[Index](../../../index-all.md)**
- **[Help](../../../help-doc.md)**

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Package](../parsers/package-summary.md)**
- **[Next Package](dom/package-summary.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
