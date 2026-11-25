## Examples of How to Use the AutoUpgrade Console

The AutoUpgrade console provides a set of commands to monitor the progress of AutoUpgrade jobs. The console starts by default when you run the AutoUpgrade utility, and is enabled or disabled by the parameters `console` and `noconsole`.

In console mode, the AutoUpgrade console enables you to run commands to monitor specific aspects of your AutoUpgrade jobs while they are running on your systems.

**Note:**

If the AutoUpgrade console is exited out before it completes, then the jobs that are running stop, and the job that are scheduled do not start. For this reason, do not exit the console or stop the AutoUpgrade process until all of the AutoUpgrade jobs are completed.

Example 3-24 Example of How to Enable and Disable the AutoUpgrade Console

**Note:**

You can run only one AutoUpgrade instance at a time that is associated with a given configuration file.

In this example, AutoUpgrade is run in Analyze mode, using the configuration file in `noconsole` mode.

    java -jar autoupgrade.jar -config autoupgrade.cfg -mode analyze -noconsole

Using the `noconsole` mode turns off requirements for user input, so it is suitable for use with scripts.

In this example, AutoUpgrade is run in Analyze mode, and the console is turned on again with the `-console` option:

    java -jar autoupgrade.jar -config autoupgrade.cfg -mode analyze -console

Console user input is again resumed.

**Parent topic:** [Using AutoUpgrade for Oracle Database Upgrades](using-autoupgrade-oracle-database-upgrades.md)
