## Adding Gold Images to the Fleet Patching and Provisioning Server

Use RHPCTL to add gold images for later provisioning of software.

The Fleet Patching and Provisioning Server stores and serves gold images of software homes. These images must be instantiated on the Fleet Patching and Provisioning Server. Images are read-only, and you cannot run programs from them. To create a usable software home from an image, you must create a working copy of a gold image. You cannot directly use images as software homes. You can, however, use images to create working copies (software homes).

**Note:**

Starting with Oracle Grid Infrastructure 19c Release Update (19.11), Oracle FPP allows you to install the gold images without transferring them to the target host. This feature is known as zipcopy and you can use it to provision Oracle Database homes. You can also use this feature to provision Oracle Grid Infrastructure homes that exists on the target hosts, but not to provision new Oracle Grid Infrastructure homes.

You can import software to the Fleet Patching and Provisioning Server using any one of the following methods:

- You can import an image from an installed home on the Fleet Patching and Provisioning Server using the following command:

      rhpctl import image -image image_name -path path_to_installed_home
        [-imagetype ORACLEDBSOFTWARE | ORACLEGISOFTWARE | ORACLEGGSOFTWARE | SOFTWARE]

- You can import a new image from a zip file using the `-zip` and `-location` parameters:

      $ rhpctl import image -image image_name -zip zip_file_path -location
        location_on_target_host_where_image_is_available

  The `-zip` parameter specifies the location from which you can import the image to the Oracle FPP server. The `-location` parameter specifies a location where the image is available on the target host as a zip file. The `-location` parameter also instructs the Oracle FPP server to not copy the image-related files from the Oracle FPP server to the target host.

  You can make the image zip files available on the target hosts using either local or shared storage. For shared storage, you can use NFS file system shared with servers and targets. For local storage, you can copy the zip file using any option that guarantees its consistency on the target because Oracle FPP does not verify consistency of the zip file. You can use SFTP, SCP, or download the zip file using `curl` or `wget` methods from a shared location. The file must be available at the specified location.

- You can import a ZIP file of an image created from an installed home on the Fleet Patching and Provisioning Server using the following command:

      rhpctl import image -image image_name -zip zipped_home_path

- You can import an image from an installed home on a Fleet Patching and Provisioning Client, using the following command run from the Fleet Patching and Provisioning Client:

      rhpctl import image -image image_name -path path_to_installed_home

- You can create an image from an existing working copy using the following command:

      rhpctl add image –image image_name -workingcopy working_copy_name

Use the first two commands in the preceding list to seed the image repository, and to add additional images over time. Use the fourth command on the Fleet Patching and Provisioning Server as part of the workflow for creating a gold image that includes patches applied to a pre-existing gold image.

The preceding three commands also create an Oracle ACFS file system in the Fleet Patching and Provisioning root directory, similar to the following:

    /u01/rhp/images/images/RDBMS_121020617524

- [Image State](image-state.md)
  Am image state is a way to restrict provisioning of an image for users with specified roles.
- [Image Series](image-series.md)
  An image series is a convenient way to group different gold images into a logical sequence.
- [Image Type](image-type.md)
  When you add or import a gold image, you must specify an image type.

**Related Topics**

- [Patching Oracle Database](patching-oracle-database.md)
- [RHPCTL Command Reference](rhpctl-command-reference.md)

**Parent topic:** [Managing Gold Images and Working Copies](managing-gold-images-and-working-copies.md)
