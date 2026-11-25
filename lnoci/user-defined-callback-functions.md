Oracle Call Interface can execute user-specific code in addition to OCI calls.

You can use this functionality for:

- Adding tracing and performance measurement code to enable users to tune their applications

- Performing preprocessing or postprocessing code for specific OCI calls

- Accessing other data sources with OCI by using the native OCI interface for Oracle Databases and directing the OCI calls to use user callbacks for non-Oracle data sources

The OCI callback feature provides support for calling user code before or after executing the OCI calls. It also allows the user-defined code to be executed instead of executing the OCI code.

The user callback code can be registered dynamically without modifying the source code of the application. The dynamic registration is implemented by loading up to five user-created dynamically linked libraries after the initialization of the environment handle during the `OCIEnvCreate()` call. These user-created libraries (such as dynamic-link libraries (DLLs) on Windows, or shared libraries on Solaris, register the user callbacks for the selected OCI calls transparently to the application.

### Sample Application

For a listing of the complete demonstration programs that illustrate the OCI user callback feature, see Appendix B.

This section includes the following topics:

- About Registering User Callbacks in OCI

- OCI Callbacks from External Procedures

**See Also:**

[OCIEnvCreate()](connect-authorize-and-initialize-functions.md)

### 14.1 About Registering User Callbacks in OCI

An application can register user callback libraries with the `OCIUserCallbackRegister()` function.

Callbacks are registered in the context of the environment handle. An application can retrieve information about callbacks registered with a handle with the `OCIUserCallbackGet()` function.

A user-defined callback is a subroutine that is registered against an OCI call and an environment handle. It can be specified to be either an entry callback, a replacement callback, or an exit callback.

- If it is an entry callback, it is called when the program enters the OCI function.

- Replacement callbacks are executed after entry callbacks. If the replacement callback returns a value of `OCI_CONTINUE`, then a subsequent replacement callback or the normal OCI-specific code is executed. If a replacement callback returns anything other than `OCI_CONTINUE`, then subsequent replacement callbacks and the OCI code do not execute.

- After a replacement callback returns something other than `OCI_CONTINUE`, or an OCI function successfully executes, program control transfers to the exit callback (if one is registered).

If a replacement or exit callback returns anything other than `OCI_CONTINUE`, then the return code from the callback is returned from the associated OCI call.

A user callback can return `OCI_INVALID_HANDLE` when either an invalid handle or an invalid context is passed to it.

**Note:**

If any callback returns anything other than `OCI_CONTINUE`, then that return code is passed to the subsequent callbacks. If a replacement or exit callback returns a return code other than `OCI_CONTINUE`, then the final (not `OCI_CONTINUE`) return code is returned from the OCI call.

This section includes the following topics:

- OCIUserCallbackRegister

- User Callback Function

- User Callback Control Flow

- User Callback for OCIErrorGet()

- Errors from Entry Callbacks

- Dynamic Callback Registrations

- About Loading Multiple Packages

- Package Format

- User Callback Chaining

- About Accessing Other Data Sources Through OCI

- Restrictions on Callback Functions

- Example of OCI Callbacks

**See Also:**

[OCIUserCallbackGet()](miscellaneous-functions.md) and [OCIUserCallbackRegister()](miscellaneous-functions.md)

#### 14.1.1 OCIUserCallbackRegister

A user callback is registered using the OCIUserCallbackRegister() call.

Currently, `OCIUserCallbackRegister()` is only registered on the environment handle. The user's callback function of typedef `OCIUserCallback` is registered along with its context for the OCI call identified by the OCI function code, fcode. The type of the callback, whether entry, replacement, or exit, is specified by the when parameter.

For example, the `stmtprep_entry_dyncbk_fn` entry callback function and its context `dynamic_context`, are registered against the environment handle `hndlp` for the `OCIStmtPrepare2()` call by calling the `OCIUserCallbackRegister()` function with the following parameters.

    OCIUserCallbackRegister( hndlp,
                             OCI_HTYPE_ENV,
                             errh,
                             stmtprep_entry_dyncbk_fn,
                             dynamic_context,
                             OCI_FNCODE_STMTPREPARE,
                             OCI_UCBTYPE_ENTRY
                             (OCIUcb*) NULL);

**See Also:**

- [OCIUserCallbackRegister()](miscellaneous-functions.md)

- [OCIStmtPrepare2()](statement-functions.md)

#### 14.1.2 User Callback Function

Details about the user callback function.

The user callback function must use the following syntax:

    typedef sword (*OCIUserCallback)
         (void *ctxp,      /* context for the user callback*/
          void *hndlp,     /* handle for the callback, env handle for now */
          ub4 type,         /* type of handlp, OCI_HTYPE_ENV for this release */
          ub4 fcode,        /* function code of the OCI call */
          ub1 when,         /* type of the callback, entry or exit */
          sword returnCode, /* OCI return code */
          ub4 *errnop,      /* Oracle error number */
          va_list arglist); /* parameters of the oci call */

In addition to the parameters described in the `OCIUserCallbackRegister()` call, the callback is called with the return code, errnop, and all the parameters of the original OCI as declared by the prototype definition.

The return code is always passed in as `OCI_SUCCESS` and `*errnop` is always passed in as 0 for the first entry callback. Note that `*errnop` refers to the content of `errnop` because `errnop` is an IN/OUT parameter.

If the callback does not want to change the OCI return code, then it must return `OCI_CONTINUE`, and the value returned in `*errnop` is ignored. If, however, the callback returns any return code other than `OCI_CONTINUE`, the last returned return code becomes the return code for the call. At this point, the value returned for `*errnop` is set in the error handle, or in the environment handle if the error information is returned in the environment handle because of the absence of the error handle for certain OCI calls such as `OCIHandleAlloc()`.

For replacement callbacks, the `returnCode` is the non-`OCI_CONTINUE` return code from the previous callback or OCI call, and `*errnop` is the value of the error number being returned in the error handle. This allows the subsequent callback to change the return code or error information if needed.

The processing of replacement callbacks is different in that if it returns anything other than `OCI_CONTINUE`, then subsequent replacement callbacks and OCI code are bypassed and processing jumps to the exit callbacks.

Note that if the replacement callbacks return `OCI_CONTINUE` to allow processing of OCI code, then the return code from entry callbacks is ignored.

All the original parameters of the OCI call are passed to the callback as variable parameters, and the callback must retrieve them using the va_arg macros. The callback demonstration programs provide examples.

A null value can be registered to deregister a callback. That is, if the value of the callback (`OCIUserCallback()`) is `NULL` in the `OCIUserCallbackRegister()` call, then the user callback is deregistered.

When using the thread-safe mode, the OCI program acquires all mutexes before calling the user callbacks.

**See Also:**

- [OCI Demonstration Programs](oci-demo-programs.md)

- [OCIUserCallbackRegister()](miscellaneous-functions.md)

- [OCIHandleAlloc()](handle-and-descriptor-functions.md)

#### 14.1.3 User Callback Control Flow

Shows the control flow for a user callback.

Example 14-1 shows pseudocode that describes the overall processing of a typical OCI call.

Example 14-1 Pseudocode That Describes the Overall Processing of a Typical OCI Call

    OCIXyzCall()
    {
     Acquire mutexes on handles;
     retCode = OCI_SUCCESS;
     errno = 0;
     for all ENTRY callbacks do
      {

         EntryretCode = (*entryCallback)(..., retcode, &errno, ...);
         if (retCode != OCI_CONTINUE)
          {
             set errno in error handle or environment handle;
             retCode = EntryretCode;
           }
       }
      for all REPLACEMENT callbacks do
      {
       retCode = (*replacementCallback) (..., retcode, &errno, ...);
       if (retCode != OCI_CONTINUE)
          {
           set errno in error handle or environment handle
           goto executeEXITCallback;
           }
       }

       retCode = return code for XyzCall; /* normal processing of OCI call */

       errno = error number from error handle or env handle;

     executeExitCallback:
       for all EXIT callbacks do
       {
           exitRetCode = (*exitCallback)(..., retCode, &errno,...);
           if (exitRetCode != OCI_CONTINUE)
           {
               set errno in error handle or environment handle;
               retCode = exitRetCode;
           }
       }
        release mutexes;
        return retCode
    }

#### 14.1.4 User Callback for OCIErrorGet()

If the callbacks are a total replacement of the OCI code, then they usually maintain their own error information in the call context and use that to return error information in `bufp` and `errcodep` parameters of the replacement callback of the `OCIErrorGet()` call.

If, however, the callbacks are either partially overriding OCI code, or just doing some other postprocessing, then they can use the exit callback to modify the error text and `errcodep` parameters of the `OCIErrorGet()` call by their own error message and error number. Note that the `*errnop` passed into the exit callback is the error number in the error or the environment handle.

**See Also:**

[OCIErrorGet()](miscellaneous-functions.md)

#### 14.1.5 Errors from Entry Callbacks

If an entry callback wants to return an error to the caller of the OCI call, then it must register a replacement or exit callback.

This is because if the OCI code is executed, then the error code from the entry callback is ignored. Therefore, the entry callback must pass the error to the replacement or exit callback through its own context.

#### 14.1.6 Dynamic Callback Registrations

Because user callbacks are expected to be used for monitoring OCI behavior or to access other data sources, it is desirable that the registration of the callbacks be done transparently and nonintrusively.

This is accomplished by loading user-created dynamically linked libraries at OCI initialization time. These dynamically linked libraries are called packages. The user-created packages register the user callbacks for the selected OCI calls. These callbacks can further register or deregister user callbacks as needed when receiving control at runtime.

A makefile (`ociucb.mk` on Solaris) is provided with the OCI demonstration programs to create the package. The exact naming and location of this package is operating system-dependent. The source code for the package must provide code for special callbacks that are called at OCI initialization and environment creation times.

Setting an operating system environment variable, `ORA_OCI_UCBPKG`, controls the loading of the package. This variable names the packages in a generic way. The packages must be located in the `$ORACLE_HOME/lib` directory.

#### 14.1.7 About Loading Multiple Packages

The `ORA_OCI_UCBPKG` variable can contain a semicolon-separated list of package names. The packages are loaded in the order they are specified in the list.

For example, in the past the package was specified as:

    setenv ORA_OCI_UCBPKG mypkg

Currently, you can still specify the package as before, but in addition multiple packages can be specified as:

    setenv ORA_OCI_UCBPKG "mypkg;yourpkg;oraclepkg;sunpkg;msoftpkg"

All these packages are loaded in order. That is, `mypkg` is loaded first and `msoftpkg` is loaded last.

A maximum of five packages can be specified.

**Note:**

The sample makefile `ociucb.mk` creates `ociucb.so.1.0` on a Solaris or `ociucb.dll` on a Windows system. To load the `ociucb` package, the environmental variable `ORA_OCI_UCBPKG` must be set to `ociucb`. On Solaris, if the package name ends with `.so`, OCIEnvCreate() or OCIEnvNlsCreate() fails. The package name must end with `.so.1.0`.

For further details about creating the dynamic-link libraries, read the Makefiles provided in the demo directory for your operating system. For further information about user-defined callbacks, see your operating system-specific documentation on compiling and linking applications.

#### 14.1.8 Package Format

The package source must provide two functions.

In the past, a package had to specify the source code for the `OCIEnvCallback()` function. However, the `OCIEnvCallback()` function is obsolete. Instead, the package source must provide two functions. The first function must be named as packagename suffixed with the word Init. For example, if the package is named `foo`, then the source file (for example, but not necessarily, foo.c) must contain a `fooInit()` function with a call to `OCISharedLibInit()` function specified exactly as:

    sword fooInit(metaCtx, libCtx, argfmt, argc, argv)
          void *     metaCtx;         /* The metacontext */
          void *     libCtx;          /* The context for this package. */
          ub4        argfmt;          /* package argument format */
          sword      argc;            /* package arg count*/
          void *     argv[];          /* package arguments */
    {
      return  (OCISharedLibInit(metaCtx, libCtx, argfmt, argc, argv,
                                fooEnvCallback));
    }

The last parameter of the `OCISharedLibInit()` function, `fooEnvCallback()` in this case, is the name of the second function. It can be named anything, but by convention it is named packagename suffixed with the word EnvCallback.

This function is a replacement for `OCIEnvCallback()`. Currently, all the dynamic user callbacks must be registered in this function. The function must be of type `OCIEnvCallbackType`, which is specified as:

    typedef sword (*OCIEnvCallbackType)(OCIEnv *env, ub4 mode,
                                        size_t xtramem_sz, void *usrmemp,
                                        OCIUcb *ucbDesc);

When an environment handle is created, then this callback function is called at the very end. The `env` parameter is the newly created environment handle.

The `mode`, `xtramem_sz`, and `usrmempp` are the parameters passed to the OCIEnvCreate() call. The last parameter, `ucbDesc`, is a descriptor that is passed to the package. The package uses this descriptor to register the user callbacks as described later.

A sample `ociucb.c` file is provided in the `demo` directory. The makefile `ociucb.mk` is also provided (on Solaris) in the `demo` directory to create the package. Please note that this may be different on other operating systems. The `demo` directory also contains full user callback demo programs (`cdemoucb.c, cdemoucbl.c`) illustrating this.

#### 14.1.9 User Callback Chaining

User callbacks can be registered statically in the application itself or dynamically at runtime in the DLLs.

A mechanism is needed to allow the application to override a previously registered callback and then later invoke the overridden one in the newly registered callback to preserve the behavior intended by the dynamic registrations. This can result in chaining of user callbacks.

The `OCIUserCallbackGet()` function determines which function and context is registered for an OCI call.

**See Also:**

[OCIUserCallbackGet()](miscellaneous-functions.md)

#### 14.1.10 About Accessing Other Data Sources Through OCI

Because Oracle Database is the predominant database software accessed, applications can take advantage of the OCI interface to access non-Oracle data by using the user callbacks to access them.

This allows an application written in OCI to access Oracle data without any performance penalty. Drivers can be written that access the non-Oracle data in user callbacks. Because OCI provides a very rich interface, there is usually a straightforward mapping of OCI calls to most data sources. This solution is better than writing applications for other middle layers such as ODBC that introduce performance penalties for all data sources. Using OCI does not incur any penalty to access Oracle data sources, and incurs the same penalty that ODBC does for non-Oracle data sources.

#### 14.1.11 Restrictions on Callback Functions

Details the restrictions on callback functions.

There are certain restrictions on the usage of callback functions, including `OCIEnvCallback()`:

- A callback cannot call other OCI functions except `OCIUserCallbackRegister()`, `OCIUserCallbackGet()`, `OCIHandleAlloc()`, and `OCIHandleFree()`. Even for these functions, if they are called in a user callback, then callbacks on them are not called to avoid recursion. For example, if `OCIHandleFree()` is called in the callback for `OCILogoff()`, then the callback for `OCIHandleFree()` is disabled during the execution of the callback for `OCILogoff()`.

- A callback cannot modify OCI data structures such as the environment or error handles.

- A callback cannot be registered for the `OCIUserCallbackRegister()` call itself, or for any of the following calls:

  - `OCIUserCallbackGet()`

  - `OCIEnvCreate()`

  - `OCIInitialize()` (Deprecated)

  - `OCIEnvNlsCreate()`

**See Also:**

- [OCIUserCallbackRegister()](miscellaneous-functions.md)

- [OCIUserCallbackGet()](miscellaneous-functions.md)

- [OCIHandleAlloc()](handle-and-descriptor-functions.md)

- [OCIHandleFree()](handle-and-descriptor-functions.md)

- [OCILogoff()](connect-authorize-and-initialize-functions.md)

- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)

- [OCIInitialize()](deprecated-oci-functions.md)

- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)

#### 14.1.12 Example of OCI Callbacks

Shows examples of using OCI callbacks.

Suppose that there are five packages each registering entry, replacement, and exit callbacks for the `OCIStmtPrepare2()` call. That is, the `ORA_OCI_UCBPKG` variable is set as shown in Example 14-2.

In each package `pkgN` (where N can be 1 through 5), the `pkgNInit()` and `PkgNEnvCallback()` functions are specified, as shown in Example 14-3.

Example 14-4 shows how the `pkgNEnvCallback()` function registers the entry, replacement, and exit callbacks.

Finally, Example 14-5 shows how in the source code for the application, user callbacks can be registered with the `NULL` ucbDesc.

Example 14-6 shows that when the `OCIStmtPrepare2()` call is executed, the callbacks are called in the following order.

**Note:**

The exit callbacks are called in the reverse order of the entry and replacement callbacks.

The entry and exit callbacks can return any return code and the processing continues to the next callback. However, if the replacement callback returns anything other than `OCI_CONTINUE`, then the next callback (or OCI code if it is the last replacement callback) in the chain is bypassed and processing jumps to the exit callback. For example, if `pkg3_replace_callback_fn()` returned `OCI_SUCCESS`, then `pkg4_replace_callback_fn()`, `pkg5_replace_callback_fn()`, and the OCI processing for the `OCIStmtPrepare2()` call are bypassed. Instead, `pkg5_exit_callback_fn()` is executed next.

Example 14-2 Environment Variable Setting for the ORA_OCI_UCBPKG Variable

    setenv ORA_OCI_UCBPKG "pkg1;pkg2;pkg3;pkg4;pkg5"

Example 14-3 Specifying the pkgNInit() and PkgNEnvCallback() Functions

    pkgNInit(void *metaCtx, void *libCtx, ub4 argfmt, sword argc, void **argv)
    {
      return OCISharedLibInit(metaCtx, libCtx, argfmt, argc, argv, pkgNEnvCallback);
    }

Example 14-4 Using pkgNEnvCallback() to Register Entry, Replacement, and Exit Callbacks

    pkgNEnvCallback(OCIEnv *env, ub4 mode, size_t xtramemsz,
                                    void *usrmemp, OCIUcb *ucbDesc)
    {
      OCIHandleAlloc((void *)env, (void **)&errh, OCI_HTYPE_ERROR, (size_t) 0,
            (void **)NULL);

      OCIUserCallbackRegister(env, OCI_HTYPE_ENV, errh, pkgN_entry_callback_fn,
            pkgNctx, OCI_FNCODE_STMTPREPARE, OCI_UCBTYPE_ENTRY, ucbDesc);

      OCIUserCallbackRegister(env, OCI_HTYPE_ENV, errh, pkgN_replace_callback_fn,
            pkgNctx, OCI_FNCODE_STMTPREPARE, OCI_UCBTYPE_REPLACE, ucbDesc);

      OCIUserCallbackRegister(env, OCI_HTYPE_ENV, errh, pkgN_exit_callback_fn,
            pkgNctx, OCI_FNCODE_STMTPREPARE, OCI_UCBTYPE_EXIT, ucbDesc);

      return OCI_CONTINUE;
    }


Example 14-5 Registering User Callbacks with the NULL ucbDesc

      OCIUserCallbackRegister(env, OCI_HTYPE_ENV, errh, static_entry_callback_fn,
            pkgNctx, OCI_FNCODE_STMTPREPARE, OCI_UCBTYPE_ENTRY, (OCIUcb *)NULL);

      OCIUserCallbackRegister(env, OCI_HTYPE_ENV, errh, static_replace_callback_fn,
            pkgNctx, OCI_FNCODE_STMTPREPARE, OCI_UCBTYPE_REPLACE, (OCIUcb *)NULL);

      OCIUserCallbackRegister(env, OCI_HTYPE_ENV, errh, static_exit_callback_fn,
            pkgNctx, OCI_FNCODE_STMTPREPARE, OCI_UCBTYPE_EXIT, (OCIUcb *)NULL);


Example 14-6 Using the OCIStmtPrepare() Call to Call the Callbacks in Order

    static_entry_callback_fn()
    pkg1_entry_callback_fn()
    pkg2_entry_callback_fn()
    pkg3_entry_callback_fn()
    pkg4_entry_callback_fn()
    pkg5_entry_callback_fn()

    static_replace_callback_fn()
     pkg1_replace_callback_fn()
      pkg2_replace_callback_fn()
       pkg3_replace_callback_fn()
        pkg4_replace_callback_fn()
         pkg5_replace_callback_fn()

          OCI code for OCIStmtPrepare call

    pkg5_exit_callback_fn()
    pkg4_exit_callback_fn()
    pkg3_exit_callback_fn()
    pkg2_exit_callback_fn()
    pkg1_exit_callback_fn()

    static_exit_callback_fn()

**See Also:**

[OCIStmtPrepare2()](statement-functions.md)

### 14.2 OCI Callbacks from External Procedures

Provides additional reference information about using OCI callbacks from external procedures.

There are several OCI functions that you can use as callbacks from external procedures.

**See Also:**

- [OCI Cartridge Functions](oci-cartridge-functions.md) for a list of functions you can use as callbacks from external procedures

- [ Oracle Database Development Guide](../adfns/design_basics.md) for information about writing C subroutines that can be called from PL/SQL code, including a list of which OCI calls you can use and some example code
