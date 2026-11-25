## 1.251 OPTIMIZER_IGNORE_PARALLEL_HINTS

`OPTIMIZER_IGNORE_PARALLEL_HINTS` enables embedded parallel hints to be ignored.

| Property            | Description                                         |
|:--------------------|:----------------------------------------------------|
| Parameter type      | Boolean                                             |
| Default value       | `FALSE`                                             |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM`                     |
| Modifiable in a PDB | Yes                                                 |
| Range of values     | `true | false`                                      |
| Basic               | No                                                  |
| Oracle RAC          | Different values can be set on different instances. |

When this parameter is set to `TRUE`, the optimizer ignores embedded parallel hints.

The default value is `FALSE`. When this parameter’s value is `FALSE`, the optimizer does not ignore parallel embedded hints.
