Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](EngineConfig.md)
- [Next Class](LODConfigException.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.spatial.network.lod.config

## Class LODConfig

- java.lang.Object

- - oracle.spatial.network.lod.config.LODConfig

<!-- -->

-

  ------------------------------------------------------------------------



      public class LODConfig
      extends java.lang.Object

  Load-on-demand configuration, which consists of configuration for network IO and configuration for network analysis.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `LODConfig``()`<br>Default constructor.                                                                                                                                    |
    | `LODConfig``(org.w3c.dom.Element elem)`<br>Constructs an LODConfig object from an XML element.                                                                             |
    | `LODConfig``(org.w3c.dom.Element elem, java.lang.String version)`<br>Constructs an LODConfig object from an XML element.                                                   |
    | `LODConfig``(`[`NetworkIOConfig`](NetworkIOConfig.md)` ioConfig, `[`NetworkAnalysisConfig`](NetworkAnalysisConfig.md)` analysisConfig)`<br>Constructs an LODConfig object. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                   | Method and Description                                                                |
    |-----------------------------------------------------|---------------------------------------------------------------------------------------|
    | `java.lang.Object`                                  | `clone``()`<br>Sets the full class name of the user data input/output implementation. |
    | [`NetworkAnalysisConfig`](NetworkAnalysisConfig.md) | `getNetworkAnalysisConfig``()`                                                        |
    | [`NetworkIOConfig`](NetworkIOConfig.md)             | `getNetworkIOConfig``()`                                                              |
    | `java.lang.String`                                  | `toString``()`                                                                        |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### LODConfig

          public LODConfig()

      Default constructor. Default partition BLOB translator is `oracle.spatial.network.lod.PartitionBlobTranslator11g`. Default user data IO implementation is `oracle.spatial.network.lod.LODUserDataIOSDO`. Default read from blob is set to false.

    <!-- -->

    - #### LODConfig

          public LODConfig(NetworkIOConfig ioConfig,
                           NetworkAnalysisConfig analysisConfig)

      Constructs an LODConfig object.
      Parameters:
      `ioConfig` - configuration for network I/O

      `analysisConfig` - configuration for network analysis

      Throws:
      [`LODConfigException`](LODConfigException.md)

    <!-- -->

    - #### LODConfig

          public LODConfig(org.w3c.dom.Element elem)
                    throws LODConfigException

      Constructs an LODConfig object from an XML element.
      Parameters:
      `elem` - xml element

      Throws:
      [`LODConfigException`](LODConfigException.md)

    <!-- -->

    - #### LODConfig

          public LODConfig(org.w3c.dom.Element elem,
                           java.lang.String version)
                    throws LODConfigException

      Constructs an LODConfig object from an XML element.
      Parameters:
      `elem` - xml element

      Throws:
      [`LODConfigException`](LODConfigException.md)

  <!-- -->

  - ### Method Detail

    - #### getNetworkIOConfig

          public NetworkIOConfig getNetworkIOConfig()

    <!-- -->

    - #### getNetworkAnalysisConfig

          public NetworkAnalysisConfig getNetworkAnalysisConfig()

    <!-- -->

    - #### clone

          public java.lang.Object clone()

      Sets the full class name of the user data input/output implementation.
      Overrides:
      `clone` in class `java.lang.Object`

      Parameters:
      `userDataIO` - full class name of the user data IO implementation public void setUserDataIO(String userDataIO) { this.userDataIO = userDataIO; }

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](EngineConfig.md)
- [Next Class](LODConfigException.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
