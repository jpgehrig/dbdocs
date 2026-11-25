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

- [Prev Class](NetworkAnalysisConfig.md)
- Next Class

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

## Class NetworkIOConfig

- java.lang.Object

- - oracle.spatial.network.lod.config.NetworkIOConfig

<!-- -->

-

  ------------------------------------------------------------------------



      public class NetworkIOConfig
      extends java.lang.Object

  Configuration for network IO.
  Since:
  12.1

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                      |
    |--------------------------------------------------|
    | `NetworkIOConfig``()`                            |
    | `NetworkIOConfig``(org.w3c.dom.Element ioElem)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type       | Method and Description                                                                                                       |
    |-------------------------|------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`      | `clone``()`                                                                                                                  |
    | `int`                   | `getBatchSize``()`                                                                                                           |
    | `org.w3c.dom.Element[]` | `getCachingPolicies``()`                                                                                                     |
    | `double`                | `getGeometryTolerance``()`                                                                                                   |
    | `org.w3c.dom.Element`   | `getNetworkIOElement``()`<br>Returns the networkIO element that was used initially to construct this NetworkIOConfig object. |
    | `org.w3c.dom.Element`   | `getPartitionBlobTranslator``()`                                                                                             |
    | `org.w3c.dom.Element[]` | `getUserDataIOs``()`                                                                                                         |
    | `boolean`               | `isReadFromBlob``()`                                                                                                         |
    | `void`                  | `setBatchSize``(int batchSize)`                                                                                              |
    | `void`                  | `setCachingPolicies``(org.w3c.dom.Element[] cachingPolicies)`                                                                |
    | `void`                  | `setCachingPolicies``(java.lang.String cachingPoliciesXml)`                                                                  |
    | `void`                  | `setGeometryTolerance``(double tolerance)`                                                                                   |
    | `void`                  | `setPartitionBlobTranslator``(org.w3c.dom.Element partitionBlobTranslator)`                                                  |
    | `void`                  | `setPartitionBlobTranslator``(java.lang.String partitionBlobTranslatorXmlElement)`                                           |
    | `void`                  | `setReadFromBlob``(boolean readFromBlob)`                                                                                    |
    | `void`                  | `setUserDataIOs``(org.w3c.dom.Element[] userDataIOs)`                                                                        |
    | `void`                  | `setUserDataIOs``(java.lang.String userDataIOsXml)`                                                                          |
    | `void`                  | `updateNetworkIOElement``()`<br>Update the networkIO element to reflect the current status of this object.                   |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NetworkIOConfig

          public NetworkIOConfig()

    <!-- -->

    - #### NetworkIOConfig

          public NetworkIOConfig(org.w3c.dom.Element ioElem)
                          throws LODConfigException

      Throws:
      [`LODConfigException`](LODConfigException.md)

  <!-- -->

  - ### Method Detail

    - #### setBatchSize

          public void setBatchSize(int batchSize)

    <!-- -->

    - #### getBatchSize

          public int getBatchSize()

    <!-- -->

    - #### setGeometryTolerance

          public void setGeometryTolerance(double tolerance)

    <!-- -->

    - #### getGeometryTolerance

          public double getGeometryTolerance()

    <!-- -->

    - #### setReadFromBlob

          public void setReadFromBlob(boolean readFromBlob)

    <!-- -->

    - #### isReadFromBlob

          public boolean isReadFromBlob()

    <!-- -->

    - #### setPartitionBlobTranslator

          public void setPartitionBlobTranslator(java.lang.String partitionBlobTranslatorXmlElement)

    <!-- -->

    - #### setPartitionBlobTranslator

          public void setPartitionBlobTranslator(org.w3c.dom.Element partitionBlobTranslator)

    <!-- -->

    - #### getPartitionBlobTranslator

          public org.w3c.dom.Element getPartitionBlobTranslator()

    <!-- -->

    - #### setCachingPolicies

          public void setCachingPolicies(java.lang.String cachingPoliciesXml)

    <!-- -->

    - #### setCachingPolicies

          public void setCachingPolicies(org.w3c.dom.Element[] cachingPolicies)

    <!-- -->

    - #### getCachingPolicies

          public org.w3c.dom.Element[] getCachingPolicies()

    <!-- -->

    - #### setUserDataIOs

          public void setUserDataIOs(java.lang.String userDataIOsXml)

    <!-- -->

    - #### setUserDataIOs

          public void setUserDataIOs(org.w3c.dom.Element[] userDataIOs)

    <!-- -->

    - #### getUserDataIOs

          public org.w3c.dom.Element[] getUserDataIOs()

    <!-- -->

    - #### getNetworkIOElement

          public org.w3c.dom.Element getNetworkIOElement()

      Returns the networkIO element that was used initially to construct this NetworkIOConfig object. The returned element may not reflect the current state of this NetworkIOConfig object, because the properties of the current object could have been changed programmatically after it was initialized.
      Returns:

    <!-- -->

    - #### updateNetworkIOElement

          public void updateNetworkIOElement()

      Update the networkIO element to reflect the current status of this object.

    <!-- -->

    - #### clone

          public java.lang.Object clone()

      Overrides:
      `clone` in class `java.lang.Object`

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

- [Prev Class](NetworkAnalysisConfig.md)
- Next Class

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
