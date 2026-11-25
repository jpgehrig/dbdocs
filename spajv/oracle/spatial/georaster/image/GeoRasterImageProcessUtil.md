Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](GeoRasterImage.NodataMapping.md)
- [Next Class](RasterImage.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.spatial.georaster.image

## Class GeoRasterImageProcessUtil

- java.lang.Object

- - oracle.spatial.georaster.image.GeoRasterImageProcessUtil

<!-- -->

-

  ------------------------------------------------------------------------



      public class GeoRasterImageProcessUtil
      extends java.lang.Object

  The `GeoRasterImageProcessUtil` class provides the following basic image processing functions:
           normalize
           equalize
           scale
           piecewiseLinearStretch
           changeContrast
           changeBrightness
           changeThreshold


  The `GeoRasterImageProcessUtil` object is initiated by a RenderedImage object as follows:

           GeoRasterImageProcessUtil util=new GeoRasterImageProcessUtil(image);


  When creating a `GeoRasterImageProcessUtil` object, it is the application's responsibility to ensure that the current working image is not null.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                          |
    |------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `GeoRasterImageProcessUtil``(java.awt.image.RenderedImage img)`<br>Constructs an `GeoRasterProcessUtil` object using the given RenderedImage object. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type              | Method and Description                                                                                                                                                                                                               |
    |--------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.awt.image.RenderedImage` | `amplitudeRescaling``()`<br>Performs amplitude rescaling; the method will calculate extreme values for the image at first, and then scale extreme low and extreme high values to 0 and 256 respectively.                             |
    | `java.awt.image.RenderedImage` | `amplitudeRescaling``(double low, double high)`<br>Performs amplitude rescaling; low value and high value will be scaled to 0 and 256, respectively.                                                                                 |
    | `java.awt.image.RenderedImage` | `changeBrightness``(int b)`<br>change brightness of the current working image                                                                                                                                                        |
    | `java.awt.image.RenderedImage` | `changeContrast``(double contrast)`<br>Changes the contrast of the current working image.                                                                                                                                            |
    | `java.awt.image.RenderedImage` | `changeThreshold``(double low_p, double high_p, double target)`<br>Applies a threshold operation on the current working image; maps all the pixels of this image whose value falls within a specified range to a specified constant. |
    | `java.awt.image.RenderedImage` | `equalize``()`<br>Applies an equalization operation on the current working image.                                                                                                                                                    |
    | `java.awt.image.RenderedImage` | `getImage``()`<br>Gets the current working image.                                                                                                                                                                                    |
    | `java.awt.image.RenderedImage` | `normalize``()`<br>Applies a normalization operation on the current working image.                                                                                                                                                   |
    | `java.awt.image.RenderedImage` | `piecewiseLinearStretch``()`<br>Applies a piecewise linear stretch operation on the current working image.                                                                                                                           |
    | `void`                         | `setImage``(java.awt.image.RenderedImage img)`<br>Sets the current working image.                                                                                                                                                    |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### GeoRasterImageProcessUtil

          public GeoRasterImageProcessUtil(java.awt.image.RenderedImage img)

      Constructs an `GeoRasterProcessUtil` object using the given RenderedImage object.
      Parameters:
      `img` - a RenderedImage object

  <!-- -->

  - ### Method Detail

    - #### setImage

          public void setImage(java.awt.image.RenderedImage img)

      Sets the current working image.
      Parameters:
      `img` - current working RenderedImage

    <!-- -->

    - #### getImage

          public java.awt.image.RenderedImage getImage()

      Gets the current working image.
      Returns:
      current working renderedImage.

    <!-- -->

    - #### amplitudeRescaling

          public java.awt.image.RenderedImage amplitudeRescaling(double low,
                                                                 double high)

      Performs amplitude rescaling; low value and high value will be scaled to 0 and 256, respectively.
      Parameters:
      `low` - low value, which will be scaled to 0

      `high` - high value, which will be scaled to 256

      Returns:
      a new RenderedImage object if scaling was successfully applied to the current working image, or null if the operation failed. Note: in both cases, the current working image is kept intact.

    <!-- -->

    - #### amplitudeRescaling

          public java.awt.image.RenderedImage amplitudeRescaling()

      Performs amplitude rescaling; the method will calculate extreme values for the image at first, and then scale extreme low and extreme high values to 0 and 256 respectively.
      Returns:
      a new RenderedImage object, if scaling was successfully applied to the current working image, or null if the operation failed. Note: in both cases, the current working image is kept intact.

    <!-- -->

    - #### normalize

          public java.awt.image.RenderedImage normalize()

      Applies a normalization operation on the current working image.
      Returns:
      a new RenderedImage object if the operation succeeded, or null if it failed. Note: in both cases, the current working image is kept intact.

    <!-- -->

    - #### piecewiseLinearStretch

          public java.awt.image.RenderedImage piecewiseLinearStretch()

      Applies a piecewise linear stretch operation on the current working image.
      Returns:
      a new RenderedImage object if the operation succeeded, or null if it failed. Note: in both cases, the current working image is kept intact.

    <!-- -->

    - #### equalize

          public java.awt.image.RenderedImage equalize()

      Applies an equalization operation on the current working image.
      Returns:
      a new RenderedImage object if the operation succeeded, or null if it failed. Note: in both cases, the current working image is kept intact.

    <!-- -->

    - #### changeBrightness

          public java.awt.image.RenderedImage changeBrightness(int b)

      change brightness of the current working image
      Parameters:
      `b` - brightness, data range is 0-256

      Returns:
      a new RenderedImage object if the operation succeeded, or null if it failed. Note: in both cases, the current working image is kept intact.

    <!-- -->

    - #### changeThreshold

          public java.awt.image.RenderedImage changeThreshold(double low_p,
                                                              double high_p,
                                                              double target)

      Applies a threshold operation on the current working image; maps all the pixels of this image whose value falls within a specified range to a specified constant. The range is specified by a low_p value and a high_p value, and the constant value is specified by the target parameter.
      Parameters:
      `low_p` - low end of data range

      `high_p` - high end of data range

      `target` - constant value for specific range of values

      Returns:
      a new RenderedImage object if the operation succeeded, or null if it failed. Note: in both cases, the current working image is kept intact.

    <!-- -->

    - #### changeContrast

          public java.awt.image.RenderedImage changeContrast(double contrast)

      Changes the contrast of the current working image.
      Parameters:
      `contrast` - contrast, data range is 0-256

      Returns:
      a new RenderedImage object if the operation succeeded, or null if it failed. Note: in both cases, the current working image is kept intact.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](GeoRasterImage.NodataMapping.md)
- [Next Class](RasterImage.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
