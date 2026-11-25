## Images of Oracle Fleet Patching and Provisioning

You can easily copy an image of an Oracle home to a new host on a new file system to serve as an active usable Oracle home.

By default, when you create a gold image using either `rhpctl import image` or `rhpctl add image`, the image is ready to provision new homes, called working copies. However, under certain conditions, you may want to restrict access to images and require someone to test or validate the image before making it available for general use.

You can also create a set of gold images on the Oracle Fleet Patching and Provisioning Server that can be collectively categorized as a gold image series which relate to each other, such as identical release versions, gold images published by a particular user, or images for a particular department within an organization.

**Related Topics**

- [Image State](image-state.md)
- [Image Series](image-series.md)
- [Image Type](image-type.md)

**Parent topic:** [Fleet Patching and Provisioning Architecture](oracle-fpp-architecture.md)
