Lists and describes the thread management functions.

Table 26-5 lists the thread management functions that are described in this section.

Table 26-5 Thread Management Functions

| Function                | Purpose                                                                                                            |
|:------------------------|:-------------------------------------------------------------------------------------------------------------------|
| OCIThreadClose()        | Close a thread handle                                                                                              |
| OCIThreadCreate()       | Create a new thread                                                                                                |
| OCIThreadHandleGet()    | Retrieve the OCIThreadHandle of the thread in which it is called                                                   |
| OCIThreadHndDestroy()   | Destroy and deallocate the thread handle                                                                           |
| OCIThreadHndInit()      | Allocate and initialize the thread handle                                                                          |
| OCIThreadIdDestroy()    | Destroy and deallocate a thread ID                                                                                 |
| OCIThreadIdGet()        | Retrieve the `OCIThreadId` of the thread in which it is called                                                     |
| OCIThreadIdInit()       | Allocate and initialize the thread ID                                                                              |
| OCIThreadIdNull()       | Determine whether a given `OCIThreadId` is the `NULL` thread ID                                                    |
| OCIThreadIdSame()       | Determine whether two `OCIThreadId`s represent the same thread                                                     |
| OCIThreadIdSet()        | Set one `OCIThreadId` to another                                                                                   |
| OCIThreadIdSetNull()    | Set the `NULL` thread ID to a given `OCIThreadId`                                                                  |
| OCIThreadInit()         | Initialize OCIThread context                                                                                       |
| OCIThreadIsMulti()      | Tell the caller whether the application is running in a multithreaded environment or a single-threaded environment |
| OCIThreadJoin()         | Allow the calling thread to join with another thread                                                               |
| OCIThreadKeyDestroy()   | Destroy and deallocate the key pointed to by `key`                                                                 |
| OCIThreadKeyGet()       | Get the calling thread's current value for a key                                                                   |
| OCIThreadKeyInit()      | Create a key                                                                                                       |
| OCIThreadKeySet()       | Set the calling thread's value for a key                                                                           |
| OCIThreadMutexAcquire() | Acquire a mutex for the thread in which it is called                                                               |
| OCIThreadMutexDestroy() | Destroy and deallocate a mutex                                                                                     |
| OCIThreadMutexInit()    | Allocate and initialize a mutex                                                                                    |
| OCIThreadMutexRelease() | Release a mutex                                                                                                    |
| OCIThreadProcessInit()  | Perform OCIThread process initialization                                                                           |
| OCIThreadTerm()         | Release the OCIThread context                                                                                      |

### 26.6.1 OCIThreadClose()

Closes a thread handle.

#### Purpose

Closes a thread handle.

#### Syntax

    sword OCIThreadClose ( void             *hndl,
                           OCIError         *err,
                           OCIThreadHandle  *tHnd );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err` and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

tHnd (IN/OUT)
The OCIThread thread handle to close.

#### Comments

The `tHnd` parameter should be initialized by `OCIThreadHndInit()`. Both the thread handle and the thread ID that was returned by the same call to `OCIThreadCreate()` are invalid after the call to `OCIThreadClose()`.

**Related Topics**

- OCIThreadCreate()
- OCIThreadHndInit()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.6.2 OCIThreadCreate()

Creates a new thread.

#### Purpose

Creates a new thread.

#### Syntax

    sword OCIThreadCreate ( void             *hndl,
                            OCIError         *err,
                            void (*start)    (void *),
                            void             *arg,
                            OCIThreadId      *tid,
                            OCIThreadHandle  *tHnd );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err` and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

start (IN)
The function in which the new thread should begin execution.

arg (IN)
The argument to give the function pointed to by `start`.

tid (IN/OUT)
If not `NULL`, gets the ID for the new thread.

tHnd (IN/OUT)
If not `NULL`, gets the handle for the new thread.

#### Comments

The new thread starts by executing a call to the function pointed to by `start` with the argument given by `arg`. When that function returns, the new thread terminates. The function should not return a value and should accept one parameter, a `void`. The call to `OCIThreadCreate()` must be matched by a call to `OCIThreadClose()` if and only if `tHnd` is non-`NULL`.

If `tHnd` is `NULL`, a thread ID placed in `*tid` is not valid in the calling thread because the timing of the spawned threads termination is unknown.

The `tid` parameter should be initialized by `OCIThreadIdInit()` and `tHnd` should be initialized by `OCIThreadHndInit()`.

**Related Topics**

- OCIThreadClose()
- OCIThreadIdInit()
- OCIThreadHndInit()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.6.3 OCIThreadHandleGet()

Retrieves the `OCIThreadHandle` of the thread in which it is called.

#### Purpose

Retrieves the `OCIThreadHandle` of the thread in which it is called.

#### Syntax

    sword OCIThreadHandleGet ( void             *hndl,
                               OCIError         *err,
                               OCIThreadHandle  *tHnd );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err` and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

tHnd (IN/OUT)
If not `NULL`, the location to place the thread handle for the thread.

#### Comments

The `tHnd` parameter should be initialized by `OCIThreadHndInit()`.

The thread handle `tHnd` retrieved by this function must be closed with `OCIThreadClose()` and destroyed by `OCIThreadHndDestroy()` after it is used.

**Related Topics**

- OCIThreadHndDestroy()
- OCIThreadHndInit()
- OCIThreadClose()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.6.4 OCIThreadHndDestroy()

Destroys and deallocates the thread handle.

#### Purpose

Destroys and deallocates the thread handle.

#### Syntax

    sword OCIThreadHndDestroy ( void              *hndl,
                                OCIError          *err,
                                OCIThreadHandle  **thnd );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err` and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

thnd (IN/OUT)
The address of pointer to the thread handle to destroy.

#### Comments

The `thnd` parameter should be initialized by `OCIThreadHndInit()`.

**Related Topics**

- OCIThreadHandleGet()
- OCIThreadHndInit()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.6.5 OCIThreadHndInit()

Allocates and initializes the thread handle.

#### Purpose

Allocates and initializes the thread handle.

#### Syntax

    sword OCIThreadHndInit ( void               *hndl,
                             OCIError           *err,
                             OCIThreadHandle   **thnd );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err` and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

thnd (OUT)
The address of the pointer to the thread handle to initialize.

**Related Topics**

- OCIThreadHandleGet()
- OCIThreadHndDestroy()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.6.6 OCIThreadIdDestroy()

Destroys and deallocates a thread ID.

#### Purpose

Destroys and deallocates a thread ID.

#### Syntax

    sword OCIThreadIdDestroy (void          *hndl,
                              OCIError      *err,
                              OCIThreadId  **tid );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error and `OCI_ERROR` is returned, the error is recorded in `err` and diagnostic information can be obtained by calling `OCIErrorGet()`.

tid (IN/OUT)
Pointer to the thread ID to destroy.

#### Comments

The `tid` parameter should be initialized by `OCIThreadHndInit()`.

**Related Topics**

- OCIThreadIdGet()
- OCIThreadIdInit()
- OCIThreadIdNull()
- OCIThreadIdSame()
- OCIThreadIdSet()
- OCIThreadIdSetNull()
- OCIThreadHndInit()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.6.7 OCIThreadIdGet()

Retrieves the `OCIThreadId` of the thread in which it is called.

#### Purpose

Retrieves the `OCIThreadId` of the thread in which it is called.

#### Syntax

    sword OCIThreadIdGet ( void         *hndl,
                           OCIError     *err,
                           OCIThreadId  *tid );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err` and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

tid (OUT)
This should point to the location in which to place the ID of the calling thread.

#### Comments

The `tid` parameter should be initialized by `OCIThreadHndInit()`. When OCIThread is used in a single-threaded environment, `OCIThreadIdGet()` always places the same value in the location pointed to by `tid`. The exact value itself is not important. The important thing is that it is different from the `NULL` thread ID and that it is always the same value.

**Related Topics**

- OCIThreadIdDestroy()
- OCIThreadIdInit()
- OCIThreadIdNull()
- OCIThreadIdSame()
- OCIThreadIdSet()
- OCIThreadIdSetNull()
- OCIThreadHndInit()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.6.8 OCIThreadIdInit()

Allocate and initialize the thread ID `tid`.

#### Purpose

Allocate and initialize the thread ID `tid`.

#### Syntax

    sword OCIThreadIdInit ( void          *hndl,
                            OCIError      *err,
                            OCIThreadId  **tid );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error and `OCI_ERROR` is returned, the error is recorded in `err` and diagnostic information can be obtained by calling `OCIErrorGet()`.

tid (OUT)
Pointer to the thread ID to initialize.

**Related Topics**

- OCIThreadIdDestroy()
- OCIThreadIdGet()
- OCIThreadIdNull()
- OCIThreadIdSame()
- OCIThreadIdSet()
- OCIThreadIdSetNull()
- [OCIErrorGet()](miscellaneous-functions.md)
- OCIThreadTerm()
- OCIThreadProcessInit()

### 26.6.9 OCIThreadIdNull()

Determines whether a given `OCIThreadId` is the `NULL` thread ID.

#### Purpose

Determines whether a given `OCIThreadId` is the `NULL` thread ID.

#### Syntax

    sword OCIThreadIdNull ( void         *hndl,
                            OCIError     *err,
                            OCIThreadId  *tid,
                            boolean      *result );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err` and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

tid (IN)
Pointer to the `OCIThreadId` to check.

result (IN/OUT)
Pointer to the result.

#### Comments

If `tid` is the `NULL` thread ID, `result` is set to `TRUE`. Otherwise, `result` is set to `FALSE`. The `tid` parameter should be initialized by `OCIThreadIdInit()`.

**Related Topics**

- OCIThreadIdDestroy()
- OCIThreadIdGet()
- OCIThreadIdInit()
- OCIThreadIdSame()
- OCIThreadIdSet()
- OCIThreadIdSetNull()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.6.10 OCIThreadIdSame()

Determines whether two `OCIThreadId`s represent the same thread.

#### Purpose

Determines whether two `OCIThreadId`s represent the same thread.

#### Syntax

    sword OCIThreadIdSame ( void          *hndl,
                            OCIError      *err,
                            OCIThreadId   *tid1,
                            OCIThreadId   *tid2,
                            boolean       *result );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err` and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

tid1 (IN)
Pointer to the first `OCIThreadId`.

tid2 (IN)
Pointer to the second `OCIThreadId`.

result (IN/OUT)
Pointer to the result.

#### Comments

If `tid1` and `tid2` represent the same thread, `result` is set to `TRUE`. Otherwise, `result` is set to `FALSE`. The `result` parameter is set to `TRUE` if both `tid1` and `tid2` are the `NULL` thread ID. The parameters `tid1` and `tid2` should be initialized by `OCIThreadIdInit()`.

**Related Topics**

- OCIThreadIdDestroy()
- OCIThreadIdGet()
- OCIThreadIdInit()
- OCIThreadIdNull()
- OCIThreadIdSet()
- OCIThreadIdSetNull()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.6.11 OCIThreadIdSet()

Sets one `OCIThreadId` to another.

#### Purpose

Sets one `OCIThreadId` to another.

#### Syntax

    sword OCIThreadIdSet ( void         *hndl,
                           OCIError     *err,
                           OCIThreadId  *tidDest,
                           OCIThreadId  *tidSrc );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error and `OCI_ERROR` is returned, the error is recorded in `err` and diagnostic information can be obtained by calling `OCIErrorGet()`.

tidDest (OUT)
This should point to the location of the `OCIThreadId` to set to.

tidSrc (IN)
This should point to the `OCIThreadId` to set from.

#### Comments

The `tid` parameter should be initialized by `OCIThreadIdInit()`.

**Related Topics**

- OCIThreadIdDestroy()
- OCIThreadIdGet()
- OCIThreadIdInit()
- OCIThreadIdNull()
- OCIThreadIdSame()
- OCIThreadIdSetNull()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.6.12 OCIThreadIdSetNull()

Sets the `NULL` thread ID to a given `OCIThreadId`.

#### Purpose

Sets the `NULL` thread ID to a given `OCIThreadId`.

#### Syntax

    sword OCIThreadIdSetNull ( void         *hndl,
                               OCIError     *err,
                               OCIThreadId  *tid );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err` and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

tid (OUT)
This should point to the `OCIThreadId` in which to put the `NULL` thread ID.

#### Comments

The `tid` parameter should be initialized by `OCIThreadIdInit()`.

**Related Topics**

- OCIThreadIdDestroy()
- OCIThreadIdGet()
- OCIThreadIdInit()
- OCIThreadIdNull()
- OCIThreadIdSame()
- OCIThreadIdSet()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.6.13 OCIThreadInit()

Initializes the OCIThread context.

#### Purpose

Initializes the OCIThread context.

#### Syntax

    sword OCIThreadInit ( void      *hndl,
                          OCIError  *err );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error and `OCI_ERROR` is returned, the error is recorded in `err` and diagnostic information can be obtained by calling `OCIErrorGet()`.

#### Comments

It is illegal for OCIThread clients to try to examine the memory pointed to by the returned pointer. It is safe to make concurrent calls to `OCIThreadInit()`. Unlike `OCIThreadProcessInit()`, there is no need to have a first call that occurs before all the others.

The first time `OCIThreadInit()` is called, it initializes the OCIThread context. It also saves a pointer to the context in some system-dependent manner. Subsequent calls to `OCIThreadInit()` return the same context.

Each call to `OCIThreadInit()` must eventually be matched by a call to `OCIThreadTerm()`.

### 26.6.14 OCIThreadIsMulti()

Tells the caller whether the application is running in a multithreaded environment or a single-threaded environment.

#### Purpose

Tells the caller whether the application is running in a multithreaded environment or a single-threaded environment.

#### Syntax

    boolean OCIThreadIsMulti ( );

#### Returns

`TRUE` if the environment is multithreaded.

`FALSE` if the environment is single-threaded.

**Related Topics**

- OCIThreadIdDestroy()
- OCIThreadIdGet()
- OCIThreadIdInit()
- OCIThreadIdNull()
- OCIThreadIdSame()
- OCIThreadIdSet()

### 26.6.15 OCIThreadJoin()

Allows the calling thread to join with another thread.

#### Purpose

Allows the calling thread to join with another thread.

#### Syntax

    sword OCIThreadJoin ( void             *hndl,
                          OCIError         *err,
                          OCIThreadHandle  *tHnd );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err` and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

tHnd (IN)
The `OCIThreadHandle` of the thread to join with.

#### Comments

This function blocks the caller until the specified thread terminates.

The `tHnd` parameter should be initialized by `OCIThreadHndInit()`. The result of multiple threads all trying to join with the same thread is undefined.

**Related Topics**

- OCIThreadIdDestroy()
- OCIThreadIdGet()
- OCIThreadIdInit()
- OCIThreadIdNull()
- OCIThreadIdSame()
- OCIThreadIdSet()
- OCIThreadHndInit()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.6.16 OCIThreadKeyDestroy()

Destroys and deallocates the key pointed to by `key`.

#### Purpose

Destroys and deallocates the key pointed to by `key`.

#### Syntax

    sword OCIThreadKeyDestroy ( void           *hndl,
                                OCIError       *err,
                                OCIThreadKey  **key );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error and `OCI_ERROR` is returned, the error is recorded in `err` and diagnostic information can be obtained by calling `OCIErrorGet()`.

key (IN/OUT)
The `OCIThreadKey` in which to destroy the key.

#### Comments

This is different from the destructor function callback passed to the key create routine. The function `OCIThreadKeyDestroy()` is used to terminate any resources that the OCIThread acquired when it created `key`. The `OCIThreadKeyDestFunc` callback of `OCIThreadKeyInit()` is a key value destructor; it does not operate on the key itself.

This must be called after the user has finished using the key. Not calling the `OCIThreadKeyDestroy()` function may result in memory leaks.

**Related Topics**

- OCIThreadKeyGet()
- OCIThreadKeyInit()
- OCIThreadKeySet()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.6.17 OCIThreadKeyGet()

Gets the calling thread's current value for a key.

#### Purpose

Gets the calling thread's current value for a key.

#### Syntax

    sword OCIThreadKeyGet ( void           *hndl,
                            OCIError       *err,
                            OCIThreadKey   *key,
                            void          **pValue );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error and `OCI_ERROR` is returned, the error is recorded in `err` and diagnostic information can be obtained by calling `OCIErrorGet()`.

key (IN)
The key.

pValue (IN/OUT)
The location in which to place the thread-specific key value.

#### Comments

It is illegal to use this function on a key that has not been created using `OCIThreadKeyInit()`.

If the calling thread has not yet assigned a value to the key, `NULL` is placed in the location pointed to by `pValue`.

**Related Topics**

- OCIThreadKeyDestroy()
- OCIThreadKeyInit()
- OCIThreadKeySet()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.6.18 OCIThreadKeyInit()

Creates a key.

#### Purpose

Creates a key.

#### Syntax

    sword OCIThreadKeyInit (void                   *hndl,
                            OCIError               *err,
                            OCIThreadKey          **key,
                            OCIThreadKeyDestFunc    destFn );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error and `OCI_ERROR` is returned, the error is recorded in `err` and diagnostic information can be obtained by calling `OCIErrorGet()`.

key (OUT)
The `OCIThreadKey` in which to create the new key.

destFn (IN)
The destructor for the key. `NULL` is permitted.

#### Comments

Each call to this routine allocates and generates a new key that is distinct from all other keys. After this function executes successfully, a pointer to an allocated and initialized key is returned. That key can be used with `OCIThreadKeyGet()` and `OCIThreadKeySet()`. The initial value of the key is `NULL` for all threads.

It is illegal for this function to be called more than once with the same value for the `key` parameter.

If the `destFn` parameter is not `NULL`, the routine pointed to by `destFn` is called whenever a thread that has a non-`NULL` value for the key terminates. The routine is called with one parameter. The parameter is the key's value for the thread at the time at which the thread terminated. If the key does not need a destructor function, pass `NULL` for `destFn`.

**Related Topics**

- OCIThreadKeyDestroy()
- OCIThreadKeyGet()
- OCIThreadKeySet()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.6.19 OCIThreadKeySet()

Sets the calling thread's value for a key.

#### Purpose

Sets the calling thread's value for a key.

#### Syntax

    sword OCIThreadKeySet ( void           *hndl,
                            OCIError       *err,
                            OCIThreadKey   *key,
                            void           *value );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error and `OCI_ERROR` is returned, the error is recorded in `err` and diagnostic information can be obtained by calling `OCIErrorGet()`.

key (IN/OUT)
The key.

value (IN)
The thread-specific value to set in the key.

#### Comments

It is illegal to use this function on a key that has not been created using `OCIThreadKeyInit()`.

**Related Topics**

- OCIThreadKeyDestroy()
- OCIThreadKeyGet()
- OCIThreadKeyInit()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.6.20 OCIThreadMutexAcquire()

Acquires a mutex for the thread in which it is called.

#### Purpose

Acquires a mutex for the thread in which it is called.

#### Syntax

    sword OCIThreadMutexAcquire ( void            *hndl,
                                  OCIError        *err,
                                  OCIThreadMutex  *mutex );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err` and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

mutex (IN/OUT)
The mutex to acquire.

#### Comments

If the mutex is held by another thread, the calling thread is blocked until it can acquire the mutex.

It is illegal to attempt to acquire an uninitialized mutex.

This function's behavior is undefined if it is used by a thread to acquire a mutex that is already held by that thread.

**Related Topics**

- OCIThreadMutexDestroy()
- OCIThreadMutexInit()
- OCIThreadMutexRelease()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.6.21 OCIThreadMutexDestroy()

Destroys and deallocates a mutex.

#### Purpose

Destroys and deallocates a mutex.

#### Syntax

    sword OCIThreadMutexDestroy ( void            *hndl,
                                  OCIError        *err,
                                  OCIThreadMutex **mutex );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error and `OCI_ERROR` is returned, the error is recorded in `err` and diagnostic information can be obtained by calling `OCIErrorGet()`.

mutex (IN/OUT)
The mutex to destroy.

#### Comments

Each mutex must be destroyed after it is no longer needed.

It is not legal to destroy a mutex that is uninitialized or is currently held by a thread. The destruction of a mutex must not occur concurrently with any other operations on the mutex. A mutex must not be used after it has been destroyed.

**Related Topics**

- OCIThreadMutexAcquire()
- OCIThreadMutexInit()
- OCIThreadMutexRelease()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.6.22 OCIThreadMutexInit()

Allocates and initializes a mutex.

#### Purpose

Allocates and initializes a mutex.

#### Syntax

    sword OCIThreadMutexInit ( void             *hndl,
                               OCIError         *err,
                               OCIThreadMutex  **mutex );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error and `OCI_ERROR` is returned, the error is recorded in `err` and diagnostic information can be obtained by calling `OCIErrorGet()`.

mutex (OUT)
The mutex to initialize.

#### Comments

All mutexes must be initialized before use.

Multiple threads must not initialize the same mutex simultaneously. Also, a mutex must not be reinitialized until it has been destroyed (see `OCIThreadMutexDestroy()`).

**Related Topics**

- OCIThreadMutexDestroy()
- OCIThreadMutexAcquire()
- OCIThreadMutexRelease()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.6.23 OCIThreadMutexRelease()

Releases a mutex.

#### Purpose

Releases a mutex.

#### Syntax

    sword OCIThreadMutexRelease ( void            *hndl,
                                  OCIError        *err,
                                  OCIThreadMutex  *mutex );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error and `OCI_ERROR` is returned, the error is recorded in `err` and diagnostic information can be obtained by calling `OCIErrorGet()`.

mutex (IN/OUT)
The mutex to release.

#### Comments

If there are any threads blocked on the mutex, one of them acquires it and becomes unblocked.

It is illegal to attempt to release an uninitialized mutex. It is also illegal for a thread to release a mutex that it does not hold.

**Related Topics**

- OCIThreadMutexDestroy()
- OCIThreadMutexInit()
- OCIThreadMutexAcquire()
- [OCIErrorGet()](miscellaneous-functions.md)

### 26.6.24 OCIThreadProcessInit()

Performs OCIThread process initialization.

#### Purpose

Performs OCIThread process initialization.

#### Syntax

    void OCIThreadProcessInit ( );

#### Comments

Whether this function must be called depends on how OCIThread is going to be used.

In a single-threaded application, calling this function is optional. If it is called at all, the first call to it must occur before calls to any other OCIThread functions. Subsequent calls can be made without restriction; they do not have any effect.

In a multithreaded application, this function must be called. The first call to it must occur strictly before any other OCIThread calls; that is, no other calls to OCIThread functions (including other calls to this one) can be concurrent with the first call.

Subsequent calls to this function can be made without restriction; they do not have any effect.

**Related Topics**

- OCIThreadIdDestroy()
- OCIThreadIdGet()
- OCIThreadIdInit()
- OCIThreadIdNull()
- OCIThreadIdSame()
- OCIThreadIdSet()

### 26.6.25 OCIThreadTerm()

Releases the OCIThread context.

#### Purpose

Releases the OCIThread context.

#### Syntax

    sword OCIThreadTerm ( void      *hndl,
                          OCIError  *err );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error and `OCI_ERROR` is returned, the error is recorded in `err` and diagnostic information can be obtained by calling `OCIErrorGet()`.

#### Comments

This function should be called exactly once for each call made to `OCIThreadInit()`.

It is safe to make concurrent calls to `OCIThreadTerm()`. `OCIThreadTerm()` does not do anything until it has been called as many times as `OCIThreadInit()` has been called. When that happens, `OCIThreadTerm()` terminates the OCIThread layer and frees the memory allocated for the context. Once this happens, the context should not be reused. It is necessary to obtain a new one by calling `OCIThreadInit()`.

**Related Topics**

- OCIThreadInit()
- [OCIErrorGet()](miscellaneous-functions.md)
