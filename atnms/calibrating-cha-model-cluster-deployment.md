As shipped with default node and database models, Oracle Cluster Health Advisor is designed not to generate false warning notifications.

You can increase the sensitivity and accuracy of the Oracle Cluster Health Advisor models for a specific workload using the `chactl calibrate` command.

Oracle recommends that a minimum of 6 hours of data be available and that both the cluster and databases use the same time range for calibration.

The `chactl calibrate` command analyzes a user-specified time interval that includes all workload phases operating normally. This data is collected while Oracle Cluster Health Advisor is monitoring the cluster and all the databases for which you want to calibrate.

1.  To check if sufficient data is available, run the `query calibration`  command.
    If 720 or more records are available, then Oracle Cluster Health Advisor successfully performs the calibration. The calibration function may not consider some data records to be normally occurring for the workload profile being used. In this case, filter the data by using the `KPISET`  parameters in both the `query calibration` command and the `calibrate` command.

    For example:
        $ chactl query calibration -db oltpacdb -timeranges
        'start=2016-07-26 01:00:00,end=2016-07-26 02:00:00,start=2016-07-26 03:00:00,end=2016-07-26 04:00:00'
        -kpiset 'name=CPUPERCENT min=20 max=40, name=IOTHROUGHPUT min=500 max=9000' -interval 2
2.  Start the calibration and store the model under a user-specified name for the specified date and time range.
    For example:
        $ chactl calibrate cluster –model weekday –timeranges ‘start=2016-07-03 20:50:00,end=2016-07-04 15:00:00’

    After completing the calibration, Oracle Cluster Health Advisor automatically stores the new model in GIMR.
3.  Use the new model to monitor the cluster as follows:
    For example:
        $ chactl monitor cluster –model weekday

Example 3-2 Output for the chactl query calibrate command

    Database name : oltpacdb
    Start time : 2016-07-26 01:03:10
    End time : 2016-07-26 01:57:25
    Total Samples : 120
    Percentage of filtered data : 8.32%
    The number of data samples may not be sufficient for calibration.

    1) Disk read (ASM) (Mbyte/sec)

    MEAN      MEDIAN    STDDEV    MIN       MAX
    4.96      0.20      8.98      0.06      25.68

    <25       <50       <75       <100      >=100
    97.50%    2.50%     0.00%     0.00%     0.00%

    2) Disk write (ASM) (Mbyte/sec)

    MEAN      MEDIAN    STDDEV    MIN       MAX
    27.73     9.72      31.75     4.16      109.39

    <50       <100      <150      <200      >=200
    73.33%    22.50%    4.17%     0.00%     0.00%

    3) Disk throughput (ASM) (IO/sec)

    MEAN      MEDIAN    STDDEV    MIN       MAX
    2407.50   1500.00   1978.55   700.00    7800.00

    <5000     <10000    <15000    <20000    >=20000
    83.33%    16.67%    0.00%     0.00%     0.00%

    4) CPU utilization (total) (%)

    MEAN      MEDIAN    STDDEV    MIN       MAX
    21.99     21.75     1.36      20.00     26.80

    <20       <40       <60       <80       >=80
    0.00%     100.00%   0.00%     0.00%     0.00%

    5) Database time per user call (usec/call)

    MEAN      MEDIAN    STDDEV    MIN       MAX
    267.39    264.87    32.05     205.80    484.57

    <10000000  <20000000  <30000000  <40000000  <50000000  <60000000  <70000000  >=70000000
    100.00%   0.00%     0.00%     0.00%     0.00%     0.00%     0.00%     0.00%

    Database name : oltpacdb
    Start time : 2016-07-26 03:00:00
    End time : 2016-07-26 03:53:30
    Total Samples : 342
    Percentage of filtered data : 23.72%
    The number of data samples may not be sufficient for calibration.

    1) Disk read (ASM) (Mbyte/sec)

    MEAN      MEDIAN    STDDEV    MIN       MAX
    12.18     0.28      16.07     0.05      60.98

    <25       <50       <75       <100      >=100
    64.33%    34.50%    1.17%     0.00%     0.00%

    2) Disk write (ASM) (Mbyte/sec)

    MEAN      MEDIAN    STDDEV    MIN       MAX
    57.57     51.14     34.12     16.10     135.29

    <50       <100      <150      <200      >=200
    49.12%    38.30%    12.57%    0.00%     0.00%

    3) Disk throughput (ASM) (IO/sec)

    MEAN      MEDIAN    STDDEV    MIN       MAX
    5048.83   4300.00   1730.17   2700.00   9000.00

    <5000     <10000    <15000    <20000    >=20000
    63.74%    36.26%    0.00%     0.00%     0.00%

    4) CPU utilization (total) (%)

    MEAN      MEDIAN    STDDEV    MIN       MAX
    23.10     22.80     1.88      20.00     31.40

    <20       <40       <60       <80       >=80
    0.00%     100.00%   0.00%     0.00%     0.00%

    5) Database time per user call (usec/call)

    MEAN      MEDIAN    STDDEV    MIN       MAX
    744.39    256.47    2892.71   211.45    45438.35

    <10000000  <20000000  <30000000  <40000000  <50000000  <60000000  <70000000  >=70000000
    100.00%   0.00%     0.00%     0.00%     0.00%     0.00%     0.00%     0.00%

**Related Topics**

- [chactl calibrate](chactl-calibrate.md)
- [chactl query calibration](chactl-query-calibration.md)
- [chactl Command Reference](chactl-command-reference.md)

**Parent topic:** [Proactively Detecting and Diagnosing Performance Issues for Oracle RAC](purpose-cluster-health-advisor.md)
