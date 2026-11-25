Describes the overview of initialization parameters.

[Oracle Database Reference](../refrn/initialization-parameters.md) describes default values for many initialization parameters as being operating system-specific. However, not all parameters that it describes as having operating system-specific values affect Windows. In these cases, Windows uses either the default value set in the Oracle Database kernel or does not use the parameter. Initialization Parameters Without Windows-Specific Values describes these initialization parameters:

Table 15-1 Initialization Parameters Without Windows-Specific Values

| Parameter                  | Description                                                                                                                                                                                                           |
|:---------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `AUDIT_FILE_DEST `         | Supported on Windows to write XML format audit files                                                                                                                                                                  |
| `DB_WRITER_PROCESSES `     | Supported, but typically unnecessary due to Windows asynchronous I/O capabilities                                                                                                                                     |
| `COMPATIBLE_NO_RECOVERY `  | Uses default value set in Oracle Database kernel (no Windows-specific value)                                                                                                                                          |
| `BACKGROUND_CORE_DUMP `    | Specifies whether Oracle Database includes SGA in core file for Oracle Database background processes                                                                                                                  |
| `SHADOW_CORE_DUMP `        | Specifies whether Oracle Database includes SGA in core file for foreground (client) processes                                                                                                                         |
| `CORE_DUMP_DEST `          | Specifies directory where Oracle Database dumps core files                                                                                                                                                            |
| `CPU_COUNT`                | Oracle Database automatically sets value to the number of processors available for your Oracle Database instance                                                                                                      |
| `HI_SHARED_MEMORY_ADDRESS` | Not applicable to Windows                                                                                                                                                                                             |
| `SHARED_MEMORY_ADDRESS`    | Not applicable to Windows                                                                                                                                                                                             |
| `LARGE_POOL_SIZE`          | Uses maximum value limited by available memory                                                                                                                                                                        |
| `LOG_BUFFER`               | Starter database uses value set in Oracle Database kernel (no Windows-specific value). The Custom database creation option of Database Configuration Assistant enables you to customize the value for this parameter. |
| `SPIN_COUNT`               | Uses default value set in Oracle Database kernel (no Windows-specific value)                                                                                                                                          |

**Parent topic:** [Oracle Database Specifications for Windows](oracle-database-specifications-for-windows.md)
