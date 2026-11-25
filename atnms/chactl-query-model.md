Use the `chactl query model` command to list all Oracle Cluster Health Advisor models or to view detailed information about a specific Oracle Cluster Health Advisor model.

### Syntax

    chactl query model [-name model_name [-verbose]][-help]

### Examples

- To list all base Oracle Cluster Health Advisor models:

      $ chactl query model
      Models: MOD1, MOD2, MOD3, MOD4, MOD5, MOD6, MOD7

      $ chactl query model -name weekday
      Model: weekday
      Target Type: DATABASE
      Version: 12.2.0.1_0
      OS Calibrated on: Linux amd64
      Calibration Target Name: prod
      Calibration Date: 2016-09-10 12:59:49
      Calibration Time Ranges: start=2016-09-09 16:00:00,end=2016-09-09 23:00:00
      Calibration KPIs: not specified

- To view detailed information, including calibration metadata, about the specific Oracle Cluster Health Advisor model:

      $ chactl query model -name MOD5 -verbose
      Model: MOD5
      CREATION_DATE:          Jan 10,2016 10:10
      VALIDATION_STATUS:      Validated
      DATA_FROM_TARGET :      inst72, inst75
      USED_IN_TARGET :        inst76, inst75, prodDB, evalDB-evalSP
      CAL_DATA_FROM_DATE:     Jan 05,2016 10:00
      CAL_DATA_TO_DATE:       Jan 07,2016 13:00
      CAL_DATA_FROM_TARGETS   inst73, inst75
      ...

**Parent topic:** [chactl Command Reference](chactl-command-reference.md)
