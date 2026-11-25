## Image Series

An image series is a convenient way to group different gold images into a logical sequence.

Fleet Patching and Provisioning treats each image as an independent entity with respect to other images. No relationship is assumed between images, even if they follow some specific nomenclature. The image administrator may choose to name images in a logical manner that makes sense to the user community, but this does not create any management grouping within the Fleet Patching and Provisioning framework.

Use the `rhpctl add series` command to create an image series and associate one or more images to this series. The list of images in an image series is an ordered list. Use the `rhpctl insertimage series` and `rhpctl deleteimage series` to add and delete images in an image series. You can also change the order of images in a series using these commands.

The `insertimage` and `deleteimage` commands do not instantiate or delete actual gold images but only change the list. Also, an image can belong to more than one series (or no series at all).

**Parent topic:** [Adding Gold Images to the Fleet Patching and Provisioning Server](adding-gold-images-to-oracle-fpp-server.md)
