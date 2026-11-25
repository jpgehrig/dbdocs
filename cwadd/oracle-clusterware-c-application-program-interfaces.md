This appendix describes the Oracle Clusterware C application program interfaces (APIs). This appendix contains the following topics:

- About the Programming Interface (C API) to Oracle Clusterware

- Interactive CLSCRS APIs

- Non-Interactive CLSCRS APIs

- Command Evaluation APIs

- Server Categorization APIs

- STAT3 API

- Miscellaneous APIs

**See Also:**

[Making Applications Highly Available Using Oracle Clusterware](making-applications-highly-available-using-oracle-clusterware.md) for detailed information about using Oracle Clusterware to make applications highly available

### About the Programming Interface (C API) to Oracle Clusterware

This section contains information about using the programming interface (C API) to Oracle Clusterware (CLSCRS).

- Overview

- Operational Notes

- Deprecated CLSCRS APIs

- Changes to Existing CLSCRS APIs

#### Overview

CLSCRS is a set of C-based APIs for Oracle Clusterware. The CLSCRS APIs enable you to manage the operation of entities that are managed by Oracle Clusterware. These entities include resources, resource types, servers, and server pools. You use the APIs to register user applications with Oracle Clusterware so that the clusterware can manage them and maintain high availability. Once an application is registered, you can manage it and query the application's status. If you no longer need the application, then you can stop it and unregister it from Oracle Clusterware.

Oracle Clusterware services are provided by Cluster Ready Services that runs as part of Oracle Clusterware. The CLSCRS API uses a context that is explicitly named in all function calls. The API does not store anything at the process or thread level. You can use the callbacks for diagnostic logging.

**Note:**

You can install the Oracle Clusterware high availability API from the Oracle Database client installation media.

#### Operational Notes

Describes programming interface (C API) to Oracle Clusterware configuration and operational requirements.

This section includes the following topics:

- Context Initialization and Persistence

- Threading Support

- CLSCRS API Data Structures

- Memory Management

- Error Handling and Tracing

- Callback Mechanism

- Filters

- Script Agent Usage

- Help Interface

##### Context Initialization and Persistence

To use the CLSCRS APIs, you must first initialize the `clscrs` context. The calls to create and terminate this context are:

- `clscrs_init_crs`: Initializes the `clscrs` context

- `clscrs_term_crs`: Terminates the `clscrs` context

The caller is responsible for terminating the context when it is no longer needed.

##### Threading Support

If initialized with the `CLSCRS_FLAG_USETHREADS` flag, then the CLSCRS API may spawn threads internally. Every API function runs in the context of the calling thread. The API context object may not be used concurrently by multiple threads. However, no thread-affinity on the part of the client is required. A process may create multiple API contexts and use those on different threads, subject to the one-thread-per-one-context-at-a-time rule.

##### CLSCRS API Data Structures

The following entities are passed into the API calls and contain return values from the API call:

- `clscrs_sp`: A stringpair (`sp`) contains a name and a value string. The value can be NULL. It is created and destroyed, and its contents can be examined and the value replaced. A stringpair can be a member of exactly one stringpair list (`splist`).

- `clscrs_splist`: A stringpair list (`splist`) is a list of zero or more stringpairs used in various contexts. An API can add stringpairs to or remove them from a stringpair list, or the API can iterate stringpairs.

- `clscrs_entity_type`: The enumeration type you can use to identify the type of Oracle Clusterware entity.

  The enumeration types are defined, as follows:

      /* enum to specify the entity type */
      typedef enum
      {
         clscrs_entity_res              = 1, /* resource */
         clscrs_entity_restype          = 2, /* resource type */
         clscrs_entity_serverpool       = 3, /* server pool */
         clscrs_entity_server           = 4, /* server */
         clscrs_entity_resinst          = 5, /* resource instances */
         clscrs_entity_config_policy    = 6, /* configuration policy */
         clscrs_entity_config_policyset = 7, /* configuration policy
      set */
         clscrs_entity_server_category  = 8  /* server category */
      } clscrs_entity_type;

- `clscrs_crsentity`: This data structure (`crsentity`) represents an Oracle Clusterware entity, which contains the name and additional data appropriate to the context in which the Oracle Clusterware entity is used. Sometimes an API contains Oracle Clusterware entity attribute data and other times it carries status and return messages about an operation. A single entity can be a member of exactly one `clscrs_crsentitylist`.

- `clscrs_crsentitylist`: An entity list (`crsentitylist`) is a data structure that contains zero or more instances of a `clscrs_crsentity`. An API can add entities to or remove them from an entity list, or the API can iterate entities.

##### Memory Management

The CLSCRS APIs work on elements and lists. The elements are added to lists. The memory for both elements and lists is allocated and released through explicit API calls. It is the caller's responsibility to release the memory that they allocate. However, when elements are added to lists, only the list must be destroyed: the destruction of the list destroys its elements implicitly. The elements must be destroyed when they are not added to any list. For recursive lists, destroying the parent list also destroys any lists contained within it. The `clscrs_sp` and `clscrs_crsentity` elements must be destroyed by the caller. If they are part of a `clscrs_splist` or `clscrs_crsentitylist`, destroying the list destroys the respective `clscrs_sp` and `clscrs_crsentity` entities.

For example, when a resource is created and added to a resource list, only the resource list must be destroyed, but not the individual resource. Destroying the resource list releases the memory for the individual resource, too.

Memory is allocated by the API through the following calls:

    clscrs_sp_create()
    clscrs_crsentity_create()
    clscrs_serverpool_create()
    clscrs_type_create()
    clscrs_splist_create()
    clscrs_crsentitylist_create()
    clscrs_entity_id_create()

Each of the calls in the preceding list has a corresponding `clscrs_*_destroy()` call.

##### Error Handling and Tracing

Interactive and non-interactive CLSCRS APIs each use a different error-handling mechanism.

For non-interactive CLSCRS APIs, the error code is returned as the return value of the function call. For example:

    clscrsret clscrs_sp_get_value(clscrs_sp *sp, oratext **value);

The error code is returned as a `clscrsret` value.

For interactive CLSCRS APIs, the output result is represented, as follows:

1.  The return value of the function call provides a high-level output of the request. Did the request reach the server? Was it completely successful, or completely or only partially unsuccessful? A successful return value means the request was received, processed, and the outcome was successful for all entities requested.

2.  For each entity on which the request operated, there is a programmatic completion code stored in the `op_status` list. If the value is not `success`, it indicates the high-level type of the problem specific to processing the request for the particular object.

3.  Optionally, the API might indicate that it wants to receive localized, human-readable error, warning, or status messages by using the callback mechanism. Each invocation of the callback provides the message, message type (severity), and the ID of the object to which the callback invocation pertains.

For example:

    CLSCRS_STAT clscrs_register_resource2(clscrs_crsentitylist *in_crsentitylist, uword flags,
                                           clscrs_msgf2 msgf, void *msgarg,
                                           clscrs_crsentitylist *op_status);

1.  The function returns an error code of value `CLSCRS_STAT`.

2.  The CRSD sends error messages, warning messages, and progress messages back to the client through the `clscrs_msgf2` callback. The client must implement the callback to process these messages returned by the CRSD.

3.  In previous Oracle Clusterware releases, the API also contained results of each operation on the Oracle Clusterware entities as part of the `op_status` list. You can access that information using the following API:

        clscrsret clscrs_entity_get_op_status(clscrs_entity *res, CLSCRS_STAT *status,
                                            oratext **msg);

    The `status` argument contains a status code about the CRSD operation on the Oracle Clusterware entity. Additionally, the `msg` argument contains a message from the CRSD about the result of the operation. Though the `op_status` list continues to contain the results of the CRSD operation for each Oracle Clusterware entity in the `msg` argument, usage of the `msg` argument to get the error codes and messages has now been deprecated and is not supported for any use of the API on a new entity. Only pre-existing use cases (for acting on resources, specifically) are supported. Use the callback function to process any messages returned by the CRSD.

##### Callback Mechanism

Interactive CLSCRS APIs provide a callback mechanism that the clients can use to process error messages, warning messages, and progress messages sent by the CRSD.

The signature of the callback mechanism is:

    typedef  void (*clscrs_msgf2)(void *usrp, const oratext *id, const oratext *msg,
                    clscrs_msgtype msgtype);

In the preceding syntax:

- `usrp`: Is a user-supplied pointer that probably contains the context of the call

- `id`: Is the identifier of the entity to which the message corresponds

- `msg`: Is the output text

- `msgtype`: Is the type of the message; either error, warning, or progress

Example H-1 describes an example of the callback mechanism.

Example H-1 Callback Mechanism

    void myCallback(void *arg, const oratext *pId, const oratext *pMsg,
                    clscrs_msgtype msgType)
    {
        if (pMsg != NULL)
       {
           cout << pMsg << endl;
        }
    }

Example H-2 describes how to use the callback mechanism in an interactive API.

Example H-2 Using the Callback Mechanism In an Interactive API

    clscrs_start_resource2(pResIdList, NULL,
                           env, myCallback, NULL,
                           0, pOpStatus);

You can also print debug trace messages for the API, itself by passing the `CLSCRS_FLAG_TRACE` flag when creating the context. The signature for context creation is:

    CLSCRS_STAT clscrs_init_crs(clscrs_ctx **ctx, clscrs_msgf2 errf, void *errCtx,
                                 ub4 flags);

For the trace messages to work, you must specify both the `CLSCRS_FLAG_TRACE` flag and a `clscrs_msgf2` callback mechanism in the `clscrs_init_crs` API.

The `clscrs_msgf2` callback mechanism has the following signature:

    typedef  void (*clscrs_msgf)(void *usrp, const oratext *msg, sword msglen);

##### Filters

You can use filters to narrow down Oracle Clusterware entities upon which a CLSCRS API operates. Simple filters are attribute-value pairs with an operator. Operators must be surrounded by spaces, as shown in the examples. You can combine simple filters into expressions called expression filters using Boolean operators.

Supported filter operators are:

- `=`
- `>`
- `<`
- `!=`
- `co`: Contains
- `st`: Starts with
- `en`: Ends with
-

Supported Boolean operators are `AND` and `OR`.

Examples of filters are:

- `TYPE = type1`

- `((TYPE = type1) AND (CHECK_INTERVAL > 50))`

- `(TYPE = type1) AND ((CHECK_INTERVAL > 30) OR (AUTO_START co never))`

- `NAME en network.res`

- `TYPE st ora.db`

**See Also:**

Use the `clscrs_comparator enum` and the `clscrs_operator enum` located in the `clscrsx.h` file (which you can download from the Oracle Clusterware web page at [Oracle Clusterware](http://www.oracle.com/goto/clusterware)) to get the correct type for the above comparators and operators, respectively, in the API calls

There are two types of filters and CLSCRS has a set of APIs to create these filters:

- Comparison filter: A simple filter that compares two values. For example:

      TYPE = ora.db.type

  Use the `clscrs_compfilter_create` API to create a comparison filter. For example, to create the `(TYPE = ora.db.type)` comparison filter:

      clscrs_compfilter_create(ctx, clscrs_TYPE,
                          clscrs_comparator_eq, (const oratext *)"ora.db.type",
                          &myCompFilter);

- Expression filter: A filter that is created from either a set of comparison filters or expression filters, or both. For example:

      ((TYPE = ora.db.type) AND (CHECK_INTERVAL > 50))

  Use the `clscrs_expfilter_create` API to create a comparison filter. For example, to create an expression filter:

      clscrs_exprfilter_create(myCompFilter1, clscrs_operator_or,
                                myCompFilter2, &myExprFilter);

**See Also:**

The `clscrsx.h` file (which you can download from the Oracle Clusterware web page at [Oracle Clusterware](http://www.oracle.com/goto/clusterware)) for usage information for the `clscrs_compfilter_create` and `clscrs_expfilter_create` APIs

**Note:**

Both the `clscrs_compfilter_create` and `clscrs_expfilter_create` APIs allocate memory that must be freed by calling `clscrs_filter_destroy()`.

You can use filters in the following interactive CLSCRS APIs in place of an entity list:

- `clscrs_start_resource2`
- `clscrs_stat2`
- `clscrs_stop_resource2`
- `clscrs_check_resource2`
- `clscrs_relocate_resource2`
-

Example H-3 describes using filters in an interactive CLSCRS API.

Example H-3 Filters In an Interactive CLSCRS API

    clscrs_start_resource2(myCompFilter, NULL,
                           env, msgf2, NULL,
                           0, pOpStatus);

##### Script Agent Usage

When you use CLSCRS APIs inside script agent entry points, keep the following in mind:

1.  Some actions, such as start, stop, and clean, are run under a lock on the resource instance. Thus, issuing a request to the server to act on the resource directly or by extension of a relation results in a dead-lock.

2.  Issuing read-only (`clscrs_stat2`) is generally safe unless it is an initial check, where the script agent must not call back on the server, because that results in a dead-lock, as well. Use the `clsagfw` APIs to query the check entry point.

**See Also:**

[Oracle Clusterware Resource Reference](oracle-clusterware-resource-reference.md) for examples of script agents

##### Help Interface

You can find the entire list of CLSCRS APIs, including usage information for each, in the `clscrsx.h` file (which you can download from the Oracle Clusterware web page at [Oracle Clusterware](http://www.oracle.com/goto/clusterware)), along with a demo called `crsapp.c`.

#### Deprecated CLSCRS APIs

Table H-1 lists the deprecated CLSCRS APIs and the corresponding replacement APIs for Oracle Clusterware.

Table H-1 Deprecated CLSCRS APIs

| Deprecated API               | Replacement                             |
|:-----------------------------|:----------------------------------------|
| `clscrs_check_resource`      | `clscrs_check_resource2`                |
| `clscrs_entity`              | `clscrs_entity_type`                    |
| `clscrs_fail_resource`       | No replacement                          |
| `clscrs_msgf`                | `clscrs_msgf2`                          |
| `clscrs_register_resource`   | `clscrs_register_resource2`             |
| `clscrs_relocate_resource`   | `clscrs_relocate_resource2`             |
| `clscrs_res_attr_count`      | `clscrs_crsentity_attr_count`           |
| `clscrs_res_create`          | `clscrs_crsentity_create`               |
| `clscrs_res_create`          | `clscrs_crsentitylist_create`           |
| `clscrs_res_destroy`         | `clscrs_crsentity_destroy`              |
| `clscrs_res_get_attr`        | `clscrs_crsentity_get_attr`             |
| `clscrs_res_get_attr_list`   | `clscrs_crsentity_get_attr_list`        |
| `clscrs_res_get_name`        | `clscrs_crsentity_get_name`             |
| `clscrs_res_get_node_list`   | `clscrs_crsentity_get_node_list`        |
| `clscrs_res_get_op_status`   | `clscrs_crsentity_get_op_status`        |
| `clscrs_res_get_reslist`     | `clscrs_crsentity_get_crsentitylist`    |
| `clscrs_res_set_attr`        | `clscrs_crsentity_set_attr`             |
| `clscrs_res_set_attr_list`   | `clscrs_crsentity_set_attr_list`        |
| `clscrs_res_set_reslist`     | `clscrs_crsentity_set_crsentitylist`    |
| `clscrs_reslist_append`      | `clscrs_crsentitylist_append`           |
| `clscrs_reslist_count`       | `clscrs_crsentitylist_count`            |
| `clscrs_reslist_delete_res`  | `clscrs_crsentitylist_delete_crsentity` |
| `clscrs_reslist_destroy`     | `clscrs_crsentitylist_destroy`          |
| `clscrs_reslist_find`        | `clscrs_crsentitylist_find`             |
| `clscrs_reslist_first`       | `clscrs_crsentitylist_first`            |
| `clscrs_reslist_next`        | `clscrs_crsentitylist_next`             |
| `clscrs_start_resource`      | `clscrs_start_resource2`                |
| `clscrs_stat`                | `clscrs_stat2`                          |
| `clscrs_stop_resource`       | `clscrs_stop_resource2`                 |
| `clscrs_unregister_resource` | `clscrs_unregister_resource2`           |

#### Changes to Existing CLSCRS APIs

Oracle has added the following flags to the `clscrs_stat2` API:

- `CLSCRS_STATFLAG_SERVERBYCATEGORY`: Use this flag to query the servers that match a particular server category.

- `CLSCRS_STATFLAG_CATEGORYBYSERVER`: Use this flag to query the server categories that match a particular server.

Oracle has added the following flags to the `clscrs_start_resource2` and `clscrs_stop_resource2` APIs:

- `CLSCRS_FLAG_T_HA_PREPARE`: Use this flag with Transparent HA (`start2`/`stop2` APIs) to instruct the Oracle Clusterware daemon (CRSD) to prepare for an external management interface to act on a resource. When the call comes back, if successful, then the interface then is expected to start or stop the resource and call back with the other flag (`CLSCRS_FLAG_T_HA_FINISH`).

- `CLSCRS_FLAG_T_HA_FINISH`: Use this flag with Transparent HA with `CLSCRS_FLAG_T_HA_PREPARE`. You must use this flag in the second call to the CRSD (start2/stop2 APIs) when the start or stop action has finished. Note that clients must indicate resource instances and never resources with this flag, because the CRSD must know to which instances the invocation of the API applies.

- `CLSCRS_NO_STATE_RESTORATION`: This flag is available for use to start and stop resource APIs and to instruct the CRSD to skip resource state restoration of the resources whose state was affected. That procedure is usually attempted unless you use this flag.

### Interactive CLSCRS APIs

These APIs make calls to the Cluster Ready Services daemon (CRSD) to run commands.

The CRSD must be up and running for these APIs to function.

Table H-2 Summary of Interactive CLSCRS APIs for Oracle Clusterware

| C API                                 | Description                                                                             |
|:--------------------------------------|:----------------------------------------------------------------------------------------|
| `clscrs_check_resource2`              | Notifies Oracle Clusterware to run the check entry points for the identified resources. |
| `clscrs_get_server_by_category`       | Obtains a list of servers that match a particular server category.                      |
| `clscrs_is_crs_admin`                 | Checks whether the user is an Oracle Clusterware administrator.                         |
| `clscrs_register_resource2`           | Registers the resources in the input resource list.                                     |
| `clscrs_register_servercategory`      | Registers server categories in the input server category list.                          |
| `clscrs_register_serverpool`          | Registers a server pool for the input list of servers.                                  |
| `clscrs_register_type`                | Registers the resource types in the input resource list.                                |
| `clscrs_relocate_resource2`           | Relocates the list of resource identifiers.                                             |
| `clscrs_relocate_server`              | Relocates a list of servers.                                                            |
| `clscrs_request_action`               | Notifies Oracle Clusterware to run a specific set of actions.                           |
| `clscrs_restart_resource`             | Instructs Oracle Clusterware to restart a named set of resources.                       |
| `clscrs_start_resource2`              | Notifies Oracle Clusterware to start a named set of resources.                          |
| `clscrs_stat2`                        | Obtains information about specific resources.                                           |
| `clscrs_stat3`                        | Obtains information about specific entities.                                            |
| `clscrs_stop_resource2`               | Notifies Oracle Clusterware to stop a named set of resources.                           |
| `clscrs_stop_resource_in_pools`       | Instructs Oracle Clusterware to stop specific resources in server pools.                |
| `clscrs_start_resource_in_pools`      | Instructs Oracle Clusterware to start specific resources in server pools.               |
| `clscrs_unregister_resource2`         | Unregisters the resources in the input list of resource names.                          |
| `clscrs_unregister_servercategory`    | Unregisters server categories in the input server category list.                        |
| `clscrs_unregister_serverpool`        | Unregisters the given server pool.                                                      |
| `clscrs_unregister_type`              | Unregisters the resource types in the input list.                                       |
| `clscrs_whatif_add_server`            | Simulates what happens if you add a server.                                             |
| `clscrs_whatif_delete_server`         | Simulates what happens if you delete a server.                                          |
| `clscrs_whatif_fail_resource`         | Simulates what happens if a resource fails.                                             |
| `clscrs_whatif_register_resource`     | Simulates what happens if you register a resource.                                      |
| `clscrs_whatif_register_serverpool`   | Simulates what happens if you register a server pool.                                   |
| `clscrs_whatif_relocate_resource`     | Simulates what happens if you relocate a resource.                                      |
| `clscrs_whatif_relocate_server`       | Simulates what happens if you relocate a server.                                        |
| `clscrs_whatif_set_activepolicy`      | Simulates what happens if you activate a policy.                                        |
| `clscrs_whatif_start_resource`        | Simulates what happens if you start a resource.                                         |
| `clscrs_whatif_stop_resource`         | Simulates what happens if you stop a resource.                                          |
| `clscrs_whatif_unregister_serverpool` | Simulates what happens if you unregister a server pool.                                 |

### Non-Interactive CLSCRS APIs

You can use non-interactive CLSCRS APIs for functions such as context initialization, preparing request payloads for interactive APIs, and post-processing output of the interactive APIs. The non-interactive CLSCRS APIs do not call the CRSD.

A callback error reporting mechanism is not available for the non-interactive CLSCRS APIs. All interactive CLSCRS APIs, except `clscrs_stat2`, `clscrs_stat3`, and all `clscrs_whatif_*` APIs, use this callback mechanism. Clients of these APIs also use the callback mechanism to receive error, warning, and progress messages from the CRSD.

You can also use filters to reduce the list of Oracle Clusterware entities. You can also use filters in the interactive APIs to reduce the list of Oracle Clusterware entities.

#### Thread Safety

The routines provided to manage API data structures cannot be used with the same API context in multiple threads concurrently; however, no thread-affinity on the part of the client is required. If a separate API context is used in each instance, then a process may invoke these routines on multiple threads.

The following table lists describes the non-interactive CLSCRS APIs.

Table H-3 Non-Interactive CLSCRS APIs

| C API                                   | Description                                                                                                                                                                                                                     |
|:----------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `clscrs_action_getentity`               | Returns the entity for the action.                                                                                                                                                                                              |
| `clscrs_action_getparams`               | Returns the list of parameters for the action.                                                                                                                                                                                  |
| `clscrs_action_gettype`                 | Returns the type for the action.                                                                                                                                                                                                |
| `clscrs_actionlist_count`               | Counts the number of actions in the action list.                                                                                                                                                                                |
| `clscrs_actionlist_create`              | Creates an action list.                                                                                                                                                                                                         |
| `clscrs_actionlist_destroy`             | Destroys the action list.                                                                                                                                                                                                       |
| `clscrs_actionlist_first`               | Returns the first action in an action list.                                                                                                                                                                                     |
| `clscrs_actionlist_next`                | Returns the next action in an action list.                                                                                                                                                                                      |
| `clscrs_actionlist_print`               | Prints the action list.                                                                                                                                                                                                         |
| `clscrs_actionlist_seqid`               | Returns the sequence ID for the action lists                                                                                                                                                                                    |
| `clscrs_compfilter_create`              | Constructs a simple filter that compares two values.                                                                                                                                                                            |
| `clscrs_crsentity_attr_count`           | Counts the number of attributes for an entity.                                                                                                                                                                                  |
| `clscrs_crsentity_create`               | Creates a new entity (allocates memory).                                                                                                                                                                                        |
| `clscrs_crsentity_destroy`              | Destroys an entity and frees up memory.                                                                                                                                                                                         |
| `clscrs_crsentity_get_attr`             | Obtains the value of an entity, server pool, or server attribute.                                                                                                                                                               |
| `clscrs_crsentity_get_attr_list`        | Obtains the attribute list for an entity, resource type, server pool, or server.                                                                                                                                                |
| `clscrs_crsentity_get_crsentitylist`    | Obtains the entity list for an entity.                                                                                                                                                                                          |
| `clscrs_crsentity_get_name`             | Obtains the name of an entity.                                                                                                                                                                                                  |
| `clscrs_crsentity_get_node_list`        | Obtains a list of nodes currently hosting the entity.                                                                                                                                                                           |
| `clscrs_crsentity_get_op_status`        | Obtains the status of an operation for an entity.                                                                                                                                                                               |
| `clscrs_crsentity_get_registered`       | Obtains the registration status of an entity.                                                                                                                                                                                   |
| `clscrs_crsentity_set_attr`             | Sets an attribute for an entity and a server pool.                                                                                                                                                                              |
| `clscrs_crsentity_set_attr_list`        | Sets the attribute list for an entity, resource type, server pool, or server.                                                                                                                                                   |
| `clscrs_crsentity_set_crsentitylist`    | Sets the resource list for an entity.                                                                                                                                                                                           |
| `clscrs_crsentitylist_append`           | Adds an entity to an entity list.                                                                                                                                                                                               |
| `clscrs_crsentitylist_count`            | Counts the number of entities in an entity list.                                                                                                                                                                                |
| `clscrs_crsentitylist_create`           | Creates a list of entities.                                                                                                                                                                                                     |
| `clscrs_crsentitylist_delete_crsentity` | Deletes an entity matching a given name from an entity list.                                                                                                                                                                    |
| `clscrs_crsentitylist_destroy`          | Destroys an entity list and frees up memory.                                                                                                                                                                                    |
| `clscrs_crsentitylist_find`             | Finds an entity in an entity list matching a given name.                                                                                                                                                                        |
| `clscrs_crsentitylist_first`            | Obtains the first entity on an entity list.                                                                                                                                                                                     |
| `clscrs_crslist_next`                   | Obtains the current next entity from an entity list.                                                                                                                                                                            |
| `clscrs_entity_id_create`               | Creates an entity identifier that identifies an Oracle Clusterware entity such as a resource, resource type, server group, and so on.                                                                                           |
| `clscrs_entity_id_destroy`              | Frees the memory associated with an entity identifier created from `clscrs_entity_id_create()`.                                                                                                                                 |
| `clscrs_exprfilter_create`              | Constructs an expression filter from comparison or expression filters, or both.                                                                                                                                                 |
| `clscrs_filter_destroy`                 | Frees the memory for a filter.                                                                                                                                                                                                  |
| `clscrs_get_entity_type`                | Obtains the entity type corresponding to the entity identifier provided.                                                                                                                                                        |
| `clscrs_get_fixed_attrlist`             | Obtains the list of attributes that correspond to an attribute group identifier.                                                                                                                                                |
| `clscrs_get_resource_instance_details`  | Obtains the resource instance details, such as resource name, cardinality, and degree, from the resource instance identifier that is used.                                                                                      |
| `clscrs_getnodename`                    | Obtains the node name.                                                                                                                                                                                                          |
| `clscrs_init_crs`                       | Initializes a context for communications with Oracle Clusterware.                                                                                                                                                               |
| `clscrs_sp_get`                         | Obtains the name and value components of a stringpair.                                                                                                                                                                          |
| `clscrs_sp_get_value`                   | Obtains the value component of a stringpair.                                                                                                                                                                                    |
| `clscrs_sp_set`                         | Changes the value part of a stringpair.                                                                                                                                                                                         |
| `clscrs_splist_append`                  | Adds a new stringpair (`sp`) to a stringpair list (`splist`).                                                                                                                                                                   |
| `clscrs_splist_count`                   | Counts the number of stringpairs (`sp`) in a stringpair list (`splist`).                                                                                                                                                        |
| `clscrs_splist_create`                  | Creates a new stringpair list.                                                                                                                                                                                                  |
| `clscrs_splist_create_and_set`          | Creates a new stringpair list (`splist`) and set the name and value for the first stringpair in the list.                                                                                                                       |
| `clscrs_splist_delete_sp`               | Deletes a stringpair (`sp`) from a stringpair list (`splist`).                                                                                                                                                                  |
| `clscrs_splist_destroy`                 | Frees the memory for a stringpair list (`splist`).                                                                                                                                                                              |
| `clscrs_splist_find`                    | Finds the value for a stringpair (`sp`) in a stringpair list (`splist`).                                                                                                                                                        |
| `clscrs_splist_first`                   | Obtains the first stringpair (`sp`) from a stringpair list (`splist`).                                                                                                                                                          |
| `clscrs_splist_next`                    | Obtains the current next stringpair (`sp`) from a stringpair list (`splist`). Current next stringpair is effectively the next stringpair in the stringpair list. The list iterator is stored within the API and is not exposed. |
| `clscrs_splist_replace`                 | Replaces the value for a stringpair (`sp`) in a stringpair list (`splist`).                                                                                                                                                     |
| `clscrs_term_crs`                       | Releases a context for communications with Oracle Clusterware.                                                                                                                                                                  |
| `clscrs_type_create`                    | Creates a new resource type.                                                                                                                                                                                                    |
| `clscrs_type_get_attr`                  | Obtains the value/properties of a resource type attribute.                                                                                                                                                                      |
| `clscrs_type_set_attr`                  | Adds an attribute to a resource type.                                                                                                                                                                                           |

**Related Topics**

- Error Handling and Tracing
- Callback Mechanism
- Filters

### Command Evaluation APIs

You can use the command evaluation APIs to predict Oracle Clusterware's response to a hypothetical planned or unplanned event.

Oracle Clusterware can react to events in the system and produce a response action plan. This action plan consists of a series of resource state transitions or server pool reconfigurations, or both. The command evaluation APIs provide a mechanism to expose this action plan externally and to enable clients to predict the consequences of an event before it actually happens.

Additionally, by specifying a flag to the APIs listed in subsequent sections, you can obtain reasoned command evaluation information that explains why Oracle Clusterware made the decisions it did to form a response action plan to the event.

Command evaluation response plans are available for the following event categories:

- Resources: Start, stop, relocate, add, and modify

- Server pools: Add, remove, and modify

- Servers: Add, remove, and relocate

- Policy: Change active policy

- Server category: Modify

Reasoned command evaluation response plans are available for the following event categories:

- Server pools: Add, remove, and modify

- Servers: Add and remove

- Policy: Change active policy

Oracle Clusterware provides command evaluation output as a list of actions, where each action represents a specific step performed by Oracle Clusterware. Each action is encapsulated by a `clscrs_action` structure, and the `clscrs_actionlist` structure represents the entire sequence of actions. Oracle Clusterware also provides a set of functions (`clscrs_action_*` for action structures and `clscrs_actionlist_*` for action lists) to create, examine, iterate over, and destroy these structures. Their usage is identical to that of the corresponding entity list and entity functions.

The command evaluation APIs also provide clients with the ability to make a query on the projected state of the system. The `clscrs_querylist` structure using the `stat3` format specifies the query, and the `clscrs_crsentitylist` structure provides the result. Refer to the `stat3` section for details on their usage.

Each command evaluation response that Oracle Clusterware provides includes a sequence ID, which indicates the current state of Oracle Clusterware. The sequence ID is incremented for every new event that Oracle Clusterware manages. Oracle Clusterware guarantees that, as long the sequence ID has not changed, the action plan provided will be run, as is, for the event in question. For example, the action plan that Oracle Clusterware provides for a `whatif start resource FOO` request will be identical to the actions Oracle Clusterware takes take when an actual `start resource FOO` request is submitted, provided the sequence ID has not changed.

Example H-4 describes how you can use command evaluation APIs.

Example H-4 Sample Usage of Command Evaluation API

    boolean            tracectx = TRUE;
    oratext           *resid;
    clscrs_ctx        *ctx;
    clscrs_env         env;
    clscrs_splist     *resid_list;
    clscrs_action     *cur_actn;
    clscrs_actionlist *alist;
    clscrs_splist     *params;

    // Init crs
    clscrs_init_crs(&ctx, (clscrs_msgf)clsuslztrace, &tracectx, (ub4)0);

    // Init parameters to the call
    clscrs_entity_id_create(ctx, "MYRES", clscrs_entity_res, &resid);
    clscrs_splist_create(ctx, &resid_list);
    clscrs_splist_append(resid_list, resid, NULL);
    clscrs_actionlist_create(ctx, &alist);

    // Make call into the what-if API
    clscrs_whatif_start_resource(resid_list, nodename, flags, NULL, NULL, alist);

    // Process the resulting list of actions
    for(clscrs_actionlist_first(alist,&cur_actn);cur_actn;clscrs_actionlist_next(alist,&cur_actn))
     {
      params = clscrs_action_getparams(cur_actn);
      switch(clscrs_action_gettype(cur_actn))
      {
       case clscrs_actiontype_resstate:
          // Read params and do something
             break;
       case clscrs_actiontype_srvmove:
          // Read params and do something
             break;
       case clscrs_actiontype_newgroup:
          // Read params and do something
             break;
       case clscrs_actiontype_errorcase:
          // Read params and do something
             break;
       }
      }
      clscrs_actionlist_destroy(alist);
      clscrs_splist_destroy(resid_list);
      clscrs_term_crs(&ctx);

Parameters for the APIs listed in this section are separated into those for which you provide input and those that display information when the function completes successfully.

#### clscrs_whatif_set_activepolicy

Determines the actions that Oracle Clusterware takes if you activate a specific policy.

##### Syntax

    clscrs_whatif_set_activepolicy(const oratext *name, uword flags,
                                    clscrs_querylist *qlist,
                                    clscrs_crsentitylist *status,
                                    clscrs_actionlist *alist);

##### Input

- `name`: Name of the policy.
- `flags`: `CLSCRS_FLAG_NONE`
- `CLSCRS_FLAG_WHATIF_VERBOSE`
- `CLSCRS_FLAG_WHYIF`: Displays reasoned command evaluation information
- `CLSCRS_FLAG_FORCE`
- `qlist`: Specifies the client query on Oracle Clusterware entity status. NULL indicates no query specified.

##### Output

- `status`: List containing the returned entity information.
- `alist`: Action list containing the actions that Oracle Clusterware will perform.

##### Returns

- `CLSCRS_STAT_SUCCESS`: Indicates that Oracle Clusterware completed the request successfully or that no entities matched a filter.
- `CLSCRS_STAT_AUTHORIZATION_FAILURE`: Displays when authorization fails.
- `CLSCRS_STAT_CONNECTION`: Displays if there is a communication error.
- `CLSCRS_STAT_WRONG_ACTIVE_VERSION`: Displays if you use the API before you have upgraded Oracle Clusterware.
- `CLSCRS_STAT_INTERNAL_ERROR`: Displays if an unexpected, non-user error occurs.
- `CLSCRS_STAT_INVALID_ARGS`: Displays if you provide incorrect arguments.

#### clscrs_whatif_fail_resource

Determines the actions that Oracle Clusterware takes if specific resources fail.

##### Syntax

    clscrs_whatif_fail_resource(clscrs_splist *name, const oratext *server,
                                 uword flags, clscrs_querylist *qlist,
                                 clscrs_crsentitylist *status,
                                 clscrs_actionlist *alist);

##### Input

- `name`: Resource or instance ID, or a filter.
- `server`: Name of the server on which the resource failure occurs. NULL is allowed.
- `flags`: `CLSCRS_FLAG_NONE`
- `CLSCRS_FLAG_WHATIF_VERBOSE`
- `qlist`: Specifies the client query on Oracle Clusterware entity status. NULL indicates no query specified.

##### Output

- `status`: List containing the returned entity information.
- `alist`: Action list containing the actions that Oracle Clusterware will perform.

##### Returns

- `CLSCRS_STAT_SUCCESS`: Indicates that Oracle Clusterware completed the request successfully or that no entities matched a filter.
- `CLSCRS_STAT_AUTHORIZATION_FAILURE`: Displays when authorization fails.
- `CLSCRS_STAT_CONNECTION`: Displays if there is a communication error.
- `CLSCRS_STAT_WRONG_ACTIVE_VERSION`: Displays if you use the API before you have upgraded Oracle Clusterware.
- `CLSCRS_STAT_INTERNAL_ERROR`: Displays if an unexpected, non-user error occurs.
- `CLSCRS_STAT_INVALID_ARGS`: Displays if you provide incorrect arguments.

#### clscrs_whatif_register_resource

Determines the actions that Oracle Clusterware takes if you add or modify a specific resource.

##### Syntax

    clscrs_whatif_register_resource(const oratext *name, clscrs_splist *attrs,
                                     uword flags, clscrs_querylist *qlist,
                                     clscrs_crsentitylist *status,
                                     clscrs_actionlist *alist);

##### Input

- `name`: Name of the resource.
- `attrs`: The attributes of the specified resource.
- `flags`: `CLSCRS_FLAG_NONE`
- `CLSCRS_FLAG_WHATIF_VERBOSE`
- `CLSCRS_FLAG_FORCE`
- `CLSCRS_FLAG_REG_UPDATE` (to modify the resource)
- `qlist`: Specifies the client query on Oracle Clusterware entity status. NULL indicates no query specified.

##### Output

- `status`: List containing the returned entity information.
- `alist`: Action list containing the actions that Oracle Clusterware will perform.

##### Returns

- `CLSCRS_STAT_SUCCESS`: Indicates that Oracle Clusterware completed the request successfully or that no entities matched a filter.
- `CLSCRS_STAT_AUTHORIZATION_FAILURE`: Displays when authorization fails.
- `CLSCRS_STAT_CONNECTION`: Displays if there is a communication error.
- `CLSCRS_STAT_WRONG_ACTIVE_VERSION`: Displays if you use the API before you have upgraded Oracle Clusterware.
- `CLSCRS_STAT_INTERNAL_ERROR`: Displays if an unexpected, non-user error occurs.
- `CLSCRS_STAT_INVALID_ARGS`: Displays if you provide incorrect arguments.

#### clscrs_whatif_relocate_resource

Determines the actions that Oracle Clusterware takes if you relocate specific resources.

##### Syntax

    clscrs_whatif_relocate_resource(clscrs_splist *name, const oratext *destnode,
                                  uword flags, clscrs_querylist *qlist,
                                  clscrs_crsentitylist *status,
                                  clscrs_actionlist *alist);

##### Input

- `name`: Resource or instance ID, or a filter.
- `flags`: `CLSCRS_FLAG_NONE`
- `CLSCRS_FLAG_WHATIF_VERBOSE`
- `CLSCRS_FLAG_FORCE`
- `qlist`: Specifies the client query on Oracle Clusterware entity status. NULL indicates no query specified.

##### Output

- `status`: List containing the returned entity information.
- `alist`: Action list containing the actions that Oracle Clusterware will perform.

##### Returns

- `CLSCRS_STAT_SUCCESS`: Indicates that Oracle Clusterware completed the request successfully or that no entities matched a filter.
- `CLSCRS_STAT_AUTHORIZATION_FAILURE`: Displays when authorization fails.
- `CLSCRS_STAT_CONNECTION`: Displays if there is a communication error.
- `CLSCRS_STAT_WRONG_ACTIVE_VERSION`: Displays if you use the API before you have upgraded Oracle Clusterware.
- `CLSCRS_STAT_INTERNAL_ERROR`: Displays if an unexpected, non-user error occurs.
- `CLSCRS_STAT_INVALID_ARGS`: Displays if you provide incorrect arguments.

#### clscrs_whatif_start_resource

Determines the actions that Oracle Clusterware takes if you start specific resources.

##### Syntax

    clscrs_whatif_start_resource(clscrs_splist *name, const oratext *node,
                                  uword flags, clscrs_querylist *qlist,
                                  clscrs_crsentitylist *status,
                                  clscrs_actionlist *alist);

##### Input

- `name`: Resource or instance ID, or a filter.
- `node`: Name of the node on which you want to start the resource. NULL is allowed.
- `flags`: `CLSCRS_FLAG_NONE`
- `CLSCRS_FLAG_WHATIF_VERBOSE`
- `CLSCRS_FLAG_FORCE`
- `qlist`: Specifies the client query on Oracle Clusterware entity status. NULL indicates no query specified.

##### Output

- `status`: List containing the returned entity information.
- `alist`: Action list containing the actions that Oracle Clusterware will perform.

##### Returns

- `CLSCRS_STAT_SUCCESS`: Indicates that Oracle Clusterware completed the request successfully or that no entities matched a filter.
- `CLSCRS_STAT_AUTHORIZATION_FAILURE`: Displays when authorization fails.
- `CLSCRS_STAT_CONNECTION`: Displays if there is a communication error.
- `CLSCRS_STAT_WRONG_ACTIVE_VERSION`: Displays if you use the API before you have upgraded Oracle Clusterware.
- `CLSCRS_STAT_INTERNAL_ERROR`: Displays if an unexpected, non-user error occurs.
- `CLSCRS_STAT_INVALID_ARGS`: Displays if you provide incorrect arguments.

#### clscrs_whatif_stop_resource

Determines the actions that Oracle Clusterware takes if you stop specific resources.

##### Syntax

    clscrs_whatif_stop_resource(clscrs_splist *name, uword flags,
                                  clscrs_querylist *qlist,
                                  clscrs_crsentitylist *status,
                                  clscrs_actionlist *alist);

##### Input

- `name`: Resource or instance ID, or a filter.
- `flags`: `CLSCRS_FLAG_NONE`
- `CLSCRS_FLAG_WHATIF_VERBOSE`
- `CLSCRS_FLAG_FORCE`
- `qlist`: Specifies the client query on Oracle Clusterware entity status. NULL indicates no query specified.

##### Output

- `status`: List containing the returned entity information.
- `alist`: Action list containing the actions that Oracle Clusterware will perform.

##### Returns

- `CLSCRS_STAT_SUCCESS`: Indicates that Oracle Clusterware completed the request successfully or that no entities matched a filter.
- `CLSCRS_STAT_AUTHORIZATION_FAILURE`: Displays when authorization fails.
- `CLSCRS_STAT_CONNECTION`: Displays if there is a communication error.
- `CLSCRS_STAT_WRONG_ACTIVE_VERSION`: Displays if you use the API before you have upgraded Oracle Clusterware.
- `CLSCRS_STAT_INTERNAL_ERROR`: Displays if an unexpected, non-user error occurs.
- `CLSCRS_STAT_INVALID_ARGS`: Displays if you provide incorrect arguments.

#### clscrs_whatif_register_serverpool

Determines the actions that Oracle Clusterware takes if you register a specific server pool.

##### Syntax

    clscrs_whatif_register_serverpool(const oratext *pname, clscrs_splist *attrs,
                                       uword flags, clscrs_querylist *qlist,
                                       clscrs_crsentitylist *status,
                                       clscrs_actionlist *alist);

##### Input

- `name`: Name of the server pool.
- `attrs`: The attributes of the specified server pool.
- `flags`: `CLSCRS_FLAG_NONE`
- `CLSCRS_FLAG_WHATIF_VERBOSE`
- `CLSCRS_FLAG_WHYIF`: Displays reasoned command evaluation information
- `CLSCRS_FLAG_FORCE`
- `CLSCRS_FLAG_REG_UPDATE` (to modify the server pool)
- `qlist`: Specifies the client query on Oracle Clusterware entity status. NULL indicates no query specified.

##### Output

- `status`: List containing the returned entity information.
- `alist`: Action list containing the actions that Oracle Clusterware will perform.

##### Returns

- `CLSCRS_STAT_SUCCESS`: Indicates that Oracle Clusterware completed the request successfully or that no entities matched a filter.
- `CLSCRS_STAT_AUTHORIZATION_FAILURE`: Displays when authorization fails.
- `CLSCRS_STAT_CONNECTION`: Displays if there is a communication error.
- `CLSCRS_STAT_WRONG_ACTIVE_VERSION`: Displays if you use the API before you have upgraded Oracle Clusterware.
- `CLSCRS_STAT_INTERNAL_ERROR`: Displays if an unexpected, non-user error occurs.
- `CLSCRS_STAT_INVALID_ARGS`: Displays if you provide incorrect arguments.

#### clscrs_whatif_unregister_serverpool

Determines the actions that Oracle Clusterware takes if you unregister a specific server pool.

##### Syntax

    clscrs_whatif_unregister_serverpool(const oratext *poolname, uword flags,
                                         clscrs_querylist *qlist,
                                         clscrs_crsentitylist *status,
                                         clscrs_actionlist *alist);

##### Input

- `name`: Name of the server pool.
- `flags`: `CLSCRS_FLAG_NONE`
- `CLSCRS_FLAG_WHATIF_VERBOSE`
- `CLSCRS_FLAG_WHYIF`: Displays reasoned command evaluation information
- `CLSCRS_FLAG_FORCE`
- `qlist`: Specifies the client query on Oracle Clusterware entity status. NULL indicates no query specified.

##### Output

- `status`: List containing the returned entity information.
- `alist`: Action list containing the actions that Oracle Clusterware will perform.

##### Returns

- `CLSCRS_STAT_SUCCESS`: Indicates that Oracle Clusterware completed the request successfully or that no entities matched a filter.
- `CLSCRS_STAT_AUTHORIZATION_FAILURE`: Displays when authorization fails.
- `CLSCRS_STAT_CONNECTION`: Displays if there is a communication error.
- `CLSCRS_STAT_WRONG_ACTIVE_VERSION`: Displays if you use the API before you have upgraded Oracle Clusterware.
- `CLSCRS_STAT_INTERNAL_ERROR`: Displays if an unexpected, non-user error occurs.
- `CLSCRS_STAT_INVALID_ARGS`: Displays if you provide incorrect arguments.

#### clscrs_whatif_add_server

Determines the actions that Oracle Clusterware takes if you add a server.

##### Syntax

    clscrs_whatif_add_server(const oratext *name, clscrs_splist *attrs, uword flags,
                              clscrs_querylist *qlist, clscrs_crsentitylist *status,
                              clscrs_actionlist *alist);

##### Input

- `name`: Name of the server.
- `attrs`: The attributes of the specified server.
- `flags`: `CLSCRS_FLAG_NONE`
- `CLSCRS_FLAG_WHATIF_VERBOSE`
- `CLSCRS_FLAG_WHYIF`: Displays reasoned command evaluation information
- `CLSCRS_FLAG_FORCE`
- `qlist`: Specifies the client query on Oracle Clusterware entity status. NULL indicates no query specified.

##### Output

- `status`: List containing the returned entity information.
- `alist`: Action list containing the actions that Oracle Clusterware will perform.

##### Returns

- `CLSCRS_STAT_SUCCESS`: Indicates that Oracle Clusterware completed the request successfully or that no entities matched a filter.
- `CLSCRS_STAT_AUTHORIZATION_FAILURE`: Displays when authorization fails.
- `CLSCRS_STAT_CONNECTION`: Displays if there is a communication error.
- `CLSCRS_STAT_WRONG_ACTIVE_VERSION`: Displays if you use the API before you have upgraded Oracle Clusterware.
- `CLSCRS_STAT_INTERNAL_ERROR`: Displays if an unexpected, non-user error occurs.
- `CLSCRS_STAT_INVALID_ARGS`: Displays if you provide incorrect arguments.

#### clscrs_whatif_delete_server

Determines the actions that Oracle Clusterware takes if you delete a server.

##### Syntax

    clscrs_whatif_delete_server(const oratext *name, uword flags,
                                 clscrs_querylist *qlist,
                                 clscrs_crsentitylist *status,
                                 clscrs_actionlist *alist);

##### Input

- `name`: Name of the server.
- `flags`: `CLSCRS_FLAG_NONE`
- `CLSCRS_FLAG_WHATIF_VERBOSE`
- `CLSCRS_FLAG_WHYIF`: Displays reasoned command evaluation information
- `CLSCRS_FLAG_FORCE`
- `qlist`: Specifies the client query on Oracle Clusterware entity status. NULL indicates no query specified.

##### Ouput

- `status`: List containing the returned entity information.
- `alist`: Action list containing the actions that Oracle Clusterware will perform.

##### Returns

- `CLSCRS_STAT_SUCCESS`: Indicates that Oracle Clusterware completed the request successfully or that no entities matched a filter.
- `CLSCRS_STAT_AUTHORIZATION_FAILURE`: Displays when authorization fails.
- `CLSCRS_STAT_CONNECTION`: Displays if there is a communication error.
- `CLSCRS_STAT_WRONG_ACTIVE_VERSION`: Displays if you use the API before you have upgraded Oracle Clusterware.
- `CLSCRS_STAT_INTERNAL_ERROR`: Displays if an unexpected, non-user error occurs.
- `CLSCRS_STAT_INVALID_ARGS`: Displays if you provide incorrect arguments.

#### clscrs_whatif_relocate_server

Determines the actions that Oracle Clusterware takes if you relocate a server to a different server pool.

##### Syntax

    clscrs_whatif_relocate_server(const oratext *name, const oratext *topool,
                                   uword flags, clscrs_querylist *qlist,
                                   clscrs_crsentitylist *status,
                                   clscrs_actionlist *alist);

##### Input

- `name`: Name of the server.
- `topool`: The name of the server pool to which you want to relocate the server.
- `flags`: `CLSCRS_FLAG_NONE`
- `CLSCRS_FLAG_WHATIF_VERBOSE`
- `CLSCRS_FLAG_FORCE`
- `qlist`: Specifies the client query on Oracle Clusterware entity status. NULL indicates no query specified.

##### Output

- `status`: List containing the returned entity information.
- `alist`: Action list containing the actions that Oracle Clusterware will perform.

##### Returns

- `CLSCRS_STAT_SUCCESS`: Indicates that Oracle Clusterware completed the request successfully or that no entities matched a filter.
- `CLSCRS_STAT_AUTHORIZATION_FAILURE`: Displays when authorization fails.
- `CLSCRS_STAT_CONNECTION`: Displays if there is a communication error.
- `CLSCRS_STAT_WRONG_ACTIVE_VERSION`: Displays if you use the API before you have upgraded Oracle Clusterware.
- `CLSCRS_STAT_INTERNAL_ERROR`: Displays if an unexpected, non-user error occurs.
- `CLSCRS_STAT_INVALID_ARGS`: Displays if you provide incorrect arguments.

### Server Categorization APIs

Oracle Clusterware includes an entity called `clsrcs_entity_server_category`.

Parameters for the APIs listed in this section are separated into those for which you provide input and those that display information when the function completes successfully.

#### clscrs_servercategory_create

Creates a server category.

##### Syntax

    clscrs_servercategory_create(clscrs_ctx *ctx, const oratext *sc_name,
                                    clscrs_crsentity **sc);

##### Input

- `ctx`: CLSCRS context.
- `sc_name`: Name of the server category.
-

##### Output

`sc`: The newly created server category.

##### Returns

- `clscrsretSUCC`: Indicates that Oracle Clusterware completed the request successfully.
- `clscrsretNOMEM`: Displays if no memory can be allocated.
- `clscrsretBADCTX`: Displays if the context is NULL.
- `clscrsretBADARG`: Displays if the server name is NULL.

#### clscrs_servercategory_destroy

Frees memory for a server category.

##### Syntax

    clscrs_servercategory_destroy(clscrs_crsentity **sc);

##### Input

`sc_name`: Name of the server category you want to destroy to free up memory

##### Returns

`clscrsretSUCC`: Indicates that Oracle Clusterware completed the request successfully

#### clscrs_register_servercategory

Registers the server categories that you specify in the input server category list.

##### Syntax

    clscrs_register_servercategory(clscrs_crsentitylist *in_entitylist, uword flags,
                                   clscrs_msgf2 msgf, void *msgarg,
                                   clscrs_crsentitylist *op_status);

##### Input

- `in_entitylist`: The list of server categories you want to register.
- `flags`: `CLSCRS_FLAG_REG_UPDATE`
- `CLSCRS_FLAG_QUEUE`
- `CLSCRS_FLAG_FORCE`
- `CLSCRS_FLAG_NONE`
- `msgf`: User message callback, which can be NULL.
- `msgarg`: User callback argument, which can be NULL.

##### Output

`op_status`: The entity list that holds the status of the register operation for each server category.

##### Returns

- `CLSCRS_STAT_SUCCESS`: Indicates that all input server categories are successfully registered.
- `CLSCRS_STAT_FAILURE`: Displays if at least one server category cannot be registered.
- `CLSCRS_STAT_CONNECTION`: Displays if there is a communication error.
- `CLSCRS_STAT_WRONG_ACTIVE_VERSION`: Displays if you use the API before you have upgraded Oracle Clusterware.
- `CLSCRS_STAT_INVALID_ARGS`: Displays if any of the server categories in the input entity list do not have attributes.

##### Usage Notes

- The attributes for the server category are contained in the input server category list.

- The `op_status` list contains the results of the register operation for each server category and contains no valid attributes.

- The caller must create and populate the `in_entitylist` and must create the `op_status` list. Both of these lists must be destroyed by the caller.

- The `op_status` list cannot be reused with another API call. It must be created and destroyed for each API call.

- One or more attributes of an already registered server category can be modified by passing the `CLSCRS_FLAG_REG_UPDATE` flag.

- The flags apply to all server categories in the input entity list.

#### clscrs_unregister_servercategory

Unregisters the server categories that you specify in the input list.

##### Syntax

    clscrs_unregister_servercategory(clscrs_splist *sclist, uword flags,
                                     clscrs_msgf2 msgf, void *msgarg,
                                     clscrs_crsentitylist *op_status);

##### Input

- `sclist`: The list of server categories you want to unregister.
- `flags`: Specify option flags.
- `msgf`: User message callback, which can be NULL.
- `msgarg`: User callback argument, which can be NULL.

##### Output

`op_status`: The entity list that holds the status of the unregister operation for each server category.

##### Returns

- `CLSCRS_STAT_SUCCESS`: Indicates that all input server categories are successfully registered.
- `CLSCRS_STAT_FAILURE`: Displays if at least one server category cannot be unregistered.
- `CLSCRS_STAT_CONNECTION`: Displays if there is a communication error.
- `CLSCRS_STAT_WRONG_ACTIVE_VERSION`: Displays if you use the API before you have upgraded Oracle Clusterware.

##### Usage Notes

- The `op_status` list contains the results of the unregister operation for each server category.

- The caller must create and populate the `sclist` and must create the `op_status` list. Both of these lists must be destroyed by the caller.

- The `op_status` list cannot be reused with another API call and must be created and destroyed for each API call.

#### clscrs_get_server_by_category

Obtains a list of servers that match a particular server category.

##### Syntax

    clscrs_get_server_by_category(clscrs_splist *in_list,
                                  clscrs_crsentitylist *out_entitylist);

##### Input

`in_list`: The list of server categories or a filter.

##### Output

`out_entitylist`: Lists the servers matching the server category.

##### Returns

- `CLSCRS_STAT_SUCCESS`: Indicates that all input server categories are successfully registered.
- `CLSCRS_STAT_FAILURE`: Displays if at least one server category cannot be unregistered.
- `CLSCRS_STAT_CONNECTION`: Displays if there is a communication error.

#### clscrs_register_server

Modifies the server attributes.

##### Syntax

    clscrs_register_server(clscrs_crsentitylist *in_entitylist, uword flags,
                           clscrs_msgf2 msgf, void *msgarg,
                           clscrs_crsentitylist *op_status);

##### Input

- `in_entitylist`: The list of server categories you want to register.
- `flags`: `CLSCRS_FLAG_QUEUE`
- `CLSCRS_FLAG_FORCE`
- `CLSCRS_FLAG_REG_UPDATE`
- `CLSCRS_FLAG_NONE`
- `msgf`: User message callback, which can be NULL.
- `msgarg`: User callback argument, which can be NULL.

##### Output

`op_status`: The entity list that holds the status of the register operation for each server.

##### Returns

- `CLSCRS_STAT_SUCCESS`: Indicates that all input server categories are successfully registered.
- `CLSCRS_STAT_FAILURE`: Displays if at least one server category cannot be registered.
- `CLSCRS_STAT_CONNECTION`: Displays if there is a communication error.
- `CLSCRS_STAT_WRONG_ACTIVE_VERSION`: Displays if you use the API before you have upgraded Oracle Clusterware.
- `CLSCRS_STAT_INVALID_ARGS`: Displays if any of the server categories in the input entity list do not have attributes.

##### Usage Notes

- The attributes for the server are contained in the input server list.

- The `op_status` list contains the results of the modify operation for each server but contains no valid attributes.

- The caller must create and populate the `in_entitylist` and must create the `op_status` list. Both of these lists must be destroyed by the caller.

- The `op_status` list cannot be reused with another API call and it must be created and destroyed for each API call.

**Note:**

Since Oracle currently supports, only, the `CLSCRS_FLAG_REG_UPDATE` flag must always be passed. The flags apply to all servers in the input entity list.

(Optional) Provide detailed information about using the API or subprogram here.

### STAT3 API

Oracle Clusterware manages several entities, such as resources, server pools, and so on. However, the `clscrs_stat2` interface only allows retrieving (reading) entities by type, which means that a single retrieval can only return entities of a single type. Therefore, clients that need to get different types of entities and need to have a consistent view of the data structures to make further decisions have to rely on a work around using a special event sequence ID and, if necessary, reissue query requests several times. In theory, in a system with ever changing state/configuration such a solution is time-unbounded.

Oracle Clusterware 12c and later releases provide a mechanism to perform a consistent read of entities of several kinds. The mechanism works on entities transparently, such that addition of new managed entities do not require any changes to the mechanism.

This is achieved by the `clscrs_stat3` API.

#### clscrs_stat3

Obtains information about the Oracle Clusterware entities identified in `qlist`.

##### Syntax

    clscrs_stat3(clscrs_querylist *qlist,
                 uword flags,
                 clscrs_crsentitylist *out_entitylist);

##### Input

`qlist`: The list of Oracle Clusterware entities you want to query.

##### Output

`out_entitylist`: The entity list that holds the returned entity information.

##### Returns

- `CLSCRS_STAT_SUCCESS`: Indicates that the API successfully queried Oracle Clusterware.
- `CLSCRS_STAT_FAILURE`: Displays if there is an error querying Oracle Clusterware.
- `CLSCRS_STAT_CONNECTION`: Displays if there is a communication error.

##### Usage Notes

- Information is returned in `out_entitylist`. Queries are run such that the subsequent output set is consistent.

- You create `clscrs_query` objects and append them to the `clscrs_querylist` object before passing the object to this function. Any attributes required for each entity type must be present in the `clscrs_query` object. If the attribute list is empty, then Oracle Clusterware returns all attributes.

- The `out_entitylist` must be created and passed as an empty list. Any errors for an entity are returned in the `out_entitylist`.

- The output is returned as a nested entity list. Results for individual queries are returned as respective entities in the `out_entitylist`. The output for individual queries is returned as an entity list for that specific entity. The type of results in the entity can be verified by calling `clscrs_crsentity_get_type`, to get the Oracle Clusterware entity type of the entity that is part of the `out_entitylist`.

  For example, if you have two queries, one for resources and the other for resource types, then `out_entitylist` will contain two entity objects, one for each of the aforementioned Oracle Clusterware entity types. The entity list for each of these entity objects will contain the results of the queries. To determine what type of entity object a particular object is, you must call the `clscrs_crsentity_get_type` function on that entity object. If the query returns zero matches, then the size of the entity list for that entity object will be zero.

**Note:**

Oracle supports only one `clscrs_query` object per entity type. If more than one `clscrs_query` object is created for the same entity type, then Oracle does not guarantee the `stat3` API behavior.

### Miscellaneous APIs

Parameters for the APIs listed in this section are separated into those for which you provide input and those that display information when the function completes successfully.

#### clscrs_get_error_details

Returns the `clsk` exception stack if there are any failures while invoking other CLSCRS APIs.

##### Syntax

    clscrs_get_error_details(oratext* error_buf, size_t* buf_size);

##### Input

- `error_buf`: The buffer that will be populated with the error stack.
- `buf_size`: The size of the buffer for `error_buf`. If the size of the buffer given is smaller than what is required, then the API returns a value for the necessary buffer size.

##### Returns

- `clscrsretSUCC`: Indicates that the error stack printed successfully.
- `clscrsretEMPTY`: Displays if the error stack is empty.
- `clscrsretBADARG`: Displays if either `error_buf` or `buf_size` is NULL.
- `clscrsretBUFFSMALL`: Displays if the buffer size that you specify is smaller than what is required.

##### Usage Notes

The caller is responsible for allocating memory for `error_buf`.

#### clscrs_request_action

Instructs Oracle Clusterware to run an action on a named set of resources.

##### Syntax

    clscrs_request_action(oratext *action_name, clscrs_splist *ridlist,
                          clscrs_env env, clscrs_msgf2 msgf,
                          void *msgarg, uword flag, clscrs_reslist *op_status);

##### Input

- `action_name`: The name of the action to be performed.
- `ridlist`: The list of resources or resource instance IDs to stop, or a filter.
- `env`: Specify environment arguments to the stop operation.
- `msgf`: User message callback, which can be NULL.
- `msgarg`: User callback argument, which can be NULL.
- `flag`: Either `async` or `queue` options.

##### Output

`op_status`: The resource list that holds the status of the action operation for each resource.

##### Returns

- `CLSCRS_STAT_INVALID_RESNAME`: Displays if `ridlist` is empty.
- `CLSCRS_STAT_AUTHORIZATION_FAILURE`: Displays when authorization fails.
- `CLSCRS_STAT_SUCCESS`: Displays if the request completes successfully for all requested entities or if no entities match a filter.
- `CLSCRS_STAT_FAILURE`: Displays if at least one resource or resource ID does not stop successfully.
- `CLSCRS_STAT_CONNECTION`: Displays if there is a communication error.

##### Usage Notes

- In the first argument, you can specify either a list of resource IDs or a filter.

- Specifying a filter enables the query and action to take place in a single call. The filter searches all registered resources.

#### clscrs_restart_resource

Instructs Oracle Clusterware to restart a named set of resources.

##### Syntax

    clscrs_restart_resource(clscrs_splist *ridlist,
                            clscrs_env env, clscrs_msgf2 msgf, void *msgarg,
                            uword flag, clscrs_reslist *op_status);

##### Input

- `ridlist`: The list of resources or resource instance IDs to restart, or a filter.
- `env`: Specify environment arguments to the restart operation.
- `msgf`: User message callback, which can be NULL.
- `msgarg`: User callback argument, which can be NULL.
- `flag`: Either `async`, `force`, or `event` options.

##### Output

`op_status`: The resource list that holds the status of the restart operation for each resource.

##### Returns

- `CLSCRS_STAT_INVALID_RESNAME`: Displays if `ridlist` is empty.
- `CLSCRS_STAT_AUTHORIZATION_FAILURE`: Displays when authorization fails.
- `CLSCRS_STAT_SUCCESS`: Displays if the request completes successfully for all requested entities or if no entities match a filter.
- `CLSCRS_STAT_FAILURE`: Displays if at least one resource or resource ID does not start successfully.
- `CLSCRS_STAT_CONNECTION`: Displays if there is a communication error.
- `CLSCRS_STAT_WRONG_ACTIVE_VERSION`: Displays if you use the API before you have upgraded Oracle Clusterware.

##### Usage Notes

- If the flag is `async`, then the `msgf` callback function you specify is never called. The API returns an `OK` status after initiating the call to Oracle Clusterware, and asynchronously runs the restarts.

- If the flag is not `async`, and `msgf` is not NULL, then the API drives `msgf` one line at a time with collected output from the restart programs. An optional `event` flag maybe passed to indicate that this is not a request to perform an action, but rather a notification that the action has already started. The flag should only be used for a narrow set of co-managed resources.

- In the first argument, you can specify either a list of resource IDs or a filter. Specifying a filter enables the query and action to take place in a single call. The filter searches all registered resources.

#### clscrs_start_resource_in_pools

Instructs Oracle Clusterware to start a named set of resources in server pools.

##### Syntax

    clscrs_start_resource_in_pools(clscrs_splist *ridlist,clscrs_splist *spoollist,
                                   clscrs_env env,clscrs_msgf2 msgf2, void *msgarg,
                                   uword flags, clscrs_reslist *op_status);

##### Input

- `ridlist`: The list of resources or resource instance IDs to start, or a filter.
- `spoollist`: The list of server pool names where a resource that you want to start is running, or a filter.
- `env`: Specify environment arguments to the start operation.
- `msgf`: User message callback, which can be NULL.
- `msgarg`: User callback argument, which can be NULL.
- `flag`: Either `async`, `force`, or `event` options.

##### Output

`op_status`: The resource list that holds the status of the start operation for each resource.

##### Returns

- `CLSCRS_STAT_INVALID_RESNAME`: Displays if `ridlist` is empty.
- `CLSCRS_STAT_AUTHORIZATION_FAILURE`: Displays when authorization fails.
- `CLSCRS_STAT_SUCCESS`: Displays if the request completes successfully for all requested entities or if no entities match a filter.
- `CLSCRS_STAT_FAILURE`: Displays if at least one resource or resource ID does not start successfully.
- `CLSCRS_STAT_CONNECTION`: Displays if there is a communication error.

##### Usage Notes

- Functionality is similar to `clscrs_start_resource2`, except that this function takes an extra argument—`spoollist`—which is a list of server pool names or a filter based on which a list of server pools is generated.

- This function does not take `node` as an argument.

#### clscrs_stop_resource_in_pools

Instructs Oracle Clusterware to stop a named set of resources in server pools.

##### Syntax

    clscrs_stop_resource_in_pools(clscrs_splist *ridlist,clscrs_splist *spoollist,
                                  clscrs_env env,clscrs_msgf2 msgf2, void *msgarg,
                                  uword flags, clscrs_reslist *op_status);

##### Input

- `ridlist`: The list of resources or resource instance IDs to stop, or a filter.
- `spoollist`: The list of server pool names where a resource that you want to stop is running, or a filter.
- `env`: Specify environment arguments to the stop operation.
- `msgf`: User message callback, which can be NULL.
- `msgarg`: User callback argument, which can be NULL.
- `flag`: Either `async`, `force`, or `event` options.

##### Output

`op_status`: The resource list that holds the status of the stop operation for each resource.

##### Returns

- `CLSCRS_STAT_INVALID_RESNAME`: Displays if `ridlist` is empty.
- `CLSCRS_STAT_AUTHORIZATION_FAILURE`: Displays when authorization fails.
- `CLSCRS_STAT_SUCCESS`: Displays if the request completes successfully for all requested entities or if no entities match a filter.
- `CLSCRS_STAT_FAILURE`: Displays if at least one resource or resource ID does not stop successfully.
- `CLSCRS_STAT_CONNECTION`: Displays if there is a communication error.

##### Usage Notes

- Functionality is similar to `clscrs_stop_resource2`, except that this function takes an extra argument—`spoollist`—which is a list of server pool names or a filter based on which a list of server pools is generated.

- This function does not take `node` as an argument.
