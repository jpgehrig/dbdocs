In-memory features provide techniques for parallel execution.

This section discusses in-memory parallel execution.

- Buffer Cache Usage in Parallel Execution

- Automatic Big Table Caching

### 8.3.1 Buffer Cache Usage in Parallel Execution

By default parallel execution does not use the SGA (buffer cache) to cache the scanned blocks unless the object is very small or is declared as CACHE.

In-Memory Parallel Execution, enabled by setting the parameter `PARALLEL_DEGREE_POLICY` is set to `AUTO`, enables parallel statements to leverage the SGA to cache object blocks. Oracle Database decides if an object that is accessed using parallel execution would benefit from being cached in the SGA. The decision to cache an object is based on a well-defined set of heuristics including the size of the object and frequency on which it is accessed. In an Oracle Real Applications Cluster (Oracle RAC) environment, Oracle Database maps pieces of the object into each of the buffer caches on the active instances. By creating this mapping, Oracle Database automatically knows which buffer cache to access to find different parts or pieces of the object. Using this information, Oracle Database prevents multiple instances from reading the same information from disk over and over again, thus maximizing the amount of memory that can cache objects. It does this by using PX servers on the instances where the blocks are cached.

If the size of the object is larger than a specific threshold value based on the total size of the buffer cache (single instance) or the size of the buffer cache multiplied by the number of active instances in an Oracle RAC cluster, then the object is read using direct-path reads and not cached in the SGA.

### 8.3.2 Automatic Big Table Caching

Automatic big table caching integrates queries with the buffer cache to enhance the in-memory query capabilities of Oracle Database, in both single instance and Oracle RAC environments.

In Oracle Real Application Clusters (Oracle RAC) environments, this feature is supported only with parallel queries. In single instance environments, this feature is supported with both parallel and serial queries.

The cache section reserved for the big table cache is used for caching data for table scans. While the big table cache is primarily designed to enhance performance for data warehouse workloads, it also improves performance in Oracle Database running mixed workloads.

Automatic big table caching uses temperature and object based algorithms to track medium and big tables. Oracle does cache very small tables, but automatic big table caching does not track these tables.

To enable automatic big table caching for serial queries, you must set a value (percentage) for the `DB_BIG_TABLE_CACHE_PERCENT_TARGET` initialization parameter. Additionally, you must set the `PARALLEL_DEGREE_POLICY` initialization parameter to `AUTO` or `ADAPTIVE` to enable parallel queries to use automatic big table caching. In Oracle RAC environments, automatic big table caching is only supported in parallel queries so both settings are required.

If a large table is approximately the size of the combined size of the big table cache of all instances, then the table is partitioned and cached, or mostly cached, on all instances. An in-memory query could eliminate most disk reads for queries on the table, or the database could intelligently read from disk only for that portion of the table that does not fit in the big table cache. If the big table cache cannot cache all the tables to be scanned, only the most frequently accessed table are cached, and the rest are read through direct read automatically.

The `DB_BIG_TABLE_CACHE_PERCENT_TARGET` parameter determines the percentage of the buffer cache size used for scans. If `DB_BIG_TABLE_CACHE_PERCENT_TARGET` is set to `80` (%), then `80` (%) of the buffer cache is used for scans and the remaining `20` (%) is used for OLTP workloads.

The `DB_BIG_TABLE_CACHE_PERCENT_TARGET` parameter is only enabled in an Oracle RAC environment if `PARALLEL_DEGREE_POLICY` is set to `AUTO` or `ADAPTIVE`. The default for `DB_BIG_TABLE_CACHE_PERCENT_TARGET` is `0` (disabled) and the upper limit is `90` (%) reserving at least 10% buffer cache for usage besides table scans. When the value is `0`, in-memory queries run with the existing least recently used (LRU) mechanism. You can adjust the `DB_BIG_TABLE_CACHE_PERCENT_TARGET` parameter dynamically.

Use the following guidelines when setting the `DB_BIG_TABLE_CACHE_PERCENT_TARGET` parameter:

- If you do not enable automatic degree of parallelism (DOP) in an Oracle RAC environment, then you should not set this parameter because the big table cache section is not used in that situation.

- When setting this parameter, you should consider the workload mix: how much of the workload is for OLTP; insert, update, and random access; and how much of the workload involves table scans. Because data warehouse workloads often perform large table scans, you may consider giving big table cache section a higher percentage of buffer cache space for data warehouses.

- This parameter can be dynamically changed if the workload changes. The change could take some time depending on the current workload to reach the target, because buffer cache memory might be actively used at the time.

When `PARALLEL_DEGREE_POLICY` is set to `AUTO` or `ADAPTIVE`, additional object-level statistics for a data warehouse load and scan buffers are added to represent the number of parallel queries (PQ) scans on the object on the particular (helper) instance.

The `V$BT_SCAN_CACHE` and `V$BT_SCAN_OBJ_TEMPS` views provide information about the big table cache.

**See Also:**

- [Oracle Database Administrator’s Guide](../admin/managing-memory.md) for information about automatic big table caching

- [Oracle Database Concepts](../cncpt/memory-architecture.md) for information about automatic big table caching

- [Oracle Database Reference](../refrn/DB_BIG_TABLE_CACHE_PERCENT_TARGET.md) for information about the `DB_BIG_TABLE_CACHE_PERCENT_TARGET` initialization parameter

- [Oracle Database Reference](../refrn/dynamic-performance-v-views-1.md) for information about the `V$BT_SCAN*` views
