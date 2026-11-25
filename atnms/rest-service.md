Learn to configure REST service, and use REST service APIs.

- Configuring REST Service Using ORDS
  Oracle Trace File Analyzer includes REST support allowing invocation and query over HTTPS.
- Configuring REST Service Using Apache Tomcat
  The Oracle Trace File Analyzer install includes a Web Application Resource (WAR) file to enable the REST service via Apache Tomcat.
- REST Service print API
  Learn to use the REST Service `print` API
- REST Service diagcollect API
  Learn to use the REST Service `diagcollect` API.
- REST Service download API
  Learn to use the REST Service `download` API.
- REST Service run API
  Learn to use REST Service `run` API.
- REST Service user API
  Learn to use REST Service `user` API.

**Parent topic:** [Collecting Diagnostic Data and Triaging, Diagnosing, and Resolving Issues](diagnose-troubleshoot-issues-errors.md)

### 16.1 Configuring REST Service Using ORDS

Oracle Trace File Analyzer includes REST support allowing invocation and query over HTTPS.

#### Syntax

To facilitate this REST support Oracle REST Data Services (ORDS) is included within the install.

    tfactl rest [-status|-start|-stop|-upgrade|-uninstall] [-dir] [-port] [-user] [-debug [-level]]

**Note:**

You can run the REST command only as `root` user.

#### Parameters

Table 16-1 REST Command Parameters

| Parameter    | Description                                                                                                                                                 |
|:-------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-status`    | Prints the current status.                                                                                                                                  |
| `-start`     | Starts Oracle Trace File Analyzer REST services if not already running.                                                                                     |
| `-stop`      | Stops Oracle Trace File Analyzer REST services if running.                                                                                                  |
| `-upgrade`   | Checks if the configured ORDS API should be upgraded.<br>If the ORDS API needs upgrading, then stops ORDS, upgrades the API, and then restarts ORDS.        |
| `-uninstall` | Removes the Oracle Trace File Analyzer REST configuration.                                                                                                  |
| `–dir`       | The directory to use to store the Oracle Trace File Analyzer REST configuration details.<br>Defaults to the users home directory.                           |
| `–port`      | The port to run ORDS on.<br>Defaults to 9090.                                                                                                               |
| `-user`      | The user to start ORDS as.<br>Defaults to the GRID owner.                                                                                                   |
| `–debug`     | Enables debug.                                                                                                                                              |
| `–level`     | The level of debug to use, where available levels are:<br>• 1 – FATAL<br>• 2 – ERROR<br>• 3 – WARNING<br>• 4 – INFO (default)<br>• 5 – DEBUG<br>• 6 – TRACE |

Once ORDS is running, you can invoke REST using the following APIs using requests of the form:

    https://host:port/ords/api

For example:

    https://host:port/ords/tfactl/print/status

#### REST Authentication

Oracle Trace File Analyzer REST uses first-party cookie-based authentication (basic authentication).

The Oracle Trace File Analyzer REST application is able to authenticate and authorize itself to the RESTful API using the same cookie session that the web application is using. The first party application has full access to the RESTful API.

During start-up Oracle Trace File Analyzer prompts you for the password for the `tfaadmin` and `tfarest` users.

- Use `tfarest` user for REST calls

- Use `tfaadmin` for making REST calls and to manage the REST service, for example, changing the logging level

<!-- -->

    # ./tfactl rest -start

    Configuring TFA REST Services using ORDS :

    This might take couple of minutes. Please be patient.

    Adding Dependency Jars to ORDS

    Adding users to ORDS :

    Enter a password for user tfaadmin:
    Confirm password for user tfaadmin:

    Enter a password for user tfarest:
    Confirm password for user tfarest:

    Starting TFA REST Services

    Successfully started TFA REST Services [PID : 32650]

    URL : https://myserver:9090/ords/tfactl/print/status

Access the web service from a browser using the following URL:

    https://host_name:9090/ords/tfactl/print/status

You are presented with a 401 message, which includes a sign in link. Click the link, sign in with `tfarest` credentials you just created, and you will be directed to REST output.

Alternatively, you can also specify the credentials in a `curl` command.

    # curl -k --user tfarest:mypassword https://myserver:9090/ords/tfactl/print/status
    [ {
      "status" : "CheckOK",
      "hostname" : "myserver",
      "pid" : 2430,
      "port" : 5000,
      "version" : "18.2.0.0.0",
      "buildId" : "18200020180501035221",
      "inventoryStatus" : "COMPLETE"
    } ]

**Parent topic:** REST Service

### 16.2 Configuring REST Service Using Apache Tomcat

The Oracle Trace File Analyzer install includes a Web Application Resource (WAR) file to enable the REST service via Apache Tomcat.

To enable the REST service using Apache Tomcat:

1.  Deploy the `WAR` file located at `TFA_HOME/jlib/tfa.war` to your Tomcat server.
2.  Change the `tfaadmin` user password.
        curl -k --user tfaadmin:tfaadmin -X POST "https://host/tfa/tfactl/user/update" '{ "password" : "some_new_password" }'
3.  Change the `tfarest` user password.
        curl -k --user tfarest:tfarest -X POST "https://host/tfa/tfactl/user/update" '{ "password" : "some_new_password" }'
4.  Add the Tomcat user to the Oracle Trace File Analyzer access list.
        tfactl access add -user tomcat_user

**Parent topic:** REST Service

### 16.3 REST Service print API

Learn to use the REST Service `print` API

- print
  Use GET requests to print the statuses of all hosts.
- hosts
  Use GET requests to print the list of hosts.
- actions
  Use GET requests to print the list of actions performed on all hosts.
- repository
  Use GET requests to print the repository details of all hosts.
- collections
  Use GET requests to print the details of all collections, or a specific collection.
- config
  Use GET requests to print the configuration details of all hosts.
- protocols
  Use GET requests to print the details of protocols of all hosts.
- directories
  Use GET requests to print the details of directories of all hosts.

**Parent topic:** REST Service

#### 16.3.1 print

Use GET requests to print the statuses of all hosts.

##### Syntax

    /tfactl/print/status

Example 16-1 print

    [ {
      "status" : "CheckOK",
      "hostname" : "myhost",
      "pid" : 73637,
      "port" : 9090,
      "version" : "18.1.0.0.0",
      "buildId" : "18100020180109014331",
      "inventoryStatus" : "COMPLETE"
    } ]

**Parent topic:** REST Service print API

#### 16.3.2 hosts

Use GET requests to print the list of hosts.

##### Syntax

    /tfactl/print/hosts

Example 16-2 hosts

    [ {
      "hostname" : "myhost"
    } ]

**Parent topic:** REST Service print API

#### 16.3.3 actions

Use GET requests to print the list of actions performed on all hosts.

##### Syntax

    /tfactl/print/actions

Example 16-3 actions

    [ {
      "actionName" : "Run inventory",
      "hostname" : "Requested in all nodes",
      "client" : "tfactl",
      "startTime" : "Jan 09 07:50:26 PST",
      "endTime" : "Jan 09 07:50:29 PST",
      "status" : "COMPLETE",
      "comments" : null
    } ]

**Parent topic:** REST Service print API

#### 16.3.4 repository

Use GET requests to print the repository details of all hosts.

##### Syntax

    /tfactl/print/repository

Example 16-4 repository

    [ {
      "hostname" : "myhost",
      "directory" : "/scratch/smith/view_storage/smith_tfa_latest/oracle/log/tfa/repository",
      "status" : "OPEN",
      "maxSizeMB" : 10240,
      "currentSizeMB" : 13,
      "freeSpaceMB" : 10227
    } ]

**Parent topic:** REST Service print API

#### 16.3.5 collections

Use GET requests to print the details of all collections, or a specific collection.

##### Syntax

    /tfactl/print/collections
    /tfactl/print/collections/{collectionid}

Example 16-5 collections

    [ {
      "id" : "20171010115528myhost",
      "type" : "Manual Collection",
      "requestUser" : "smith",
      "nodeList" : "[]",
      "masterHost" : "myhost",
      "startTime" : "Mon Oct 09 23:55:32 PDT 2017",
      "endTime" : "Tue Oct 10 11:55:32 PDT 2017",
      "tag" : "/scratch/smith/view_storage/smith_tfa_latest/oracle/log/tfa/repository/tfa_11",
      "zipFileName" : "myhost.tfa_Tue_Oct_10_11_55_28_PDT_2017.zip",
      "componentList" : "[emagent, crsclient, oms, dbwlm,emplugins, cfgtools, afd, wls]",
      "zipFileSize" : 3055,
      "collectionTime" : 16,
      "events" : null
    }]

    [{
      "id" : "20171011044112myhost",
      "type" : "Manual Collection",
      "requestUser" : "smith",
      "nodeList" : "[]",
      "masterHost" : "myhost",
      "startTime" : "null",
      "endTime" : "Wed Oct 11 04:41:14 PDT 2017",
      "tag" : "/scratch/smith/view_storage/smith_tfa_latest/oracle/log/tfa/repository/TFA_T1",
      "zipFileName" : "myhost.TFA_T1.zip",
      "componentList" : "[]",
      "zipFileSize" : 0,
      "collectionTime" : 0,
      "events" : null
    }]

**Parent topic:** REST Service print API

#### 16.3.6 config

Use GET requests to print the configuration details of all hosts.

##### Syntax

    /tfactl/print/config

Example 16-6 config

    [ {
      "hostname" : "myhost",
      "tfaVersion" : "18.1.0.0.0",
      "javaVersion" : "1.8",
      "inventoryTraceLevel" : 1,
      "collectionTraceLevel" : 1,
      "scanTraceLevel" : 1,
      "otherTraceLevel" : 3,
      "currentSizeMB" : 13,
      "maxSizeMB" : 10240,
      "maxLogSize" : 50,
      "maxLogCount" : 10,
      "maxCoreFileSize" : 50,
      "maxCoreCollectionSize" : 500,
      "minSpaceForRTScan" : 500,
      "diskUsageMoninterInterval" : 60,
      "manageLogsAutoPurgeInterval" : 60,
      "manageLogsAutoPurgePolicyAge" : "30d",
      "minFileAgeToPurge" : 12,
      "language" : "en",
      "encoding" : "UTF-8",
      "country" : "US",
      "alertLogLevel" : "ALL",
      "userLogLevel" : "ALL",
      "baseLogPath" : "ERROR",
      "tfaIpsPoolSize" : 5,
      "autoPurge" : true,
      "publicIp" : false,
      "fireZipsInRT" : true,
      "rtscan" : true,
      "diskUsageMonOn" : true,
      "manageLogsAutoPurgeOn" : false,
      "trimmingOn" : true
    } ]

**Parent topic:** REST Service print API

#### 16.3.7 protocols

Use GET requests to print the details of protocols of all hosts.

##### Syntax

    /tfactl/print/protocols

Example 16-7 protocols

    {
      "hostname" : "myhost",
      "available" : [ "TLSv1.2" ],
      "restricted" : [ "SSLv3", "SSLv2Hello", "TLSv1", "TLSv1.1" ]}

**Parent topic:** REST Service print API

#### 16.3.8 directories

Use GET requests to print the details of directories of all hosts.

##### Syntax

    /tfactl/print/directories

Example 16-8 directories

    [ {
      "hostname" : "myhost",
      "directory" : "/oem/app/oracle/product/emagent/agent_inst/install/logs",
      "components" : [ "EMPLUGINS" ],
      "permission" : "public",
      "owner" : "root",
      "collectionPolicy" : "exclusions",
      "collectAll" : false
    }, {
      "hostname" : "myhost",
      "directory" : "/oem/app/oracle/product/emagent/agent_inst/sysman/log",
      "components" : [ "EMAGENT" ],
      "permission" : "public",
      "owner" : "root",
      "collectionPolicy" : "exclusions",
      "collectAll" : false
    } ]

**Parent topic:** REST Service print API

### 16.4 REST Service diagcollect API

Learn to use the REST Service `diagcollect` API.

- diagcollect
  Use POST requests to view collection details.

**Parent topic:** REST Service

#### 16.4.1 diagcollect

Use POST requests to view collection details.

##### Syntax

    /tfactl/diagcollect

##### Returns

Oracle Trace File Analyzer default collection for last 12 hours for all components.

Or, Oracle Trace File Analyzer collection per JSON data as parameters specified.

Example 16-9 diagcollect–default collection

    {
      "collectionId" : "20180111011121slc12ekf",
      "zipName" : "TFA_DEF_ZIP_20180111011121",
      "tagName" : "TFA_DEF_TAG_20180111011121"
    }

Example 16-10 diagcollect–JSON data as Parameters

Input:

    [{
      "components": "-database -asm -tns -crs -acfs -install -cfgtools -os",
      "timePeriod": "-since n[d|h] | -last n[d|h] | -for date |
            -from date -to date",
      "tagName": "crs_crash_collection",
      "nodeList": "node1,node2",
      "options": "-nocopy | -notrim | -silent | -nocores |
           -collectalldirs | -collectdir dir1,dir2..."
    }]

Output:

    [{
      "collectionId" : "20180111011121slc12ekf",
      "zipName" : "TFA_DEF_ZIP_20180111011121",
      "tagName" : "TFA_DEF_TAG_20180111011121"
    }]

**Parent topic:** REST Service diagcollect API

### 16.5 REST Service download API

Learn to use the REST Service `download` API.

- download
  Use GET requests to download collection ZIP file for a specific collection ID.

**Parent topic:** REST Service

#### 16.5.1 download

Use GET requests to download collection ZIP file for a specific collection ID.

##### Syntax

    /tfactl/download/{collectionid}

##### Returns

Collection ZIP file for the collection ID specified.

##### Usage Notes

Specify the collection ID for which you want to download the collection ZIP file.

**Parent topic:** REST Service download API

### 16.6 REST Service run API

Learn to use REST Service `run` API.

- alertsummary
  Use GET requests to run the `alertsummary` command.
- calog
  Use GET requests to run the `calog` command.
- changes
  Use GET requests to run the `changes` command.
- events
  Use GET requests to run the `events` command.
- history
  Use GET requests to run the `history` command.

**Parent topic:** REST Service

#### 16.6.1 alertsummary

Use GET requests to run the `alertsummary` command.

##### Syntax

    /tfactl/run/alertsummary

##### Returns

Runs the `alertsummary` command and returns the alert summary.

Example 16-11 alertsummary

    [ {
      "line" : "Output from host : myserver"
    }, {
      "line" : "------------------------------"
    }, {
      "line" : "Reading /scratch/app/oradb/diag/rdbms/apxcmupg/apxcmupg_2/trace/alert_apxcmupg_2.log"
    }, {
      "line" : "+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-"
    }, {
      "line" : "------------------------------------------------------------------------"
    }, {
      "line" : "Oct 20 08:20:43 Database started"
    }, {
      "line" : "------------------------------------------------------------------------"
    }, {
      "line" : "Nov 05 20:27:50 Database started"
    },
    ....
    ....

**Parent topic:** REST Service run API

#### 16.6.2 calog

Use GET requests to run the `calog` command.

##### Syntax

    /tfactl/run/calog

**Parent topic:** REST Service run API

#### 16.6.3 changes

Use GET requests to run the `changes` command.

##### Syntax

    /tfactl/run/changes

Example 16-12 changes

    [ {
      "line" : "Output from host : myserver"
    }, {
      "line" : "------------------------------"
    }, {
      "line" : "[Jul/25/2018 03:45:15.325]: Parameter: fs.aio-nr: Value: 276224 => 277760"
    }, {
      "line" : "[Jul/25/2018 03:45:15.325]: Parameter: kernel.random.entropy_avail: Value: 192 => 152"
    }, {
      "line" : "[Jul/25/2018 03:45:15.325]: Parameter: kernel.random.uuid:
    Value: 5eac06d7-560a-466d-a035-efe836fe0b57 => 3f329d9c-25d3-4057-ab00-17d031645490"
    }, {
      "line" : "[Jul/25/2018 15:46:15.325]: Parameter: fs.aio-nr: Value: 277760 => 279296"
    },
    ....
    ....

**Parent topic:** REST Service run API

#### 16.6.4 events

Use GET requests to run the `events` command.

##### Syntax

    /tfactl/run/events

Example 16-13 events

    [ {
      "line" : "Output from host : myserver"
    }, {
      "line" : "------------------------------"
    }, {
      "line" : "Event Summary:"
    }, {
      "line" : "INFO    :0"
    }, {
      "line" : "ERROR   :0"
    }, {
      "line" : "WARNING :0"
    }, {
      "line" : "Event Timeline:"
    }, {
      "line" : "No Events Found"
    } ]

**Parent topic:** REST Service run API

#### 16.6.5 history

Use GET requests to run the `history` command.

##### Syntax

    /tfactl/run/history

**Parent topic:** REST Service run API

### 16.7 REST Service user API

Learn to use REST Service `user` API.

- add
  Use POST requests to add users to Oracle Trace File Analyzer REST Services.
- delete
  Use POST requests to delete an Oracle Trace File Analyzer REST Services user.
- update
  Use POST requests to update the password of an Oracle Trace File Analyzer REST Services user.

**Parent topic:** REST Service

#### 16.7.1 add

Use POST requests to add users to Oracle Trace File Analyzer REST Services.

##### Syntax

    /tfactl/user/add

Example 16-14 add

Input:

    {
      "userName" : "test",
      "password" : "test"
    }

Output:

    {
      "status": "SUCCESS",
      "message": "Successfully added test to TFA REST Services"
    }

**Parent topic:** REST Service user API

#### 16.7.2 delete

Use POST requests to delete an Oracle Trace File Analyzer REST Services user.

##### Syntax

    /tfactl/user/delete

Example 16-15 delete

Input:

    {
      "userName" : "test"
    }

Output:

    {
      "status": "SUCCESS",
      "message": "Successfully removed test from TFA REST Services"
    }

**Parent topic:** REST Service user API

#### 16.7.3 update

Use POST requests to update the password of an Oracle Trace File Analyzer REST Services user.

##### Syntax

    /tfactl/user/update

Example 16-16 update

Input:

    {
      "password" : "test"
    }

Output:

    {
      "status": "SUCCESS",
      "message": "Successfully updated users's profile in TFA"
    }

**Parent topic:** REST Service user API
