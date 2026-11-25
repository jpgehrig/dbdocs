Oracle Cluster Health Advisor repository stores the historical records of cluster host problems, database problems, and associated metric evidence, along with models.

The Oracle Cluster Health Advisor repository is used to diagnose and triage periodic problems. By default, the repository is sized to retain data for 16 targets (nodes and database instances) for 72 hours. If the number of targets increase, then the retention time is automatically decreased. Oracle Cluster Health Advisor generates warning messages when the retention time goes below 72 hours, and stops monitoring and generates a critical alert when the retention time goes below 24 hours.

Use CHACTL commands to manage the repository and set the maximum retention time.

1.  To retrieve the repository details, use the following command:

        $ chactl query repository

    For example, running the command mentioned earlier shows the following output:
        specified max retention time(hrs) : 72
        available retention time(hrs)     : 212
        available number of entities      : 2
        allocated number of entities      : 0
        total repository size(gb)         : 2.00
        allocated repository size(gb)     : 0.07

2.  To set the maximum retention time in hours, based on the current number of targets being monitored, use the following command:

        $ chactl set maxretention -time number_of_hours

    For example:
        $ chactl set maxretention -time 80
        max retention successfully set to 80 hours

    **Note:**

    The `maxretention` setting limits the oldest data retained in the repository, but is not guaranteed to be maintained if the number of monitored targets increase. In this case, if the combination of monitored targets and number of hours are not sufficient, then increase the size of the Oracle Cluster Health Advisor repository.

3.  To increase the size of the Oracle Cluster Health Advisor repository, use the `chactl resize repository` command.

    For example, to resize the repository to support 32 targets using the currently set maximum retention time, you would use the following command:

        $ chactl resize repository –entities 32
        repository successfully resized for 32 targets

**Parent topic:** [Proactively Detecting and Diagnosing Performance Issues for Oracle RAC](purpose-cluster-health-advisor.md)
