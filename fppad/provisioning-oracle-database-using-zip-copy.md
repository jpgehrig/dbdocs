## Provisioning an Oracle Database Using Zip Copy

Starting with Oracle Grid Infrastructure 19c Release Update (19.11), Oracle FPP allows you to install the gold images without transferring them to the destination host.

This feature is known as zipcopy and you can use it to provision Oracle Database homes. You can also use this feature to provision Oracle Grid Infrastructure homes that exists on the destination hosts, but not to provision new Oracle Grid Infrastructure homes.

The ZipCopy feature has a requirement of shared storage between the Oracle FPP Server and the targets, including Oracle FPP Client and `rhpclient`-less targets. When importing an image to the Oracle FPP Server, you must provide to a zip file location of the Oracle Home software as input. You also need to specify a mount path on which this zip file is accessible on all targets where you want to provision this image. When provisioning using the ZipCopy feature, the Oracle FPP Server uses the zip file of the image already available on the mount path locally on the target hosts, instead of the transferring the software from the Oracle FPP server to the target hosts.

1.  Import a new image from a zip file using the `-zip` and `-location` parameters.
        $ rhpctl import image -image DB_1914 -zip /orastage/db1914000.zip -location /orastage/db1914000.zip

    - `-zip` specifies the location from which you can import the image to the Oracle FPP server.
    - `-location` specifies a location where the image is available on the destination host as a zip file. Oracle FPP does not copy the zip file from the Oracle FPP server to the destination host.

    **Note:**

    You can make the image zip files available on the destination hosts using either local or shared storage.
2.  Inspect the images on your Oracle Fleet Patching and Provisioning Server.
        $ rhpctl query image -image DB_1914

    Make sure the `Location on target` value is available in the image query results.
3.  Provision the working copy created using the zip file.
        $ rhpctl add workingcopy -image DB_1914 -workingcopy fppc01_DB_1914 -user oracle -oraclebase /u01/app/oracle
        -client  dbSyslrfe3mla -path /u01/app/oracle/product/19.0.0.0/dbhome_2 -localmount -location /orastage/db1914000.zip
        -groups osdba=dba,osoper=dbaoper,osdg=dba,osbackup=dba,oskm=dba,osrac=dba -storagetype LOCAL

    `fppc01_DB_1914` is the working copy based on the image `DB_1914`.

**Parent topic:** [Oracle Fleet Patching and Provisioning Use Cases](fleet-patching-provisioning-use-cases.md)
