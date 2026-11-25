## 121 DBMS_OPTIM_BUNDLE

The `DBMS_OPTIM_BUNDLE` package is used to manage the installed but disabled module bug fixes which cause an execution plan change.

This chapter contains the following topics:

- DBMS_OPTIM_BUNDLE Security Model
- Summary of DBMS_OPTIM_BUNDLE Subprograms

### 121.1 DBMS_OPTIM_BUNDLE Security Model

The `DBMS_OPTIM_BUNDLE` package runs with the privileges of the user starting the package. DBA role is required to run this package.

### 121.2 Summary of DBMS_OPTIM_BUNDLE Subprograms

This table lists the `DBMS_OPTIM_BUNDLE` subprograms and briefly describes them.

Table 121-1 DBMS_OPTIM_BUNDLE Package Subprograms

| Subprogram                       | Description                                                                                                     |
|:---------------------------------|:----------------------------------------------------------------------------------------------------------------|
| ENABLE_OPTIM_FIXES Procedure     | This procedure enables or disables fixes with plan changes up to the latest installed release update.           |
| GETBUGSFORBUNDLE Procedure       | This procedure displays execution plan bug fixes applied as part of release updates.                            |
| LISTBUNDLESWITHFCFIXES Procedure | This procedure lists the release update names and release update IDs of release updates with fix control fixes. |
| SET_FIX_CONTROLS Procedure       | This procedure enables or disables a list of fixes with `_fix_controls`.                                        |

#### 121.2.1 ENABLE_OPTIM_FIXES Procedure

The `DBMS_OPTIM_BUNDLE` subprogram, `ENABLE_OPTIM_FIXES` procedure enables or disables fixes with plan changes up to the latest installed release update.

##### Syntax

    DBMS_OPTIM_BUNDLE.ENABLE_OPTIM_FIXES (
       action                           IN  VARCHAR2  DEFAULT 'OFF',
       scope                            IN  VARCHAR2  DEFAULT 'MEMORY',
       current_setting_precedence       IN  VARCHAR2  DEFAULT 'YES');

##### Parameters

Table 121-2 ENABLE_OPTIM_FIXES Procedure Parameters

| Parameter                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `action`                     | Enables or disables all of the installed but disabled execution plan bug fixes up to and including the current release update.<br>The possible values are:<br>• `ON`-enables the bundle fixes.<br>• `OFF`-disables bundle fixes by setting the `_fix_controls` to the value `0`. It will not remove `_fix_control` entries from `SPFILE`.<br>The default value is `OFF`.                                                                                                                                                                                                                      |
| `scope`                      | The scope of enabling or disabling the installed but disabled execution plan bug fixes.<br>The possible values are:<br>• `MEMORY`<br>• `SPFILE`<br>• `BOTH`<br>• `INITORA`<br>`MEMORY`/`SPFILE`/`BOTH`: These three input values enables or disables the fixes in a given scope.<br>`INITORA`: This input value will just display manual command syntax that the user needs to manually enter into the database's `init.ora` file in order to enable or disable execution plan bug fixes. When using `SCOPE=INITORA` in this way, the `current_setting_precedence` field has no significance. |
| `current_setting_precedence` | Sets the precedence of environment settings or release update settings, where these settings are in conflict.<br>The possible values are:<br>• `YES`-the current environment settings take precedence in case of conflict<br>• `NO`-release update settings take precedence in case of conflict<br>The default value is `YES`.                                                                                                                                                                                                                                                                |

##### Examples

To enable all of the installed but disabled execution plan bug fixes up to and including those from the current release update:

    SQL> execute dbms_optim_bundle.enable_optim_fixes('ON','BOTH', 'YES');

This instruction would enable all fixes, in both `MEMORY` and in the persistant `SPFILE`, with a precedence of current setting.

##### Exceptions

The following exceptions are raised by the `ENABLE_OPTIM_FIXES Procedure`:

- `ORA-20001`: Bad input value
- `ORA-20002`: Internal or other errors

#### 121.2.2 GETBUGSFORBUNDLE Procedure

The `DBMS_OPTIM_BUNDLE` subprogram, `GETBUGSFORBUNDLE` procedure displays execution plan bug fixes applied as part of release updates.

##### Syntax

    DBMS_OPTIM_BUNDLE.GETBUGSFORBUNDLE (
       bundleid            IN  NUMBER  DEFAULT NULL);

##### Parameters

Table 121-3 GETBUGSFORBUNDLE Procedure Parameters

| Parameter  | Description                                                                                                                                                                                                                                    |
|:-----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `bundleid` | The release update ID.<br>If `NULL`, the execution plan bug fixes from the latest bundle is displayed. If a bundle ID is specified, then the execution plan bug fixes up to the specified bundle is displayed.<br>The default value is `NULL`. |

##### Examples

To view a listing of the installed but disabled execution plan bug fixes from the most recent release update applied:

    SQL> set serveroutput on;
    SQL> execute dbms_optim_bundle.getbugsforbundle;

    19.8.0.0.200714DBRU:
       Bug: 29304314, fix_controls: 29304314
       Bug: 29930457, fix_controls: 29930457

The above example lists the installed but disabled execution plan bug fixes from the `19.8.0.0.200714DBRU` release.

To view a listing of the installed but disabled execution plan bug fixes from release updates up to and including release update 171017:

    SQL> execute dbms_optim_bundle.getbugsforbundle(171017);

##### Exceptions

The following exceptions are raised by the `GETBUGSFORBUNDLE Procedure`:

- `ORA-20001`: Bad input value
- `ORA-20002`: Internal or other errors

#### 121.2.3 LISTBUNDLESWITHFCFIXES Procedure

The `DBMS_OPTIM_BUNDLE` subprogram, `LISTBUNDLESWITHFCFIXES` procedure lists the release update names and release update IDs of release updates with fix control fixes.

##### Syntax

    DBMS_OPTIM_BUNDLE.LISTBUNDLESWITHFCFIXES ( );

##### Examples

To view the release update names and release update IDs:

    SQL> set serveroutput on
    SQL> exec dbms_optim_bundle.listBundlesWithFCFixes;
       bundleId: 190719, bundleName: 19.4.0.0.190719DBRU
       bundleId: 191015, bundleName: 19.5.0.0.191015DBRU
       bundleId: 200414, bundleName: 19.7.0.0.200414DBRU
       bundleId: 200714, bundleName: 19.8.0.0.200714DBRU
       bundleId: 201020, bundleName: 19.9.0.0.201020DBRU
       bundleId: 210119, bundleName: 19.10.0.0.210119DBRU
       bundleId: 210420, bundleName: 19.11.0.0.210420DBRU
       bundleId: 210720, bundleName: 19.12.0.0.210720DBRU

       PL/SQL procedure successfully completed.

##### Exceptions

The following exception is raised by the `LISTBUNDLESWITHFCFIXES Procedure`:

`ORA-20002`: Internal or other errors

#### 121.2.4 SET_FIX_CONTROLS Procedure

The `DBMS_OPTIM_BUNDLE` subprogram, `SET_FIX_CONTROLS` procedure enables or disables a list of fixes with `_fix_controls`. The fixes can be present in a base version, in a release update, or in a one-off release. This procedure appends the new fix control settings to the existing ones.

##### Syntax

    DBMS_OPTIM_BUNDLE.SET_FIX_CONTROLS (
       fix_control_string               IN  VARCHAR2,
       sid                              IN  VARCHAR2  DEFAULT '*',
       scope                            IN  VARCHAR2  DEFAULT 'MEMORY',
       current_setting_precedence       IN  VARCHAR2  DEFAULT 'YES');

##### Parameters

Table 121-4 SET_FIX_CONTROLS Procedure Parameters

| Parameter                    | Description                                                                                                                                                                                                                                                       |
|:-----------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `fix_control_string`         | Comma separated list of `fix_control:value` pair. For example: `'13329748:0,20355502:4, 27060221:1'`                                                                                                                                                              |
| `sid`                        | The name of the instance on which `fix_control` setting need to be made.<br>Acceptable values are `*` or valid `instance_name` from `sys.gv$instance`. The default value is `*`.                                                                                  |
| `scope`                      | The scope of enabling or disabling the installed but disabled execution plan bug fixes.<br>The possible values are:<br>• `MEMORY`<br>• `SPFILE`<br>• `BOTH`<br>The default value is `MEMORY`.                                                                     |
| `current_setting_precedence` | Precedence of current setting over user supplied setting.<br>The possible values are:<br>• `YES`–the current environment settings take precedence in case of conflict<br>• `NO`–input settings take precedence in case of conflict<br>The default value is `YES`. |

##### Exceptions

The following exceptions are raised by the `SET_FIX_CONTROLS Procedure`:

- `ORA-20001`: Bad input value
- `ORA-20002`: Internal or other errors
