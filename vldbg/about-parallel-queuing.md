In some situations, parallel statements are queued while waiting for resources.

When the parameter `PARALLEL_DEGREE_POLICY` is set to `AUTO`, Oracle Database queues SQL statements that require parallel execution if the necessary number of parallel execution server processes are not available. After the necessary resources become available, the SQL statement is dequeued and allowed to execute. The default dequeue order is a simple first in, first out queue based on the time a statement was issued.

The following is a summary of parallel statement processing.

1.  A SQL statements is issued.

2.  The statement is parsed and the DOP is automatically determined.

3.  Available parallel resources are checked.

    1.  If there are sufficient parallel execution servers available and there are no statements ahead in the queue waiting for the resources, the SQL statement is executed.

    2.  If there are not sufficient parallel execution servers available, the SQL statement is queued based on specified conditions and dequeued from the front of the queue when specified conditions are met.

Parallel statements are queued if running the statements would increase the number of active parallel servers above the value of the `PARALLEL_SERVERS_TARGET` initialization parameter. For example, if `PARALLEL_SERVERS_TARGET` is set to `64`, the number of current active servers is 60, and a new parallel statement needs 16 parallel servers, it would be queued because 16 added to 60 is greater than 64, the value of `PARALLEL_SERVERS_TARGET`.

This value is not the maximum number of parallel server processes allowed on the system, but the number available to run parallel statements before parallel statement queuing is used. It is set lower than the maximum number of parallel server processes allowed on the system (`PARALLEL_MAX_SERVERS`) to ensure each parallel statement gets all of the parallel server resources required and to prevent overloading the system with parallel server processes. Note all serial (nonparallel) statements execute immediately even if parallel statement queuing has been activated.

If a statement has been queued, it is identified by the `resmgr:pq` `queued` wait event.

This section discusses the following topics:

- About Managing Parallel Statement Queuing with Oracle Database Resource Manager

- Grouping Parallel Statements with BEGIN_SQL_BLOCK END_SQL_BLOCK

- About Managing Parallel Statement Queuing with Hints

**See Also:**

- [V\$RSRC_SESSION_INFO](monitor-parallel-performance.md) and [V\$RSRCMGRMETRIC](monitor-parallel-performance.md) for information about views for monitoring and analyzing parallel statement queuing

- [Oracle Database Reference](../refrn/PARALLEL_SERVERS_TARGET.md) for more information about the `PARALLEL_SERVERS_TARGET` initialization parameter

### 8.4.1 About Managing Parallel Statement Queuing with Oracle Database Resource Manager

By default, the parallel statement queue operates as a first-in, first-out queue, but you can modify the default behavior with a resource plan.

By configuring and setting a resource plan, you can control the order in which parallel statements are dequeued and the number of parallel execution servers used by each workload or consumer group.

Oracle Database Resource Manager operates based on the concept of consumer groups and resource plans. Consumer groups identify groups of users with identical resource privileges and requirements. A resource plan consists of a collection of directives for each consumer group which specify controls and allocations for various database resources, such as parallel servers. For multitenant container databases (CDBs) and pluggable databases (PDBs), the order of the parallel statement queue is managed by the directive called `shares`.

A resource plan is enabled by setting the `RESOURCE_MANAGER_PLAN` parameter to the name of the resource plan.

You can use the directives described in the following sections to manage the processing of parallel statements for consumer groups when the parallel degree policy is set to `AUTO`.

- About Managing the Order of the Parallel Statement Queue

- About Limiting the Parallel Server Resources for a Consumer Group

- Specifying a Parallel Statement Queue Timeout for Each Consumer Group

- Specifying a Degree of Parallelism Limit for Consumer Groups

- Critical Parallel Statement Prioritization

- A Sample Scenario for Managing Statements in the Parallel Queue

In all cases, the parallel statement queue of a given consumer group is managed as a single queue on an Oracle RAC database. Limits for each consumer group apply to all sessions across the Oracle RAC database that belong to that consumer group. The queuing of parallel statements occurs based on the sum of the values of the `PARALLEL_SERVERS_TARGET` initialization parameter across all database instances.

You can also manage parallel statement queuing for multitenant container databases (CDBs) and pluggable databases (PDBs).

**See Also:**

- [Oracle Database Administrator’s Guide](../admin/managing-resources-with-oracle-database-resource-manager.md) for information about managing Oracle Database resources with Oracle Database Resource Manager

- [Oracle Multitenant Administrator's Guide](../multi/using-oracle-resource-manager-for-pdbs-with-sql-plus.md) for information about parallel execution (PX) servers and utilization limits for for multitenant container databases (CDBs) and pluggable databases (PDBs)

- [Oracle Database Reference](../refrn/dynamic-performance-views.md) for information about `V$RSRC`\* views, the `DBA_HIST_RSRC_CONSUMER_GROUP` view, and parallel query wait events

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_RESOURCE_MANAGER.md) for information about the `DBMS_RESOURCE_MANAGER` package

#### 8.4.1.1 About Managing the Order of the Parallel Statement Queue

You can use Oracle Database Resource Manager to manage the priority for dequeuing parallel statements from the parallel statement queue across multiple consumer groups.

The parallel statements for a particular consumer group are dequeued in FIFO order by default. With the directives `shares`, you can determine the order in which the parallel statements of a consumer group are dequeued. You configure these directives with the `CREATE_PLAN_DIRECTIVE` or `UPDATE_PLAN_DIRECTIVE` procedure of the `DBMS_RESOURCE_MANAGER` PL/SQL package. You can also set `shares` in a CDB resource plan to manage the order of parallel statements among PDBs.

For example, you can create the `PQ_HIGH`, `PQ_MEDIUM`, and `PQ_LOW` consumer groups and map parallel statement sessions to these consumer groups based on priority. You then create a resource plan that sets `shares=14` for `PQ_HIGH`, `shares=5` for `PQ_MEDIUM`, and `shares=1` for `PQ_LOW`. This indicates that `PQ_HIGH` statements are dequeued with a probability of `70%` (14/(14+5+1)=.70) of the time, `PQ_MEDIUM` dequeued with a probability of `25%` (5/(14+5+1)=.25) of the time, and `PQ_LOW` dequeued with a probability of `5%` (1/(14+5+1)=.05) of the time.

If a parallel statement has been queued and you determine that the parallel statement must be run immediately, then you can run the `DBMS_RESOURCE_MANAGER.DEQUEUE_PARALLEL_STATEMENT` PL/SQL procedure to dequeue the parallel statement.

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_RESOURCE_MANAGER.md) for information about procedures in the `DBMS_RESOURCE_MANAGER` package

- [Oracle Database Administrator’s Guide](../admin/managing-resources-with-oracle-database-resource-manager.md) for information about creating resource plan directives

#### 8.4.1.2 About Limiting the Parallel Server Resources for a Consumer Group

You can use Oracle Database Resource Manager to limit the number of parallel servers that parallel statements from lower priority consumer groups can use for parallel statement processing.

Using Oracle Database Resource Manager you can map parallel statement sessions to different consumer groups that each have specific limits on the number of the parallel servers that can be used. Every consumer group has its own individual parallel statement queue. When these limits for consumer groups are specified, parallel statements from a consumer group are queued when its limit would be exceeded.

This limitation becomes useful when a database has high priority and low priority consumer groups. Without limits, a user may issue a large number of parallel statements from a low-priority consumer group that uses all parallel servers. When a parallel statement from a high priority consumer group is issued, the resource allocation directives can ensure that the high priority parallel statement is dequeued first. By limiting the number of parallel servers a low-priority consumer group can use, you can ensure that there are always some parallel servers available for a high priority consumer group.

To limit the parallel servers used by a consumer group, use the `parallel_server_limit` parameter with the `CREATE_PLAN_DIRECTIVE` procedure or the `new_parallel_server_limit` parameter with the `UPDATE_PLAN_DIRECTIVE` procedure in the `DBMS_RESOURCE_MANAGER` package. The `parallel_server_limit` parameter specifies the maximum percentage of the Oracle RAC-wide parallel server pool that is specified by `PARALLEL_SERVERS_TARGET` that a consumer group can use.

For multitenant container database (CDB) resource plans, the parallel server limit applies to pluggable databases (PDBs). For PDB resource plans or non-CDB resource plans, this limit applies to consumer groups.

For example, on an Oracle RAC database in nonmultitenant configuration, the initialization parameter `PARALLEL_SERVERS_TARGET` is set to `32` on two nodes so there are a total of 32 x 2 = 64 parallel servers that can be used before queuing begins. You can set up the consumer group `PQ_LOW` to use 50% of the available parallel servers (`parallel_server_limit` = 50) and low priority statements can then be mapped to the `PQ_LOW` consumer group. This scenario limits any parallel statements from the `PQ_LOW` consumer group to 64 x 50% = 32 parallel servers, even though there are more inactive or unused parallel servers. In this scenario, after the statements from the `PQ_LOW` consumer group have used 32 parallel servers, statements from that consumer group are queued.

It is possible in one database to have some sessions with the parallelism degree policy set to `MANUAL` and some sessions set to `AUTO`. In this scenario, only the sessions with parallelism degree policy set to `AUTO` can be queued. However, the parallel servers used in sessions where the parallelism degree policy is set to `MANUAL` are included in the total of all parallel servers used by a consumer group.

**See Also:**

[PARALLEL_SERVERS_TARGET](parameters-parallel-exec.md) for information about limiting parallel resources for users

#### 8.4.1.3 Specifying a Parallel Statement Queue Timeout for Each Consumer Group

You can use Oracle Database Resource Manager to set specific maximum queue timeouts for consumer groups so that parallel statements do not stay in the queue for long periods of time.

To manage the queue timeout, the `parallel_queue_timeout` parameter is used with the `CREATE_PLAN_DIRECTIVE` procedure or the `new_parallel_queue_timeout` parameter is used with the `UPDATE_PLAN_DIRECTIVE` procedure in the `DBMS_RESOURCE_MANAGER` package. The `parallel_queue_timeout` and `new_parallel_queue_timeout` parameters specify the time in seconds that a statement can remain in a consumer group parallel statement queue. After the timeout period expires, the statement is either terminated with error `ORA-7454` or removed from the parallel statement queue and enabled to run based on the value for the `PQ_TIMEOUT_ACTION` directive in the resource manager plan.

You can specify queue timeout actions for parallel statements using the `PQ_TIMEOUT_ACTION` resource manager directive. Setting this directive to `CANCEL` terminates the statement with the error `ORA-7454`. Setting this directive to `RUN` enables the statement to run.

#### 8.4.1.4 Specifying a Degree of Parallelism Limit for Consumer Groups

You can use Oracle Database Resource Manager to the limit the degree of parallelism for specific consumer groups.

Using Oracle Database Resource Manager you can map parallel statement sessions to different consumer groups that each have specific limits for the degree of parallelism in a resource plan.

To manage the limit of parallelism in consumer groups, use the `parallel_degree_limit_p1` parameter with the `CREATE_PLAN_DIRECTIVE` procedure in the `DBMS_RESOURCE_MANAGER` package or the `new_parallel_degree_limit_p1` parameter with the `UPDATE_PLAN_DIRECTIVE` procedure in the `DBMS_RESOURCE_MANAGER` package. The `parallel_degree_limit_p1` and `new_parallel_degree_limit_p1` parameters specify a limit on the degree of parallelism for any operation.

For example, you can create the PQ_HIGH, PQ_MEDIUM, and PQ_LOW consumer groups and map parallel statement sessions to these consumer groups based on priority. You then create a resource plan that specifies degree of parallelism limits so that the PQ_HIGH limit is set to 16, the PQ_MEDIUM limit is set to 8, and the PQ_LOW limit is set to 2.

The degree of parallelism limit is enforced, even if `PARALLEL_DEGREE_POLICY` is not set to `AUTO`.

#### 8.4.1.5 Critical Parallel Statement Prioritization

The setting of the `PARALLEL_STMT_CRITICAL` parameter affects the critical designation of parallel statements in the plan directive with respect to the parallel statement queue.

- If the `PARALLEL_STMT_CRITICAL` parameter is set to `QUEUE`, then parallel statements that have `PARALLEL_DEGREE_POLICY` set to `MANUAL` are queued.

- If the `PARALLEL_STMT_CRITICAL` parameter is set to `BYPASS_QUEUE`, then parallel statements bypass the parallel statement queue and execute immediately.

- If `PARALLEL_STMT_CRITICAL` is set to `FALSE`, then that specifies the default behavior and no statement is designated as critical.

Because critical parallel statements bypass the parallel statement queue, the system may encounter more active parallel servers than specified by the `PARALLEL_SERVERS_TARGET` parameter. Critical parallel statements are allowed to run after the number of parallel servers reaches `PARALLEL_MAX_SERVERS`, so some critical parallel statements may be downgraded.

The `PARALLEL_STMT_CRITICAL` column in the `DBA_RSRC_PLAN_DIRECTIVES` view indicates whether parallel statements are from a consumer group that has been marked critical.

#### 8.4.1.6 A Sample Scenario for Managing Statements in the Parallel Queue

This scenario discusses how to manage statements in the parallel queue with consumer groups set up with Oracle Database Resource Manager.

For this scenario, consider a data warehouse workload that consists of three types of SQL statements:

- Short-running SQL statements

  Short-running identifies statements running less than one minute. You expect these statements to have very good response times.

- Medium-running SQL statements

  Medium-running identifies statements running more than one minute, but less than 15 minutes. You expect these statements to have reasonably good response times.

- Long-running SQL statements

  Long-running identifies statements that are ad-hoc or complex queries running more than 15 minutes. You expect these statements to take a long time.

For this data warehouse workload, you want better response times for the short-running statements. To achieve this goal, you must ensure that:

- Long-running statements do not use all of the parallel server resources, forcing shorter statements to wait in the parallel statement queue.

- When both short-running and long-running statements are queued, short-running statements should be dequeued ahead of long-running statements.

- The DOP for short-running queries is limited because the speedup from a very high DOP is not significant enough to justify the use of a large number of parallel servers.

Example 8-3 shows how to set up consumer groups using Oracle Database Resource Manager to set priorities for statements in the parallel statement queue. Note the following for this example:

- By default, users are assigned to the `OTHER_GROUPS` consumer group. If the estimated execution time of a SQL statement is longer than 1 minute (60 seconds), then the user switches to `MEDIUM_SQL_GROUP`. Because `switch_for_call` is set to `TRUE`, the user returns to `OTHER_GROUPS` when the statement has completed. If the user is in `MEDIUM_SQL_GROUP` and the estimated execution time of the statement is longer than 15 minutes (900 seconds), the user switches to `LONG_SQL_GROUP`. Similarly, because `switch_for_call` is set to `TRUE`, the user returns to `OTHER_GROUPS` when the query has completed. The directives used to accomplish the switch process are `switch_time`, `switch_estimate`, `switch_for_call`, and `switch_group`.

- After the number of active parallel servers reaches the value of the `PARALLEL_SERVERS_TARGET` initialization parameter, subsequent parallel statements are queued. The `shares` directives control the order in which parallel statements are dequeued when parallel servers become available. Because `shares` is set to `100%` for `SYS_GROUP` in this example, parallel statements from `SYS_GROUP` are always dequeued first. If no parallel statements from `SYS_GROUP` are queued, then parallel statements from `OTHER_GROUPS` are dequeued with probability 70%, from `MEDIUM_SQL_GROUP` with probability 20%, and `LONG_SQL_GROUP` with probability 10%.

- Parallel statements issued from `OTHER_GROUPS` are limited to a DOP of 4 with the setting of the `parallel_degree_limit_p1` directive.

- To prevent parallel statements of the `LONG_SQL_GROUP` group from using all of the parallel servers, which could potentially cause parallel statements from `OTHER_GROUPS` or `MEDIUM_SQL_GROUP` to wait for long periods of time, its `parallel_server_limit` directive is set to `50%`. This setting means that after `LONG_SQL_GROUP` has used up 50% of the parallel servers set with the `PARALLEL_SERVERS_TARGET` initialization parameter, its parallel statements are forced to wait in the queue.

- Because parallel statements of the `LONG_SQL_GROUP` group may be queued for a significant amount of time, a timeout is configured for 14400 seconds (4 hours). When a parallel statement from `LONG_SQL_GROUP` has waited in the queue for 4 hours, the statement is terminated with the error ORA-7454.

Example 8-3 Using consumer groups to set priorities in the parallel statement queue

    BEGIN
      DBMS_RESOURCE_MANAGER.CREATE_PENDING_AREA();

      /* Create consumer groups.
       * By default, users start in OTHER_GROUPS, which is automatically
       * created for every database.
       */
      DBMS_RESOURCE_MANAGER.CREATE_CONSUMER_GROUP(
        'MEDIUM_SQL_GROUP',
        'Medium-running SQL statements, between 1 and 15 minutes.  Medium priority.');

      DBMS_RESOURCE_MANAGER.CREATE_CONSUMER_GROUP(
        'LONG_SQL_GROUP',
        'Long-running SQL statements of over 15 minutes.  Low priority.');

      /* Create a plan to manage these consumer groups */
      DBMS_RESOURCE_MANAGER.CREATE_PLAN(
        'REPORTS_PLAN',
        'Plan for daytime that prioritizes short-running queries');

      DBMS_RESOURCE_MANAGER.CREATE_PLAN_DIRECTIVE(
        'REPORTS_PLAN', 'SYS_GROUP', 'Directive for sys activity',
        shares => 100);

      DBMS_RESOURCE_MANAGER.CREATE_PLAN_DIRECTIVE(
        'REPORTS_PLAN', 'OTHER_GROUPS', 'Directive for short-running queries',
        shares => 70,
        parallel_degree_limit_p1 => 4,
        switch_time => 60, switch_estimate => TRUE, switch_for_call => TRUE,
        switch_group => 'MEDIUM_SQL_GROUP');

      DBMS_RESOURCE_MANAGER.CREATE_PLAN_DIRECTIVE(
        'REPORTS_PLAN', 'MEDIUM_SQL_GROUP', 'Directive for medium-running queries',
        shares => 20,
        parallel_server_limit => 80,
        switch_time => 900, switch_estimate => TRUE, switch_for_call => TRUE,
        switch_group => 'LONG_SQL_GROUP');

      DBMS_RESOURCE_MANAGER.CREATE_PLAN_DIRECTIVE(
        'REPORTS_PLAN', 'LONG_SQL_GROUP', 'Directive for medium-running queries',
        shares => 10,
        parallel_server_limit => 50,
        parallel_queue_timeout => 14400);

      DBMS_RESOURCE_MANAGER.SUBMIT_PENDING_AREA();
    END;
    /

    /* Allow all users to run in these consumer groups */
    EXEC DBMS_RESOURCE_MANAGER_PRIVS.GRANT_SWITCH_CONSUMER_GROUP(
      'public', 'MEDIUM_SQL_GROUP', FALSE);

    EXEC DBMS_RESOURCE_MANAGER_PRIVS.GRANT_SWITCH_CONSUMER_GROUP(
      'public', 'LONG_SQL_GROUP', FALSE);

### 8.4.2 Grouping Parallel Statements with BEGIN_SQL_BLOCK END_SQL_BLOCK

Often it is important for a report or batch job that consists of multiple parallel statements to complete as quickly as possible.

For example, when many reports are launched simultaneously, you may want all of the reports to complete as quickly as possible. However, you also want some specific reports to complete first, rather than all reports finishing at the same time.

If a report contains multiple parallel statements and `PARALLEL_DEGREE_POLICY` is set to `AUTO`, then each parallel statement may be forced to wait in the queue on a busy database. For example, the following steps describe a scenario in SQL statement processing:

    serial statement
    parallel query - dop 8
      -> wait in queue
    serial statement
    parallel query - dop 32
      -> wait in queue
    parallel query - dop 4
      -> wait in queue

For a report to be completed quickly, the parallel statements must be grouped to produce the following behavior:

    start SQL block
    serial statement
    parallel query - dop 8
      -> first parallel query: ok to wait in queue
    serial statement
    parallel query - dop 32
      -> avoid or minimize wait
    parallel query - dop 4
      -> avoid or minimize wait
    end SQL block

To group the parallel statements, you can use the `BEGIN_SQL_BLOCK` and `END_SQL_BLOCK` procedures in the `DBMS_RESOURCE_MANAGER` PL/SQL package. For each consumer group, the parallel statement queue is ordered by the time associated with each of the consumer group's parallel statements. Typically, the time associated with a parallel statement is the time that the statement was enqueued, which means that the queue appears to be FIFO. When parallel statements are grouped in a SQL block with the `BEGIN_SQL_BLOCK` and `END_SQL_BLOCK` procedures, the first queued parallel statement also uses the time that it was enqueued. However, the second and all subsequent parallel statements receive special treatment and are enqueued using the enqueue time of the first queued parallel statement within the SQL block. With this functionality, the statements frequently move to the front of the parallel statement queue. This preferential treatment ensures that their wait time is minimized.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_RESOURCE_MANAGER.md) for information about the `DBMS_RESOURCE_MANAGER` package

### 8.4.3 About Managing Parallel Statement Queuing with Hints

You can use the `NO_STATEMENT_QUEUING` and `STATEMENT_QUEUING` hints in SQL statements to influence whether or not a statement is queued with parallel statement queuing.

- `NO_STATEMENT_QUEUING`

  When `PARALLEL_DEGREE_POLICY` is set to `AUTO`, this hint enables a statement to bypass the parallel statement queue. However, a statement that bypasses the statement queue can potentially cause the system to exceed the maximum number of parallel execution servers defined by the value of the `PARALLEL_SERVERS_TARGET` initialization parameter, which determines the limit at which parallel statement queuing is initiated.

  There is no guarantee that the statement that bypasses the parallel statement queue receives the number of parallel execution servers requested because only the number of parallel execution servers available on the system, up to the value of the `PARALLEL_MAX_SERVERS` initialization parameter, can be allocated.

  For example:

      SELECT /*+ NO_STATEMENT_QUEUING */ last_name, department_name
        FROM employees e, departments d
        WHERE e.department_id = d.department_id;

- `STATEMENT_QUEUING`

  When `PARALLEL_DEGREE_POLICY` is not set to `AUTO`, this hint enables a statement to be considered for parallel statement queuing, but to run only when enough parallel processes are available to run at the requested DOP. The number of available parallel execution servers, before queuing is enabled, is equal to the difference between the number of parallel execution servers in use and the maximum number allowed in the system, which is defined by the `PARALLEL_SERVERS_TARGET` initialization parameter.

  For example:

      SELECT /*+ STATEMENT_QUEUING */ last_name, department_name
        FROM employees e, departments d
        WHERE e.department_id = d.department_id;
