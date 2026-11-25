Use the `chactl calibrate` command to create a new model that has greater sensitivity and accuracy.

The user-generated models are effective for Oracle Real Application Clusters (Oracle RAC) monitored systems in your operating environment as the user-generated models use calibration data from the target. Oracle Cluster Health Advisor adds the user-generated model to the list of available models and stores the new model in the Oracle Cluster Health Advisor repository.

If a model with the same name exists, then overwrite the old model with the new one by using the `-force` option.

### Key Performance and Workload Indicators

A set of metrics or Key Performance Indicators describe high-level constraints to the training data selected for calibration. This set consists of relevant metrics to describe performance goals and resource utilization bandwidth, for example, response times or CPU utilization.

The Key Performance Indicators are also operating system and database signals which are monitored, estimated, and associated with fault detection logic. Most of these Key Performance Indicators are also either predictors, that is, their state is correlated with the state of other signals, or predicted by other signals. The fact that the Key Performance Indicators correlate with other signals makes them useful as filters for the training or calibration data.

The Key Performance Indicators ranges are used in the `query calibrate` and `calibrate` commands to filter out data points.

The following Key Performance Indicators are supported for database:

- `CPUPERCENT` - CPU utilization - Percent

- `IOREAD` - Disk read - Mbyte/sec

- `DBTIMEPERCALL` - Database time per user call - usec/call

- `IOWRITE` - Disk write - Mbyte/sec

- `IOTHROUGHPUT` - Disk throughput - IO/sec

The following Key Performance Indicators are supported for cluster:

- `CPUPERCENT` - CPU utilization - Percent

- `IOREAD` - Disk read - Mbyte/sec

- `IOWRITE` - Disk write - Mbyte/sec

- `IOTHROUGHPUT` - Disk throughput - IO/sec

### Syntax

    chactl calibrate {cluster|database -db db_unique_name} -model model_name
    [-force] [-timeranges 'start=time_stamp,end=time_stamp,...']
    [-kpiset 'name=kpi_name min=val max=val,...' ][-help]

Specify timestamp in the `YYYY-MM-DD HH24:MI:SS` format.

### Examples

    chactl calibrate database -db oracle -model weekday
    -timeranges 'start=start=2016-09-09 16:00:00,end=2016-09-09 23:00:00'

    chactl calibrate database -db oracle -model weekday
    -timeranges 'start=start=2016-09-09 16:00:00,end=2016-09-09 23:00:00'
    -kpiset 'name=CPUPERCENT min=10 max=60'

### Error Messages

Error: `input string “xc#? %” is misconstructed`

Description: Confirm if the given model name exists with `Warning: ``model_name`` already exists, please use [-force]` message.

Error: `start_time`` and/or ``end_time`` are misconstructed`

Description: Input time specifiers are badly constructed.

Error: `no sufficient calibration data exists for the specified period, please reselect another period`

Description: Evaluator couldn’t find enough calibration data.

**Parent topic:** [chactl Command Reference](chactl-command-reference.md)
