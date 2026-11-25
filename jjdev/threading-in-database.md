Oracle JVM is based on the database session model, which is a single-client, nonpreemptive threading model. Although Java in Oracle Database allows running threaded programs, it is single-threaded at the execution level. In this model, JVM runs all Java threads associated with a database session on a single operating system thread. Once dispatched, a thread continues execution until it explicitly yields by calling `Thread.yield(),` blocks by calling `Socket.read(),` or is preempted by the execution engine. Once a thread yields, blocks or is preempted, JVM dispatches another thread.

**Note:**

Starting with 11g release 1 (11.1), Oracle JVM supports thread preemption. Thread preemption is not mandated by the Java specification, but is needed to support the new `java.util.concurrent` API, present in JDK1.5, properly.

Oracle JVM has added the following features for better performance and thread management:

- System calls are at a minimum. Oracle JVM has exchanged some of the standard system calls with nonsystem solutions. For example, entering a monitor-synchronized block or method does not require a system call.

- Deadlocks are detected.

  - Oracle JVM monitors for deadlocks between threads. If a deadlock occurs, then Oracle JVM terminates one of the threads and throws the `oracle.aurora.vm.DeadlockError` exception.

  - Single-threaded applications cannot suspend. If the application has only a single thread and you try to suspend it, then the `oracle.aurora.vm.LimboError` exception is thrown.

### 2.12.1 Thread Life Cycle

In a single-threaded application, a call ends when one of the following events occurs:

- The thread returns to its caller.

- An exception is thrown and is not caught in Java code.

- The `System.exit(),` `OracleRuntime.exitSession(),` or `oracle.aurora.vm.OracleRuntime.exitCall()` method is called.

- The `DBMS_JAVA.endsession()` or `DBMS_JAVA.endsession_and_related_state()` method is called.

If the initial thread creates and starts other Java threads, then the call ends in one of the following ways:

- The main thread returns to its caller or an exception is thrown and not caught in this thread and in either case all other non-daemon threads are processed. Non-daemon threads complete either by returning from their initial method or because an exception is thrown and not caught in the thread.

- Any thread calls the `System.exit(),` `OracleRuntime.exitSession(),` or `oracle.aurora.vm.OracleRuntime.exitCall()` method.

- A call to `DBMS_JAVA.endsession()` or `DBMS_JAVA.endsession_and_related_state()` method.

Prior to 11g release 1 (11.1), when a call ended because of a call to `System.exit()` or `oracle.aurora.vm.OracleRuntime.exitCall()`, Oracle JVM ended the call abruptly and terminated all threads, in both the dedicated and shared server modes. Since 11g release 1 (11.1), this is addressed by the addition of the following PL/SQL functions to the `DBMS_JAVA` package:

- `FUNCTION endsession RETURN VARCHAR2;`

- `FUNCTION endsession_and_related_state RETURN VARCHAR2;`

During a call, a Java program can recursively cause more Java code to be run. For example, your program can issue a SQL query using JDBC or SQLJ that, in turn, calls a trigger written in Java. All the preceding remarks regarding call lifetime apply to the top-most call to Java code, not to the recursive call. For example, a call to `System.exit()` from within a recursive call exits the entire top-most call to Java, not just the recursive call.

**Related Topics**

- [Operating System Resources Affected Across Calls](shared-server-consideration.md)
- [Two-Tier Duration for Java Session State](two-tier-Java-session-duration.md)

### 2.12.2 System.exit(), OracleRuntime.exitSession(), and OracleRuntime.exitCall()

The `System.exit()` method terminates JVM, preserving no Java state. It does not cause the database session to terminate or the client to disconnect.

However, the database session may, and often does, terminate itself immediately afterward. `OracleRuntime.exitSession()` also terminates JVM, preserving no Java state. However, it also terminates the database session and disconnects the client.

The behavior of `OracleRuntime.exitCall()` varies depending on `OracleRuntime.threadTerminationPolicy()`. This method returns a `boolean` value. If this value is `true`, then any active thread should be terminated, rather than left quiescent, at the end of a database call.

- In a shared server process, `threadTerminationPolicy()` is always `true`.

- In a shadow (dedicated) process, the default value is `false`. You can change the value by calling `OracleRuntime.setThreadTerminationPolicy()`.

  - If you set the value to false, that is the default value, all threads are left quiescent but receive a `ThreadDeath` exception for graceful termination.

  - If the value is true, all threads are terminated abruptly.

In addition, there is another method, `OracleRuntime.callExitPolicy()`. This method determines when a call is exited if none of the `OracleRuntime.exitSession()`, `OracleRuntime.exitCall()`, or `System.exit()` methods were ever called. The call exit policy can be set to one of the following, using `OracleRuntime.setCallExitPolicy()`:

- `OracleRuntime.EXIT_CALL_WHEN_MAIN_THREAD_TERMINATES`

  If set to this value, then as soon as the main thread returns or an uncaught exception occurs on the main thread, all remaining threads, both daemon and non-daemon are:

  - Stopped, if `threadTerminationPolicy()` is true, always in shared server mode.

  - Left quiescent, if `threadTerminationPolicy()` is false.

- `OracleRuntime.EXIT_CALL_WHEN_ALL_NON_DAEMON_THREADS_TERMINATE`

  This is the default value. If this value is set, then the call ends when only daemon threads are left running. At this point:

  - If the `threadTerminationPolicy()` is `true`, always in shared server mode, then the daemon threads are stopped.

  - If the `threadTerminationPolicy()` is `false`, then the daemon threads are left quiescent until the next call. This is the default setting for shadow (dedicated) server mode.

- `OracleRuntime.EXIT_CALL_WHEN_ALL_THREADS_TERMINATE`

  If set to this value, then the call ends only when all threads have either returned or ended due to an uncaught exception. At this point, the call ends regardless of the value of `threadTerminationPolicy()`.
