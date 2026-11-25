You should perform the following types of monitoring when trying to diagnose parallel execution performance problems.

These types of monitoring include:

- Monitoring Parallel Execution Performance with Dynamic Performance Views

- Monitoring Session Statistics

- Monitoring System Statistics

- Monitoring Operating System Statistics

**See Also:**

[Oracle Database Reference](../refrn/dynamic-performance-views.md) for information about dynamic views

### 8.7.1 Monitoring Parallel Execution Performance with Dynamic Performance Views

You can monitor parallel execution performance with dynamic performance views.

Oracle Database real-time monitoring feature enables you to monitor the performance of SQL statements while they are executing. SQL monitoring is automatically started when a SQL statement runs parallel or when it has consumed at least 5 seconds of CPU or I/O time for a single execution.

After your system has run for a few days, you should monitor parallel execution performance statistics to determine whether your parallel processing is optimal. Do this using any of the views discussed in this section.

In Oracle Real Application Clusters, global versions of the views described in this section aggregate statistics from multiple instances. The global views have names beginning with `G`, such as `GV$FILESTAT` for `V$FILESTAT`, and so on.

**See Also:**

[Oracle Database SQL Tuning Guide](../tgsql/introduction-to-sql-tuning.md) for more information about monitoring performance

#### 8.7.1.1 V\$PX_BUFFER_ADVICE

You can monitor parallel execution performance with the `V$PX_BUFFER_ADVICE` dynamic performance view.

The `V$PX_BUFFER_ADVICE` view provides statistics on historical and projected maximum buffer usage by all parallel queries. You can consult this view to reconfigure SGA size in response to insufficient memory problems for parallel queries.

#### 8.7.1.2 V\$PX_SESSION

You can monitor parallel execution performance with the `V$PX_SESSION` dynamic performance view.

The `V$PX_SESSION` view shows data about query server sessions, groups, sets, and server numbers. It also displays real-time data about the processes working on behalf of parallel execution. This table includes information about the requested degree of parallelism (DOP) and the actual DOP granted to the operation.

#### 8.7.1.3 V\$PX_SESSTAT

You can monitor parallel execution performance with the `V$PX_SESSTAT` dynamic performance view.

The `V$PX_SESSTAT` view provides a join of the session information from `V$PX_SESSION` and the `V$SESSTAT` table. Thus, all session statistics available to a standard session are available for all sessions performed using parallel execution.

#### 8.7.1.4 V\$PX_PROCESS

You can monitor parallel execution performance with the `V$PX_PROCESS` dynamic performance view.

The `V$PX_PROCESS` view contains information about the parallel processes, including status, session ID, process ID, and other information.

#### 8.7.1.5 V\$PX_PROCESS_SYSSTAT

You can monitor parallel execution performance with the `V$PX_PROCESS_SYSSTAT` dynamic performance view.

The `V$PX_PROCESS_SYSSTAT` view shows the status of query servers and provides buffer allocation statistics.

#### 8.7.1.6 V\$PQ_SESSTAT

You can monitor parallel execution performance with the `V$PQ_SESSTAT` dynamic performance view.

The `V$PQ_SESSTAT` view shows the status of all current server groups in the system such as data about how queries allocate processes and how the multiuser and load balancing algorithms are affecting the default and hinted values.

You might need to adjust some parameter settings to improve performance after reviewing data from these views. In this case, refer to the discussion of [Tuning General Parameters for Parallel Execution](parameters-parallel-exec.md). Query these views periodically to monitor the progress of long-running parallel operations.

For many dynamic performance views, you must set the parameter `TIMED_STATISTICS` to `TRUE` in order for Oracle Database to collect statistics for each view. You can use the `ALTER` `SYSTEM` or `ALTER` `SESSION` statements to turn `TIMED_STATISTICS` on and off.

#### 8.7.1.7 V\$PQ_TQSTAT

You can monitor parallel execution performance with the `V$PQ_TQSTAT` dynamic performance view.

As a simple example, consider a hash join between two tables, with a join on a column with only two distinct values. At best, this hash function has one hash value to parallel execution server A and the other to parallel execution server B. A DOP of two is fine, but, if it is four, then at least two parallel execution servers have no work. To discover this type of deviation, use a query similar to the following example:

    SELECT dfo_number, tq_id, server_type, process, num_rows
    FROM V$PQ_TQSTAT ORDER BY dfo_number DESC, tq_id, server_type, process;

The best way to resolve this problem might be to choose a different join method; a nested loop join might be the best option. Alternatively, if one join table is small relative to the other, a `BROADCAST` distribution method can be hinted using `PQ_DISTRIBUTE` hint. The optimizer considers the `BROADCAST` distribution method, but requires `OPTIMIZER_FEATURES_ENABLE` set to 9.0.2 or higher.

Now, assume that you have a join key with high cardinality, but one value contains most of the data, for example, lava lamp sales by year. The only year that had big sales was 1968, and the parallel execution server for the 1968 records is overwhelmed. You should use the same corrective actions as described in the previous paragraph.

The `V$PQ_TQSTAT` view provides a detailed report of message traffic at the table queue level. `V$PQ_TQSTAT` data is valid only when queried from a session that is executing parallel SQL statements. A table queue is the pipeline between query server groups, between the parallel execution coordinator and a query server group, or between a query server group and the coordinator. The table queues are represented explicitly in the operation column by `PX SEND <partitioning type>` (for example, `PX SEND HASH`) and `PX` `RECEIVE`.

`V$PQ_TQSTAT` has a row for each query server process that it reads from or writes to in each table queue. A table queue connecting 10 consumer processes to 10 producer processes has 20 rows in the view. Total the bytes column and group by `TQ_ID`, and the table queue identifier, to obtain the total number of bytes sent through each table queue. Compare this to the optimizer estimates; large variations might indicate a need to analyze the data using a larger sample.

Compute the variance of bytes grouped by `TQ_ID`. Large variances indicate workload imbalances. You should investigate large variances to determine whether the producers start out with unequal distributions of data, or whether the distribution itself is skewed. If the data itself is skewed, this might indicate a low cardinality, or low number of distinct values.

#### 8.7.1.8 V\$RSRC_CONS_GROUP_HISTORY

You can monitor parallel execution performance with the `V$RSRC_CONS_GROUP_HISTORY` dynamic performance view.

The `V$RSRC_CONS_GROUP_HISTORY` view displays a history of consumer group statistics for each entry in `V$RSRC_PLAN_HISTORY` that has a non-NULL plan, including information about parallel statement queuing.

#### 8.7.1.9 V\$RSRC_CONSUMER_GROUP

You can monitor parallel execution performance with the `V$RSRC_CONSUMER_GROUP` dynamic performance view.

The `V$RSRC_CONSUMER_GROUP` view displays data related to currently active resource consumer groups, including information about parallel statements.

#### 8.7.1.10 V\$RSRC_PLAN

You can monitor parallel execution performance with the `V$RSRC_PLAN` dynamic performance view.

The `V$RSRC_PLAN` view displays the names of all currently active resource plans, including the state of parallel statement queuing.

#### 8.7.1.11 V\$RSRC_PLAN_HISTORY

You can monitor parallel execution performance with the `V$RSRC_PLAN_HISTORY` dynamic performance view.

The `V$RSRC_PLAN_HISTORY` displays a history of when a resource plan was enabled, disabled, or modified on the instance. The history includes the state of parallel statement queuing

#### 8.7.1.12 V\$RSRC_SESSION_INFO

You can monitor parallel execution performance with the `V$RSRC_SESSION_INFO` dynamic performance view.

The `V$RSRC_SESSION_INFO` view displays resource manager statistics per session, including parallel statement queue statistics. Columns include `PQ_SERVERS` and `PQ_STATUS`.

The `PQ_SERVERS` column of the `V$RSRC_SESSION_INFO` view contains the number of active parallel servers if the session is active and running the parallel query. If the query is queued, the number of parallel servers that this query is trying to run with is shown.

The `PQ_STATUS` column maintains the reason that a parallel statement is queued

**See Also:**

[Oracle Database Reference](../refrn/dynamic-performance-views.md) for information about the `V$RSRC_SESSION_INFO` view

#### 8.7.1.13 V\$RSRCMGRMETRIC

You can monitor parallel execution performance with the `V$RSRCMGRMETRIC` dynamic performance view.

The `V$RSRCMGRMETRIC` view displays statistics related to parallel statement queuing.

Statistics related to parallel statement queuing are added to the resource manager metrics that takes statistics for a given one-minute window and retains them for approximately one hour.

Columns include `AVG_ACTIVE_PARALLEL_STMTS`, `AVG_QUEUED_PARALLEL_STMTS`, `AVG_ACTIVE_PARALLEL_SERVERS`, `AVG_QUEUED_PARALLEL_SERVERS`, and `PARALLEL_SERVERS_LIMIT`.

**See Also:**

[Oracle Database Reference](../refrn/dynamic-performance-views.md) for information about the `V$RSRCMGRMETRIC` view

### 8.7.2 Monitoring Session Statistics

You can monitor session statistics with the dynamic performance views to diagnose parallel execution performance.

Use `GV$PX_SESSION` to determine the configuration of the server group executing in parallel. In this example, session 9 is the query coordinator, while sessions 7 and 21 are in the first group, first set. Sessions 18 and 20 are in the first group, second set. The requested and granted DOP for this query is 2, as shown by the output from the following query:

    SELECT QCSID, SID, INST_ID "Inst", SERVER_GROUP "Group", SERVER_SET "Set",
      DEGREE "Degree", REQ_DEGREE "Req Degree"
    FROM GV$PX_SESSION ORDER BY QCSID, QCINST_ID, SERVER_GROUP, SERVER_SET;

Your output should resemble the following:

    QCSID      SID        Inst       Group      Set        Degree     Req Degree
    ---------- ---------- ---------- ---------- ---------- ---------- ----------
             9          9          1
             9          7          1          1          1          2          2
             9         21          1          1          1          2          2
             9         18          1          1          2          2          2
             9         20          1          1          2          2          2

For a single instance, use `SELECT` `FROM` `V$PX_SESSION` and do not include the column name `Instance` `ID`.

The processes shown in the output from the previous example using `GV$PX_SESSION` collaborate to complete the same task. The next example shows the execution of a join query to determine the progress of these processes in terms of physical reads. Use this query to track any specific statistic:

    SELECT QCSID, SID, INST_ID "Inst", SERVER_GROUP "Group", SERVER_SET "Set",
      NAME "Stat Name", VALUE
    FROM GV$PX_SESSTAT A, V$STATNAME B
    WHERE A.STATISTIC# = B.STATISTIC# AND NAME LIKE 'PHYSICAL READS'
      AND VALUE > 0 ORDER BY QCSID, QCINST_ID, SERVER_GROUP, SERVER_SET;

Your output should resemble the following:

    QCSID  SID   Inst   Group  Set    Stat Name          VALUE
    ------ ----- ------ ------ ------ ------------------ ----------
         9     9      1               physical reads           3863
         9     7      1      1      1 physical reads              2
         9    21      1      1      1 physical reads              2
         9    18      1      1      2 physical reads              2
         9    20      1      1      2 physical reads              2

Use the previous type of query to track statistics in `V$STATNAME`. Repeat this query as often as required to observe the progress of the query server processes.

The next query uses `V$PX_PROCESS` to check the status of the query servers.

    SELECT * FROM V$PX_PROCESS;

Your output should resemble the following:

    SERV STATUS    PID    SPID      SID    SERIAL# IS_GV   CON_ID
    ---- --------- ------ --------- ------ ------- -----  -------
    P002 IN USE        16     16955     21   7729  FALSE        0
    P003 IN USE        17     16957     20   2921  FALSE        0
    P004 AVAILABLE     18     16959                FALSE        0
    P005 AVAILABLE     19     16962                FALSE        0
    P000 IN USE        12      6999     18   4720  FALSE        0
    P001 IN USE        13      7004      7    234  FALSE        0

**See Also:**

Monitoring Parallel Execution Performance with Dynamic Performance Views for descriptions of the dynamic performance views used in the examples

### 8.7.3 Monitoring System Statistics

You can monitor system statistics with the dynamic performance views to diagnose parallel execution performance.

The `V$SYSSTAT` and `V$SESSTAT` views contain several statistics for monitoring parallel execution. Use these statistics to track the number of parallel queries, DMLs, DDLs, data flow operators (DFOs), and operations. Each query, DML, or DDL can have multiple parallel operations and multiple DFOs.

In addition, statistics also count the number of query operations for which the DOP was reduced, or downgraded, due to either the adaptive multiuser algorithm or the depletion of available parallel execution servers.

Finally, statistics in these views also count the number of messages sent on behalf of parallel execution. The following syntax is an example of how to display these statistics:

    SELECT NAME, VALUE FROM GV$SYSSTAT
      WHERE UPPER (NAME) LIKE '%PARALLEL OPERATIONS%'
      OR UPPER (NAME) LIKE '%PARALLELIZED%' OR UPPER (NAME) LIKE '%PX%';

Your output should resemble the following:

    NAME                                               VALUE
    -------------------------------------------------- ----------
    queries parallelized                                      347
    DML statements parallelized                                 0
    DDL statements parallelized                                 0
    DFO trees parallelized                                    463
    Parallel operations not downgraded                         28
    Parallel operations downgraded to serial                   31
    Parallel operations downgraded 75 to 99 pct               252
    Parallel operations downgraded 50 to 75 pct               128
    Parallel operations downgraded 25 to 50 pct                43
    Parallel operations downgraded 1 to 25 pct                 12
    PX local messages sent                                  74548
    PX local messages recv'd                                74128
    PX remote messages sent                                     0
    PX remote messages recv'd                                   0

The following query shows the current wait state of each worker (child process) and query coordinator process on the system:

    SELECT px.SID "SID", p.PID, p.SPID "SPID", px.INST_ID "Inst",
           px.SERVER_GROUP "Group", px.SERVER_SET "Set",
           px.DEGREE "Degree", px.REQ_DEGREE "Req Degree", w.event "Wait Event"
    FROM GV$SESSION s, GV$PX_SESSION px, GV$PROCESS p, GV$SESSION_WAIT w
    WHERE s.sid (+) = px.sid AND s.inst_id (+) = px.inst_id AND
          s.sid = w.sid (+) AND s.inst_id = w.inst_id (+) AND
          s.paddr = p.addr (+) AND s.inst_id = p.inst_id (+)
    ORDER BY DECODE(px.QCINST_ID,  NULL, px.INST_ID,  px.QCINST_ID), px.QCSID,
    DECODE(px.SERVER_GROUP, NULL, 0, px.SERVER_GROUP), px.SERVER_SET, px.INST_ID;

### 8.7.4 Monitoring Operating System Statistics

There is considerable overlap between information available in Oracle Database and information available though operating system utilities, such as `sar` and `vmstat` on UNIX-based systems.

Operating systems provide performance statistics on I/O, communication, CPU, memory and paging, scheduling, and synchronization primitives. The `V$SESSTAT` view provides the major categories of operating system statistics as well.

Typically, operating system information about I/O devices and semaphore operations is harder to map back to database objects and operations than is Oracle Database information. However, some operating systems have good visualization tools and efficient means of collecting the data.

Operating system information about CPU and memory usage is very important for assessing performance. Probably the most important statistic is CPU usage. The goal of low-level performance tuning is to become CPU bound on all CPUs. After this is achieved, you can work at the SQL level to find an alternate plan that might be more I/O intensive but use less CPU.

Operating system memory and paging information is valuable for fine tuning the many system parameters that control how memory is divided among memory-intensive data warehouse subsystems like parallel communication, sort, and hash join.
