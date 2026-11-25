## A AutoUpgrade REST APIs

The AutoUpgrade REST APIs for Oracle Database enable you to automate database upgrades using RESTful Services in a web environment.

- Introduction to AutoUpgrade REST APIs
  Learn about the AutoUpgrade Utility REST API method of upgrading Oracle Database.
- Get Started
  Set up your system so that you upgrade your databases using the AutoUpgrade REST APIs.
- REST APIs for AutoUpgrade
  These REST APIs are available for the AutoUpgrade REST services feature in Oracle REST Data Services (ORDS).

### Introduction to AutoUpgrade REST APIs

Learn about the AutoUpgrade Utility REST API method of upgrading Oracle Database.

- About AutoUpgrade REST APIs
  The AutoUpgrade REST API implementation uses the Oracle REST Data Services plug-in framework.

**Parent topic:** AutoUpgrade REST APIs

#### About AutoUpgrade REST APIs

The AutoUpgrade REST API implementation uses the Oracle REST Data Services plug-in framework.

The AutoUpgrade REST APIs provide a uniform interface for AutoUpgrade on client-server architecture, and enable you to leverage and integrate AutoUpgrade features through HTTP and HTTPS protocols to upgrade Oracle Databases automatically. The Oracle REST Data Services implementation is based on a Java Enterprise Edition (Java EE) data service that provides enhanced security, file-caching features, and RESTful Web Services. This service provides increased flexibility for standalone deployments, as well as through servers, such as Oracle WebLogic Server and Apache Tomcat. Oracle REST Data Services is a common plugin mechanism used by most Oracle Database components and tools.

**Related Topics**

- [REST APIs for Oracle Database](https://docs.oracle.com/pls/topic/lookup?ctx=dblatest&id=DBRST)

**Parent topic:** Introduction to AutoUpgrade REST APIs

### Get Started

Set up your system so that you upgrade your databases using the AutoUpgrade REST APIs.

- Install cURL
  The examples within this document use the cURL command-line tool to demonstrate how to access the Autoupgrade REST API.
- How to Set Up and Use AutoUpgrade REST APIs
  To use the AutoUpgrade REST APIs, you must install Oracle REST Data Services, and enable AutoUpgrade REST service.
- How to Use AutoUpgrade REST API Authentication Privileges
  To configure users with AutoUpgrade Administrator user privileges to access AutoUpgrade REST APIs, complete this setup procedure.

**Parent topic:** AutoUpgrade REST APIs

#### Install cURL

The examples within this document use the cURL command-line tool to demonstrate how to access the Autoupgrade REST API.

To connect securely to the server, you must install a version of cURL that supports SSL and provide an SSL certificate authority (CA) certificate file or bundle to authenticate against the Verisign CA certificate.

1.  In your browser, navigate to the cURL home page, and click Download in the left navigation menu.
2.  On the cURL Releases and Downloads page, locate the SSL-enabled version of the cURL software that corresponds to your operating system, click the link to download the tar or ZIP file, and install the software.
3.  Navigate to the cURL CA certificates extracted from Mozilla page, and download the The Mozilla CA certificate store in PEM format (`cacert.pem`) in the folder where you installed cURL.
4.  Open a command window, navigate to the directory where you installed cURL, and set the cURL environment variable, `CURL_CA_BUNDLE`, to the location of an SSL certificate authority (CA) certificate bundle. For example:
        C:\curl> set CURL_CA_BUNDLE=cacert.pem

You are now ready to send REST requests to the AutoUpgrade REST API instance using cURL.

**Related Topics**

- [cURL command line tool and library](https://curl.se/)
- [CA certificates extracted from Mozilla](https://curl.se/docs/caextract.html)

**Parent topic:** Get Started

#### How to Set Up and Use AutoUpgrade REST APIs

To use the AutoUpgrade REST APIs, you must install Oracle REST Data Services, and enable AutoUpgrade REST service.

Before you enable or install the AutoUpgrade REST API, ensure that you have completed installation of the Oracle REST Data Services in standalone mode:

[Configuring and Installing Oracle REST Data Services](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/upgrd&id=AELIG-GUID-34C2C8C8-4AF1-402A-A956-E0A42FCED85E)

1.  After installing `ords.war` and before starting ORDS service, you must set the `autoupgrade.api.enabled` property to `true` (the default is `false`), and set the environment variables for the APIs.

        ords --config /path/to/config config set autoupgrade.api.enabled true
        ords --config /path/to/config config set autoupgrade.api.loglocation /databases/working
        ords --config /path/to/config config set autoupgrade.api.aulocation /autoupgrade/ords/ords/autoupgrade.jar
        ords --config /path/to/config config set autoupgrade.api.jvmlocation /usr/bin/java

2.  Revise your AutoUpgrade configuration file to use a JSON format.

    To submit a new task through AutoUpgrade REST APIs, you must convert the standard AutoUpgrade configuration file format to JSON format.

    For example, here is a standard configuration file (`config.cfg`) for AutoUpgrade:

        [oracle@localhost curl]$ more config.cfg
        #Global configurations
        #Autoupgrade's global directory, non-job logs generated,
        #temp files created and other autoupgrade files will be
        #send here
        global.autoupg_log_dir=/autoupgrade/test/glog
        #
        # Database number 1
        #
        upg1.start_time=NOW
        upg1.source_home=/databases/product/12.2.0/dbhome_1
        upg1.target_home=/databases/product/19c/dbhome_1
        upg1.sid=db122
        upg1.log_dir=/autoupgrade/test/log
        upg1.upgrade_node=localhost
        upg1.target_version=19.1

    Here is the same configuration file, specifying the same parameter information, but rewritten as a JSON configuration input file (`config.json`) for use with the AutoUpgrade REST API method:

        [oracle@localhost curl]$ more config.json
        {
        "global": {
                "autoupg_log_dir": "/autoupgrade/test/glog"
            },
            "jobs": [{
                "start_time": "NOW",
                "source_home": "/databases/product/12.2.0/dbhome_1",
                "target_home": "/databases/product/19c/dbhome_1",
                "sid": "db122",
                "log_dir": "/autoupgrade/test/log",
                "upgrade_node": "localhost",
                "target_version": "19.1"
            }]
        }

**Parent topic:** Get Started

#### How to Use AutoUpgrade REST API Authentication Privileges

To configure users with AutoUpgrade Administrator user privileges to access AutoUpgrade REST APIs, complete this setup procedure.

AutoUpgrade REST API has it's own authentication role for Oracle REST Data Services (ORDS), called `AutoUpgrade Administrator`. If the ORDS configuration parameter `autoupgrade.api.ordsauth` is set to `true`, then an ORDS user requires the `AutoUpgrade Administrator` role to use AutoUpgrade REST APIs.

To disable this feature, enter the following command:

    ords --config /path/to/config config set autoupgrade.api.ordsauth false

When `autoupgrade.api.ordsauth` is set to `true`, you must explicitly grant the `AutoUpgrade Administrator` role to users before they can access the AutoUpgrade REST APIs.

Before you enable or disable the AutoUpgrade REST API Administrator role, ensure that you have completed installation of the Oracle REST Data Services in standalone mode:

[Configuring and Installing Oracle REST Data Services](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/upgrd&id=AELIG-GUID-34C2C8C8-4AF1-402A-A956-E0A42FCED85E)

1.  After installing `ords.war` and before starting ORDS service, ensure that `autoupgrade.api.ordsauth` is set to true:

        ords --config /path/to/config config set autoupgrade.api.ordsauth true

2.  Create a user with the AutoUpgrade Administrator role. For example, the following command creates the user `roderigo` with the `AutoUpgrade Administrator` role:

        ords --config /path/to/config config user add roderigo "AutoUpgrade Administrator"

        Enter a password for user roderigo:

        Confirm password for user roderigo:

3.  Start the `ords.war` server.

4.  Ensure that the user that you have created can access the AutoUpgrade endpoints successfully.

    The following is an example of successful authentication with user `roderigo`:

        [oracle@localhost curl]$ curl -u roderigo
        "http://localhost:8080/autoupgrade/tasks"

        Enter host password for user 'roderigo':

        {

            "total_tasks": 0,

            "tasks": [

            ]

        }

    The following is an example of unsuccessful authentication:

        [oracle@localhost curl]$ curl "http://localhost:8080/autoupgrade/tasks"

        {

            "code": "Unauthorized",

            "message": "Unauthorized",

            "type": "tag:oracle.com,2020:error/Unauthorized",

            "instance": "tag:oracle.com,2020:ecid/LI6fVLjXrI2rvmEFoBzAAw"

        }

5.  Create additional authenticated users as needed for the AutoUpgrade REST APIs.

6.  Use the following command to disable the AutoUpgrade REST API authorization:

        ords --config /path/to/config config set autoupgrade.api.ordsauth false

7.  Restart the ORDS server.

8.  You should now be able to access AutoUpgrade REST API endpoints directly without requiring password authentication:

        [oracle@localhost curl]$ curl "http://localhost:8080/autoupgrade/tasks"

        {

            "total_tasks": 0,

            "tasks": [

            ]

        }

**Parent topic:** Get Started

### REST APIs for AutoUpgrade

These REST APIs are available for the AutoUpgrade REST services feature in Oracle REST Data Services (ORDS).

- Create a New AutoUpgrade Task
  Submit an AutoUpgrade task through the REST API, either with or without a JSON configuration file.
- Progress Report Request for an AutoUpgrade Task
  Use the `progress` API to get a progress report of an AutoUpgrade task specified by the `taskid`.
- Console Request for an AutoUpgrade Task
  Use the `console` API to get a console for the AutoUpgrade task specified by the `taskid`.
- Task Details Request for AutoUpgrade
  Use the `task` API to get AutoUpgrade task details for the task specified by the `taskid`.
- Task List Request for AutoUpgrade Tasks
  Use the `tasks` API to get an AutoUpgrade task list.
- Log or Log List for an AutoUpgrade Task
  Use the `log` API to open a log, or to get a log list of a task specified by `taskid`.
- Status Report of Task Request for AutoUpgrade
  Use the `status` API to get a status report of an AutoUpgrade task specified by the `taskid`.

**Parent topic:** AutoUpgrade REST APIs

#### Create a New AutoUpgrade Task

Submit an AutoUpgrade task through the REST API, either with or without a JSON configuration file.

##### Method

POST

##### Path

    /autoupgrade/task

##### Usage Notes

There are two uses:

1.  Submit an AutoUpgrade task. To submit the task, the databases specified in the AutoUpgrade configuration file must be on the same host as the Oracle REST Data Services server instance, and the target database release must be a release that is supported for direct upgrade from the source database release. The AutoUpgrade configuration file must be uploaded through the HTTP or HTTPS request body in JSON format.

2.  Resubmit an existing task through the AutoUpgrade REST APIs. When you resubmit a task by providing an existing `taskid` parameter, the configuration file previously associated with that task is used, so you do not need to provide a configuration file. However, you can specify different values for the parameters `mode` and `restore_on_fail`. For example: you can submit a task where the `mode` parameter is set to `analyze`. After the analyze tasks complete without any check failures, you can resubmit the task with the same `taskid`, but proceed to upgrade the database by changing the `mode` parameter to `deploy`.

##### Request

Path parameters:

| Parameter         | Description                                                                                              |
|:------------------|:---------------------------------------------------------------------------------------------------------|
| `mode`            | (Required) AutoUpgrade processing mode. Options: `analyze`, `fixups`, `deploy`, `upgrade`, `postfixups`. |
| `restore_on_fail` | (Optional) Generates a restore point during the upgrade. Options: `yes`, `no`                            |
| `taskid`          | (Optional) Reruns the existing AutoUpgrade task that you specify with a `taskid`.                        |

##### Response

- 201 Response: Description of the new AutoUpgrade task.
- 400 Response: Returned if parameters are missing.

##### Examples

Example A-1 Submit an AutoUpgrade Task Request

The following example shows how to submit an AutoUpgrade configuration file to create a new AutoUpgrade task in analyze mode by submitting a POST request on the REST resource using cURL

    curl --data-binary "@config.json" -X POST --header "Content-Type:application/json"
    'http://localhost:8080/autoupgrade/task?mode=analyze'

In the JSON configuration file (`config.json`) for this analyze request, there is one source database instance, `db122`, which you specify to upgrade from Oracle Database 12c (12.2) to Oracle Database 19c:

    {
    "global": {
            "autoupg_log_dir": "/autoupgrade/test/glog"
        },
        "jobs": [{
            "start_time": "NOW",
            "source_home": "/databases/product/12.2.0/dbhome_1",
            "target_home": "/databases/product/19.0.0/dbhome_1",
            "sid": "db122",
            "log_dir": "/autoupgrade/test/log",
            "upgrade_node": "localhost",
            "target_version": "19.1"
        }]
    }

The location of the returning header for this task request can be used to view the AutoUpgrade task.

    Type:application/json" 'http://localhost:8080/autoupgrade/task?mode=analyze' -i
    HTTP/1.1 201 Created
    Date: Thu, 14 Oct 2021 19:52:59 GMT
    Set-Cookie: JSESSIONID=node01efwo2229s7kj11rxw2l2mltc10.node0; Path=/
    Expires: Thu, 01 Jan 1970 00:00:00 GMT
    Content-Type: application/json
    X-Frame-Options: SAMEORIGIN
    Location: http://localhost:8080/autoupgrade/task?taskid=job_2021-10-14_15_53_00.085_0
    Transfer-Encoding: chunked

The 201 response body for this analyze request shows the AutoUpgrade job status description, returned in JSON format:

    {
        "taskid": "job_2021-10-14_15_53_00.085_0",
        "status": "submitted",
        "message": "",
        "link": "http://localhost:8080/autoupgrade/task?taskid=job_2021-10-14_15_53_00.085_0",
        "config": {
            "global": {
                "autoupg_log_dir": "/autoupgrade/test/glog"
            },
            "jobs": [
                {
                    "start_time": "NOW",
                    "source_home": "/databases/product/12.2.0/dbhome_1",
                    "target_home": "/databases/product/19.1.0/dbhome_1",
                    "sid": "db122",
                    "log_dir": "/autoupgrade/test/log",
                    "upgrade_node": "localhost",
                    "target_version": "19.1"
                }
            ]
        }
    }

Example A-2 Response for an AutoUpgrade Job After a Faulty Request

In the following example, an AutoUpgrade job is submitted with an invalid `mode` parameter:

    curl --data-binary "@config.json" -X POST --header "Content-Type:application/json"
    'http://localhost:8080/autoupgrade/task?mode=NULL'

The 400 response header to the faulty request is as follows:

    Type:application/json" 'http://localhost:8080/autoupgrade/task?mode=null' -i
    HTTP/1.1 400 Bad Request
    Date: Wed, 20 Oct 2021 18:02:46 GMT
    Content-Type: application/json
    X-Frame-Options: SAMEORIGIN
    Transfer-Encoding: chunked

The following example shows this 400 response body, returned in JSON format:

    {
        "taskid": "job_2021-10-20_14_02_46.855_4",
        "status": "Bad Request",
        "message": "AutoUpgrade parameter mode is invalid.",
        "link": "",
        "config": null
    }

Example A-3 Rerunning an AutoUpgrade Job Using a `taskid`

In this example, Task ID `job_2021-10-14_15_53_00.085_0` is rerun in analyze mode:

    curl -X POST 'http://localhost:8080/autoupgrade/task?mode=analyze&taskid=job_2021-10-14_15_53_00.085_0'

The 201 response header for this rerun job is as follows:

    HTTP/1.1 201 Created
    Date: Mon, 10 Jan 2022 19:44:40 GMT
    Set-Cookie: JSESSIONID=node0sjsoy3w4cntl13qnat979zc6n4.node0; Path=/
    Expires: Thu, 01 Jan 1970 00:00:00 GMT
    Content-Type: application/json
    X-Frame-Options: SAMEORIGIN
    Location: http://localhost:8080/autoupgrade/task?taskid=job_2022-01-10_14_19_09.156_1
    Transfer-Encoding: chunked

The task body describes the task in JSON format:

    {    "taskid": "job_2021-10-14_15_53_00.085_0",    "status": "submitted",    "message": "",    "link": "http://localhost:8080/autoupgrade/task?taskid=job_2021-10-14_15_53_00.085_0",
              "config": {
                  "global": {
                      "autoupg_log_dir": "/autoupgrade/test/glog"
                  },
                  "jobs": [
                      {
                          "start_time": "NOW",
                          "source_home": "/databases/product/12.2.0/dbhome_1",
                          "target_home": "/databases/product/19.1.0/dbhome_1",
                          "sid": "db122",
                          "log_dir": "/autoupgrade/test/log",
                          "upgrade_node": "localhost",
                          "target_version": "19.1"
                      }
                  ]
              } }

**Parent topic:** REST APIs for AutoUpgrade

#### Progress Report Request for an AutoUpgrade Task

Use the `progress` API to get a progress report of an AutoUpgrade task specified by the `taskid`.

##### Method

GET

##### Path

    /autoupgrade/progress

##### Usage Notes

When you submit the progress request for the task that you specify with the `taskid`, you receive a report of the progress of the AutoUpgrade task identified by that `taskid`.

##### Requests

Request parameters:

| Parameter | Description                                                                      |
|:----------|:---------------------------------------------------------------------------------|
| `taskid`  | (Required) Identifies the task for which you want to obtain the progress report. |

##### Response

- 200 Response: Reports the progress of the task that you specify with the `taskid`.
- 400 Response: Reports that the `taskid` is missing
- 404 Response: Reports that the `taskid` is invalid

##### Examples

Example A-4 Submit Task Progress Report GET Request

The following example shows how to get an AutoUpgrade task progress by providing an AutoUpgrade `taskid` with cURL.

    curl http://localhost:8080/autoupgrade/progress?taskid=job_2021-10-20_14_44_57.11_1

This is the 200 response to the preceding GET task progress report for a job:

    HTTP/1.1 200 OK
    Date: Wed, 20 Oct 2021 19:56:32 GMT
    Set-Cookie: JSESSIONID=node01rkapzylgd2tljf28bghba9bx6.node0; Path=/
    Expires: Thu, 01 Jan 1970 00:00:00 GMT
    Content-Type: application/json
    X-Frame-Options: SAMEORIGIN
    Transfer-Encoding: chunked

The 200 response body for this GET progress report for a job request is as follows, in JSON format:

    {
        "taskid": "job_2021-10-20_14_44_57.11_1",
        "status": "successful",
        "message": "",
        "autoupgrade_progress": {
            "totalJobs": 1,
            "totalFinishedJobs": 1,
            "startTime": "2021-10-20 14:44:59",
            "lastUpdateTime": "2021-10-20 14:45:10",
            "jobs": [
                {
                    "sid": "db122",
                    "jobNo": 100,
                    "isCDB": false,
                    "totalPercentCompleted": 100,
                    "totalContainers": 1,
                    "totalStages": 1,
                    "additionalInfo": "",
                    "lastUpdateTime": "2021-10-20 14:45:10",
                    "stages": [
                        {
                            "stage": "PRECHECKS",
                            "percentCompleted": "100",
                            "totalChecks": 104,
                            "totalCompletedChecks": 104,
                            "additionalInfo": "",
                            "lastUpdateTime": "2021-10-20 14:44:59",
                            "containers": [
                                {
                                    "container": "db122",
                                    "totalChecks": 104,
                                    "completedChecks": 104,
                                    "succeededChecks": 91,
                                    "failedChecks": 13,
                                    "runningChecks": [
                                    ],
                                    "finishedChecks": [
                                        "PLUGIN_COMP_COMPATIBILITY",
                                        "AMD_EXISTS",
                                        "COMPATIBLE_NOT_SET",
                                        "COMPATIBLE_PARAMETER",
                                        "CASE_INSENSITIVE_AUTH",
                                        "CYCLE_NUMBER",
                                        "CREATE_WINDOWS_SERVICE",
                                        "AUDTAB_ENC_TS",
                                        "CONC_RES_MGR",
                                        "DATA_MINING_OBJECT",
                                        "DV_ENABLED",
                                        "AWR_EXPIRED_SNAPSHOTS",
                                        "DV_SIMULATION",
                                        "DEPEND_USR_TABLES",
                                        "FLASH_RECOVERY_AREA_SETUP",
                                        "FILES_NEED_RECOVERY",
                                        "INVALID_SYS_TABLEDATA",
                                        "INVALID_OBJECTS_EXIST",
                                        "JAVAVM_STATUS",
                                        "ORACLE_RESERVED_USERS",
                                        "HIDDEN_PARAMS",
                                        "JVM_MITIGATION_PATCH",
                                        "TRGOWNER_NO_ADMNDBTRG",
                                        "MV_REFRESH",
                                        "PENDING_DST_SESSION",
                                        "RAISE_COMPATIBLE",
                                        "COMPATIBLE_PFILES",
                                        "INVALID_USR_TABLEDATA",
                                        "POST_JVM_MITIGAT_PATCH",
                                        "PURGE_RECYCLEBIN",
                                        "PRE_FIXED_OBJECTS",
                                        "SYNC_STANDBY_DB",
                                        "SYS_DEFAULT_TABLESPACE",
                                        "TWO_PC_TXN_EXIST",
                                        "UNDERSCORE_EVENTS",
                                        "UNIAUD_TAB",
                                        "XBRL_VERSION",
                                        "PARAMETER_DEPRECATED",
                                        "XDB_RESOURCE_TYPE",
                                        "PARAMETER_NEW_NAME_VAL",
                                        "PARAMETER_OBSOLETE",
                                        "PARAMETER_RENAME",
                                        "MIN_ARCHIVE_DEST_SIZE",
                                        "NEW_TIME_ZONES_EXIST",
                                        "PARAMETER_MIN_VAL",
                                        "DISK_SPACE_FOR_RECOVERY_AREA",
                                        "PA_PROFILE",
                                        "UPG_BY_STD_UPGRD",
                                        "MIN_RECOVERY_AREA_SIZE",
                                        "OLS_VERSION",
                                        "ROLLBACK_SEGMENTS",
                                        "ARCHIVE_MODE_ON",
                                        "PGA_AGGREGATE_LIMIT",
                                        "APEX_MANUAL_UPGRADE",
                                        "TABLESPACES",
                                        "OLAP_PAGE_POOL_SIZE",
                                        "STANDARD_EDITION",
                                        "TEMPTS_NOTEMPFILE",
                                        "TS_FORUPG_STATUS",
                                        "APPL_PRINCIPAL",
                                        "TDE_IN_USE",
                                        "STREAMS_SETUP",
                                        "DIR_SYMLINKS",
                                        "ORDIM_DESUPPORT",
                                        "UTLRP_RUN_SERIAL",
                                        "DESUPPORT_RAC_ON_SE",
                                        "COMPATIBLE_GRP",
                                        "EDS_EXISTS",
                                        "UNIAUD_RECORDS_IN_FILE",
                                        "JOB_TABLE_INTEGRITY",
                                        "TARGET_CDB_COMPATIBILITY",
                                        "DUPLICATE_DB_HASHES",
                                        "UNPLUG_PLUG_UPGRADE",
                                        "ENABLE_LOCAL_UNDO",
                                        "AUTO_LOGIN_KEYSTORE_REQUIRED",
                                        "NO_KEYSTORE_FILES",
                                        "INFORM_DROP_GRP",
                                        "PRE_DISABLE_BCT_UPG",
                                        "MAX_STRING_SIZE_ON_DB",
                                        "POST_RECOMPILE_IN_CDB",
                                        "TEMPTS_ALLOFFLINE",
                                        "PRE_RECOMPILE_IN_CDB",
                                        "MAX_DB_FILES_EXCEEDED",
                                        "POST_DISABLE_BCT_UPG",
                                        "TARGET_HOME_REGISTERED_INVENTORY",
                                        "ISRAC_SWITCHEDON_TARGETHOME",
                                        "KEYSTORE_CONFLICT",
                                        "WALLET_ROOT_KEYSTORE",
                                        "ORACLE_HOME_KEYSTORE",
                                        "DEPLOY_JOB_VALIDATIONS",
                                        "DUPLIC_SYS_SYSTEM_OBJS"
                                    ],
                                    "checksWithExecutionError": [
                                    ],
                                    "checksFailed": [
                                        "DICTIONARY_STATS",
                                        "POST_DICTIONARY",
                                        "POST_FIXED_OBJECTS",
                                        "OLD_TIME_ZONES_EXIST",
                                        "MANDATORY_UPGRADE_CHANGES",
                                        "RMAN_RECOVERY_VERSION",
                                        "TABLESPACES_INFO",
                                        "ORDIM_INFO_DESUPPORT",
                                        "POST_UTLRP",
                                        "COMPONENT_INFO",
                                        "INVALID_ORA_OBJ_INFO",
                                        "INVALID_APP_OBJ_INFO",
                                        "TIMESTAMP_MISMATCH"
                                    ],
                                    "additionalInfo": "",
                                    "lastUpdateTime": "2021-10-20 14:45:10"
                                }
                            ]
                        }
                    ],
                    "summary": [
                        {
                            "stage": "PRECHECKS",
                            "complete": "Yes",
                            "duration": "11.08S"
                        }
                    ]
                }
            ]
        }
    }

Example A-5 Task Progress Report Request With an Invalid Task ID

In this example, the task report progress is submitted for an invalid task id:

    curl http://localhost:8080/autoupgrade/progress?taskid=null

The 404 response header for the preceding invalid request is as follows:

    HTTP/1.1 404 Not Found
    Date: Wed, 20 Oct 2021 18:49:12 GMT
    Set-Cookie: JSESSIONID=node06xkycdfv7k1f1bus3q43zefum2.node0; Path=/
    Expires: Thu, 01 Jan 1970 00:00:00 GMT
    Content-Type: application/json
    X-Frame-Options: SAMEORIGIN
    Transfer-Encoding: chunked

The 404 response body for this request is as follows, returned in JSON format:

    {
        "taskid": "null",
        "status": "Bad Request",
        "message": "taskid is invalid.",
        "link": "",
        "config": ""
    }

    }

**Parent topic:** REST APIs for AutoUpgrade

#### Console Request for an AutoUpgrade Task

Use the `console` API to get a console for the AutoUpgrade task specified by the `taskid`.

##### Method

GET

##### Path

    /autoupgrade/console

##### Usage Notes

Get console outputs of an AutoUpgrade task, which is specified by `taskid`.

##### Request

Path parameters:

| Parameter | Description                                                                      |
|:----------|:---------------------------------------------------------------------------------|
| `taskid`  | (Required) Identifies the task for which you want to obtain the console outputs. |

##### Response

- 200 Response: An AutoUpgrade console opens.
- 400 Response: Reports that the `taskid` is missing
- 404 Response: Reports that the `taskid` is invalid

##### Examples

Example A-6 Submit Task Console GET Request

The following example shows how to submit a console request by providing an AutoUpgrade `taskid` with cURL:

    curl http://localhost:8080/autoupgrade/console?taskid=job_2021-10-20_14_44_57.11_1

The 200 response header for the preceding GET task console request is as follows:

    HTTP/1.1 200 OK
    Date: Wed, 20 Oct 2021 20:09:04 GMT
    Set-Cookie: JSESSIONID=node01hwo60q3c5irz1pnn4fa8hhm2k9.node0; Path=/
    Expires: Thu, 01 Jan 1970 00:00:00 GMT
    Content-Type: plain/text
    X-Frame-Options: SAMEORIGIN
    Transfer-Encoding: chunked

The 200 response body for this request is as follows, reporting the progress of the AutoUpgrade job returned in plain (text) format:

    AutoUpgrade tool launched with default options
    Processing config file ...
    +--------------------------------+
    | Starting AutoUpgrade execution |
    +--------------------------------+
    1 databases will be analyzed
    Job 100 database db122
    Job 100 completed
    ------------------- Final Summary --------------------
    Number of databases            [ 1 ]

    Jobs finished                  [1]
    Jobs failed                    [0]
    Jobs restored                  [0]
    Jobs pending                   [0]

    Please check the summary report at:
    /databases/working/job_2021-10-20_14_44_57.11_1/cfgtoollogs/upgrade/auto/status/status.html
    /databases/working/job_2021-10-20_14_44_57.11_1/cfgtoollogs/upgrade/auto/status/status.log

Example A-7 Response Header for a Console Request With an Invalid Task ID

In this example, the console request is submitted for an invalid task id:

    curl http://localhost:8080/autoupgrade/console?taskid=null

The preceding request returns the following 404 header response to the Console request:

    HTTP/1.1 404 Not Found
    Date: Wed, 20 Oct 2021 18:49:12 GMT
    Set-Cookie: JSESSIONID=node06xkycdfv7k1f1bus3q43zefum2.node0; Path=/
    Expires: Thu, 01 Jan 1970 00:00:00 GMT
    Content-Type: application/json
    X-Frame-Options: SAMEORIGIN
    Transfer-Encoding: chunked

The 404 response body for this Console request is as follows, returned in JSON format:

    {
        "taskid": "null",
        "status": "Bad Request",
        "message": "taskid is invalid.",
        "link": "",
        "config": ""
    }

**Parent topic:** REST APIs for AutoUpgrade

#### Task Details Request for AutoUpgrade

Use the `task` API to get AutoUpgrade task details for the task specified by the `taskid`.

##### Method

GET

##### Path

    /autoupgrade/task

##### Usage Notes

When you provide a `taskid`, you obtain details about the task that is associated with that `taskid`.

For example:

    curl http://localhost:8080/autoupgrade/task?taskid=job_2021-10-20_14_44_57.11_1

##### Request

Path parameters:

| Parameter | Description                                                                              |
|:----------|:-----------------------------------------------------------------------------------------|
| `taskid`  | (Required) System-generated identifier for the task for which you want to obtain details |

##### Response

- 200 Response: Reports details of the task that you specify with the `taskid`.
- 400 Response: Reports that the `taskid` is missing
- 404 Response: Reports that the `taskid` is invalid

Example A-8 Submit Task Details GET Request

The following example shows how to submit an AutoUpgrade get task details request by providing an AutoUpgrade `taskid` with cURL:

    curl http://localhost:8080/autoupgrade/task?taskid=job_2021-10-20_14_44_57.11_1

The 200 response to the preceding get task details request is as follows. The Location header returns the URI that you can use to view the AutoUpgrade task.

    HTTP/1.1 200 OK
    Date: Wed, 20 Oct 2021 18:45:20 GMT
    Set-Cookie: JSESSIONID=node0tl6lz63xj3xd11i05p8bfmw8u1.node0; Path=/
    Expires: Thu, 01 Jan 1970 00:00:00 GMT
    Content-Type: application/json
    X-Frame-Options: SAMEORIGIN
    Location: http://localhost:8080/autoupgrade/task?taskid=job_2021-10-20_14_44_57.11_1
    Transfer-Encoding: chunked

The 200 response body to this GET task details request is as follows, returned in a JSON format:

    {
        "taskid": " job_2021-10-20_14_44_57.11_1",
        "status": "submitted",
        "message": "",
        "link": "http://localhost:8080/autoupgrade/task?taskid=job_2021-10-14_15_53_00.085_0",
        "config": {
            "global": {
                "autoupg_log_dir": "/autoupgrade/test/glog"
            },
            "jobs": [
                {
                    "dbname": "db122",
                    "start_time": "NOW",
                    "source_home": "/databases/product/12.2.0/dbhome_1",
                    "target_home": "/databases/product/19c/dbhome_1",
                    "sid": "db122",
                    "log_dir": "/autoupgrade/test/log",
                    "upgrade_node": "localhost",
                    "target_version": "19.1"
                }
            ]
        }
    }

Example A-9 Task Details Request with an Invalid `taskid`

A GET request with an invalid `taskid` is submitted:

    curl http://localhost:8080/autoupgrade/task?taskid=null

The 404 response header for the invalid request is as follows:

    {HTTP/1.1 404 Not Found
    Date: Wed, 20 Oct 2021 18:49:12 GMT
    Set-Cookie: JSESSIONID=node06xkycdfv7k1f1bus3q43zefum2.node0; Path=/
    Expires: Thu, 01 Jan 1970 00:00:00 GMT
    Content-Type: application/json
    X-Frame-Options: SAMEORIGIN
    Transfer-Encoding: chunked

The 404 response body to this request is as follows, returned in JSON format:

    {
        "taskid": "null",
        "status": "Bad Request",
        "message": "taskid is invalid.",
        "link": "",
        "config": ""
    }

**Parent topic:** REST APIs for AutoUpgrade

#### Task List Request for AutoUpgrade Tasks

Use the `tasks` API to get an AutoUpgrade task list.

##### Method

GET

##### Path

    /autoupgrade/tasks

##### Requests

There are no parameters.

##### Response

200 Response: Reports details of all tasks.

##### Usage Notes

Use this method to obtain a list of tasks.

Example A-10 Submit Task List GET Request

The following example shows how to get an AutoUpgrade task list with cURL:

    curl http://localhost:8080/autoupgrade/tasks

The following example shows a response header for a GET task list request:

    HTTP/1.1 200 OK
    Date: Wed, 20 Oct 2021 19:51:46 GMT
    Set-Cookie: JSESSIONID=node0yawyihk3msz91eeauxijfaw6z3.node0; Path=/
    Expires: Thu, 01 Jan 1970 00:00:00 GMT
    Content-Type: application/json
    X-Frame-Options: SAMEORIGIN
    Transfer-Encoding: chunked

The 200 response body for this list request is as follows, returned in JSON format:

    {
        "total_tasks": 2,
        "tasks": [
            {
                "mode": "analyze",
                "taskid": "job_2021-10-20_14_44_57.11_1",
                "config": {
                    "jobs": [
                        {
                            "source_home": "/databases/product/12.2.0/dbhome_1",
                            "sid": "db122"
                        }
                    ]
                },
                "link": "http://localhost:8080/autoupgrade/task?taskid=job_2021-10-20_14_44_57.11_1"
            },
            {
                "mode": "analyze",
                "taskid": "job_2021-10-20_15_54_01.568_2",
                "config": {
                    "jobs": [
                        {
                            "source_home": "/databases/product/12.2.0/dbhome_1",
                            "sid": "db122"
                        }
                    ]
                },
                "link": "http://localhost:8080/autoupgrade/task?taskid=job_2021-10-20_15_54_01.568_2"
            }
        ]
    }

**Parent topic:** REST APIs for AutoUpgrade

#### Log or Log List for an AutoUpgrade Task

Use the `log` API to open a log, or to get a log list of a task specified by `taskid`.

##### Method

GET

##### Path

    /autoupgrade/log

##### Usage Notes

When you submit a log request with the type or name, you receive an AutoUpgrade log for the task, specified by `taskid`. If you do not provide the type or name, then you receive an AutoUpgrade log list, which includes all HTML, JSON, and XML log files for the task, specified by `taskid`.

##### Request

Request parameters:

| Parameter | Description                                                                                                                                               |
|:----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------|
| `taskid`  | (Required) Specifies the AutoUpgrade task ID for which you want to open a log, or list logs.                                                              |
| `type`    | (Optional) Specifies the type of an AutoUpgrade log. Options:<br>`autolog`: AutoUpgrade log file<br>`errlog`: Errors log file<br>`userlog`: user log file |
| `name`    | (Optional) Specify the filename of a specific log within a task ID log list.                                                                              |

##### Response

- 200 Response: AutoUpgrade opens the AutoUpgrade task err/user/auto log for the `taskid` that you specify.
- 400 Response: Reports that the `taskid` is missing
- 404 Response: Reports that the `taskid` is invalid

##### Examples

Example A-11 Submit Task Log GET Request

The following example shows how to get an AutoUpgrade user log by providing an AutoUpgrade `taskid` and `type` with cURL:

    curl "http://localhost:8080/autoupgrade/log?type=userlog&taskid=job_2021-10-20_14_44_57.11_1"

The 200 response header to the preceding task log request with `type` specified as `userlog` is as follows:

    HTTP/1.1 200 OK
    Date: Wed, 20 Oct 2021 20:30:02 GMT
    Set-Cookie: JSESSIONID=node0jrq0bg40ya86mr8icb87d8z16.node0; Path=/
    Expires: Thu, 01 Jan 1970 00:00:00 GMT
    Content-Type: plain/text
    X-Frame-Options: SAMEORIGIN
    Transfer-Encoding: chunked

The 200 response body for this request is as follows, returned in plain (text) format for a task log with `type` specified as `userlog`:

    2021-10-20 14:44:57.737 INFO
    build.hash:71778e3
    build.version:23.0.0
    build.date:2021/05/05 10:42:40 -0700
    build.max_target_version:23
    build.supported_target_versions:12.2,18,19,21,23
    build.type:beta
    build.hash_date:2021/04/15 15:06:03 -0700
    build.label:rest_api

    2021-10-20 14:44:57.791 INFO Loading user config file metadata
    2021-10-20 14:44:58.598 INFO The target_version parameter was updated from 19.1 to 19.3.0.0.0 due to finding a more accurate value
    2021-10-20 14:44:58.844 INFO srvctl command is not available or user does not have permission to execute it
    2021-10-20 14:44:59.163 INFO Finished processing dbEntry job_0
    2021-10-20 14:44:59.475 INFO Current settings Initialized
    2021-10-20 14:44:59.576 INFO Job 100 database db122
    2021-10-20 14:45:11.685 INFO Job 100 completed

Example A-12 Response Header for a Log Request With an Invalid Task ID

In this example, the GET log request is submitted for an invalid task id:

    curl http://localhost:8080/autoupgrade/log?taskid=null

This request returns the following 404 header response:

    HTTP/1.1 404 Not Found
    Date: Wed, 20 Oct 2021 18:49:12 GMT
    Set-Cookie: JSESSIONID=node06xkycdfv7k1f1bus3q43zefum2.node0; Path=/
    Expires: Thu, 01 Jan 1970 00:00:00 GMT
    Content-Type: application/json
    X-Frame-Options: SAMEORIGIN
    Transfer-Encoding: chunked

The 404 response body for the invalid `taskid` is as follows, returned in JSON format:

    {
        "taskid": "null",
        "status": "Bad Request",
        "message": "taskid is invalid.",
        "link": "",
        "config": ""
    }

\\

Example A-13 Response Body for a Task ID Log List

The following example shows how to get an AutoUpgrade log list by providing an AutoUpgrade `taskid` with cURL. :

     curl 'http://localhost:8080/autoupgrade/log?taskid='job_2022-01-10_14:19:09.156_1

The following example shows the 200 response body showing the log list for the `taskid`, returned in JSON format:

    {
        "logs": [
            {
                "filename": "cfgtoollogs/upgrade/auto/autoupgrade.log",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=cfgtoollogs/upgrade/auto/autoupgrade.log"
            },
            {
                "filename": "cfgtoollogs/upgrade/auto/autoupgrade_user.log",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=cfgtoollogs/upgrade/auto/autoupgrade_user.log"
            },
            {
                "filename": "cfgtoollogs/upgrade/auto/autoupgrade_err.log",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=cfgtoollogs/upgrade/auto/autoupgrade_err.log"
            },
            {
                "filename": "cfgtoollogs/upgrade/auto/status/status.json",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=cfgtoollogs/upgrade/auto/status/status.json"
            },
            {
                "filename": "cfgtoollogs/upgrade/auto/status/progress.json",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=cfgtoollogs/upgrade/auto/status/progress.json"
            },
            {
                "filename": "cfgtoollogs/upgrade/auto/status/status.html",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=cfgtoollogs/upgrade/auto/status/status.html"
            },
            {
                "filename": "cfgtoollogs/upgrade/auto/status/status.log",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=cfgtoollogs/upgrade/auto/status/status.log"
            },
            {
                "filename": "db122/100/autoupgrade_20220110.log",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=db122/100/autoupgrade_20220110.log"
            },
            {
                "filename": "db122/100/autoupgrade_20220110_user.log",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=db122/100/autoupgrade_20220110_user.log"
            },
            {
                "filename": "db122/100/autoupgrade_err.log",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=db122/100/autoupgrade_err.log"
            },
            {
                "filename": "db122/100/prechecks/prechecks_db122.log",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=db122/100/prechecks/prechecks_db122.log"
            },
            {
                "filename": "db122/100/prechecks/db122_checklist.xml",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=db122/100/prechecks/db122_checklist.xml"
            },
            {
                "filename": "db122/100/prechecks/db122_checklist.json",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=db122/100/prechecks/db122_checklist.json"
            },
            {
                "filename": "db122/100/prechecks/db122_preupgrade.html",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=db122/100/prechecks/db122_preupgrade.html"
            },
            {
                "filename": "db122/100/prechecks/upgrade.xml",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=db122/100/prechecks/upgrade.xml"
            },
            {
                "filename": "db122/100/prechecks/db122_preupgrade.log",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=db122/100/prechecks/db122_preupgrade.log"
            },
            {
                "filename": "db122/101/autoupgrade_20220110.log",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=db122/101/autoupgrade_20220110.log"
            },
            {
                "filename": "db122/101/autoupgrade_20220110_user.log",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=db122/101/autoupgrade_20220110_user.log"
            },
            {
                "filename": "db122/101/autoupgrade_err.log",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=db122/101/autoupgrade_err.log"
            },
            {
                "filename": "db122/101/prechecks/prechecks_db122.log",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=db122/101/prechecks/prechecks_db122.log"
            },
            {
                "filename": "db122/101/prechecks/db122_checklist.xml",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=db122/101/prechecks/db122_checklist.xml"
            },
            {
                "filename": "db122/101/prechecks/db122_checklist.json",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=db122/101/prechecks/db122_checklist.json"
            },
            {
                "filename": "db122/101/prechecks/db122_preupgrade.html",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=db122/101/prechecks/db122_preupgrade.html"
            },
            {
                "filename": "db122/101/prechecks/upgrade.xml",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=db122/101/prechecks/upgrade.xml"
            },
            {
                "filename": "db122/101/prechecks/db122_preupgrade.log",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=db122/101/prechecks/db122_preupgrade.log"
            },
            {
                "filename": "db122/102/autoupgrade_20220110.log",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=db122/102/autoupgrade_20220110.log"
            },
            {
                "filename": "db122/102/autoupgrade_20220110_user.log",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=db122/102/autoupgrade_20220110_user.log"
            },
            {
                "filename": "db122/102/autoupgrade_err.log",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=db122/102/autoupgrade_err.log"
            },
            {
                "filename": "db122/102/prechecks/prechecks_db122.log",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=db122/102/prechecks/prechecks_db122.log"
            },
            {
                "filename": "db122/102/prechecks/db122_checklist.xml",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=db122/102/prechecks/db122_checklist.xml"
            },
            {
                "filename": "db122/102/prechecks/db122_checklist.json",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=db122/102/prechecks/db122_checklist.json"
            },
            {
                "filename": "db122/102/prechecks/db122_preupgrade.html",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=db122/102/prechecks/db122_preupgrade.html"
            },
            {
                "filename": "db122/102/prechecks/upgrade.xml",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=db122/102/prechecks/upgrade.xml"
            },
            {
                "filename": "db122/102/prechecks/db122_preupgrade.log",
                "link": "http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=db122/102/prechecks/db122_preupgrade.log"
            }
        ]
    }


Example A-14 Request a Specific Log with `name` Parameter

The following example shows how to request a specific log file within a task ID log list, by providing the filename with the `name` parameter, and the `taskid` of the task that generated the log:

    curl 'http://localhost:8080/autoupgrade/log?taskid=job_2022-01-10_14_19_09.156_1&name=db122/102/autoupgrade_20220110_user.log'

This request returns this 200 response body that displays the log file information for the filename specified:

    2022-01-10 14:44:43.447 INFO
    build.hash:71778e3
    build.version:23.0.0
    build.date:2021/05/05 10:42:40 -0700
    build.max_target_version:23
    build.supported_target_versions:12.2,18,19,21,23
    build.type:beta
    build.hash_date:2021/04/15 15:06:03 -0700
    build.label:rest_api

    2022-01-10 14:44:49.529 INFO Analyzing db122, 104 checks will run using 4 threads

**Parent topic:** REST APIs for AutoUpgrade

#### Status Report of Task Request for AutoUpgrade

Use the `status` API to get a status report of an AutoUpgrade task specified by the `taskid`.

##### Method

GET

##### Path

    /autoupgrade/status

##### Usage Notes

To receive an AutoUpgrade task status in JSON format, submit an AutoUpgrade `taskid`.

##### Request

Path parameters:

| Parameter | Description                                                                              |
|:----------|:-----------------------------------------------------------------------------------------|
| `taskid`  | (Required) System-generated identifier for the task for which you want to obtain status. |

##### Response

- 200 Response: Reports the status of the task that you specify with the `taskid`.
- 400 Response: Reports that the `taskid` is missing
- 404 Response: Reports that the `taskid` is invalid

##### Examples

Example A-15 Submit Task Status GET Request

The following example shows how to get an AutoUpgrade task status request with cURL:

    curl http://localhost:8080/autoupgrade/status?taskid=job_2021-10-20_14_44_57.11_1

This is the 200 response header for the preceding GET task status report request:

    HTTP/1.1 200 OK
    Date: Wed, 20 Oct 2021 19:51:46 GMT
    Set-Cookie: JSESSIONID=node0yawyihk3msz91eeauxijfaw6z3.node0; Path=/
    Expires: Thu, 01 Jan 1970 00:00:00 GMT
    Content-Type: application/json
    X-Frame-Options: SAMEORIGIN
    Transfer-Encoding: chunked

This is the response body for the GET task status report request, in JSON format:

    {
        "taskid": "job_2021-10-20_14_44_57.11_1",
        "status": "successful",
        "message": "",
        "autoupgrade_status": {
            "totalJobs": 1,
            "lastUpdateTime": "2021-10-20 14:45:11",
            "jobs": [
                {
                    "sid": "db122",
                    "jobNo": 100,
                    "logDirectory": "/databases/working/job_2021-10-20_14_44_57.11_1/db122/100",
                    "conNumber": 1,
                    "lastUpdateTime": "2021-10-20 14:45:11",
                    "modules": [
                        {
                            "moduleName": "PRECHECKS",
                            "status": 0,
                            "errors": [
                            ],
                            "lastUpdateTime": "2021-10-20 14:45:11"
                        }
                    ]
                }
            ]
        }
    }

Example A-16 Submit Task Status GET Request with an invalid `taskid`

In the following example, an AutoUpgrade GET task status request is submitted with an invalid `taskid` parameter:

    curl http://localhost:8080/autoupgrade/status?taskid=null

The 404 response header for the preceding invalid GET task status request is as follows:

    HTTP/1.1 404 Not Found
    Date: Wed, 20 Oct 2021 18:49:12 GMT
    Set-Cookie: JSESSIONID=node06xkycdfv7k1f1bus3q43zefum2.node0; Path=/
    Expires: Thu, 01 Jan 1970 00:00:00 GMT
    Content-Type: application/json
    X-Frame-Options: SAMEORIGIN
    Transfer-Encoding: chunked

The response body for this invalid GET task status request is as follows, in JSON format:

    {
        "taskid": "null",
        "status": "Bad Request",
        "message": "taskid is invalid.",
        "link": "",
        "config": ""
    }

**Parent topic:** REST APIs for AutoUpgrade
