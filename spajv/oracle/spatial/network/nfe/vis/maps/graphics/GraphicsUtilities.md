Skip navigation links

- [Overview](../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../deprecated-list.md)
- [Index](../../../../../../../index-all.md)
- [Help](../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](AnimatedStroke.md)
- [Next Class](MapTip.md)

<!-- -->

- [Frames](../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.vis.maps.graphics

## Class GraphicsUtilities

- java.lang.Object

- - oracle.spatial.network.nfe.vis.maps.graphics.GraphicsUtilities

<!-- -->

-

  ------------------------------------------------------------------------



      public class GraphicsUtilities
      extends java.lang.Object

  `GraphicsUtilities` contains a set of tools to perform common graphics operations easily. These operations are divided into several themes, listed below.

  ## Compatible Images

  Compatible images can, and should, be used to increase drawing performance. This class provides a number of methods to load compatible images directly from files or to convert existing images to compatibles images.

  ## Creating Thumbnails

  This class provides a number of methods to easily scale down images. Some of these methods offer a trade-off between speed and result quality and should be used all the time. They also offer the advantage of producing compatible images, thus automatically resulting into better runtime performance.

  All these methods are both faster than `Image.getScaledInstance(int, int, int)` and produce better-looking results than the various `drawImage()` methods in `Graphics`, which can be used for image scaling.

  ## Image Manipulation

  This class provides two methods to get and set pixels in a buffered image. These methods try to avoid unmanaging the image in order to keep good performance.

<!-- -->

- - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                     | Method and Description                                                                                                                                                                                                             |
    |---------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static java.awt.image.BufferedImage` | `convertToBufferedImage``(java.awt.Image img)`<br>Converts the specified image into a compatible buffered image.                                                                                                                   |
    | `static java.awt.image.BufferedImage` | `createColorModelCompatibleImage``(java.awt.image.BufferedImage image)`<br>Returns a new `BufferedImage` using the same color model as the image passed as a parameter.                                                            |
    | `static java.awt.image.BufferedImage` | `createCompatibleImage``(java.awt.image.BufferedImage image)`<br>Returns a new compatible image with the same width, height and transparency as the image specified as a parameter.                                                |
    | `static java.awt.image.BufferedImage` | `createCompatibleImage``(java.awt.image.BufferedImage image, int width, int height)`<br>Returns a new compatible image of the specified width and height, and the same transparency setting as the image specified as a parameter. |
    | `static java.awt.image.BufferedImage` | `createCompatibleImage``(int width, int height)`<br>Returns a new opaque compatible image of the specified width and height.                                                                                                       |
    | `static java.awt.image.BufferedImage` | `createCompatibleTranslucentImage``(int width, int height)`<br>Returns a new translucent compatible image of the specified width and height.                                                                                       |
    | `static java.awt.image.BufferedImage` | `createThumbnail``(java.awt.image.BufferedImage image, int newSize)`<br>Returns a thumbnail of a source image.                                                                                                                     |
    | `static java.awt.image.BufferedImage` | `createThumbnail``(java.awt.image.BufferedImage image, int newWidth, int newHeight)`<br>Returns a thumbnail of a source image.                                                                                                     |
    | `static java.awt.image.BufferedImage` | `createThumbnailFast``(java.awt.image.BufferedImage image, int newSize)`<br>Returns a thumbnail of a source image.                                                                                                                 |
    | `static java.awt.image.BufferedImage` | `createThumbnailFast``(java.awt.image.BufferedImage image, int newWidth, int newHeight)`<br>Returns a thumbnail of a source image.                                                                                                 |
    | `static int[]`                        | `getPixels``(java.awt.image.BufferedImage img, int x, int y, int w, int h, int[] pixels)`<br>Returns an array of pixels, stored as integers, from a `BufferedImage`.                                                               |
    | `static java.awt.image.BufferedImage` | `loadCompatibleImage``(java.io.InputStream in)`<br>Returns a new compatible image from a stream.                                                                                                                                   |
    | `static java.awt.image.BufferedImage` | `loadCompatibleImage``(java.net.URL resource)`<br>Returns a new compatible image from a URL.                                                                                                                                       |
    | `static java.awt.Shape`               | `mergeClip``(java.awt.Graphics g, java.awt.Shape clip)`<br>Sets the clip on a graphics object by merging a supplied clip with the existing one.                                                                                    |
    | `static void`                         | `setPixels``(java.awt.image.BufferedImage img, int x, int y, int w, int h, int[] pixels)`<br>Writes a rectangular area of pixels in the destination `BufferedImage`.                                                               |
    | `static java.awt.image.BufferedImage` | `toCompatibleImage``(java.awt.image.BufferedImage image)`<br>Return a new compatible image that contains a copy of the specified image.                                                                                            |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### convertToBufferedImage

          public static java.awt.image.BufferedImage convertToBufferedImage(java.awt.Image img)

      Converts the specified image into a compatible buffered image.
      Parameters:
      `img` - the image to convert

      Returns:
      a compatible buffered image of the input

    <!-- -->

    - #### createColorModelCompatibleImage

          public static java.awt.image.BufferedImage createColorModelCompatibleImage(java.awt.image.BufferedImage image)

      Returns a new `BufferedImage` using the same color model as the image passed as a parameter. The returned image is only compatible with the image passed as a parameter. This does not mean the returned image is compatible with the hardware.

      Parameters:
      `image` - the reference image from which the color model of the new image is obtained

      Returns:
      a new `BufferedImage`, compatible with the color model of `image`

    <!-- -->

    - #### createCompatibleImage

          public static java.awt.image.BufferedImage createCompatibleImage(java.awt.image.BufferedImage image)

      Returns a new compatible image with the same width, height and transparency as the image specified as a parameter. That is, the returned BufferedImage will be compatible with the graphics hardware. If this method is called in a headless environment, then the returned BufferedImage will be compatible with the source image.

      Parameters:
      `image` - the reference image from which the dimension and the transparency of the new image are obtained

      Returns:
      a new compatible `BufferedImage` with the same dimension and transparency as `image`

      See Also:
      `Transparency`, `createCompatibleImage(int, int)`, `createCompatibleImage(java.awt.image.BufferedImage, int, int)`, `createCompatibleTranslucentImage(int, int)`, `loadCompatibleImage(java.net.URL)`, `toCompatibleImage(java.awt.image.BufferedImage)`

    <!-- -->

    - #### createCompatibleImage

          public static java.awt.image.BufferedImage createCompatibleImage(java.awt.image.BufferedImage image,
                                                                           int width,
                                                                           int height)

      Returns a new compatible image of the specified width and height, and the same transparency setting as the image specified as a parameter. That is, the returned `BufferedImage` is compatible with the graphics hardware. If the method is called in a headless environment, then the returned BufferedImage will be compatible with the source image.

      Parameters:
      `width` - the width of the new image

      `height` - the height of the new image

      `image` - the reference image from which the transparency of the new image is obtained

      Returns:
      a new compatible `BufferedImage` with the same transparency as `image` and the specified dimension

      See Also:
      `Transparency`, `createCompatibleImage(java.awt.image.BufferedImage)`, `createCompatibleImage(int, int)`, `createCompatibleTranslucentImage(int, int)`, `loadCompatibleImage(java.net.URL)`, `toCompatibleImage(java.awt.image.BufferedImage)`

    <!-- -->

    - #### createCompatibleImage

          public static java.awt.image.BufferedImage createCompatibleImage(int width,
                                                                           int height)

      Returns a new opaque compatible image of the specified width and height. That is, the returned `BufferedImage` is compatible with the graphics hardware. If the method is called in a headless environment, then the returned BufferedImage will be compatible with the source image.

      Parameters:
      `width` - the width of the new image

      `height` - the height of the new image

      Returns:
      a new opaque compatible `BufferedImage` of the specified width and height

      See Also:
      `createCompatibleImage(java.awt.image.BufferedImage)`, `createCompatibleImage(java.awt.image.BufferedImage, int, int)`, `createCompatibleTranslucentImage(int, int)`, `loadCompatibleImage(java.net.URL)`, `toCompatibleImage(java.awt.image.BufferedImage)`

    <!-- -->

    - #### createCompatibleTranslucentImage

          public static java.awt.image.BufferedImage createCompatibleTranslucentImage(int width,
                                                                                      int height)

      Returns a new translucent compatible image of the specified width and height. That is, the returned `BufferedImage` is compatible with the graphics hardware. If the method is called in a headless environment, then the returned BufferedImage will be compatible with the source image.

      Parameters:
      `width` - the width of the new image

      `height` - the height of the new image

      Returns:
      a new translucent compatible `BufferedImage` of the specified width and height

      See Also:
      `createCompatibleImage(java.awt.image.BufferedImage)`, `createCompatibleImage(java.awt.image.BufferedImage, int, int)`, `createCompatibleImage(int, int)`, `loadCompatibleImage(java.net.URL)`, `toCompatibleImage(java.awt.image.BufferedImage)`

    <!-- -->

    - #### loadCompatibleImage

          public static java.awt.image.BufferedImage loadCompatibleImage(java.io.InputStream in)
                                                                  throws java.io.IOException

      Returns a new compatible image from a stream. The image is loaded from the specified stream and then turned, if necessary into a compatible image.

      Parameters:
      `in` - the stream of the picture to load as a compatible image

      Returns:
      a new translucent compatible `BufferedImage` of the specified width and height

      Throws:
      `java.io.IOException` - if the image cannot be read or loaded

      See Also:
      `createCompatibleImage(java.awt.image.BufferedImage)`, `createCompatibleImage(java.awt.image.BufferedImage, int, int)`, `createCompatibleImage(int, int)`, `createCompatibleTranslucentImage(int, int)`, `toCompatibleImage(java.awt.image.BufferedImage)`

    <!-- -->

    - #### loadCompatibleImage

          public static java.awt.image.BufferedImage loadCompatibleImage(java.net.URL resource)
                                                                  throws java.io.IOException

      Returns a new compatible image from a URL. The image is loaded from the specified location and then turned, if necessary into a compatible image.

      Parameters:
      `resource` - the URL of the picture to load as a compatible image

      Returns:
      a new translucent compatible `BufferedImage` of the specified width and height

      Throws:
      `java.io.IOException` - if the image cannot be read or loaded

      See Also:
      `createCompatibleImage(java.awt.image.BufferedImage)`, `createCompatibleImage(java.awt.image.BufferedImage, int, int)`, `createCompatibleImage(int, int)`, `createCompatibleTranslucentImage(int, int)`, `toCompatibleImage(java.awt.image.BufferedImage)`

    <!-- -->

    - #### toCompatibleImage

          public static java.awt.image.BufferedImage toCompatibleImage(java.awt.image.BufferedImage image)

      Return a new compatible image that contains a copy of the specified image. This method ensures an image is compatible with the hardware, and therefore optimized for fast blitting operations.

      If the method is called in a headless environment, then the returned `BufferedImage` will be the source image.

      Parameters:
      `image` - the image to copy into a new compatible image

      Returns:
      a new compatible copy, with the same width and height and transparency and content, of `image`

      See Also:
      `createCompatibleImage(java.awt.image.BufferedImage)`, `createCompatibleImage(java.awt.image.BufferedImage, int, int)`, `createCompatibleImage(int, int)`, `createCompatibleTranslucentImage(int, int)`, `loadCompatibleImage(java.net.URL)`

    <!-- -->

    - #### createThumbnailFast

          public static java.awt.image.BufferedImage createThumbnailFast(java.awt.image.BufferedImage image,
                                                                         int newSize)

      Returns a thumbnail of a source image. `newSize` defines the length of the longest dimension of the thumbnail. The other dimension is then computed according to the dimensions ratio of the original picture.

      This method favors speed over quality. When the new size is less than half the longest dimension of the source image, `createThumbnail(BufferedImage, int)` or `createThumbnail(BufferedImage, int, int)` should be used instead to ensure the quality of the result without sacrificing too much performance.

      Parameters:
      `image` - the source image

      `newSize` - the length of the largest dimension of the thumbnail

      Returns:
      a new compatible `BufferedImage` containing a thumbnail of `image`

      Throws:
      `java.lang.IllegalArgumentException` - if `newSize` is larger than the largest dimension of `image` or \<= 0

      See Also:
      `createThumbnailFast(java.awt.image.BufferedImage, int, int)`, `createThumbnail(java.awt.image.BufferedImage, int)`, `createThumbnail(java.awt.image.BufferedImage, int, int)`

    <!-- -->

    - #### createThumbnailFast

          public static java.awt.image.BufferedImage createThumbnailFast(java.awt.image.BufferedImage image,
                                                                         int newWidth,
                                                                         int newHeight)

      Returns a thumbnail of a source image.

      This method favors speed over quality. When the new size is less than half the longest dimension of the source image, `createThumbnail(BufferedImage, int)` or `createThumbnail(BufferedImage, int, int)` should be used instead to ensure the quality of the result without sacrificing too much performance.

      Parameters:
      `image` - the source image

      `newWidth` - the width of the thumbnail

      `newHeight` - the height of the thumbnail

      Returns:
      a new compatible `BufferedImage` containing a thumbnail of `image`

      Throws:
      `java.lang.IllegalArgumentException` - if `newWidth` is larger than the width of `image` or if code\>newHeight is larger than the height of `image` or if one of the dimensions is \<= 0

      See Also:
      `createThumbnailFast(java.awt.image.BufferedImage, int)`, `createThumbnail(java.awt.image.BufferedImage, int)`, `createThumbnail(java.awt.image.BufferedImage, int, int)`

    <!-- -->

    - #### createThumbnail

          public static java.awt.image.BufferedImage createThumbnail(java.awt.image.BufferedImage image,
                                                                     int newSize)

      Returns a thumbnail of a source image. `newSize` defines the length of the longest dimension of the thumbnail. The other dimension is then computed according to the dimensions ratio of the original picture.

      This method offers a good trade-off between speed and quality. The result looks better than `createThumbnailFast(java.awt.image.BufferedImage, int)` when the new size is less than half the longest dimension of the source image, yet the rendering speed is almost similar.

      Parameters:
      `image` - the source image

      `newSize` - the length of the largest dimension of the thumbnail

      Returns:
      a new compatible `BufferedImage` containing a thumbnail of `image`

      Throws:
      `java.lang.IllegalArgumentException` - if `newSize` is larger than the largest dimension of `image` or \<= 0

      See Also:
      `createThumbnailFast(java.awt.image.BufferedImage, int, int)`, `createThumbnailFast(java.awt.image.BufferedImage, int)`, `createThumbnail(java.awt.image.BufferedImage, int, int)`

    <!-- -->

    - #### createThumbnail

          public static java.awt.image.BufferedImage createThumbnail(java.awt.image.BufferedImage image,
                                                                     int newWidth,
                                                                     int newHeight)

      Returns a thumbnail of a source image.

      This method offers a good trade-off between speed and quality. The result looks better than `createThumbnailFast(java.awt.image.BufferedImage, int)` when the new size is less than half the longest dimension of the source image, yet the rendering speed is almost similar.

      Parameters:
      `image` - the source image

      `newWidth` - the width of the thumbnail

      `newHeight` - the height of the thumbnail

      Returns:
      a new compatible `BufferedImage` containing a thumbnail of `image`

      Throws:
      `java.lang.IllegalArgumentException` - if `newWidth` is larger than the width of `image` or if code\>newHeight is larger than the height of `image or if one the dimensions is not > 0`

      See Also:
      `createThumbnailFast(java.awt.image.BufferedImage, int)`, `createThumbnailFast(java.awt.image.BufferedImage, int, int)`, `createThumbnail(java.awt.image.BufferedImage, int)`

    <!-- -->

    - #### getPixels

          public static int[] getPixels(java.awt.image.BufferedImage img,
                                        int x,
                                        int y,
                                        int w,
                                        int h,
                                        int[] pixels)

      Returns an array of pixels, stored as integers, from a `BufferedImage`. The pixels are grabbed from a rectangular area defined by a location and two dimensions. Calling this method on an image of type different from `BufferedImage.TYPE_INT_ARGB` and `BufferedImage.TYPE_INT_RGB` will unmanage the image.

      Parameters:
      `img` - the source image

      `x` - the x location at which to start grabbing pixels

      `y` - the y location at which to start grabbing pixels

      `w` - the width of the rectangle of pixels to grab

      `h` - the height of the rectangle of pixels to grab

      `pixels` - a pre-allocated array of pixels of size w\*h; can be null

      Returns:
      `pixels` if non-null, a new array of integers otherwise

      Throws:
      `java.lang.IllegalArgumentException` - is `pixels` is non-null and of length \< w\*h

    <!-- -->

    - #### setPixels

          public static void setPixels(java.awt.image.BufferedImage img,
                                       int x,
                                       int y,
                                       int w,
                                       int h,
                                       int[] pixels)

      Writes a rectangular area of pixels in the destination `BufferedImage`. Calling this method on an image of type different from `BufferedImage.TYPE_INT_ARGB` and `BufferedImage.TYPE_INT_RGB` will unmanage the image.

      Parameters:
      `img` - the destination image

      `x` - the x location at which to start storing pixels

      `y` - the y location at which to start storing pixels

      `w` - the width of the rectangle of pixels to store

      `h` - the height of the rectangle of pixels to store

      `pixels` - an array of pixels, stored as integers

      Throws:
      `java.lang.IllegalArgumentException` - is `pixels` is non-null and of length \< w\*h

    <!-- -->

    - #### mergeClip

          public static java.awt.Shape mergeClip(java.awt.Graphics g,
                                                 java.awt.Shape clip)

      Sets the clip on a graphics object by merging a supplied clip with the existing one. The new clip will be an intersection of the old clip and the supplied clip. The old clip shape will be returned. This is useful for resetting the old clip after an operation is performed.
      Parameters:
      `g` - the graphics object to update

      `clip` - a new clipping region to add to the graphics clip.

      Returns:
      the current clipping region of the supplied graphics object. This may return `null` if the current clip is `null`.

      Throws:
      `java.lang.NullPointerException` - if any parameter is `null`

Skip navigation links

- [Overview](../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../deprecated-list.md)
- [Index](../../../../../../../index-all.md)
- [Help](../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](AnimatedStroke.md)
- [Next Class](MapTip.md)

<!-- -->

- [Frames](../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../allclasses-noframe.md)

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
