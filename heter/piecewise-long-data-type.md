The gateways now manage the data piecewise between the agent and Oracle Database, eliminating the large memory and network bandwidth requirements.

Earlier versions of gateways had limited support for the `LONG` data type. `LONG` is an Oracle data type that can store up to 2 GB of character data or raw data (`LONG RAW`). These earlier versions restricted the amount of `LONG` data to 4 MB because they treated `LONG` data as a single piece. This caused memory and network bandwidth restrictions on the size of the data that could be handled. Current gateways extended the functionality to support the full 2 GB of heterogeneous `LONG` data.

The `HS_LONG_PIECE_TRANSFER_SIZE` Heterogeneous Services initialization parameter can be used to set the size of the transferred pieces. For example, consider retrieving 2 GB of `LONG` data from a heterogeneous source. A smaller piece requires less memory, but it requires more round-trips to retrieve all the data. A larger piece requires fewer round-trips, but it requires a larger amount of memory to store the intermediate pieces internally. The initialization parameter can be used to tune a system for the best performance, that is, for the best trade-off between round-trips and memory requirements. If the initialization parameter is not set, the system uses 64 KB as the default piece size.

**Note:**

Do not confuse this feature with piecemeal operations on `LONG` data on the client side. Piecemeal fetch and insert operations on the client side worked with the earlier versions of the gateways, and they continue to do so. The only difference on the client side is that, where earlier versions of the gateways were able to fetch a maximum of 4 MB of `LONG` data, now they can retrieve the 2 GB of `LONG` data. This is a significant improvement because 4 MB is only 0.2 percent of the data type's capacity.

**Parent topic:** [Features of Oracle Database Gateways](oracle-database-gateways-features.md)
