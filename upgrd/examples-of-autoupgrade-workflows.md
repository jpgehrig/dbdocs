## Examples of How to Use AutoUpgrade

To guide your upgrade, use the AutoUpgrade workflow example that matches your upgrade use case.

These examples are presented in a typical workflow sequence. To see how you can use the configuration file to run scripts with the `noconsole` parameter, see examples under "How to Use the AutoUpgrade Console."

- AutoUpgrade with Source and Target Database Homes on Same Server (Typical)
  When your Oracle Database Source and Target Oracle homes are installed on the same physical server, use this example.
- AutoUpgrade with Source and Target Database Homes on Different Servers
  When your Oracle Database Source and Target Oracle homes are located on different physical servers, you must complete tasks on both servers.

**Related Topics**

- [Examples of How to Use the AutoUpgrade Console](how-to-use-autoupgrade-console.md)

**Parent topic:** [Using AutoUpgrade for Oracle Database Upgrades](using-autoupgrade-oracle-database-upgrades.md)

### AutoUpgrade with Source and Target Database Homes on Same Server (Typical)

When your Oracle Database Source and Target Oracle homes are installed on the same physical server, use this example.

Context: Source and Target homes are on the same server.

To start the analysis, enter the following command.

    java -jar autoupgrade.jar -config config.txt -mode analyze

The command produces a report that indicates any error conditions that the command finds. Review the error conditions.

To start the deployment of the upgrade, enter the following command:

    java -jar autoupgrade.jar -config config.txt -mode deploy

**Parent topic:** Examples of How to Use AutoUpgrade

### AutoUpgrade with Source and Target Database Homes on Different Servers

When your Oracle Database Source and Target Oracle homes are located on different physical servers, you must complete tasks on both servers.

Context: Source and Target Oracle homes are on different physical servers.

To start the analysis, enter the following command.

    java -jar autoupgrade.jar -config config.txt -mode analyze

The command produces a report that indicates any error conditions that the command finds. Review the error conditions.

Because the source and target Oracle Database Oracle homes are on different servers, you run fixups on the source server, and the upgrade on the target server.

1.  Run fixups on the source server:

        java -jar autoupgrade.jar -config config.txt -mode fixups

2.  Complete the tasks to move the source Oracle Database from the source server to the target server.

3.  On the target server, start up the database in upgrade mode, and then run AutoUpgrade in `upgrade` mode:

        java -jar autoupgrade.jar -config config.txt -mode upgrade

**Parent topic:** Examples of How to Use AutoUpgrade
