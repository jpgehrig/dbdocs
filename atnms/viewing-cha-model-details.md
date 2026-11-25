Use the `chactl query model` command to view the model details.

1.  You can review the details of an Oracle Cluster Health Advisor model at any time using the `chactl query model` command.
    For example:
        $ chactl query model –name weekday
        Model: weekday
        Target Type: CLUSTERWARE
        Version: OS12.2_V14_0.9.8
        OS Calibrated on: Linux amd64
        Calibration Target Name: MYCLUSTER
        Calibration Date: 2016-07-05 01:13:49
        Calibration Time Ranges: start=2016-07-03 20:50:00,end=2016-07-04 15:00:00
        Calibration KPIs: not specified

    You can also rename, import, export, and delete the models.

**Parent topic:** [Proactively Detecting and Diagnosing Performance Issues for Oracle RAC](purpose-cluster-health-advisor.md)
