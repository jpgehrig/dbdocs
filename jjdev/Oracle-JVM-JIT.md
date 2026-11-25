This section describes the just-in-time (JIT) compiler that has been introduced since Oracle Database 11g release 1 (11.1). This section covers the following topics:

- Overview of Oracle JVM JIT

- Advantages of JIT Compilation

- Methods Introduced in Oracle Database 11g

**Note:**

The JIT compiler is a replacement of the compilers that were used in the earlier versions of Oracle Database.

### 9.1.1 Overview of Oracle JVM JIT

A JIT compiler for Oracle JVM enables much faster execution because it manages the invalidation, recompilation, and storage of code without an external mechanism.

Based on dynamically gathered profiling data, this compiler transparently selects Java methods to compile the native machine code and dynamically makes them available to running Java sessions. Additionally, the compiler can take advantage of the class resolution model of Oracle JVM to optionally persist compiled Java methods across database calls, sessions, or instances. Such persistence avoids the overhead of unnecessary recompilations across sessions or instances, when it is known that semantically the Java code has not changed.

The JIT compiler is controlled by a new boolean-valued initialization parameter called `java_jit_enabled`. When running heavily used Java methods with `java_jit_enabled` parameter value as `true`, the Java methods are automatically compiled to native code by the JIT compiler and made available for use by all sessions in the instance. Setting the `java_jit_enabled` parameter to `true` also causes further JIT compilation to cease, and reverts any already compiled methods to be interpreted. The VM automatically recompiles native code for Java methods when necessary, such as following reresolution of the containing Java class.

**Note:**

On Linux, Oracle JVM JIT uses POSIX shared memory that requires access to the `/dev/shm` directory. The `/dev/shm` directory should be of type `tmpfs` and you must mount this directory as follows:

- With `rw` and `execute` permissions set on it

- Without `noexec` or `nosuid` set on it

If the correct mount options are not used, then the following failure may occur during installation of the database:

    ORA-29516: Aurora assertion failure: Assertion failure at joez.c:
    Bulk load of method java/lang/Object.<init> failed; insufficient shm-object space

The JIT compiler runs as an MMON worker process, in a single background process for the instance. So, while the JIT compiler is running and actively compiling methods, you may see this background process consuming CPU and memory resources equivalent to an active user Java session.

### 9.1.2 Advantages of JIT Compilation

The following are the advantages of using JIT compilation over the compilation techniques used in earlier versions of Oracle database:

- JIT compilation works transparently

- JIT compilation speeds up the performance of Java classes

- JIT stored compiled code avoids recompilation of Java programs across sessions or instances when it is known that semantically the Java code has not changed.

- JIT compilation does not require a C compiler

- JIT compilation eliminates some of the array bounds checking

- JIT compilation eliminates common sub-expressions within blocks

- JIT compilation eliminates empty methods

- JIT compilation defines the region for register allocation of local variables

- JIT compilation eliminates the need of flow analysis

- JIT compilation limits inline code

### 9.1.3 Methods Introduced in Oracle Database 11g

Since 11g release 1 (11.1), the `DBMS_JAVA` package has been enhanced with the following new public methods to provide Java entry points for controlling synchronous method compilation and reverting to interpreted method execution:

#### set_native_compiler_option

This procedure sets a native-compiler option to the specified value for the current schema. If the option given by optionName is not allowed to have duplicate values, then the value is ignored.

    PROCEDURE set_native_compiler_option(optionName VARCHAR2,
    value VARCHAR2);

#### unset_native_compiler_option

This procedure unsets a native-compiler option/value pair for the current schema. If the option given by optionName is not allowed to have duplicate values, then the value is ignored.

    PROCEDURE unset_native_compiler_option(optionName VARCHAR2,
    value VARCHAR2);

#### compile_class

This function compiles all methods defined by the class that is identified by classname in the current schema. It returns the number of methods successfully compiled. If the class does not exist, then an `ORA-29532 (Uncaught Java exception)` occurs.

    FUNCTION compile_class(classname VARCHAR2) return NUMBER;

#### uncompile_class

This function uncompiles all methods defined by the class that is identified by classname in the current schema. It returns the number of methods successfully uncompiled. If the value of the argument permanentp is nonzero, then mark these methods as permanently dynamically uncompilable. Otherwise, they are eligible for future dynamic recompilation. If the class does not exist, then an `ORA-29532 (Uncaught Java exception)` occurs.

    FUNCTION uncompile_class(classname VARCHAR2,
    permanentp NUMBER default 0) return NUMBER;

#### compile_method

This function compiles the method specified by name and Java type signatures defined by the class, which is identified by classname in the current schema. It returns the number of methods successfully compiled. If the class does not exist, then an ORA-29532 (Uncaught Java exception) occurs.

    FUNCTION compile_method(classname  VARCHAR2,
    methodname VARCHAR2,
    methodsig  VARCHAR2) return NUMBER;

#### uncompile_method

This function uncompiles the method specified by the name and Java type signatures defined by the class that is identified by classname in the current schema. It returns the number of methods successfully uncompiled. If the value of the argument permanentp is nonzero, then mark the method as permanently dynamically uncompilable. Otherwise, it is eligible for future dynamic recompilation. If the class does not exist, then an `ORA-29532 (Uncaught Java exception)` occurs.

    FUNCTION uncompile_method(classname  VARCHAR2,
    methodname VARCHAR2,
    methodsig  VARCHAR2,
    permanentp NUMBER default 0) return NUMBER;
