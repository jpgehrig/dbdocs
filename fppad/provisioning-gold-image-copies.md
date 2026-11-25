## Provisioning Copies of Gold Images

Use RHPCTL to provision copies of gold images to Fleet Patching and Provisioning Servers, Clients, and targets.

After you create and import a gold image, you can provision software by adding a copy of the gold image (called a working copy) on the Fleet Patching and Provisioning Server, on a Fleet Patching and Provisioning Client, or a target. You can run the software provisioning command on either the Server or a Client.

**Note:**

Starting with Oracle Grid Infrastructure 19c Release Update (19.11), you can add working copy as Zip files by using the `-location` parameter and make the zip files available either on a local or a shared storage at the specified location on all the targets. You must specify the `-localmount` parameter to avoid transferring the image and to decompress the zip file on the local storage.

- To create a working copy on the Fleet Patching and Provisioning Server:
      $ rhpctl add workingcopy -workingcopy working_copy_name -image image_name
- To create a working copy in a local file system on a Fleet Patching and Provisioning Client:
      $ rhpctl add workingcopy -workingcopy working_copy_name -image image_name
         -storagetype LOCAL -path path_to_software_home
- To create a working copy on a Fleet Patching and Provisioning Client from the Fleet Patching and Provisioning Server:
      $ rhpctl add workingcopy -workingcopy working_copy_name -image image_name
         -client client_cluster_name
- To create a working copy on the Fleet Patching and Provisioning Server using the image file that you imported with the `-zip` option:
      $ rhpctl add workingcopy -image image_name -workingcopy working_copy_name -user oracle
      -oraclebase Oracle_base -targetnode target_node_name -path path_to_software_home
      -localmount -location location_on_target_host_where_image_is_available -sudouser opc -sudopath /bin/sudo -storagetype LOCAL

  The `-localmount` option instructs the Oracle FPP server to skip the copy operation. The `-location` option specifies where the zip image is available on the target host. By default, Oracle FPP uses the location used to import the image.

**Note:**

- The directory you specify in the `-path` parameter must be empty.

- You can re-run the provisioning command in case of an interruption or failure due to system or user errors. After you fix the reported errors, re-run the command and it will resume from the point of failure.

<!-- -->

- [Storage Options for Provisioned Software](storage-options-for-provisioned-software.md)
  Choose one of two storage options where Fleet Patching and Provisioning stores working copies of gold images.
- [Provisioning for a Different User](provisioning-for-a-different-user.md)
  If you want a different user to provision software other than the user running the command, then use the `-user` parameter of the `rhpctl add workingcopy` command.
- [User Group Management in Fleet Patching and Provisioning](user-group-management-in-oracle-fpp.md)
  When you create a working copy of a gold image as part of a move or upgrade operation, Fleet Patching and Provisioning configures the operating system groups in the new working copy to match those of the source software home (either the unmanaged or the managed home from which you move or upgrade).

**Related Topics**

- [Storage Options for Provisioned Software](storage-options-for-provisioned-software.md)

**Parent topic:** [Managing Gold Images and Working Copies](managing-gold-images-and-working-copies.md)
