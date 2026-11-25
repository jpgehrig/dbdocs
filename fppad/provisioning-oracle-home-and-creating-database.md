## Provisioning an Oracle Database Home and Creating a Database

This procedure provisions Oracle Database 19c software and creates Oracle Database instances.

### Procedure

1.  From the Fleet Patching and Provisioning Server, provision the Oracle Database home software:
        $ rhpctl add workingcopy -image db19c -path /u01/app/dbusr/product/19.0.0/db19c
          -client client_001 -oraclebase /u01/app/dbusr/ -workingcopy db19wc

    The command provisions the working copy `db19wc` to the specified path on the cluster `client_001`, from the image `db19c`.
2.  Create the database instance:
        $ rhpctl add database -workingcopy db19wc -dbname db -dbtype RAC

    The command creates an Oracle RAC database instance `db` . You can use the `add database` command repeatedly to create more instances on the working copy.

Watch a video

**Parent topic:** [Oracle Fleet Patching and Provisioning Use Cases](fleet-patching-provisioning-use-cases.md)
