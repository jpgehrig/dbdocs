## Working Copies of Oracle Fleet Patching and Provisioning

Working copy is a copy of the gold image that you use to provision the software on an Oracle Fleet Patching and Provisioning (Oracle FPP) Client or an `rhpclient`-less target.

By default, when you create a gold image using either `rhpctl import image` or `rhpctl add image`, the image is ready to provision working copies. You can use the `rhpctl add workingcopy` command to add a working copy to a client cluster.

After you create and import a gold image, you can provision software by adding a copy of the gold image (called a working copy) on the Fleet Patching and Provisioning Server, on a Fleet Patching and Provisioning Client, or an `rhpclient`-less target.

**Related Topics**

- [Image State](image-state.md)
- [Image Series](image-series.md)
- [Image Type](image-type.md)

**Parent topic:** [Fleet Patching and Provisioning Architecture](oracle-fpp-architecture.md)
