## 1.38 CLIENT_RESULT_CACHE_LAG

`CLIENT_RESULT_CACHE_LAG` specifies the maximum time (in milliseconds) since the last round trip to the server, before which the OCI client query execute makes a round trip to get any database changes related to the queries cached on the client.

| Property            | Description                           |
|:--------------------|:--------------------------------------|
| Parameter type      | Big integer                           |
| Syntax              | `CLIENT_RESULT_CACHE_LAG = ``integer` |
| Default value       | `3000`                                |
| Modifiable          | No                                    |
| Modifiable in a PDB | Yes                                   |
| Range of values     | `0` to operating system-dependent     |
| Basic               | No                                    |

**See Also:**

[Oracle Call Interface Programmer's Guide](../lnoci/performance-topics.md) for more information about the client query cache feature
