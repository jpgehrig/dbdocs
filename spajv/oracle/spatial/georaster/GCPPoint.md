Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](GCPGeoreference.md)
- [Next Class](GeoRasterException.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.spatial.georaster

## Class GCPPoint

- java.lang.Object

- - oracle.spatial.georaster.GCPPoint

<!-- -->

-

  ------------------------------------------------------------------------



      public class GCPPoint
      extends java.lang.Object

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                        |
    |------------------------------------------------------------------------------------------------------------------------------------|
    | `GCPPoint``(int gcpPointType, int cellDimension, int modelDimension)`<br>Constructs a `GCPPoint` object with the given parameters. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type   | Method and Description                                                                                                                                                                                                                                                                                           |
    |---------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`               | `getcellDimension``()`<br>Returns the GCP point cell Dimension.                                                                                                                                                                                                                                                  |
    | `double`            | `getColumn``()`<br>Returns the GCP point column.                                                                                                                                                                                                                                                                 |
    | `java.lang.String`  | `getDescription``()`<br>Returns the GCP point description.                                                                                                                                                                                                                                                       |
    | `int`               | `getGCPPointType``()`<br>Returns the GCP point description.                                                                                                                                                                                                                                                      |
    | `java.lang.String`  | `getID``()`<br>Returns the GCP point ID.                                                                                                                                                                                                                                                                         |
    | `int`               | `getModelDimension``()`<br>Returns the GCP point model Dimension.                                                                                                                                                                                                                                                |
    | `double`            | `getRow``()`<br>Returns the GCP point row.                                                                                                                                                                                                                                                                       |
    | `java.lang.Integer` | `getStatus``()`<br>Returns the GCP point status, the valid value as below: SpatialReferenceInfo.GCPPOINT_STATUS_MEASURED SpatialReferenceInfo.GCPPOINT_STATUS_REMOVED SpatialReferenceInfo.GCPPOINT_STATUS_ESTIMATED SpatialReferenceInfo.GCPPOINT_STATUS_VALIDATED SpatialReferenceInfo.GCPPOINT_STATUS_INVALID |
    | `java.lang.Integer` | `getVertical``()`<br>Returns the GCP point vertical.                                                                                                                                                                                                                                                             |
    | `double`            | `getX``()`<br>Returns the GCP point x.                                                                                                                                                                                                                                                                           |
    | `java.lang.Double`  | `getXRMS``()`<br>Returns the GCP point xRMS.                                                                                                                                                                                                                                                                     |
    | `double`            | `getY``()`<br>Returns the GCP point y.                                                                                                                                                                                                                                                                           |
    | `java.lang.Double`  | `getYRMS``()`<br>Returns the GCP point yRMS.                                                                                                                                                                                                                                                                     |
    | `java.lang.Double`  | `getZ``()`<br>Returns the GCP point z.                                                                                                                                                                                                                                                                           |
    | `java.lang.Double`  | `getZRMS``()`<br>Returns the GCP point zRMS.                                                                                                                                                                                                                                                                     |
    | `void`              | `setCellDimension``(int cellDimension)`<br>Sets the GCP point cell Dimension.                                                                                                                                                                                                                                    |
    | `void`              | `setColumn``(double column)`<br>Sets the GCP point column.                                                                                                                                                                                                                                                       |
    | `void`              | `setDescription``(java.lang.String description)`<br>Sets the GCP point description.                                                                                                                                                                                                                              |
    | `void`              | `setGCPPointType``(int type)`<br>Sets the GCP point type.                                                                                                                                                                                                                                                        |
    | `void`              | `setID``(java.lang.String ID)`<br>Sets the GCP point ID.                                                                                                                                                                                                                                                         |
    | `void`              | `setModelDimension``(int modelDimension)`<br>Sets the GCP point model Dimension.                                                                                                                                                                                                                                 |
    | `void`              | `setRow``(double row)`<br>Sets the GCP point row.                                                                                                                                                                                                                                                                |
    | `void`              | `setStatus``(java.lang.Integer status)`<br>Sets the GCP point status.                                                                                                                                                                                                                                            |
    | `void`              | `setVertical``(java.lang.Integer vertical)`<br>Sets the GCP point vertical.                                                                                                                                                                                                                                      |
    | `void`              | `setX``(double x)`<br>Sets the GCP point x.                                                                                                                                                                                                                                                                      |
    | `void`              | `setXRMS``(java.lang.Double xRMS)`<br>Sets the GCP point xRMS.                                                                                                                                                                                                                                                   |
    | `void`              | `setY``(double y)`<br>Sets the GCP point y.                                                                                                                                                                                                                                                                      |
    | `void`              | `setYRMS``(java.lang.Double yRMS)`<br>Sets the GCP point yRMS.                                                                                                                                                                                                                                                   |
    | `void`              | `setZ``(java.lang.Double z)`<br>Sets the GCP point z.                                                                                                                                                                                                                                                            |
    | `void`              | `setZRMS``(java.lang.Double zRMS)`<br>Sets the GCP point zRMS.                                                                                                                                                                                                                                                   |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### GCPPoint

          public GCPPoint(int gcpPointType,
                          int cellDimension,
                          int modelDimension)

      Constructs a `GCPPoint` object with the given parameters.
      Parameters:
      `gcpPointType` - GCP point type, the following are valid values: SpatialReferenceInfo.GCPPOINT_TYPE_CONTROLPOINT SpatialReferenceInfo.GCPPOINT_TYPE_CHECKPOINT

      `cellDimension` - cell dimension size

      `modelDimension` - model dimension size

  <!-- -->

  - ### Method Detail

    - #### getID

          public java.lang.String getID()

      Returns the GCP point ID.
      Returns:
      the GCP point ID.

    <!-- -->

    - #### setID

          public void setID(java.lang.String ID)

      Sets the GCP point ID.
      Parameters:
      `ID` - GCP point ID

    <!-- -->

    - #### getDescription

          public java.lang.String getDescription()

      Returns the GCP point description.
      Returns:
      the GCP point description.

    <!-- -->

    - #### setDescription

          public void setDescription(java.lang.String description)

      Sets the GCP point description.
      Parameters:
      `description` - GCP point description

    <!-- -->

    - #### getGCPPointType

          public int getGCPPointType()

      Returns the GCP point description.
      Returns:
      the GCP point description.

    <!-- -->

    - #### setGCPPointType

          public void setGCPPointType(int type)

      Sets the GCP point type.
      Parameters:
      `type` - GCP point type

    <!-- -->

    - #### getcellDimension

          public int getcellDimension()

      Returns the GCP point cell Dimension.
      Returns:
      the GCP point cell Dimension.

    <!-- -->

    - #### setCellDimension

          public void setCellDimension(int cellDimension)

      Sets the GCP point cell Dimension.
      Parameters:
      `cellDimension` - GCP point cell Dimension

    <!-- -->

    - #### getRow

          public double getRow()

      Returns the GCP point row.
      Returns:
      the GCP point row.

    <!-- -->

    - #### setRow

          public void setRow(double row)

      Sets the GCP point row.
      Parameters:
      `row` - GCP point row

    <!-- -->

    - #### getColumn

          public double getColumn()

      Returns the GCP point column.
      Returns:
      the GCP point column.

    <!-- -->

    - #### setColumn

          public void setColumn(double column)

      Sets the GCP point column.
      Parameters:
      `column` - GCP point column

    <!-- -->

    - #### getVertical

          public java.lang.Integer getVertical()

      Returns the GCP point vertical.
      Returns:
      the GCP point vertical.

    <!-- -->

    - #### setVertical

          public void setVertical(java.lang.Integer vertical)

      Sets the GCP point vertical.
      Parameters:
      `vertical` - GCP point vertical

    <!-- -->

    - #### getModelDimension

          public int getModelDimension()

      Returns the GCP point model Dimension.
      Returns:
      the GCP point model Dimension.

    <!-- -->

    - #### setModelDimension

          public void setModelDimension(int modelDimension)

      Sets the GCP point model Dimension.
      Parameters:
      `modelDimension` - GCP point model Dimension

    <!-- -->

    - #### getX

          public double getX()

      Returns the GCP point x.
      Returns:
      the GCP point x.

    <!-- -->

    - #### setX

          public void setX(double x)

      Sets the GCP point x.
      Parameters:
      `x` - GCP point x

    <!-- -->

    - #### getY

          public double getY()

      Returns the GCP point y.
      Returns:
      the GCP point y.

    <!-- -->

    - #### setY

          public void setY(double y)

      Sets the GCP point y.
      Parameters:
      `y` - GCP point y

    <!-- -->

    - #### getZ

          public java.lang.Double getZ()

      Returns the GCP point z.
      Returns:
      the GCP point z.

    <!-- -->

    - #### setZ

          public void setZ(java.lang.Double z)

      Sets the GCP point z.
      Parameters:
      `z` - GCP point z

    <!-- -->

    - #### getXRMS

          public java.lang.Double getXRMS()

      Returns the GCP point xRMS.
      Returns:
      the GCP point xRMS.

    <!-- -->

    - #### setXRMS

          public void setXRMS(java.lang.Double xRMS)

      Sets the GCP point xRMS.
      Parameters:
      `xRMS` - GCP point xRMS

    <!-- -->

    - #### getYRMS

          public java.lang.Double getYRMS()

      Returns the GCP point yRMS.
      Returns:
      the GCP point yRMS.

    <!-- -->

    - #### setYRMS

          public void setYRMS(java.lang.Double yRMS)

      Sets the GCP point yRMS.
      Parameters:
      `yRMS` - GCP point yRMS

    <!-- -->

    - #### getZRMS

          public java.lang.Double getZRMS()

      Returns the GCP point zRMS.
      Returns:
      the GCP point zRMS.

    <!-- -->

    - #### setZRMS

          public void setZRMS(java.lang.Double zRMS)

      Sets the GCP point zRMS.
      Parameters:
      `zRMS` - GCP point zRMS

    <!-- -->

    - #### getStatus

          public java.lang.Integer getStatus()

      Returns the GCP point status, the valid value as below: SpatialReferenceInfo.GCPPOINT_STATUS_MEASURED SpatialReferenceInfo.GCPPOINT_STATUS_REMOVED SpatialReferenceInfo.GCPPOINT_STATUS_ESTIMATED SpatialReferenceInfo.GCPPOINT_STATUS_VALIDATED SpatialReferenceInfo.GCPPOINT_STATUS_INVALID
      Returns:
      the GCP point status.

    <!-- -->

    - #### setStatus

          public void setStatus(java.lang.Integer status)

      Sets the GCP point status.
      Parameters:
      `status` - GCP point status

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](GCPGeoreference.md)
- [Next Class](GeoRasterException.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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
