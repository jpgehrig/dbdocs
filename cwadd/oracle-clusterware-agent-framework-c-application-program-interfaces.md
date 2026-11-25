Oracle Clusterware manages applications registered as resources with Oracle Clusterware and must have access to application-specific primitives that have the ability to start, stop, and monitor a specific resource. Oracle Clusterware runs all resource-specific commands through an entity called an agent.

An agent is a program that contains the agent framework and user code to manage resources. The agent framework is a C library that enables you to plug in your application-specific code to manage customized applications. You program all of the actual application management functions in C or C++, such as starting, stopping, and checking the health of an application, into the agent. These functions are referred to as entry points. The agent framework is responsible for invoking these entry point functions on behalf of Oracle Clusterware. Agent developers can use these entry points to plug in the required functionality for a specific resource regarding how to start, stop, and monitor a resource. Agents are capable of managing multiple resources.

This appendix includes the following topics:

- Agent Framework Data Types

- Agent Framework Context Initialization and Persistence

- Prototype for C and C++ Entry Point Functions

- C and C++ Entry Point Types and Codes

- C and C++ Entry Point Function Return Values

- Multithreading Considerations

- Deprecated APIs

- API Reference

- Agent Example

### Agent Framework Data Types

The Oracle Clusterware agent framework uses Oracle-defined portable data types to represent strings and numbers. By using these data types, you can build and run agent programs on multiple platforms.

Table G-1 lists and describes the Oracle data types used in the agent framework.

Table G-1 Oracle Data Types Used in the Agent Framework

| Oracle Data Type | Description                                                        |
|:-----------------|:-------------------------------------------------------------------|
| ub4              | Unsigned 32-bit integer                                            |
| sb4              | Signed 32-bit integer                                              |
| oratext\*        | C style null-terminated strings, explicit cast to char \* required |

The agent framework APIs return a status value of type `clsagfwret`, as follows:

- `CLSAGFW_SUCCESS`: Function processed successfully
- `CLSAGFW_FAIL`: There was error in the parameters or in execution of the function
-

String values returned by an API are only accessible in the scope of the current command entry point. Agents can copy the returned string value to its own buffers to retain the value.

### Agent Framework Context Initialization and Persistence

The agent framework is initialized by the `clsagfw_init()` function call. There is no context that you need to maintain. Action entry point functions are passed a pointer to the agent framework context (type `clsagfw_aectx`). This context is specific to the entry point being called and cannot be used beyond the scope of the entry point. Other agent framework APIs take this context pointer as a parameter. This is an opaque data structure that the agent framework maintains but does not explicitly initialize or destroy.

### Prototype for C and C++ Entry Point Functions

The agent implements the entry point functions for the resource management commands and registers these functions with the agent framework.

The agent framework calls an entry point function to run a command or action on a resource. The entry point functions need to conform to the following prototype and convention:

    typedef ub4 (*clsagfw_action_entry) (const clsagfw_aectx *aectx)

The entry point function is called with a pointer to a context area that the agent framework maintains. This function should return a value indicating the status of execution of the entry point. For the CHECK entry point, the function returns the current state of the resource.

If you develop the agent using C++, then you declare the entry point function prototypes using the `extern ‘C'` keyword.

### C and C++ Entry Point Types and Codes

The agent framework currently defines seven entry point types corresponding to resource management commands and operations performed on a resource.

Agents must register entry points for START, STOP, CHECK, and CLEAN commands. Other command entry points are optional. The agent registers entry points by calling the `clsagfw_set_entrypoint()` API for each resource type and command. Table G-2 lists and describes entry point types and their equivalent type codes.

Table G-2 Entry Point Types

| Name   | Description                                     | Type Code                  |
|:-------|:------------------------------------------------|:---------------------------|
| START  | Start a resource and bring it online            | CLSAGFW_ACTION_START       |
| STOP   | Stop a resource and take it offline             | CLSAGFW_ACTION_STOP        |
| CLEAN  | Clean up after a failed command on the resource | CLSAGFW_ACTION_CLEAN       |
| CHECK  | Check the state of the resource                 | CLSAGFW_ACTION_CHECK       |
| ABORT  | End an running command that has timed out       | CLSAGFW_ACTION_ABORT       |
| DELETE | Resource is about to be deleted                 | CLSAGFW_ACTION_RES_DELETED |
| MODIFY | Resource is modified                            | CLSAGFW_RESATTR_MODIFIED   |
| ACTION | Invoke custom action on the resource            | CLSAGFW_RES_ACTION         |

**See Also:**

"[Oracle Clusterware Resources and Agents](making-applications-highly-available-using-oracle-clusterware.md)" for more information about entry points

### C and C++ Entry Point Function Return Values

All entry point functions, except for the CHECK entry point, return one of the following values to indicate the status of execution of the entry point:

- CLSAGFW_AE_SUCCESS: Entry point execution completed successfully

- CLSAGFW_AE_FAIL: Entry point execution failed

The agent framework calls the CHECK entry point function to monitor the state of the resource. This function returns one of the following values that represents the current state of the resource:

- CLSAGFW_ONLINE
- CLSAGFW_UNPLANNED_OFFLINE
- CLSAGFW_PLANNED_OFFLINE
- CLSAGFW_UNKNOWN
- CLSAGFW_PARTIAL
- CLSAGFW_FAILED

**See Also:**

"[Agents in Oracle Clusterware](making-applications-highly-available-using-oracle-clusterware.md)" for more information about evaluating and returning the state of a resource

### Multithreading Considerations

The Oracle Clusterware agent framework is multithreaded by design. The agent code can also start new threads to run application-specific functionality, such as monitoring external event sources.

The agent framework processes only one entry point of a resource at a time, with the only exception being the ABORT entry point which is invoked to end a currently active action on a resource. C and C++ developers must ensure that all agent code is multithread safe. Access to global variables and other resources must be serialized using locking mechanisms, such mutexes. Other external C or C++ libraries included by the agent should also be multithread safe.

### Deprecated APIs

Table G-3 lists the deprecated agent framework APIs and the corresponding replacement APIs for Oracle Clusterware.

Table G-3 Deprecated Agent Framework APIs

| Deprecated API          | Replacement              |
|:------------------------|:-------------------------|
| `clsagfw_exit()`        | `clsagfw_exit2()`        |
| `clsagfw_send_status()` | `clsagfw_send_status2()` |

### API Reference

This section lists and describes the following functions:

- `clsagfw_add_type()`

- `clsagfw_check_resource()`

- `clsagfw_create_attr_iterator()`

- `clsagfw_delete_cookie()`

- `clsagfw_exit2()`

- `clsagfw_get_attr_from_iterator()`

- `clsagfw_get_attrvalue()`

- `clsagfw_get_check_type()`

- `clsagfw_get_cmdid()`

- `clsagfw_get_cookie()`

- `clsagfw_get_request_action_name()`

- `clsagfw_get_resource_id()`

- `clsagfw_get_resource_name()`

- `clsagfw_get_retry_count()`

- `clsagfw_get_type_name()`

- `clsagfw_init()`

- `clsagfw_is_cmd_timedout()`

- `clsagfw_log()`

- `clsagfw_modify_attribute()`

- `clsagfw_reset_attr_iterator()`

- `clsagfw_send_status2()`

- `clsagfw_set_cookie()`

- `clsagfw_set_entrypoint()`

- `clsagfw_set_exitcb()`

- `clsagfw_set_resource_state_label()`

- `clsagfw_startup()`

#### clsagfw_add_type()

Registers a resource type that the agent manages.

##### Syntax

    clsagfwret clsagfw_add_type(const oratext *type_name);

##### Input

`type_name`: Resource type name that the agent is to manage

##### Usage Notes

On startup, an agent must register all the resource types that it manages. A single agent can manage multiple resource types and multiple resources.

#### clsagfw_check_resource()

Initiates a check action on a specific resource.

##### Syntax

    void clsagfw_check_resource(const oratext *pResId)

##### Input

`pResId`: Identification of the resource

##### Usage Notes

Agents can use this function in entry points or in other background threads to initiate a check action on a specific resource. The agent framework schedules and runs the check action in another thread. This function has no effect if invoked from a CHECK entry point.

#### clsagfw_create_attr_iterator()

Creates an iterator to access all the attributes of the current resource.

##### Syntax

    clsagfwret clsagfw_create_attr_iterator(const clsagfw_aectx *pAeCtx,
                                            clsagfw_ai_flags    flags);

##### Input

- `pAeCtx`: Agent framework context pointer that is passed to entry points

- `flags`:

  `CLSAGFW_ALL_ATTRS`: All attributes of the resource

  `CLSAGFW_MODIFIED_ATTRS`: Only modified attributes

##### Usage Notes

Agents call this function to create an iterator to navigate through all the attributes of the resource. This is useful for agents managing multiple resources of different types. The iterator is an internal iterator maintained in the agent framework context. Each attribute is retrieved by calling the `clsagfw_get_attr_from_iterator()` API. Modified attributes can be accessed only in the MODIFY entry point. At any given time, an entry point can create only one iterator. All subsequent attempts to create an iterator gets the pointer to the iterator that is already created.

#### clsagfw_delete_cookie()

Deletes a cookie stored in the agent framework.

##### Syntax

    clsagfwret clsagfw_delete_cookie(const oratext *key);

##### Input

`key`: Key of the cookie, null terminated string

##### Usage Notes

This function deletes the cookie and frees all the memory used by the cookie and its value.

#### clsagfw_exit2()

Terminates the agent process with resource retry feedback.

##### Syntax

    void clsagfw_exit2(const oratext *rid, sb4 exitCode, bool retry);

##### Input

- `rid`: Resource ID of the resource causing the irrecoverable error

- `exitCode`: Process exit code

- `retry`: option to retry resource

##### Usage Notes

An agent can encounter a irrecoverable error when running an entry point for a resource and then must terminate the current process. An agent can use this API to end the agent process and provide feedback to the agent framework on the resource that is the cause for the irrecoverable error. If the retry parameter is set to true, then the current command on the resource is retried when the agent process restarts. If the parameter is set to false, then the current resource command is not retried and monitoring of the resource is disabled. This option can be used when a particular resource is the cause of repeated failures of an agent. The Oracle Clusterware server keeps track of the resources causing agent exits and automatically disables a resource if the failure rate is high. To re-enable a resource disabled due to high failure rate, must issue an explicit request to start the resource (for example, using CRSCTL).

The Oracle Clusterware server restarts the agent to continue monitoring resources managed by the agent.

#### clsagfw_get_attr_from_iterator()

Returns the next attribute name and value from the created iterator.

##### Syntax

    clsagfwret clsagfw_get_attr_from_iterator(const clsagfw_aectx *pAeCtx,
                                              const oratext **argName,
                                              const oratext **argValue);

##### Input

`pAeCtx`: Agent framework context pointer that is passed to entry points

##### Returns

- `argname`: Attribute name

- `argValue`: Attribute value

##### Usage Notes

Use this function to retrieve attributes after the iterator has been created in the agent framework context. The iterator is advanced to the next attribute when this function returns. If the API returns CLSAGFW_FAIL, then there are no more attributes to retrieve for the resource.

#### clsagfw_get_attrvalue()

Obtains the value of an attribute of the current resource.

##### Syntax

    void clsagfw_get_attrvalue(const clsagfw_aectx *pAeCtx,
                               const oratext *pAttrName,
                               const oratext **pAttrValue);

##### Input

- `pAeCtx`: Agent framework context pointer that is passed to entry points

- `pAttrName`: Name of attribute to retrieve

##### Returns

`pAttrValue`: Value of the specified attribute

##### Usage Notes

Agents use this API to retrieve the value of a single attribute of the current command resource.

#### clsagfw_get_check_type()

Returns the type of the check command currently being processed.

##### Syntax

    clsagfw_checktype
    clsagfw_get_check_type(const clsagfw_aectx *pAeCtx);

##### Input

`pAeCtx`: Agent framework context pointer that is passed to entry points

##### Usage Notes

The agent framework invokes the CHECK entry point of a resource for multiple conditions. By using this function, the agent can identify the exact condition for the current CHECK entry point and perform appropriate actions.

Possible conditions include:

- CLSAGFW_INITIAL_CHECK: Check entry point invoked as part of the initial probe stage when the Oracle Clusterware server is started or restarted.

- CLSAGFW_CHECK_AFTER_CMD: Check entry point invoked to follow up the prior action (such as start or stop) to determine the resultant resource state after the action execution.

- CLSAGFW_PERIODIC_CHECK: Check entry point invoked by the agent framework at periodic intervals to monitor the state of a resource. The time interval is specified in the `CHECK_INTERVAL` attribute of the resource.

- CLSAGFW_EXTERNAL_CHECK: Check entry point invoked by agent framework when it receives an explicit check request from external entities, such as CRSCTL.

- CLSAGFW_CHECKFROM_EP: Check action initiated by the agent itself by calling the `clsagfw_check_resource()` API.

#### clsagfw_get_cmdid()

Returns the type of the command for which the entry point is invoked.

##### Syntax

    clsagfw_aecode clsagfw_get_cmdid(const clsagfw_aectx *pAeCtx);

##### Input

`pAeCtx`: Agent framework context pointer that is passed to entry points

##### Usage Notes

The agent can call this API in the ABORT entry point to determine the resource command that is being terminated.

#### clsagfw_get_cookie()

Retrieves the value of a cookie stored in the agent framework.

##### Syntax

    clsagfwret clsagfwret clsagfw_set_cookie(const oratext *key,
                                             const void **value);

##### Input

`key`: Key of the cookie, null terminated string

`Value`: Pointer to the value of the cookie

#### clsagfw_get_request_action_name()

Returns the name of the custom action to be performed on a resource.

##### Syntax

    const oratext *
    clsagfw_get_request_action_name(const clsagfw_aectx *pAeCtx);

##### Input

`pAeCtx`: Agent framework context that is passed to user entry points

##### Usage Notes

This function is called in the ACTION entry point to retrieve the action name that you specified in a request action command. You configure the list of actions for a resource in the ACTION attribute of the resource.

#### clsagfw_get_resource_id()

Retrieves the ID of the resource for which the entry point is being processed.

##### Syntax

    const oratext* clsagfw_get_resource_id(const clsagfw_aectx *pAeCtx);

##### Input

`pAeCtx`: Agent framework context pointer that is passed to entry points

##### Usage Notes

This function returns the Oracle Clusterware-generated resource ID. To retrieve the public display name of the resource, use the `clsagfw_get_resource_name()` API.

#### clsagfw_get_resource_name()

Retrieves the resource name of the current command.

##### Syntax

    const oratext*
      clsagfw_get_resource_name(const clsagfw_aectx *pAeCtx);

##### Input

`pAeCtx`: Agent framework context pointer that is passed to entry points

##### Usage Notes

This function returns the name of the resource for which the current command and entry point are being run.

#### clsagfw_get_retry_count()

Returns the retry attempt number for the current command.

##### Syntax

    ub4 clsagfw_get_retry_count(const clsagfw_aectx *pAeCtx)

##### Input

`pAeCtx`: Agent framework context that is passed to user entrypoints

##### Usage Notes

Agents can call this function in entrypoints to check if the current command is being retried. An agent process or Oracle Clusterware server process can terminate in the middle of running a command on a resource. Oracle Clusterware retries the failed command when the agent or server process restarts. The command may have successfully or partially run in the previous attempt. The agent can perform resume or clean up actions when Oracle Clusterware retries the command. The number of times a command can be retried is an internal parameter of Oracle Clusterware.

#### clsagfw_get_type_name()

Retrieves the type name of the resource for which the entry point is being run.

##### Syntax

    const oratext* clsagfw_get_type_name(const clsagfw_aectx *pAeCtx);

##### Input

`pAeCtx`: Agent framework context pointer that is passed to entry points

##### Usage Notes

This function returns the Oracle Clusterware-generated resource ID. To retrieve the public display name of the resource, use the `clsagfw_get_resource_name()` API.

#### clsagfw_init()

Initializes the agent framework.

##### Syntax

    clsagfwret clsagfw_init(sb4 argc,
                            oratext **argv,
                            ub4 flags,
                            const oratext *logName,
                            void *reserved);

##### Input

`argc`: Number of command line arguments passed to the agent process

`argv`: Command line arguments passed to the agent process

`flags`:

`logName`: Name of the log file for this agent

`reserved`: Pass NULL

##### Usage Notes

Oracle Clusterware automatically starts the agent configured for a resource when actions must be performed on the resource. On startup, the agent process calls this function first to initialize the agent framework run time. The command line arguments passed to the agent process by the Oracle Clusterware server must be passed to `clsagfw_init()`. After initialization is complete, the agent can register resource types that are managed by the agent.

#### clsagfw_is_cmd_timedout()

Returns the cause of the ABORT entry point.

##### Syntax

    bool clsagfw_is_cmd_timedout(const clsagfw_aectx *pAeCtx);

##### Input

`pAeCtx`: Agent framework context pointer that is passed to entry points

##### Usage Notes

Agents can use this function in the ABORT entry point to identify the cause of the ABORT entry point invocation. The ABORT entry point can either be invoked if a command execution time exceeds its time out value or if the Oracle Clusterware administrator terminates the command.

#### clsagfw_log()

Prints a diagnostic message to the agent log file.

##### Syntax

    void clsagfw_log(const clsagfw_aectx *pAeCtx,
                    const ub4 log_level,
                    const oratext *fmtp, ...);

##### Input

`pAeCtx`: Agent framework context that is passed to user entry points

`log_level`: Log level of the message in the range of 1-5

`fmtp`: Message format string, according to Standard C library print specifications

`...`: Variable parameters corresponding to the format string

##### Usage Notes

Agents call this function to log diagnostic messages that help in debugging and understanding agent execution. You can use the `LOG_LEVEL` parameter to control the volume of log messages. You can configure the current logging level of a resource using CRSCTL, as follows:

    $ crsctl set log level res "myResource1=3"

The misusages are logged to the agent log file in the `TODO` directory. By default, the name of the log file is the same as the agent executable name. You can change this by passing the `logName` parameter to the `clsagfw_init()` API.

#### clsagfw_modify_attribute()

Modifies an attribute of the current resource.

##### Syntax

    void clsagfw_modify_attribute(const clsagfw_aectx *pAeCtx,
                                  const oratext *pAttrName,
                                  const oratext *pAttrValue);

##### Input

`pAeCtx`: Agent framework context pointer that is passed to entry points

`pAttrName`: Name of attribute to be modified

`pAttrValue`: New value of attribute

##### Usage Notes

Agents can modify the value of an attribute of the current command resource by calling this API. A resource modification request is sent to the Oracle Clusterware server for validation and the updated attribute value is reflected in the agent only after confirmation from the Oracle Clusterware server. This function can be only called from the START, STOP, and CLEAN entry points.

#### clsagfw_reset_attr_iterator()

Resets the attribute iterator.

##### Syntax

    clsagfwret clsagfw_reset_attr_iterator(const clsagfw_aectx *pAeCtx,
                                           clsagfw_ai_flags    flags);

##### Input

`pAeCtx`: Agent framework context pointer that is passed to entry points

`flags`: Which attributes to be accessed:

`CLSAGFW_ALL_ATTRS`: All attributes of the resource

`CLSAGFW_MODIFIED_ATTRS`: Only modified attributes

##### Usage Notes

This function resets the iterator in the agent framework context so that agents can restart attribute navigation.

#### clsagfw_send_status2()

Reports progress, warning, and error messages to the Oracle Clusterware server and the user.

##### Syntax

    void clsagfw_send_status2(const clsagfw_aectx* pAeCtx,
                              const oratext*       pResId,
                              clsagfw_status_type type,
                              const oratext* fmtp,...);

##### Input

`pAeCtx`: Agent framework context pointer that is passed to entry points

`pResId`: Resource for which the message is being reported

`type`: One of the following types of messages:

`CLSAGFW_STATUS_PROGRESS`: Progress message

`CLSAGFW_STATUS_WARNING`: Warning message

`CLSAGFW_STATUS_ERROR`: Error message

`fmtp`: Message format string

`...`: Variables corresponding to positions in the message format string

##### Usage Notes

During execution of a command, the agent can send informational messages to the Oracle Clusterware server and to the user performing operations on resources. These messages can inform you about execution progress and if there are any warnings or errors.

#### clsagfw_set_cookie()

Stores a cookie and its value in the agent framework.

##### Syntax

    clsagfwret clsagfwret clsagfw_set_cookie(const oratext *key,
                                             const void *value);

##### Input

`key`: Key of the cookie, null terminated string

`Value`: Pointer to the value of the cookie to be stored

##### Usage Notes

The value of the saved cookie can be later retrieved by calling `clsagfw_get_cookie()`.

#### clsagfw_set_entrypoint()

Sets the C/C++ entry point function to be run for a particular action on the resource.

##### Syntax

    void clsagfw_set_entrypoint(const oratext *type_name,
                                clsagfw_action_entry action_entry,
                                clsagfw_aecode action_entrycode)

##### Input

`key`: Key of the cookie, null terminated string

`Value`: Pointer to the value of the cookie to be stored

##### Usage Notes

The value of the saved cookie can be later retrieved by calling `clsagfw_get_cookie()`.

#### clsagfw_set_exitcb()

Registers a function to be called when the agent process exits.

##### Syntax

    typedef void (*clsagfw_exit_callback) (sb4 exitCode);
    void clsagfw_set_exitcb(clsagfw_exit_callback exit_func)

##### Input

`exit_func`: Function to be invoked when agent process exits

##### Usage Notes

Agents can register a callback function to be invoked when the agent framework terminates the agent process. The callback function can perform proper clean up of any internal resources instantiated by the agent. If the agent process is exiting to recover from an irrecoverable error, then the Oracle Clusterware server does not restart the agent until the old incarnation has exited.

#### clsagfw_set_resource_state_label()

Sets a custom label on the current resource.

##### Syntax

    void clsagfw_set_resource_state_label(const clsagfw_aectx *pAeCtx,
                                          const oratext *pLabel);

##### Input

`pAeCtx`: Agent framework context pointer that is passed to entry points

`pLabel`: Label to associate with the resource, null terminated string

##### Usage Notes

Agents can use this function to set a descriptive label associated with the state of the resource. This label is reported in the `STATE_DETAILS` attribute of the resource.

#### clsagfw_startup()

Starts the agent framework.

##### Syntax

    clsagfwret clsagfw_startup(void)

##### Usage Notes

After the agent framework is initialized and the resource types and their entry points are registered, the agent calls this API to start the agent framework, which, in turn, starts the multithreaded infrastructure to monitor and perform actions on the resources.

On success, this function never returns to the calling thread. Entry points for the resource actions are invoked by the agent framework threads as and when required.

### Agent Example

Example G-1 details an agent implementation to manage a resource that represents a file.

Example G-1 demoagent1.cpp

    /* Copyright (c) 2004, 2012, Oracle and/or its affiliates.
    All rights reserved. */

    /*
     * NAME
     * Demoagent1.cpp: Demonstrates agent to monitor a file
     *
     * DESCRIPTION
     * This is a sample program that demonstrates an agent to monitor
     * a file. The agent has the following tasks:
     *  - On startup         : Create the file.
     *  - On shutdown        : Delete the file.
     *  - On check command   : Detect whether the file is present or not.
     *  - On clean command   : Delete the file.
     * This program can be used as a basis to build up more complicated
     * agents that manage real-world resources.
     *

    #include <stdlib.h>
    #include <stdio.h>
    #include <string.h>
    #include <clsagfw.h>

Include the agent framework `clsagfw.h` header file.

    #define TEST_TYPE1                   (oratext *) "HOTFILE_TYPE"
    #define TEST_PATHNAME_ATTR           (oratext *) "PATH_NAME"

    /*
     * NAME
     *    test_agent_exit
     * DESCRIPTION
     *    Function to clean up, called by framework whenever the agent
     *    process is about to terminate
     * PARAMS
     *    exitCode, which is an sb4 describing the reason for exit.
     * RETURNS
     *    void
     */
    void
    test_agent_exit(sb4 exitCode)
    {
      clsagfw_log(NULL, 1, (oratext *)"Demo Agent is exiting..\n");
    }

Exit callback function registered with the agent framework.

    /*
     * NAME
     *    type1_start
     * DESCRIPTION
     *    Action entry point for the 'start' command. Creates the file for
     *    monitoring.
     * PARAMS
     *    Pointer to the agent framework context
     * RETURNS
     *    ub4 which could be CLSAGFW_AE_FAIL or CLSAGFW_AE_SUCCESS
     *    depending on whether the action failed or succeeded.
     */
    ub4
    type1_start(const clsagfw_aectx *ectx)
    {
        ub4  ret = CLSAGFW_AE_FAIL;
        const oratext   *pResName  = NULL;
        const oratext   *pPathName = NULL;
        FILE *fp;

        clsagfw_log(ectx, 1, (oratext *)"Start action called..");

        /* Try to read the resource name */
        if (clsagfw_get_attrvalue(ectx, (oratext *)"NAME", &pResName) !=
                CLSAGFW_SUCCESS)
        {
          goto done;
        }

        /* Try to read the PATH_NAME attribute */
        if (clsagfw_get_attrvalue(ectx, TEST_PATHNAME_ATTR, &pPathName) !=
                CLSAGFW_SUCCESS)
        {
          goto done;
        }

Retrieve the resource name and the value of the `PATH_NAME` attribute using `clsagfw_get_attrvalue()`.

        clsagfw_log(ectx, 1,
                    (oratext *)"Start action arguments: resName = %s,
                    pathName = %s", pResName, pPathName);

        /* Try to create the file */
        fp = fopen((char *)pPathName, "w");

        if(!fp)
        {
          /* Could not create the file */
            clsagfw_log(ectx, 1, (oratext *) "START action for resource %s:
                        FAILED\n", pResName);
            ret = CLSAGFW_AE_FAIL;
        }
        else
        {
          /* Created the file successfully */
            clsagfw_log(ectx, 1, (oratext *) "START action for resource %s:
                        SUCCESS\n", pResName);
            ret = CLSAGFW_AE_SUCCESS;
          fclose(fp);
        }

    done:
        return ret;
    }

Diagnostic and error messages are logged to the agent log file by calling `clsagfw_log()`.

    /*
     * NAME
     *    type1_stop
     * DESCRIPTION
     *    Action entry point for the 'stop' and 'clean' commands. Deletes
     *    the file being monitored.
     * PARAMS
     *    Pointer to agent framework context
     * RETURNS
     *    ub4 which could be CLSAGFW_AE_FAIL or CLSAGFW_AE_SUCCESS
     *    depending on whether the action failed or succeeded.
     */
    ub4
    type1_stop (const clsagfw_aectx *ectx)
    {
        ub4             ret = CLSAGFW_AE_FAIL;
        const oratext   *pResName  = NULL;
        const oratext   *pPathName = NULL;

        clsagfw_log(ectx, 1, (oratext *)"Stop action called..");

        /* Try to read the resource name */
        if (clsagfw_get_attrvalue(ectx, (oratext *)"NAME", &pResName) !=
                CLSAGFW_SUCCESS)
        {
          clsagfw_log(ectx, 1, (oratext *)"STOP action: %s: Could not
                      read attribute\n", pResName);
          goto done;
        }

        /* Try to read the PATH_NAME attribute */
        if (clsagfw_get_attrvalue(ectx, TEST_PATHNAME_ATTR, &pPathName) !=
                CLSAGFW_SUCCESS)
        {
            pPathName = pResName;
        }

        clsagfw_log(ectx, 1,
                    (oratext *)"Stop action arguments: resName = %s,
                    pathName = %s", pResName, pPathName);

        /* Try to delete the file */
        if (remove((char *)pPathName))
        {
          /* Could not delete the file */
          clsagfw_log(ectx, 1, (oratext *)"STOP action for resource %s:
                      FAILED\n", pResName);
          ret = CLSAGFW_AE_FAIL;
        }
        else
        {
          /* Deleted the file successfully */
          clsagfw_log(ectx, 1, (oratext *)"STOP action for resource %s:
                      SUCCESS\n", pResName);
          ret = CLSAGFW_AE_SUCCESS;
        }

    done:
        return ret;
    }

    /*
     * NAME
     *    type1_check
     * DESCRIPTION
     *    Action entry point for the 'check' command. Determines if the
     *    file exists.
     * PARAMS
     *    Pointer to agent framework context.
     * RETURNS
     *    ub4 which gives the status of the resource. Check the
     *    agent framework reference for details on this function's
     *     return codes.
     */
    ub4
    type1_check(const clsagfw_aectx *ectx)
    {
        ub4             ret = CLSAGFW_UNKNOWN;
        const oratext   *pResName  = NULL;
        const oratext   *pPathName = NULL;
        FILE *fp;

        clsagfw_log(ectx, 1, (oratext *)"Check action called..");

        /* Try to read the resource name */
        if (clsagfw_get_attrvalue(ectx, (oratext *) "NAME", &pResName) !=
                CLSAGFW_SUCCESS)
        {
          goto done;
        }

        /* Try to read the PATH_NAME attribute */
        if (clsagfw_get_attrvalue(ectx, TEST_PATHNAME_ATTR, &pPathName) !=
                CLSAGFW_SUCCESS)
        {
          clsagfw_log(ectx, 1, (oratext *)"CHECK action: %s: Could not
                      read attribute\n", pResName);
          goto done;
        }

        clsagfw_log(ectx, 1,
                    (oratext *)"Check action arguments: resName = %s,
                    pathName = %s", pResName, pPathName);

        /* Check if the file is accessible */
        fp = fopen((char *)pPathName, "r");
        if (!fp)
        {
          /* Could not open file */
          clsagfw_log(ectx, 1, (oratext *)"CHECK action: %s status –
                      UNPLANNED_OFFLINE\n", pResName);
          ret = CLSAGFW_UNPLANNED_OFFLINE;
        }
        else
        {
          /* Opened file successfully */
          clsagfw_log(ectx, 1,(oratext *)"CHECK action: %s status –
                      ONLINE\n", pResName);
          fclose(fp);
          ret = CLSAGFW_ONLINE;
        }

    done:
        return ret;
    }

    /*
     * Initialization of the agent framework and registration of types is
     *  done in main.
     */
    int main(sb4 argc, oratext **argv)
    {
        clsagfw_log(NULL, 1, (oratext *)" *** Agent Framework Demo Agent
                    Started *** \n");

        /*
         * Initialize the agent framework
         */
        if (clsagfw_init(argc, argv, 0, NULL, 0)
            != CLSAGFW_SUCCESS)
        {
          clsagfw_log(NULL, 1, (oratext *)"Failed to initilize the agent
                      framework\n");
          clsagfw_exit(-1);
        }

        /*
         * Set the exit callback function
         */
        clsagfw_set_exitcb(test_agent_exit);

        /*
         * Add the type definition to the framework
         */
        if (clsagfw_add_type(TEST_TYPE1) != CLSAGFW_SUCCESS)
        {
          clsagfw_log(NULL, 1,(oratext *)"Failed in adding type %s to the
                      framework\n", TEST_TYPE1);
          clsagfw_exit(-1);
        }

        /*
         * Set all entry points for for HOTFILE_TYPE
         */
        clsagfw_set_entrypoint(TEST_TYPE1, type1_start,
                               CLSAGFW_ACTION_START);
        clsagfw_set_entrypoint(TEST_TYPE1, type1_stop,
                               CLSAGFW_ACTION_STOP);
        clsagfw_set_entrypoint(TEST_TYPE1, type1_check,
                               CLSAGFW_ACTION_CHECK);
        clsagfw_set_entrypoint(TEST_TYPE1, type1_stop,
                               CLSAGFW_ACTION_CLEAN);

        clsagfw_log(NULL, 1, (oratext *)"Added resource type [%s] to the
                    agent framework\n", TEST_TYPE1);

        /*
         * All set to go, Start the framework. This function does not
         * return if the framework starts successfully.
         */
        clsagfw_startup();

        /*** NOT REACHED **/

        return 0;
    }
