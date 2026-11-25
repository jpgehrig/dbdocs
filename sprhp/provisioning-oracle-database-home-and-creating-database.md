This procedure provisions Oracle Database 12c release 2 (12.2) software and creates Oracle Database instances.

### Procedure

1.  From the Fleet Patching and Provisioning Server, provision the Oracle Database home software:
        $ rhpctl add workingcopy -image db12201 -path /u01/app/dbusr/product/12.2.0/db12201
          -client client_001 -oraclebase /u01/app/dbusr/ -workingcopy db122

    The command provisions the working copy `db122` to the specified path on the cluster `client_001`, from the image `db12201` .
2.  Create the database instance:
        $ rhpctl add database -workingcopy db122 -dbname db -dbtype RAC

    The command creates an Oracle RAC database instance `db` . You can use the `add database` command repeatedly to create more instances on the working copy.

Watch a video

**Parent topic:** [Fleet Patching and Provisioning Use Cases](fleet-patching-and-provisioning-use-cases.md)
