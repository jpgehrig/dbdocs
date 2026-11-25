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

- [Prev Class](GeoRasterImageProcessUtil.md)
- Next Class

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

## Class RasterImage

- java.lang.Object

- - oracle.spatial.georaster.image.RasterImage

<!-- -->

-

  ------------------------------------------------------------------------



      public class RasterImage
      extends java.lang.Object

  RasterImage is a Java class that generates a RenderedImage object from a Blob or a byte array. There are two constructors which take data in byte\[\] or Blob: public RasterImage( byte\[\] data, long height, long width, long nbands, String cellDepth, String interleaving) throws GeoRasterException; public RasterImage( Blob blob, long height, long width, long nbands, String cellDepth, String interleaving) throws GeoRasterException, IOException, SQLException; Example on how to use the class: //construct a RasterImage object using the data either in byte\[\] or Blob RasterImage ri = new RasterImage(data, 800, 600, 3, '8BIT_U', 'BIP'); //optionally set the colormap, nodatamapping, or image processing. ri.setColormap(colormap); ri.setNodataMappings(nodataMapping); ri.setImageProcessing(GeoRasterImage.IP_EQUALIZATION); ri.setBandStatistcis("red", 0, 255, 80, 125, histogram); //get the RenderedImage object RenderedImage image = ri.getRenderedImage(false);

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                            |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `RasterImage``(java.sql.Blob blob, long height, long width, long nbands, java.lang.String cellDepth, java.lang.String interleaving)`<br>Constructs a RasterImage object with image information and image data in Blob. |
    | `RasterImage``(byte[] data, long height, long width, long nbands, java.lang.String cellDepth, java.lang.String interleaving)`<br>Constructs a RasterImage object with image information and image data in byte\[\].    |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                       | Method and Description                                                                                                                                                                          |
    |-----------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`GeorColormap`](../GeorColormap.md)                                                    | `getColormap``()`<br>Get Colormap                                                                                                                                                               |
    | [`GeorGrayscale`](../GeorGrayscale.md)                                                  | `getGrayScale``()`<br>Get Grayscale                                                                                                                                                             |
    | `java.util.Vector<`[`GeoRasterImage.NodataMapping`](GeoRasterImage.NodataMapping.md)`>` | `getNodataMappings``()`<br>Get nodatamapping.                                                                                                                                                   |
    | `java.awt.image.RenderedImage`                                                          | `getRenderedImage``(boolean isExport)`<br>Create a RenderedImage object from the image.                                                                                                         |
    | `boolean`                                                                               | `hasAlpha``()`<br>Check if this image has alpha channel                                                                                                                                         |
    | `void`                                                                                  | `setBandStatistics``(java.lang.String bandName, double min, double max, double std, double mean, `[`GeorHistogram`](../GeorHistogram.md)` histogram)`<br>Set band statistics for certain bands. |
    | `void`                                                                                  | `setColormap``(`[`GeorColormap`](../GeorColormap.md)` colormap)`<br>Set Colormap                                                                                                                |
    | `void`                                                                                  | `setGrayscale``(`[`GeorGrayscale`](../GeorGrayscale.md)` grayscale)`<br>Set Grayscale                                                                                                           |
    | `void`                                                                                  | `setImageProcessing``(int method)`<br>Set the image processing operator.                                                                                                                        |
    | `void`                                                                                  | `setNodataMappings``(java.util.Vector<`[`GeoRasterImage.NodataMapping`](GeoRasterImage.NodataMapping.md)`> nodataMapping)`<br>Set nodatamapping.                                                |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### RasterImage

          public RasterImage(byte[] data,
                             long height,
                             long width,
                             long nbands,
                             java.lang.String cellDepth,
                             java.lang.String interleaving)
                      throws GeoRasterException

      Constructs a RasterImage object with image information and image data in byte\[\].
      Parameters:
      `data` - The raw image data in a byte array.

      `height` - The height of the image.

      `width` - The width of the image.

      `cellDepth` - The cell depth of the image pixel, which is defined in RasterInfo class.

      `interleaving` - The interleaving of the image, which is defined in RasterInfo class.

      Throws:
      [`GeoRasterException`](../GeoRasterException.md)

    <!-- -->

    - #### RasterImage

          public RasterImage(java.sql.Blob blob,
                             long height,
                             long width,
                             long nbands,
                             java.lang.String cellDepth,
                             java.lang.String interleaving)
                      throws GeoRasterException,
                             java.io.IOException,
                             java.sql.SQLException

      Constructs a RasterImage object with image information and image data in Blob.
      Parameters:
      `data` - The raw image data in a byte array.

      `height` - The height of the image.

      `width` - The width of the image.

      `cellDepth` - The cell depth of the image pixel, which is defined in RasterInfo class.

      `interleaving` - The interleaving of the image, which is defined in RasterInfo class.

      Throws:
      [`GeoRasterException`](../GeoRasterException.md)

      `java.io.IOException`

      `java.sql.SQLException`

  <!-- -->

  - ### Method Detail

    - #### setColormap

          public void setColormap(GeorColormap colormap)

      Set Colormap
      Parameters:
      `colormap` - The colormap to be associated the image

    <!-- -->

    - #### getColormap

          public GeorColormap getColormap()

      Get Colormap
      Returns:
      The current colormap associated with the image

    <!-- -->

    - #### setGrayscale

          public void setGrayscale(GeorGrayscale grayscale)

      Set Grayscale
      Parameters:
      `grayscale` - The grayscale to be associated the image

    <!-- -->

    - #### getGrayScale

          public GeorGrayscale getGrayScale()

      Get Grayscale
      Returns:
      The current grayscale associated with the image

    <!-- -->

    - #### hasAlpha

          public boolean hasAlpha()

      Check if this image has alpha channel
      Returns:
      true or false

    <!-- -->

    - #### setNodataMappings

          public void setNodataMappings(java.util.Vector<GeoRasterImage.NodataMapping> nodataMapping)
                                 throws GeoRasterException

      Set nodatamapping.
      Parameters:
      `nodataMapping` - The nodata mappings of the image.

      Throws:
      [`GeoRasterException`](../GeoRasterException.md)

    <!-- -->

    - #### getNodataMappings

          public java.util.Vector<GeoRasterImage.NodataMapping> getNodataMappings()

      Get nodatamapping.
      Returns:
      NodataMapping objects in a vector

    <!-- -->

    - #### setImageProcessing

          public void setImageProcessing(int method)
                                  throws GeoRasterException

      Set the image processing operator.
      Parameters:
      `method` - The method of the image processing defined in GeoRasterImage class.

      Throws:
      [`GeoRasterException`](../GeoRasterException.md)

    <!-- -->

    - #### setBandStatistics

          public void setBandStatistics(java.lang.String bandName,
                                        double min,
                                        double max,
                                        double std,
                                        double mean,
                                        GeorHistogram histogram)

      Set band statistics for certain bands. The statisitics is used by the image processing.
      Parameters:
      `bandName` - The name of the band, one of "red", "green" and "blue"

      `min` - The minimum value of the pixel in the band.

      `max` - The maximum value of the pixel in the band.

      `std` - The standard deviation value of the pixel in the band.

      `mean` - The mean value of the pixel in the band.

      `histogram` - The histogram of the band.

    <!-- -->

    - #### getRenderedImage

          public java.awt.image.RenderedImage getRenderedImage(boolean isExport)
                                                        throws GeoRasterException,
                                                               java.io.IOException

      Create a RenderedImage object from the image.
      Returns:
      a RenderdImage

      Throws:
      [`GeoRasterException`](../GeoRasterException.md)

      `java.io.IOException`

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

- [Prev Class](GeoRasterImageProcessUtil.md)
- Next Class

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
