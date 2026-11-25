Lists and describes the miscellaneous OCI functions.

Table 26-8 lists the miscellaneous OCI functions that are described in this section.

Table 26-8 Miscellaneous Functions

| Function                  | Purpose                                                                    |
|:--------------------------|:---------------------------------------------------------------------------|
| OCIBreak()                | Perform an immediate asynchronous break                                    |
| OCIClientVersion()        | Return the client library version                                          |
| OCIErrorGet()             | Return error message and Oracle error                                      |
| OCILdaToSvcCtx()          | Toggle `Lda_Def` to service context handle                                 |
| OCIPasswordChange()       | Change password                                                            |
| OCIPing()                 | Confirm that the connection and the server are active                      |
| OCIReset()                | Call after `OCIBreak()` to reset asynchronous operation and protocol       |
| OCIRowidToChar()          | Convert a Universal `ROWID` to character extended (base 64) representation |
| OCIServerRelease()        | Get the Oracle release string                                              |
| OCIServerVersion()        | Get the Oracle version string                                              |
| OCISvcCtxToLda()          | Toggle service context handle to `Lda_Def`                                 |
| OCIUserCallbackGet()      | Identify the callback that is registered for handle                        |
| OCIUserCallbackRegister() | Register a user-created callback function                                  |

### 26.9.1 OCIBreak()

Performs an immediate asynchronous break.

#### Purpose

Performs an immediate (asynchronous) termination of any currently executing OCI function that is associated with a server.

#### Syntax

    sword OCIBreak ( void       *hndlp,
                     OCIError   *errhp );

#### Parameters

hndlp (IN/OUT)
The service context handle or the server context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

#### Comments

This call performs an immediate (asynchronous) termination of any currently executing OCI function that is associated with a server. It is normally used to stop a long-running OCI call being processed on the server. It can be called by a user thread in multithreaded applications, or by a user signal handler on Linux or UNIX systems. `OCIBreak()` is the only OCI call allowed in a user signal handler.

**Note:**

`OCIBreak()` works on Windows systems, including Windows 2000 and Windows XP.

This call can take either the service context handle or the server context handle as a parameter to identify the function to be terminated.

**Related Topics**

- OCIReset()
- OCIErrorGet()
- [Server Handle Attributes](handle-and-descriptor-attributes.md)
- [Nonblocking Mode in OCI](oci-programming-basics.md)
- [About Canceling Calls](oci-programming-basics.md)

### 26.9.2 OCIClientVersion()

Returns the client library version.

#### Purpose

Returns the 5 digit Oracle Database version number of the client library at run time.

#### Syntax

    void OCIClientVersion ( sword        *featureRelease,
                            sword        *releaseUpdate,
                            sword        *releaseUpdateRevision,
                            sword        *increment,
                            sword        *ext );

#### Parameters

featureRelease (OUT)
The feature release year.

releaseUpdate (OUT)
The release update number.

releaseUpdateRevision (OUT)
The release update revision number.

increment (OUT)
The release update increment number.

ext (OUT)
The extension number.

#### Comments

Beginning with release 18c, version 18.1, there are five new client macros for extracting each of the components of the database version. These macros are intended to be used in conjunction with the encoded database version number returned by `OCIServerRelease2()` to extract each of the 5 components of the database version. These macros are named according to the new release naming scheme started with version 18.1. The 5 digits extracted from the version number are: `<feature release>.<release update>.<release update revision>.<release update increment>.<extension>`. For example, 18.1.1.1.1 would represent feature release 18, release update 1, release update revision 1, release update increment 1, extension 1.`featureRelease()` returns the feture release year of OCI client that the application is running with. This is useful for the application to know at run time. An application or a test program can determine the version and the patch set of a particular OCI client installation by calling this function. This is also useful if the application wants to have different codepaths depending upon the level of the client patchset.

These macros are useful for writing a generic application that can be built and run with different versions of OCI client. For example:

    ....
    #if (featureRelease > 12)
    ...
    #endif
    ....

Even though the naming is based on the new convention, for convenience, the same macros can be used to extract the corresponding 5 components of the database version from an encoded version number returned by `OCIServerRelease()` from a pre version 18.1 database, which used a different encoding scheme. In that case though, the components correspond to the following:

- Version number

- Release number

- Update number

- Porting release number

- Porting update number

**Related Topics**

- OCIServerRelease()

### 26.9.3 OCIErrorGet()

Returns an error message and an Oracle Database error code.

#### Purpose

Returns an error message in the buffer provided and an Oracle Database error code.

#### Syntax

    sword OCIErrorGet ( void       *hndlp,
                        ub4         recordno,
                        OraText    *sqlstate,
                        sb4        *errcodep,
                        OraText    *bufp,
                        ub4         bufsiz,
                        ub4         type );

#### Parameters

hndlp (IN)
The error handle, usually, or the environment handle (for errors on `OCIEnvCreate()`, `OCIHandleAlloc()`).

recordno (IN)
Indicates the status record from which the application seeks information. Starts from 1.

sqlstate (OUT)
Not supported in release 8.x or later.

errcodep (OUT)
The error code returned.

bufp (OUT)
The error message text returned.

bufsiz (IN)
The size of the buffer provided for the error message, in number of bytes. If the error message length is more than `bufsiz`, a truncated error message text is returned in `bufp`.

If `type` is set to `OCI_HTYPE_ERROR`, then the return code during truncation for `OCIErrorGet()` is `OCI_ERROR`. The client can then specify a bigger buffer and call `OCIErrorGet()` again.

If `bufsiz` is sufficient to hold the entire message text and the message could be successfully copied into `bufp`, the return code for `OCIErrorGet()` is `OCI_SUCCESS.`

Use one of the following constants to define the error message buffers into which you get the returned message back from `OCIErrorGet()`:

    # define OCI_ERROR_MAXMSG_SIZE 1024 /* max size of an error message */
    # define OCI_ERROR_MAXMSG_SIZE2 3072 /* new length max size of an error message */

You should use `OCI_ERROR_MAXMSG_SIZE2` to ensure you get more information in the returned error text.

For example, you can do the following:

    char errorMesg[OCI_ERROR_MAXMSG_SIZE2];

Then pass this buffer into `OCIErrorGet()`. You also need to pass the same `OCI_ERROR_MAXMSG_SIZE2` value into the `OCIErrorGet()` call to indicate the size of the buffer that you have allocated.

type (IN)
The type of the handle (`OCI_HTYPE_ERROR` or `OCI_HTYPE_ENV`).

#### Comments

This function does not support SQL statements. Usually, `hndlp` is actually the error handle, or the environment handle. You should always get the message in the encoding that was set in the environment handle.

Note that if `OCIErrorGet()` is called following an OCI call that does not return an `OCI_ERROR` or `OCI_SUCCESS_WITH_INFO`, then an error message from some earlier OCI call that resulted in an error may be found by `OCIErrorGet()`. To avoid this issue, `OCIErrorGet()` should only be called following OCI calls that return either `OCI_ERROR` or `OCI_SUCCESS_WITH_INFO`.

The error handle is originally allocated with a call to `OCIHandleAlloc()`.

**Note:**

The `OCIErrorGet()` function returns at least one single diagnostic record. Multiple diagnostic records can be retrieved by calling the `OCIErrorGet()` method repeatedly, until there are no more records and the method returns `OCI_NO_DATA`.

**See Also:**

[Error Handling in OCI](oci-programming-basics.md)

#### Example

The following code example shows a simplified example of a function for error checking using `OCIErrorGet()`.

Using OCIErrorGet() for Error Checking

    static void checkerr(OCIError *errhp, sword status)
    {
      text errbuf[512];
      ub4 buflen;
      sb4 errcode;

      if (status == OCI_SUCCESS) return;

      switch (status)
      {
      case OCI_SUCCESS_WITH_INFO:
        printf("Error - OCI_SUCCESS_WITH_INFO\n");
        OCIErrorGet ((void  *) errhp, (ub4) 1, (text *) NULL, &errcode,
                errbuf, (ub4) sizeof(errbuf), (ub4) OCI_HTYPE_ERROR);
        printf("Error - %s\n", errbuf);
        break;
      case OCI_NEED_DATA:
        printf("Error - OCI_NEED_DATA\n");
        break;
      case OCI_NO_DATA:
        printf("Error - OCI_NO_DATA\n");
        break;
      case OCI_ERROR:
        OCIErrorGet ((void  *) errhp, (ub4) 1, (text *) NULL, &errcode,
                errbuf, (ub4) sizeof(errbuf), (ub4) OCI_HTYPE_ERROR);
        printf("Error - %s\n", errbuf);
        break;
      case OCI_INVALID_HANDLE:
        printf("Error - OCI_INVALID_HANDLE\n");
        break;
      case OCI_STILL_EXECUTING:
        printf("Error - OCI_STILL_EXECUTING\n");
        break;
      case OCI_CONTINUE:
        printf("Error - OCI_CONTINUE\n");
        break;
      default:
        printf("Error - %d\n", status);
        break;
      }
    }

**Related Topics**

- [OCIHandleAlloc()](handle-and-descriptor-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)

### 26.9.4 OCILdaToSvcCtx()

Converts a V7 `Lda_Def` to a V8 or later service context handle.

#### Purpose

Converts a V7 `Lda_Def` to a V8 or later service context handle.

#### Syntax

    sword OCILdaToSvcCtx ( OCISvcCtx  **svchpp,
                           OCIError    *errhp,
                           Lda_Def     *ldap );

#### Parameters

svchpp (IN/OUT)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

ldap (IN/OUT)
The Oracle7 logon data area returned by `OCISvcCtxToLda()` from this service context.

#### Comments

Converts an Oracle7 `Lda_Def` to a release 8 or later service context handle. The action of this call can be reversed by passing the resulting service context handle to the `OCISvcCtxToLda()` function.

You should use the `OCILdaToSvcCtx()` call only for resetting an `Lda_Def` obtained from `OCISvcCtxToLda()` back to a service context handle. It cannot be used to transform an `Lda_def` that started as an `Lda_def` back to a service context handle.

If the service context has been converted to an `Lda_Def`, only Oracle7 calls can be used. It is illegal to make OCI release 8 or later calls without first resetting the `Lda_Def` to a service context.

The `OCI_ATTR_IN_V8_MODE` attribute of the server handle or service context handle enables an application to determine whether the application is currently in Oracle release 7 mode or Oracle release 8 or later mode.

**Related Topics**

- OCISvcCtxToLda()
- OCIErrorGet()
- [Handler and Descriptor Attributes](handler-and-descriptor-attributes.md)

### 26.9.5 OCIPasswordChange()

Changes the password of an account.

#### Purpose

Allows the password of an account to be changed.

#### Syntax

    sword OCIPasswordChange ( OCISvcCtx     *svchp,
                              OCIError      *errhp,
                              const OraText *user_name,
                              ub4            usernm_len,
                              const OraText *opasswd,
                              ub4            opasswd_len,
                              const OraText *npasswd,
                              sb4            npasswd_len,
                              ub4            mode );

#### Parameters

svchp (IN/OUT)
A handle to a service context. The service context handle must be initialized and have a server context handle associated with it.

errhp (IN)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

user_name (IN)
Specifies the user name, which can be in UTF-16 encoding. It must be terminated with a `NULL` character if the service context has been initialized with an authentication handle.

usernm_len (IN)
The length of the user name string specified in `user_name`, in number of bytes regardless of the encoding. The `usernm_len` value must be nonzero.

opasswd (IN)
Specifies the user's old password, which can be in UTF-16 encoding.

opasswd_len (IN)
The length of the old password string specified in `opasswd`, in bytes. The `opasswd_len` value must be nonzero.

npasswd (IN)
Specifies the user's new password, which can be in UTF-16 encoding. If the password complexity verification routine is specified in the user's profile to verify the new password's complexity, the new password must meet the complexity requirements of the verification function.

npasswd_len (IN)
The length in bytes of the new password string specified in `npasswd`. For a valid password string, `npasswd_len` must be nonzero.

mode (IN)
`OCI_DEFAULT` - Use the setting in the environment handle.

- `OCI_UTF16` - Use UTF-16 encoding, regardless of the setting of the environment handle.

  There is only one encoding allowed, either UTF-16 or not, for `user_name`, `opasswd`, and `npasswd`.

- `OCI_AUTH` - If a user session context is not created, a call with this flag creates the user session context and changes the password. At the end of the call, the user session context is not cleared. Hence the user remains logged in.

  If the user session context is created, a call with this flag only changes the password and has no effect on the session. Hence the user still remains logged in.

  The `OCI_AUTH` mode can be used with any of the `OCI_CPW_*` modes listed in this section to establish the respective administrative session for the expired user account at logon before changing the password.

- `OCI_CPW_SYSDBA` — In this mode, you are authenticated for `SYSDBA` access.

- `OCI_CPW_SYSOPER` — In this mode, you are authenticated for `SYSOPER` access.

- `OCI_CPW_SYSASM` — In this mode, you are authenticated for `SYSASM` access.

- `OCI_CPW_SYSBKP` — In this mode, you are authenticated for `SYSBKP` access.

- `OCI_CPW_SYSDGD` — In this mode, you are authenticated for `SYSDGD` access.

- `OCI_CPW_SYSKMT` — In this mode, you are authenticated for `SYSKMT` access.

#### Comments

This call allows the password of an account to be changed. This call is similar to `OCISessionBegin()` with the following differences:

- If the user session is established, this call authenticates the account using the old password and then changes the password to the new password.

- If the user session is not established, this call establishes a user session and authenticates the account using the old password, and then changes the password to the new password.

This call is useful when the password of an account has expired and `OCISessionBegin()` returns an error (ORA-28001) or warning that indicates that the password has expired.

The `mode` or the environment handle determines if UTF-16 is being used.

For a Release 12.1 or later client password change with a Release 11.2 server, you must first call `OCISessionBegin()` before calling `OCIPasswordChange()`; otherwise the password change operation fails with an `ORA-1017` error.

**Related Topics**

- [OCISessionBegin()](connect-authorize-and-initialize-functions.md)
- OCIErrorGet()

### 26.9.6 OCIPing()

Confirms that the connection and the server are active.

#### Purpose

Makes a round-trip call to the server to confirm that the connection and the server are active.

#### Syntax

    sword OCIPing ( OCISvcCtx     *svchp,
                    OCIError      *errhp,
                    ub4            mode );

#### Parameters

svchp (IN)
A handle to a service context. The service context handle must be initialized and have a server context handle associated with it.

errhp (IN)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

mode (IN)
The mode for the call. Use `OCI_DEFAULT`.

#### Comments

`OCIPing()` makes a dummy round-trip call to the server; that is, a dummy packet is sent to the server for response. `OCIPing()` returns after the round-trip is completed. No server operation is performed for this call itself.

You can use `OCIPing()` to make a lightweight call to the server. A successful return of the call indicates that the connection and server are active. If the call blocks, the connection may be in use by other threads. If it fails, there may be some problem with the connection or the server, and the error can be retrieved from the error handle. Because `OCIPing()` is a round-trip call, you can also use it to flush all the pending OCI client-side calls to the server, if any exist. For example, calling `OCIPing()` after `OCIHandleFree()` can force the execution of the pending call to close back-end cursors. The call is useful when the application requires the back-end cursors to be closed immediately, which otherwise would be closed in the next round-trip on that connection. Also, with the enhanced functionality of `OCI_ATTR_SERVER_STATUS`, OCIPing may not be needed if the requirement is just to check the health of the connection. See the `OCI_ATTR_SERVER_STATUS` attribute in [Server Handle Attributes](handle-and-descriptor-attributes.md) for more information.

**Related Topics**

- [OCIHandleFree()](handle-and-descriptor-functions.md)
- OCIErrorGet()

### 26.9.7 OCIReset()

Resets the interrupted asynchronous operation and protocol.

#### Purpose

Must be called if an `OCIBreak()` call was issued while a nonblocking operation was in progress.

#### Syntax

    sword OCIReset ( void       *hndlp,
                     OCIError   *errhp );

#### Parameters

hndlp (IN)
The service context handle or the server context handle.

errhp (IN)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

#### Comments

This call is called in nonblocking mode only. It resets the interrupted asynchronous operation and protocol. OCIReset() must be called if an `OCIBreak()` call was issued while a nonblocking operation was in progress.

**Related Topics**

- OCIBreak()
- OCIErrorGet()

### 26.9.8 OCIRowidToChar()

Converts a Universal `ROWID` to character extended (base 64) representation.

#### Purpose

Converts a Universal `ROWID` to character extended (base 64) representation.

#### Syntax

    sword OCIRowidToChar ( OCIRowid      *rowidDesc,
                           OraText       *outbfp,
                           ub2           *outbflp
                           OCIError      *errhp );

#### Parameters

rowidDesc (IN)
The `ROWID` descriptor that is allocated by `OCIDescriptorAlloc()` and populated by a prior execution of a SQL statement.

outbfp (OUT)
Pointer to the buffer where the character representation is stored after successful execution of this call.

outbflp (IN/OUT)
Pointer to the output buffer length. Before execution, the buffer length contains the size of `outbfp`. After execution it contains the number of bytes converted.

If there is truncation during conversion, `outbfp` contains the length required to make conversion successful. An error is also returned.

errhp (IN)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

#### Comments

After this conversion, the `ROWID` in character format can be bound with the `OCIBindByPos()` or `OCIBindByName()` calls, and used to query a row at the given `ROWID`.

If the environment was created using `OCIEnvNlsCreate()` with parameters `charset` and `ncharset` set to `OCI_UTF16ID`, the function `OCIRowidToChar()` returns the rowid representation in ASCII, not in UTF-16 as expected.

**Related Topics**

- [OCIDescriptorAlloc()](handle-and-descriptor-functions.md)
- [OCIBindByPos()](bind-define-describe-functions.md)
- [OCIBindByPos2()](bind-define-describe-functions.md)
- [OCIBindByName()](bind-define-describe-functions.md)
- [OCIBindByName2()](bind-define-describe-functions.md)
- OCIErrorGet()

### 26.9.9 OCIServerRelease()

Returns the Oracle Database release string.

#### Purpose

Returns the Oracle Database release string.

#### Syntax

    sword OCIServerRelease ( void         *hndlp,
                             OCIError     *errhp,
                             OraText      *bufp,
                             ub4           bufsz
                             ub1           hndltype
                             ub4          *version );

#### Parameters

hndlp (IN)
The service context handle or the server context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

bufp (IN/OUT)
The buffer in which the release string is returned.

bufsz (IN)
The length of the buffer in number of bytes.

hndltype (IN)
The type of handle passed to the function.

version (IN/OUT)
The release string in integer format.

#### Comments

The buffer pointer `bufp` points to the release information in a string representation up to the `bufsz` including the `NULL` terminator. If the buffer size is too small, the result is truncated to the size `bufsz`. The `version` argument contains the 5-digit Oracle Database release string in integer format, which can be retrieved using the following macros:

    #define MAJOR_NUMVSN(v) ((sword)(((v) >> 24) & 0x000000FF))      /* version number */
    #define MINOR_NUMRLS(v) ((sword)(((v) >> 20) & 0x0000000F))      /* release number */
    #define UPDATE_NUMUPD(v) ((sword)(((v) >> 12) & 0x000000FF))     /* update number */
    #define PORT_REL_NUMPRL(v) ((sword)(((v) >> 8) & 0x0000000F))    /* port release number */
    #define PORT_UPDATE_NUMPUP(v) ((sword)(((v) >> 0) & 0x000000FF)) /* port update number */

**Related Topics**

- OCIServerVersion()
- OCIErrorGet()

### 26.9.10 OCIServerRelease2()

Returns the Oracle Database release string.

#### Purpose

Returns the Oracle Database release string.

#### Syntax

    sword OCIServerRelease2( void         *hndlp,
                             OCIError     *errhp,
                             OraText      *bufp,
                             ub4           bufsz,
                             ub1           hndltype,
                             ub4          *versionp,
                             ub4           mode );

#### Parameters

hndlp (IN)
The service context handle or the server context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

bufp (IN/OUT)
The buffer in which the release string is returned.

bufsz (IN)
The length of the buffer in number of bytes.

hndltype (IN)
The type of handle passed to the function.

versionp (IN/OUT)
The release string in integer format.

mode (IN)
The only valid value is `OCI_DEFAULT`.

#### Comments

The buffer pointer `bufp` points to the release information in a string representation up to the `bufsz` including the `NULL` terminator. If the buffer size is too small, the result is truncated to the size `bufsz`. The `version` argument contains the 5-digit Oracle Database release string in integer format, which can be retrieved using the following macros:

    OCI_SERVER_RELEASE_REL(v)
                 /* old: version number */
                 /* new: feature release */
    OCI_SERVER_RELEASE_REL_UPD(v)
                /* old: release number */
                /* new: release update */
    OCI_SERVER_RELEASE_REL_UPD_REV(v)
               /* old: update number */
               /* new: release update revision */
    OCI_SERVER_RELEASE_REL_UPD_INC(v)
              /* old: porting release number */
              /* new: release update increment */
    OCI_SERVER_RELEASE_EXT(v)
             /* old: porting update number */
             /* new: extension */

Old means applicable when connected to a pre-version 18.1 database. New means applicable when connected to version 18.1 or later database.

### 26.9.11 OCIServerVersion()

Returns the Oracle Database version string.

#### Purpose

Returns the Oracle Database version string.

#### Syntax

    sword OCIServerVersion ( void         *hndlp,
                             OCIError     *errhp,
                             OraText      *bufp,
                             ub4           bufsz
                             ub1           hndltype );

#### Parameters

hndlp (IN)
The service context handle or the server context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

bufp (IN/OUT)
The buffer in which the version information is returned.

bufsz (IN)
The length of the buffer in number of bytes.

hndltype (IN)
The type of handle passed to the function.

#### Comments

This call returns the version string of Oracle Database. It can be in Unicode if the environment handle so determines.

For example, the following is returned in `bufp` as the version string if an application is running on an 8.1.5 SunOS server:

    Oracle8i Enterprise Edition Release 8.1.5.0.0 - Production
    With the Partitioning and Java options
    PL/SQL Release 8.1.5.0.0 - Production

**Related Topics**

- OCIClientVersion()
- OCIErrorGet()

### 26.9.12 OCISvcCtxToLda()

Toggles between a V8 or later service context handle and a V7 `Lda_Def`.

#### Purpose

Toggles between a V8 or later service context handle and a V7 `Lda_Def`.

#### Syntax

    sword OCISvcCtxToLda ( OCISvcCtx    *srvhp,
                           OCIError     *errhp,
                           Lda_Def      *ldap );

#### Parameters

svchp (IN/OUT)
The service context handle.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

ldap (IN/OUT)
A Logon Data Area for Oracle7-style OCI calls that is initialized by this call.

#### Comments

Toggles between an OCI release 8 or later service context handle and an Oracle7 `Lda_Def`.

This function can only be called after a service context has been properly initialized.

Once the service context has been translated to an `Lda_Def`, it can be used in release 7.x OCI calls (for example, `obindps()`, `ofen()`).

If there are multiple service contexts that share the same server handle, only one can be in Oracle7 mode at any time.

The action of this call can be reversed by passing the resulting `Lda_Def` to the `OCILdaToSvcCtx()` function.

The `OCI_ATTR_IN_V8_MODE` attribute of the server handle or service context handle enables an application to determine whether the application is currently in Oracle release 7 mode or Oracle release 8 or later mode.

**Related Topics**

- OCILdaToSvcCtx()
- OCIErrorGet()
- [Handler and Descriptor Attributes](handler-and-descriptor-attributes.md)

### 26.9.13 OCIUserCallbackGet()

Determines the callback that is registered for a handle.

#### Purpose

Determines the callback that is registered for a handle.

#### Syntax

    sword OCIUserCallbackGet ( void    *hndlp,
                               ub4      type,
                               void    *ehndlp,
                               ub4      fcode,
                               ub4      when,
                               OCIUserCallback (*callbackp)
                                               (
                                                 void   *ctxp,
                                                 void   *hndlp,
                                                 ub4     type,
                                                 ub4     fcode,
                                                 ub1     when,
                                                 sword   returnCode,
                                                 ub4    *errnop,
                                                 va_list arglist
                                                ),
                               void    **ctxpp,
                               OCIUcb   *ucbDesc );

#### Parameters

hndlp (IN)
This is the handle whose type is specified by the type parameter.

type (IN)
The handle type. The valid handle type is `OCI_HTYPE_ENV`. The callback is registered for all calls of the function specified by `fcode` made on the environment handle.

ehndlp (IN)
The OCI error or environment handle. If there is an error, it is recorded in `ehndlp`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

fcode (IN)
A unique function code of an OCI function. These are listed in Table 26-9.

when (IN)
Defines when the callback is invoked. Valid modes are:

- `OCI_UCBTYPE_ENTRY` - The callback is invoked on entry into the OCI function.

- `OCI_UCBTYPE_EXIT` - The callback is invoked before exit from the OCI function.

- `OCI_UCBTYPE_REPLACE` - If it returns anything other than an `OCI_CONTINUE`, then the next replacement callback and the OCI code for the OCI function are not called. Instead, processing jumps to the exit callbacks. For information about this parameter, see `OCIUserCallbackRegister()`.

callbackp (OUT)
A pointer to a callback function pointer. This returns the function that is currently registered for these values of `fcode`, `when`, and `hndlp`. The value returned would be `NULL` if no callback is registered for this case.

**See Also:**

`OCIUserCallbackRegister()` for information about the parameters of `callbackp`

ctxpp (OUT)
A pointer to return context for the currently registered callback.

ucbDesc (IN)
A descriptor provided by OCI. This descriptor is passed by OCI in the environment callback. It contains the priority at which the callback would be registered. If the `ucbDesc` parameter is specified as `NULL`, then this callback has the highest priority.

User callbacks registered statically (as opposed to those registered dynamically in a package) use a `NULL` descriptor because they do not have a `ucb` descriptor to use.

#### Comments

This function discovers or detects what callback is registered for a particular handle.

**Related Topics**

- OCIUserCallbackRegister()
- OCIErrorGet()
- [Restrictions on Callback Functions](user-defined-callback-functions.md)

### 26.9.14 OCIUserCallbackRegister()

Registers a user-created callback function.

#### Purpose

Registers a user-created callback function.

#### Syntax

    sword OCIUserCallbackRegister ( void    *hndlp,
                                    ub4      type,
                                    void    *ehndlp,
                                    OCIUserCallback  (callback)
                                                     (
                                                        void    *ctxp,
                                                        void    *hndlp,
                                                        ub4      type,
                                                        ub4      fcode,
                                                        ub1      when,
                                                        sword    returnCode,
                                                        ub4     *errnop,
                                                        va_list  arglist
                                                      ),
                                   void     *ctxp,
                                   ub4       fcode,
                                   ub4       when,
                                   OCIUcb   *ucbDesc );

#### Parameters

hndlp (IN)
This is the handle whose type is specified by the type parameter.

type (IN)
The handle type. The valid handle type is `OCI_HTYPE_ENV`. The callback is registered for all calls of the function specified by `fcode` made on the environment handle.

<!-- -->

ehndlp (IN)
The OCI error or environment handle. If there is an error, it is recorded in `ehndlp` and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`. Because an error handle is not available within `OCIEnvCallback`, the environment handle is passed in as a `ehndlp`.

callback (IN)
A callback function pointer. The variable argument list in the `OCIUserCallback` function prototype are the parameters passed to the OCI function. The typedef for `OCIUserCallback` is described later.

If an entry callback returns anything other than `OCI_CONTINUE`, then the return code is passed to the subsequent entry or replacement callback, if there is one. If this is the last entry callback and there is no replacement callback, then the OCI code is executed and the return code is ignored.

If a replacement callback returns anything other than `OCI_CONTINUE`, then subsequent replacement callbacks and the OCI code are bypassed, and processing jumps to the exit callbacks.

If the exit callback returns anything other than `OCI_CONTINUE`, then that returned value is returned by the OCI function; otherwise, the return value from the OCI code or the replacement callback (if the replacement callback did not return `OCI_CONTINUE` and essentially bypassed the OCI code) is returned by the call.

If a `NULL` value is passed in for callback, then the callback is removed for the `when` value and the specified handle. This is the way to deregister a callback for a given `ucbDesc` value, including the `NULL` `ucbDesc.`

ctxp (IN)
A context pointer for the callback.

fcode (IN)
A unique function code of an OCI function. These are listed in Table 26-9.

when (IN)
Defines when the callback is invoked. Valid modes are:

- `OCI_UCBTYPE_ENTRY` - The callback is invoked on entry into the OCI function.

- `OCI_UCBTYPE_EXIT` - The callback is invoked before exit from the OCI function.

- `OCI_UCBTYPE_REPLACE` - If the callback returns anything other than `OCI_CONTINUE`, then the next replacement callback and the OCI code for the OCI function is not called. Instead, processing jumps to the exit callbacks.

ucbDesc (IN)
A descriptor provided by OCI. This descriptor is passed by OCI in the environment callback. It contains the priority at which the callback would be registered. If the `ucbDesc` parameter is specified as `NULL`, then this callback has the highest priority.

User callbacks registered statically (as opposed to those registered dynamically in a package) use a `NULL` descriptor as they do not have a ucb descriptor to use.

#### Comments

This function is used to register a user-created callback with the OCI environment.

Such callbacks allow an application to:

- Trace OCI calls for debugging and performance measurements

- Perform additional pre-processing or post-processing after selected OCI calls

- Substitute the body of a given function with proprietary code to execute on a foreign data source

The OCI supports: entry callbacks, replacement callbacks, and exit callbacks.

The three types of callbacks are identified by the modes `OCI_UCBTYPE_ENTRY`, `OCI_UCBTYPE_REPLACE`, and `OCI_UCBTYPE_EXIT`.

The control flow now is:

1.  Execute entry callbacks.

2.  Execute replacement callbacks.

3.  Execute OCI code.

4.  Execute exit callbacks.

Entry callbacks are executed when a program enters an OCI function.

Replacement callbacks are executed after entry callbacks. If the replacement callback returns a value of `OCI_CONTINUE`, then subsequent replacement callbacks or the normal OCI-specific code is executed. If the callback returns anything other than `OCI_CONTINUE`, then subsequent replacement callbacks and the OCI code do not execute.

After an OCI function successfully executes, or after a replacement callback returns something other than `OCI_CONTINUE`, program control transfers to the exit callback (if one is registered).

If a replacement or exit callback returns anything other than `OCI_CONTINUE`, then the return code from the callback is returned from the associated OCI call.

To determine the callback that is registered for the handle, you can use `OCIUserCallbackGet()`.

The prototype of the `OCIUserCallback` typedef is:

    typedef sword (*OCIUserCallback)
               (void    *ctxp,
                void    *hndlp,
                ub4     type,
                ub4     fcode,
                ub4     when,
                sword   returnCode,
                sb4     *errnop,
                va_list arglist );

The parameters to the OCIUserCallback function prototype are:

ctxp (IN)
The context passed in as `ctxp` in the register callback function.

hndlp (IN)
This is the handle whose type is specified in the `type` parameter. It is the handle on which the callback is invoked. Because only a type of `OCI_HTYPE_ENV` is allowed, the environment handle, `env`, would be passed in here.

type (IN)
The type registered for the `hndlp`. The valid handle type is `OCI_HTYPE_ENV`. The callback is registered for all calls of the function specified by `fcode` made on the environment handle.

<!-- -->

fcode (IN)
The function code of the OCI call. These are listed in Table 26-9. Note that callbacks can be registered for only the OCI calls listed in [Table 26-3](streams-advanced-queueing-and-publish-subscribe-functions.md).

when (IN)
The `when` value of the callback.

returnCode (IN)
This is the return code from the previous callback or the OCI code. For the first entry callback, `OCI_SUCCESS` is always passed in. For the subsequent callbacks, the return code from the OCI code or the previous callback is passed in.

errnop (IN/OUT)
When the first entry callback is called, the input value of `*errnop` is 0. If the callback is returning any value other than `OCI_CONTINUE`, then it must also set an error number in `*errnop`. This value is the set in the error handle passed in the OCI call.

For all subsequent callbacks, the input value of `*errnop` is the value of error number in the error handle. Therefore, if the previous callback did not return `OCI_CONTINUE`, then the out value of `*errnop` from the previous callback would be the one in the error handle, and that value would be passed in here to the subsequent callback. If, however, the previous callback returned `OCI_CONTINUE`, then whatever value is in the error handle would be passed in here.

Note that if a non-Oracle error number is returned in `*errnop`, then a callback must also be registered for the `OCIErrorGet()` function to return appropriate text for the error number.

arglist (IN)
These are the parameters to the OCI call passed in here as variable number of arguments. They should be dereferenced using `va_arg`, as illustrated in the user callback demonstration programs.

**See Also:**

[OCI Demonstration Programs](oci-demo-programs.md)

Table 26-9 and Table 26-10 list the OCI Function codes and provides the OCI routine name and its function number.

Table 26-9 OCI Function Codes  

| \#  | OCI Routine            | \#  | OCI Routine         | \#  | OCI Routine            |
|:----|:-----------------------|:----|:--------------------|:----|:-----------------------|
| 1   | OCIInitialize          | 33  | OCITransStart       | 65  | OCIDefineByPos         |
| 2   | OCIHandleAlloc         | 34  | OCITransDetach      | 66  | OCIBindByPos           |
| 3   | OCIHandleFree          | 35  | OCITransCommit      | 67  | OCIBindByName          |
| 4   | OCIDescriptorAlloc     | 36  | (not used)          | 68  | OCILobAssign           |
| 5   | OCIDescriptorFree      | 37  | OCIErrorGet         | 69  | OCILobIsEqual          |
| 6   | OCIEnvInit             | 38  | OCILobFileOpen      | 70  | OCILobLocatorIsInit    |
| 7   | OCIServerAttach        | 39  | OCILobFileClose     | 71  | OCILobEnableBuffering  |
| 8   | OCIServerDetach        | 40  | (not used)          | 72  | OCILobCharSetId        |
| 9   | (not used)             | 41  | (not used)          | 73  | OCILobCharSetForm      |
| 10  | OCISessionBegin        | 42  | OCILobCopy          | 74  | OCILobFileSetName      |
| 11  | OCISessionEnd          | 43  | OCILobAppend        | 75  | OCILobFileGetName      |
| 12  | OCIPasswordChange      | 44  | OCILobErase         | 76  | OCILogon               |
| 13  | OCIStmtPrepare         | 45  | OCILobGetLength     | 77  | OCILogoff              |
| 14  | (not used)             | 46  | OCILobTrim          | 78  | OCILobDisableBuffering |
| 15  | (not used)             | 47  | OCILobRead          | 79  | OCILobFlushBuffer      |
| 16  | (not used)             | 48  | OCILobWrite         | 80  | OCILobLoadFromFile     |
| 17  | OCIBindDynamic         | 49  | (not used)          | 81  | OCILobOpen             |
| 18  | OCIBindObject          | 50  | OCIBreak            | 82  | OCILobClose            |
| 19  | (not used)             | 51  | OCIServerVersion    | 83  | OCILobIsOpen           |
| 20  | OCIBindArrayOfStruct   | 52  | (not used)          | 84  | OCILobFileIsOpen       |
| 21  | OCIStmtExecute         | 53  | (not used)          | 85  | OCILobFileExists       |
| 22  | (not used)             | 54  | OCIAttrGet          | 86  | OCILobFileCloseAll     |
| 23  | (not used)             | 55  | OCIAttrSet          | 87  | OCILobCreateTemporary  |
| 24  | (not used)             | 56  | OCIParamSet         | 88  | OCILobFreeTemporary    |
| 25  | OCIDefineObject        | 57  | OCIParamGet         | 89  | OCILobIsTemporary      |
| 26  | OCIDefineDynamic       | 58  | OCIStmtGetPieceInfo | 90  | OCIAQEnq               |
| 27  | OCIDefineArrayOfStruct | 59  | OCILdaToSvcCtx      | 91  | OCIAQDeq               |
| 28  | OCIStmtFetch           | 60  | (not used)          | 92  | OCIReset               |
| 29  | OCIStmtGetBindInfo     | 61  | OCIStmtSetPieceInfo | 93  | OCISvcCtxToLda         |
| 30  | (not used)             | 62  | OCITransForget      | 94  | OCILobLocatorAssign    |
| 31  | (not used)             | 63  | OCITransPrepare     | 95  | (not used)             |
| 32  | OCIDescribeAny         | 64  | OCITransRollback    | 96  | OCIAQListen            |

Table 26-10 Continuation of OCI Function Codes from 97 and Higher

| \#  | OCI Routine              | \#  | OCI Routine             | \#  | OCI Routine                 |
|:----|:-------------------------|:----|:------------------------|:----|:----------------------------|
| 97  | Reserved                 | 113 | OCILobErase2            | 129 | OCILobGetOptions            |
| 98  | Reserved                 | 114 | OCILobGetLength2        | 130 | OCILobSetOptions            |
| 99  | OCITransMultiPrepare     | 115 | OCILobLoadFromFile2     | 131 | OCILobFragementInsert       |
| 100 | OCIConnectionPoolCreate  | 116 | OCILobRead2             | 132 | OCILobFragementDelete       |
| 101 | OCIConnectionPoolDestroy | 117 | OCILobTrim2             | 133 | OCILobFragementMove         |
| 102 | OCILogon2                | 118 | OCILobWrite2            | 134 | OCILobFragementReplace      |
| 103 | OCIRowidToChar           | 119 | OCILobGetStorageLimit   | 135 | OCILobGetDeduplicateRegions |
| 104 | OCISessionPoolCreate     | 120 | OCIDBStartup            | 136 | OCIAppCtxSet                |
| 105 | OCISessionPoolDestroy    | 121 | OCIDBShutdown           | 137 | OCIAppCtxClearAll           |
| 106 | OCISessionGet            | 122 | OCILobArrayRead         | 138 | OCILobGetContentType        |
| 107 | OCISessionRelease        | 123 | OCILobArrayWrite        | 139 | OCILobSetContentType        |
| 108 | OCIStmtPrepare2          | 124 | OCIAQEnqStreaming       |     |                             |
| 109 | OCIStmtRelease           | 125 | OCIAQGetReplayInfo      |     |                             |
| 110 | OCIAQEnqArray            | 126 | OCIAQResetReplayInfo    |     |                             |
| 111 | OCIAQDeqArray            | 127 | OCIArrayDescriptorAlloc |     |                             |
| 112 | OCILobCopy2              | 128 | OCIArrayDescriptorFree  |     |                             |

**Related Topics**

- OCIUserCallbackGet()
- OCIErrorGet()
