Enabling trace levels enables you to collect enough diagnostics to diagnose the cause of the problem.

Oracle Support asks you to enable certain trace levels when reproducing a problem.

Oracle Trace File Analyzer makes it easy to enable and then disable the correct trace levels. Use the `dbglevel` option to set the trace level.

You can find the required trace level settings grouped by problem trace profiles.

### To set trace levels:

1.  To set a trace profile:
        tfactl dbglevel –set profile
2.  To list all available profiles:
        tfactl dbglevel –help

- tfactl dbglevel
  Use the `tfactl dbglevel` command to set Oracle Grid Infrastructure trace levels.

**Parent topic:** [On-demand Analysis and Diagnostic Collection](ondemand-diagnostic-collection.md)

### 15.8.1 tfactl dbglevel

Use the `tfactl dbglevel` command to set Oracle Grid Infrastructure trace levels.

#### Syntax

    tfactl [run] dbglevel
    [ {-set|-unset} profile_name
    -dependency [dep1,dep2,...|all]
    -dependency_type [type1,type2,type3,...|all]
    | {-view|-drop} profile_name
    | -lsprofiles
    | -lsmodules
    | -lscomponents [module_name]
    | -lsres
    | -create profile_name [ -desc description
    | [-includeunset] [-includetrace]
    | -debugstate | -timeout time ]
    | -modify profile_name [-includeunset] [-includetrace]
    | -getstate [ -module module_name ]
    | -active [profile_name]
    | -describe [profile_name] ] ]

#### Parameters

Table 15-5 tfactl dbglevel Command Parameters

| Parameter         | Description                                                                   |
|:------------------|:------------------------------------------------------------------------------|
| `profile_name`    | Specify the name of the profile.                                              |
| `active`          | Displays the list of active profiles.                                         |
| `set`             | Sets the trace or log levels for the profile specified.                       |
| `unset`           | Unsets the trace or log levels for the profile specified.                     |
| `view`            | Displays the trace or log entries for the profile specified.                  |
| `create`          | Creates a profile.                                                            |
| `drop`            | Drops the profile specified.                                                  |
| `modify`          | Modifies the profile specified.                                               |
| `describe`        | Describes the profiles specified.                                             |
| `lsprofiles`      | Lists all the available profiles.                                             |
| `lsmodules`       | Lists all the discovered CRS modules.                                         |
| `lscomponents`    | Lists all the components associated with the CRS module.                      |
| `lsres`           | Lists all the discovered CRS resources.                                       |
| `getstate`        | Displays the current trace or log levels for the CRS components or resources. |
| `module`          | Specify the CRS module.                                                       |
| `dependency`      | Specify the dependencies to consider, start, or stop dependencies, or both.   |
| `dependency_type` | Specify the type of dependencies to be consider.                              |
| `debugstate`      | Generates a System State Dump for all the available levels.                   |
| `includeunset`    | Adds or modifies an unset value for the CRS components or resources.          |
| `includetrace`    | Adds or modifies a trace value for the CRS components.                        |

**WARNING:**

Set the profiles only at the direction of Oracle Support.

**Parent topic:** Changing Oracle Grid Infrastructure Trace Levels
