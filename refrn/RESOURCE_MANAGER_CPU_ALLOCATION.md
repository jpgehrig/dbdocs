## 1.312 RESOURCE_MANAGER_CPU_ALLOCATION

`RESOURCE_MANAGER_CPU_ALLOCATION` specifies the number of CPUs that the Resource Manager should use. The Resource Manager controls how a system's CPUs are utilized by its database's sessions.

**Note:**

The `RESOURCE_MANAGER_CPU_ALLOCATION` parameter is deprecated and is retained only for backward compatibility. Furthermore, starting with Oracle Database 19c, Release Update 19.10, the value of this parameter is ignored and its default value is set to `0`. Use the `CPU_COUNT` parameter instead.

| Property            | Description                                                  |
|:--------------------|:-------------------------------------------------------------|
| Parameter type      | Integer                                                      |
| Default value       | The number of logical CPUs reported by the operating system. |
| Modifiable          | `ALTER SYSTEM`                                               |
| Modifiable in a PDB | No                                                           |
| Range of values     | `0` to operating system-specific                             |
| Basic               | No                                                           |

The Resource Manager schedules database sessions on the CPUs according to a resource plan that has been configured and enabled by the DBA. Normally, the Resource Manager schedules enough database sessions to keep all CPUs utilized. However, in some scenarios, a DBA may only want to schedule enough database sessions to keep a subset of the CPUs utilized.

**See Also:**

"[CPU_COUNT](CPU_COUNT.md)"
