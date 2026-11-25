## 120  DBMS_ODCI

`DBMS_ODCI` package contains a single user function related to the use of Data Cartridges.

This chapter contains the following topic:

- Summary of DBMS_ODCI Subprograms

**See Also:**

- [Oracle Database Data Cartridge Developer's Guide](../addci/introduction-to-data-cartridges.md)

### 120.1 Summary of DBMS_ODCI Subprograms

The `DBMS_ODCI` package has one subprogram, the `ESTIMATE_CPU_UNITS` function.

Table 120-1 DBMS_ODCI Package Subprograms

| Subprogram                  | Description                                                                                                               |
|:----------------------------|:--------------------------------------------------------------------------------------------------------------------------|
| ESTIMATE_CPU_UNITS Function | Returns the approximate number of CPU instructions (in thousands) corresponding to a specified time interval (in seconds) |

#### 120.1.1 ESTIMATE_CPU_UNITS Function

This function returns the approximate number of CPU instructions (in thousands) corresponding to a specified time interval (in seconds). This information can be used to associate the CPU cost with a user-defined function for the extensible optimizer.

The function takes as input the elapsed time of the user function, measures CPU units by multiplying the elapsed time by the processor speed of the machine, and returns the approximate number of CPU instructions that should be associated with the user function. For a multiprocessor machine, `ESTIMATE_CPU_UNITS` considers the speed of a single processor.

##### Syntax

    DBMS_ODCI.ESTIMATE_CPU_UNITS(
       elapsed_time     NUMBER)
      RETURN NUMBER;

##### Parameters

| Parameter      | Description                                                      |
|:---------------|:-----------------------------------------------------------------|
| `elapsed_time` | The elapsed time in seconds that it takes to execute a function. |

##### Usage Notes

When associating CPU cost with a user-defined function, use the full number of CPU units rather than the number of thousands of CPU units returned by `ESTIMATE_CPU_UNITS`; multiply the number returned by `ESTIMATE_CPU_UNITS` by 1,000.
