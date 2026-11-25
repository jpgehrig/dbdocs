Provision Oracle Grid Infrastructure software on two nodes that do not currently have a Grid home, and then configure Oracle Grid Infrastructure to form a multi-node Oracle Grid Infrastructure installation.

### Before You Begin

Provide configuration details for storage, network, users and groups, and node information for installing Oracle Grid Infrastructure in a response file. You can store the response file in any location on the Fleet Patching and Provisioning Server.

You can provision an Oracle Standalone Cluster, Oracle Application Clusters, Oracle Domain Services Cluster, or Oracle Member Clusters. Ensure that the response file has the required cluster configuration details.

Ensure that you have storage, network, and operating system requirements configured as stated in the Oracle Grid Infrastructure Installation Guide.

### Procedure

- From the Fleet Patching and Provisioning Server, run the command:
      $ rhpctl add workingcopy -workingcopy GI122 -image GI_HOME_12201 –responsefile /u01/app/rhpinfo/GI_12201_install.rsp {authentication_option}

  `GI122` is the working copy based on the image `GI_HOME_12201`

  `/u01/app/rhpinfo/GI_12201_install.rsp` is the response file location.

  Cluster Verification Utility checks for preinstallation configuration as per requirements. Fleet Patching and Provisioning configures Oracle Grid Infrastructure.

Oracle Grid Infrastructure 12c release 2 is provisioned as per the settings in the same response file.

During provisioning, if an error occurs, the procedure stops and allows you to fix the error. After fixing the error, you can resume the provisioning operation from where it last stopped.

Watch a video

**Parent topic:** [Fleet Patching and Provisioning Use Cases](fleet-patching-and-provisioning-use-cases.md)
