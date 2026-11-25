## Adding Gold Images for Fleet Patching and Provisioning

Create gold images of software home and store them on the Fleet Patching and Provisioning Server, to use later to provision Oracle homes.

### Before You Begin

The Oracle home to be used for creating the gold image can be on the Fleet Patching and Provisioning Server, or Fleet Patching and Provisioning Client, or any target machine that the Fleet Patching and Provisioning Server can communicate with.

### Procedure

Create gold images of Oracle homes in any of the following ways and store them on the Fleet Patching and Provisioning server:

1.  Import an image from an installed Oracle home on the Fleet Patching and Provisioning Server:
        rhpctl import image -image db19c -path /share/software/19c/dbhome -imagetype ORACLEDBSOFTWARE

    The gold image of `imagetype` Oracle Database 19c software is created and stored on the Fleet Patching and Provisioning Server.

    You can also create gold images of Oracle Grid Infrastructure or any other software by specifying `-imagetype` as `ORACLEGISOFTWARE`, `ORACLEGGSOFTWARE`, or `SOFTWARE` respectively.
2.  Import an image from an installed Oracle home on a Fleet Patching and Provisioning Client by running the following command from the Fleet Patching and Provisioning Client:
        rhpctl import image -image db19c -path /u01/app/dbusr/product/19.0.0/

    The command creates and adds the image `db19c` based on the local Oracle home installed in the specified path.

**Note:**

You cannot directly use images as software homes. Use images to create working copies of software homes.

**Parent topic:** [Oracle Fleet Patching and Provisioning Use Cases](fleet-patching-provisioning-use-cases.md)
