Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](LASImportExport.md)
- [Next Class](Pc2Dem.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.spatial.util

## Class Logger

- java.lang.Object

- - oracle.spatial.util.Logger

<!-- -->

-

  ------------------------------------------------------------------------



      public class Logger
      extends java.lang.Object

  Logging API for Oracle LBS products. This API provides a flexible and consistent logging mechanism. The two main components of the Logger are **Logging Levels** and **Logging Flags**. The logging level determins the volumn of log messages. In other words, only log records with a level equal to or higher than the set logging level will be actually generated.
  The pre-defined Logging levels are:

              LEVEL_FATAL       //highest level: only FATAL messages are logged
              LEVEL_ERROR
              LEVEL_WARN
              LEVEL_INFO
              LEVEL_DEBUG
              LEVEL_FINEST      //lowest level: everything will be logged


  In addition to logging levels, there are flags that can be set so as to influence the format of log records. For instance you can unset the flag LOG_TIME so that the current time is not automatically included in a log record (for better run time performance). Here is a list of all the flags:

             LOG_THREAD_NAME   //flag for whether to include current thread name in a log record
             LOG_TIME          //flag for whether to include current time in a log record


  Usage:

  - Step 1. At global initialization time, read the global logging configuration file (if any) and initialize Logger's global configuration, including the global logging level, the logging output devices and flags et al.
  - Step 2. In each class, define an static instance of the Logger. Each instance will inherit the global settings initially, but you may override them at any time. Each Logger instance has a name, which follows Java's package naming convention. You can re-config all the Logger instances in a particular namespace dynamically during run-time.
  - Step 3. In your methods log messages as you see fit, using one of the Logger's logging methods. For instance use Logger's fatal() Method to log a fatal message, and info() method to log an informational message.

  Example: A sample class using the Logger API.

       package oracle.lbs.foo;
       public class Bar
       {
         private static Logger log = Logger.getLogger("oracle.lbs.foo.Bar");

         int a;
         pubilc void zero()
         {
            a = 0;
            log.info("set a to zero");
         }
         public int  divide(int m)
         {
            if(a==0)
            {
              log.error("Dividing "+m+" by zero");
              return Number.NaN;
            }
            ...
         }

         public static void main(String[] args)
         {
            //tweaking the global logging configurations
            Logger.setGlobalLevel(Logger.LEVEL_WARN);
            Logger.setGlobalFlags(Logger.LOG_TIME | Logger.LOG_THREAD_NAME);
            //special logging level for classes under "oracle.sdovis.stylex" package
            Logger.setGlobalLevel(Logger.LEVEL_DEBUG, "oracle.sdovis.stylex");
            ......
         }
       }



<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                                                                        |
    |-------------------|--------------------------------------------------------------------------------------------------------------|
    | `static int`      | `LEVEL_DEBUG`<br>the DEBUG logging level.                                                                    |
    | `static int`      | `LEVEL_ERROR`<br>the ERROR logging level.                                                                    |
    | `static int`      | `LEVEL_FATAL`<br>the highest logging level; Logs unrecoverable program events.                               |
    | `static int`      | `LEVEL_FINEST`<br>the finest possible logging level.                                                         |
    | `static int`      | `LEVEL_INFO`<br>the INFO logging level, used for logging program configuration and other useful information. |
    | `static int`      | `LEVEL_WARN`<br>the WARN logging level.                                                                      |
    | `static int`      | `LOG_THREAD_NAME`<br>Set this flag if log records should include the name of the logging thread.             |
    | `static int`      | `LOG_TIME`<br>Set this flag if log records should include the date/time of the logging event.                |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                                        |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static int`      | `addGlobalOutputStream``(java.io.PrintStream ps)`<br>Adds a global log outputstream.                                                                          |
    | `static int`      | `addGlobalOutputStream``(java.io.PrintStream ps, java.lang.String name)`<br>Adds a global log outputstream to the given namespace.                            |
    | `int`             | `addOutputStream``(java.io.PrintStream ps)`<br>Adds a logging output stream.                                                                                  |
    | `void`            | `debug``(java.lang.Exception e)`<br>Logs a debug exception                                                                                                    |
    | `void`            | `debug``(java.lang.String message)`<br>Logs a debug message                                                                                                   |
    | `void`            | `debug``(java.lang.String sourceClass, java.lang.String sourceMethod, java.lang.String message)`<br>Logs a debug message                                      |
    | `void`            | `error``(java.lang.Exception e)`<br>Logs a error exception                                                                                                    |
    | `void`            | `error``(java.lang.String message)`<br>Logs an error                                                                                                          |
    | `void`            | `error``(java.lang.String sourceClass, java.lang.String sourceMethod, java.lang.String message)`<br>Logs an error                                             |
    | `void`            | `fatal``(java.lang.Exception e)`<br>Logs a fatal exception                                                                                                    |
    | `void`            | `fatal``(java.lang.String message)`<br>Logs a fatal event                                                                                                     |
    | `void`            | `fatal``(java.lang.String sourceClass, java.lang.String sourceMethod, java.lang.String message)`<br>Logs a fatal event                                        |
    | `void`            | `finest``(java.lang.Exception e)`<br>Logs a debug exception                                                                                                   |
    | `void`            | `finest``(java.lang.String message)`<br>Logs a very fine-level message                                                                                        |
    | `void`            | `finest``(java.lang.String sourceClass, java.lang.String sourceMethod, java.lang.String message)`<br>Logs a very fine-level message                           |
    | `int`             | `getFlags``()`<br>Gets the current flags of this instance.                                                                                                    |
    | `static int`      | `getGlobalFlags``()`<br>Gets the current global logging flags.                                                                                                |
    | `static int`      | `getGlobalLevel``()`<br>Gets the current global logging level.                                                                                                |
    | `int`             | `getLevel``()`<br>Gets the logging level of this instance.                                                                                                    |
    | `static Logger`   | `getLogger``(java.lang.String name)`<br>Creates an instance of Logger with given name.                                                                        |
    | `static Logger`   | `getLogger``(java.lang.String name, int level)`<br>Creates an instance of Logger with given name and level.                                                   |
    | `void`            | `info``(java.lang.Exception e)`<br>Logs an info exception                                                                                                     |
    | `void`            | `info``(java.lang.String message)`<br>Logs a piece of information (such as configuration et al).                                                              |
    | `void`            | `info``(java.lang.String sourceClass, java.lang.String sourceMethod, java.lang.String message)`<br>Logs a piece of information (such as configuration et al). |
    | `static void`     | `readGlobalConfig``(java.util.Properties p)`<br>Reads the propeties and sets global configuration accordingly.                                                |
    | `void`            | `setFlags``(int flags)`<br>Sets the flags (an OR'ed integer of all desired flags)                                                                             |
    | `static void`     | `setGlobalFlags``(int f)`<br>Sets the global logging flags.                                                                                                   |
    | `static void`     | `setGlobalFlags``(int f, java.lang.String name)`<br>Sets the global logging flags for the named loggers only.                                                 |
    | `static void`     | `setGlobalLevel``(int level)`<br>Sets the global logging level.                                                                                               |
    | `static void`     | `setGlobalLevel``(int level, java.lang.String name)`<br>Sets the global logging level for the named loggers.                                                  |
    | `static void`     | `setGlobalOutputStream``(java.io.PrintStream ps)`<br>Sets the global log outputsream.                                                                         |
    | `static void`     | `setGlobalOutputStream``(java.io.PrintStream ps, java.lang.String name)`<br>Sets the global log outputsream for the named hiearchy.                           |
    | `void`            | `setLevel``(int level)`<br>Sets the logging level of this instance.                                                                                           |
    | `void`            | `setOutputStream``(java.io.PrintStream ps)`<br>Sets the logging output stream.                                                                                |
    | `void`            | `warn``(java.lang.Exception e)`<br>Logs a warning exception                                                                                                   |
    | `void`            | `warn``(java.lang.String message)`<br>Logs a warning                                                                                                          |
    | `void`            | `warn``(java.lang.String sourceClass, java.lang.String sourceMethod, java.lang.String message)`<br>Logs a warning                                             |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### LEVEL_FATAL

          public static final int LEVEL_FATAL

      the highest logging level; Logs unrecoverable program events.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### LEVEL_ERROR

          public static final int LEVEL_ERROR

      the ERROR logging level. Logs errors detected in the program. Usually recoverable.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### LEVEL_WARN

          public static final int LEVEL_WARN

      the WARN logging level. Logs warnings.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### LEVEL_INFO

          public static final int LEVEL_INFO

      the INFO logging level, used for logging program configuration and other useful information.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### LEVEL_DEBUG

          public static final int LEVEL_DEBUG

      the DEBUG logging level. logs all necessary traces for debugging purpose
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### LEVEL_FINEST

          public static final int LEVEL_FINEST

      the finest possible logging level. Everything is logged.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### LOG_THREAD_NAME

          public static final int LOG_THREAD_NAME

      Set this flag if log records should include the name of the logging thread. The default setting is on so that no thread name will appear in any log record.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### LOG_TIME

          public static final int LOG_TIME

      Set this flag if log records should include the date/time of the logging event. By default this filter is on so that no date/time will be recorded in any log record.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getLogger

          public static Logger getLogger(java.lang.String name)

      Creates an instance of Logger with given name.
      Parameters:
      `name` - the name for the new logger instance. The name should follow Java class package convention. Examples are "com.foo.bar" or "oracle.lbs.TestClass".

    <!-- -->

    - #### getLogger

          public static Logger getLogger(java.lang.String name,
                                         int level)

      Creates an instance of Logger with given name and level.
      Parameters:
      `name` - the name for the new logger instance. The name should follow Java class package convention. Examples are "com.foo.bar" or "oracle.lbs.TestClass".

      `level` - the logging level for this instance. Any log messages that are lower than this level will be ignored.

    <!-- -->

    - #### setGlobalLevel

          public static void setGlobalLevel(int level)

      Sets the global logging level. This level will be inherited by each Logger instance. All existing loggers will be affected and use this new logging level.
      Parameters:
      `level` - the logging level

    <!-- -->

    - #### setGlobalLevel

          public static void setGlobalLevel(int level,
                                            java.lang.String name)

      Sets the global logging level for the named loggers. All the loggers with the name and under that name hiearchy will be affected by this new logging level.
      Parameters:
      `level` - the new logging level

      `name` - the namespace for the affected loggers

    <!-- -->

    - #### getGlobalLevel

          public static int getGlobalLevel()

      Gets the current global logging level.
      Returns:
      the current global logging level

    <!-- -->

    - #### setGlobalFlags

          public static void setGlobalFlags(int f)

      Sets the global logging flags. This will affect all existing loggers.
      Parameters:
      `f` - the new global logging flags.

    <!-- -->

    - #### setGlobalFlags

          public static void setGlobalFlags(int f,
                                            java.lang.String name)

      Sets the global logging flags for the named loggers only.
      Parameters:
      `f` - the new global logging flags.

      `name` - the namespace of affected loggers

    <!-- -->

    - #### getGlobalFlags

          public static int getGlobalFlags()

      Gets the current global logging flags.
      Returns:
      the current global logging flags.

    <!-- -->

    - #### readGlobalConfig

          public static void readGlobalConfig(java.util.Properties p)

      Reads the propeties and sets global configuration accordingly. All the settings will be effective in all existing Loggers.
      Parameters:
      `p` - the properties. The following three properties are supported:

                     log_level =  fatal | error | warn | info | debug
                     log_time  = true | false
                     log_thread_name = true | false


    <!-- -->

    - #### setGlobalOutputStream

          public static void setGlobalOutputStream(java.io.PrintStream ps)

      Sets the global log outputsream. All existing loggers will be affected to use this new setting.
      Parameters:
      `ps` - the new PrintStream to use as logging destination.

    <!-- -->

    - #### setGlobalOutputStream

          public static void setGlobalOutputStream(java.io.PrintStream ps,
                                                   java.lang.String name)

      Sets the global log outputsream for the named hiearchy. All loggers in the given name space will use this new setting. This outputstrem will replace any existing ones.
      Parameters:
      `ps` - the new PrintStream to use as logging destination.

    <!-- -->

    - #### addGlobalOutputStream

          public static int addGlobalOutputStream(java.io.PrintStream ps)

      Adds a global log outputstream. This adds to the list of log outputstreams that are already exist. This operation affects all existing Loggers.
      Parameters:
      `ps` - the new outputstream to be added.

    <!-- -->

    - #### addGlobalOutputStream

          public static int addGlobalOutputStream(java.io.PrintStream ps,
                                                  java.lang.String name)

      Adds a global log outputstream to the given namespace. This adds to the list of log outputstreams that are already exist in all named Loggers.
      Parameters:
      `ps` - the new outputstream to be added.

      `name` - the named loggers will be affected.

    <!-- -->

    - #### fatal

          public void fatal(java.lang.String message)

      Logs a fatal event

    <!-- -->

    - #### fatal

          public void fatal(java.lang.Exception e)

      Logs a fatal exception

    <!-- -->

    - #### fatal

          public void fatal(java.lang.String sourceClass,
                            java.lang.String sourceMethod,
                            java.lang.String message)

      Logs a fatal event

    <!-- -->

    - #### error

          public void error(java.lang.String message)

      Logs an error

    <!-- -->

    - #### error

          public void error(java.lang.String sourceClass,
                            java.lang.String sourceMethod,
                            java.lang.String message)

      Logs an error

    <!-- -->

    - #### error

          public void error(java.lang.Exception e)

      Logs a error exception

    <!-- -->

    - #### warn

          public void warn(java.lang.String message)

      Logs a warning

    <!-- -->

    - #### warn

          public void warn(java.lang.String sourceClass,
                           java.lang.String sourceMethod,
                           java.lang.String message)

      Logs a warning

    <!-- -->

    - #### warn

          public void warn(java.lang.Exception e)

      Logs a warning exception

    <!-- -->

    - #### info

          public void info(java.lang.String message)

      Logs a piece of information (such as configuration et al).

    <!-- -->

    - #### info

          public void info(java.lang.String sourceClass,
                           java.lang.String sourceMethod,
                           java.lang.String message)

      Logs a piece of information (such as configuration et al).

    <!-- -->

    - #### info

          public void info(java.lang.Exception e)

      Logs an info exception

    <!-- -->

    - #### debug

          public void debug(java.lang.String message)

      Logs a debug message

    <!-- -->

    - #### debug

          public void debug(java.lang.String sourceClass,
                            java.lang.String sourceMethod,
                            java.lang.String message)

      Logs a debug message

    <!-- -->

    - #### debug

          public void debug(java.lang.Exception e)

      Logs a debug exception

    <!-- -->

    - #### finest

          public void finest(java.lang.String message)

      Logs a very fine-level message

    <!-- -->

    - #### finest

          public void finest(java.lang.String sourceClass,
                             java.lang.String sourceMethod,
                             java.lang.String message)

      Logs a very fine-level message

    <!-- -->

    - #### finest

          public void finest(java.lang.Exception e)

      Logs a debug exception

    <!-- -->

    - #### setLevel

          public void setLevel(int level)

      Sets the logging level of this instance.

    <!-- -->

    - #### getLevel

          public int getLevel()

      Gets the logging level of this instance.

    <!-- -->

    - #### setFlags

          public void setFlags(int flags)

      Sets the flags (an OR'ed integer of all desired flags)

    <!-- -->

    - #### getFlags

          public int getFlags()

      Gets the current flags of this instance.

    <!-- -->

    - #### setOutputStream

          public void setOutputStream(java.io.PrintStream ps)

      Sets the logging output stream.

    <!-- -->

    - #### addOutputStream

          public int addOutputStream(java.io.PrintStream ps)

      Adds a logging output stream.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](LASImportExport.md)
- [Next Class](Pc2Dem.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
