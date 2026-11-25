## Image Type

When you add or import a gold image, you must specify an image type.

Oracle Clusterware provides the following built-in base image types:

- ORACLEDBSOFTWARE
- ORACLEGISOFTWARE
- ORACLEGGSOFTWARE
- EXAPATCHSOFTWARE
- SOFTWARE

Every gold image must have an image type, and you can create your own image types. A new image type must be based on one of the built-in types. The image type directs Fleet Patching and Provisioning to apply its capabilities for managing Oracle Grid Infrastructure and Oracle Database homes. Fleet Patching and Provisioning also uses image type to organize the custom workflow support framework.

### Creating a Custom Image Type

Use the `rhpctl add imagetype` command to create custom image types.

For example, to create an image type called DBTEST, which is based on the ORACLEDBSOFTWARE image type:

    $ rhpctl add imagetype -imagetype DBTEST -basetype ORACLEDBSOFTWARE

**Note:**

When you create an image type that is based on an existing image type, the new image type does not inherit any user actions (for custom workflow support) from the base type.

**Parent topic:** [Adding Gold Images to the Fleet Patching and Provisioning Server](adding-gold-images-to-oracle-fpp-server.md)
