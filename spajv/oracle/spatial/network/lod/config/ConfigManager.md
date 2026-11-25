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

- [Prev Class](CachingPolicy.md)
- [Next Class](EngineConfig.md)

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

## Class ConfigManager

- java.lang.Object

- - oracle.spatial.network.lod.config.ConfigManager

<!-- -->

-

  ------------------------------------------------------------------------



      public class ConfigManager
      extends java.lang.Object

  This singleton class manages LOD configurations.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description |
    |---------------------------|-----------------------|
    | `static java.lang.String` | `VERSION_11`          |
    | `static java.lang.String` | `VERSION_12_1`        |
    | `static java.lang.String` | `VERSION_12_2`        |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                 | Method and Description                                                                                                                                                    |
    |-----------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`LODConfig`](LODConfig.md)       | `getConfig``(java.lang.String networkName)`<br>Returns the LOD Configuration information for the specified network.                                                       |
    | `static ConfigManager`            | `getConfigManager``()`<br>Returns the singleton of `ConfigManager`.                                                                                                       |
    | [`EngineConfig`](EngineConfig.md) | `getEngineConfig``()`                                                                                                                                                     |
    | `void`                            | `loadConfig``(org.w3c.dom.Element root)`                                                                                                                                  |
    | `void`                            | `loadConfig``(java.io.InputStream configXml)`<br>Loads LOD configuration xml.                                                                                             |
    | `void`                            | `setConfig``(java.lang.String networkName, `[`LODConfig`](LODConfig.md)` config)`                                                                                         |
    | `static void`                     | `validateConfigXml``(javax.xml.transform.Source configXmlSource, java.lang.String version)`<br>Validate the input configuration xml against the LOD configuration schema. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### VERSION_11

          public static final java.lang.String VERSION_11

      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### VERSION_12_1

          public static final java.lang.String VERSION_12_1

      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### VERSION_12_2

          public static final java.lang.String VERSION_12_2

      See Also:
      [Constant Field Values](../../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getConfigManager

          public static ConfigManager getConfigManager()

      Returns the singleton of `ConfigManager`.
      Returns:
      the singleton of `ConfigManager`

    <!-- -->

    - #### loadConfig

          public void loadConfig(java.io.InputStream configXml)
                          throws LODConfigException

      Loads LOD configuration xml.
      Parameters:
      `configXml` - configuration xml in byte stream

      Throws:
      [`LODConfigException`](LODConfigException.md)

    <!-- -->

    - #### loadConfig

          public void loadConfig(org.w3c.dom.Element root)
                          throws LODConfigException

      Throws:
      [`LODConfigException`](LODConfigException.md)

    <!-- -->

    - #### validateConfigXml

          public static void validateConfigXml(javax.xml.transform.Source configXmlSource,
                                               java.lang.String version)
                                        throws org.xml.sax.SAXException,
                                               java.io.IOException

      Validate the input configuration xml against the LOD configuration schema.
      Parameters:
      `configXmlSource` - configuration xml

      `version` - xml version. "11" for version 11, "12.1" for version 12.1.

      Throws:
      `org.xml.sax.SAXException`

      `java.io.IOException`

    <!-- -->

    - #### getEngineConfig

          public EngineConfig getEngineConfig()

    <!-- -->

    - #### getConfig

          public LODConfig getConfig(java.lang.String networkName)

      Returns the LOD Configuration information for the specified network.
      Parameters:
      `networkName` - name of the network

      Returns:
      LOD configuration information

    <!-- -->

    - #### setConfig

          public void setConfig(java.lang.String networkName,
                                LODConfig config)

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

- [Prev Class](CachingPolicy.md)
- [Next Class](EngineConfig.md)

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
