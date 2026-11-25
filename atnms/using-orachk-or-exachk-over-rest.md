Oracle ORAchk and Oracle EXAchk include full REST support allowing invocation and query over HTTPS.

- Enabling REST
  To facilitate REST support, Oracle REST Data Services (ORDS) is included within the install.
- start_client
  Use GET requests to run a normal health check run.
- start_client
  Use POST requests to run a normal health check run using specific arguments.
- profile
  Use GET requests to run a health check run for the specified profiles.
- check
  Use GET requests to run a health check run for the specified check IDs.
- status
  Use GET requests to report the status on the specified job ID.
- download
  Use GET requests to download the collection result for the specified job ID.
- checktfaupload
  Use GET requests to report if a connection can be made to upload to Oracle Trace File Analyzer service.
- checktfafaileduploads
  Use GET requests to report if any Oracle Trace File Analyzer service uploads failed.
- gettfaupload
  Use GET requests to report the Oracle Trace File Analyzer service upload settings.
- unsettfaupload
  Use GET requests to unset all of the Oracle Trace File Analyzer service upload settings, or a particular setting.
- uploadtfafailed
  Use GET requests to reattempt to upload all previously failed uploads to Oracle Trace File Analyzer service.
- showrepair
  Use GET requests to report the repair command for the specified check.
- getinfo
  Use GET requests to report the status of the specified job ID.
- start_client
  Use POST requests to run a diff of the specified collection results.
- Removing ORDS Setup

**Parent topic:** [Analyzing Risks and Complying with Best Practices](purpose-oracle-orachk-and-oracle-exachk.md)

### 2.12.1 Enabling REST

To facilitate REST support, Oracle REST Data Services (ORDS) is included within the install.

1.  To enable REST, setup ORDS and then provide a user password when prompted.
        ./orachk -ordssetup
        ./exachk -ordssetup
2.  Start the daemon using the `-ords` option:
        ./orachk -d start -ords
        ./exachk -d start -ords

    **Note:**

    Only the `root` user can start the daemon with ORDS support.

    As ORDS support requires the daemon, ORDS is available only on platform (Linux) with daemon support.

**Parent topic:** Using Oracle ORAchk or Oracle EXAchk over REST

### 2.12.2 start_client

Use GET requests to run a normal health check run.

#### Syntax

    /start_client

#### Returns

Returns JSON showing the job ID similar to:

    [{
    "ID":"UCTW5MLN7O1V1HPG8U",
    "Status":"SUBMITTED"
    }]

#### Usage Notes

You need not provide input to use this API.

Example 2-2 start_client

    -bash-4.2$ curl -i -X GET -k -u ordsadmin:adminpass
    https://node1.example.com:7080/ords/tfaml/orachk/start_client

    HTTP/1.1 200 OK Date: Thu, 05 Apr 2018 11:53:14 GMT Content-Type: text/html X-Frame-Options:
    SAMEORIGIN Transfer-Encoding: chunked Server: Jetty(9.2.z-SNAPSHOT)
    [{"ID":"UCTW5MLN7O1V1HPG8U","Status":"SUBMITTED"}]

**Parent topic:** Using Oracle ORAchk or Oracle EXAchk over REST

### 2.12.3 start_client

Use POST requests to run a normal health check run using specific arguments.

#### Syntax

    /start_client

#### Returns

Returns JSON showing the job ID similar to:

    [{ "ID":"UCTW5MLN7O1V1HPG8U", "Status":"SUBMITTED" }]

#### Usage Notes

Specify any Oracle ORAchk or Oracle EXAchk arguments and their corresponding values.

Example 2-3 JSON input

    [{
    "-clusternodes":"busm1c1,busm1c2",
    "-ibswitches":"busm1sw-ibs0,busm1sw-iba0,busm1sw-ibb0"
    }]

Example 2-4 start_client

    -bash-4.2$ curl -i -X POST -H "Content-Type: application/json" -k -u ordsadmin:adminpass
    https://host:7080/ords/tfaml/orachk/start_client -d '[{"-clusternodes":"busm1c1,busm1c2","-ibswitches":"busm1sw-ibs0,busm1sw-iba0,busm1sw-ibb0"}]

**Parent topic:** Using Oracle ORAchk or Oracle EXAchk over REST

### 2.12.4 profile

Use GET requests to run a health check run for the specified profiles.

#### Syntax

    /profile/{profile1}/{profile2}

#### Returns

Returns JSON showing the job ID similar to:

    [{ "ID":"DMBLMBTB2M2H1QCQIS", "Status":"SUBMITTED" }]

#### Usage Notes

Specify a profile, or a list of profiles delimited by forward slash (/).

Example 2-5 profile

    -bash-4.2$ curl -i -X GET -k -u ordsadmin:adminpass
    https://node1.example.com:7080/ords/tfaml/orachk/profile/asm

    HTTP/1.1 200 OK Date: Thu, 05 Apr 2018 10:50:00 GMT Content-Type: text/html X-Frame-Options:
    SAMEORIGIN Transfer-Encoding: chunked Server: Jetty(9.2.z-SNAPSHOT)
    [{"ID":"DMBLMBTB2M2H1QCQIS","Status":"SUBMITTED"}]

**Parent topic:** Using Oracle ORAchk or Oracle EXAchk over REST

### 2.12.5 check

Use GET requests to run a health check run for the specified check IDs.

#### Syntax

    /check/{check_id1,check_id2}

#### Returns

Returns JSON showing the job ID similar to:

    [{ "ID":"B2PKK9RR9M7MYJPRN8", "Status":"SUBMITTED" }]

#### Usage Notes

Specify a profile, or a comma-delimited list of check IDs.

Example 2-6 check

    -bash-4.2$ curl -i -X GET -k -u ordsadmin:adminpass
    https://node1.example.com:7080/ords/tfaml/orachk/check/E94589BC1AC24CFBE04312C0E50A3849

    HTTP/1.1 200 OK Date: Thu, 05 Apr 2018 10:53:48 GMT Content-Type: text/html X-Frame-Options:
    SAMEORIGIN Transfer-Encoding: chunked Server: Jetty(9.2.z-SNAPSHOT)
    [{"ID":"B2PKK9RR9M7MYJPRN8","Status":"SUBMITTED"}]

**Parent topic:** Using Oracle ORAchk or Oracle EXAchk over REST

### 2.12.6 status

Use GET requests to report the status on the specified job ID.

#### Syntax

    /status/{job_id}

#### Returns

Returns JSON showing the job ID similar to:

    [{ "Status of DMBLMBTB2M2H1QCQIS is SUBMITTED" }]

The status moves from `SUBMITTED` to `RUNNING` to `COMPLETED`.

#### Usage Notes

Specify the job ID for which you want to find the status.

Example 2-7 status

    -bash-4.2$ curl -i -X GET -k -u ordsadmin:adminpass
    https://node1.example.com:7080/ords/tfaml/orachk/status/DMBLMBTB2M2H1QCQIS

    HTTP/1.1 200 OK Date: Thu, 05 Apr 2018 10:51:16 GMT Content-Type: text/html X-Frame-Options:
    SAMEORIGIN Transfer-Encoding: chunked Server: Jetty(9.2.z-SNAPSHOT)
    [{"Status of DMBLMBTB2M2H1QCQIS is SUBMITTED"}]

**Parent topic:** Using Oracle ORAchk or Oracle EXAchk over REST

### 2.12.7 download

Use GET requests to download the collection result for the specified job ID.

#### Syntax

    /download/{job_id}

#### Returns

Returns the zip binary for the collection result.

#### Usage Notes

Specify the job ID for which you want to download the collection result.

If you specify a purged ID or an invalid ID, then the error message will be in the downloaded file.

Example 2-8 download

    -bash-4.2$ curl -X GET -k -u ordsadmin:adminpass
    https://node1.example.com:7080/ords/tfaml/orachk/download/DMBLMBTB2M2H1QCQIS -J -O

    % Total % Received % Xferd Average Speed Time Time Time Current Dload Upload Total Spent Left Speed 100 1385k 0 1385k 0 0 901k
    0 --:--:-- 0:00:01 --:--:-- 901k curl: Saved to filename 'exachk_busm01client01_PDB1_040518_035118_DMBLMBTB2M2H1QCQIS.zip'

**Parent topic:** Using Oracle ORAchk or Oracle EXAchk over REST

### 2.12.8 checktfaupload

Use GET requests to report if a connection can be made to upload to Oracle Trace File Analyzer service.

#### Syntax

    /checktfaupload

#### Returns

Returns JSON similar to:

    [{ "ID":"ZFZLH06WOLE3L92PQI", "Status":"SUBMITTED" }]

#### Usage Notes

Use the `status` API to query the status of the submitted job.

Use the `getinfo` API to view the Oracle Trace File Analyzer upload status once the status of submitted API is `COMPLETED`.

Example 2-9 getinfo

With `getinfo`, returns:

    [{"Msg":"Environment is not set for uploading results to TFA."}]

**Parent topic:** Using Oracle ORAchk or Oracle EXAchk over REST

### 2.12.9 checktfafaileduploads

Use GET requests to report if any Oracle Trace File Analyzer service uploads failed.

#### Syntax

    /checktfafaileduploads

#### Returns

If no collection failed to upload, then returns:

    [{ "Msg":"There are no Failed collections under ORDS directory." }]

Or, prints the list of collections that failed to upload.

#### Usage Notes

You need not provide input to use this API.

Example 2-10 checktfafaileduploads

    bash-4.1# curl -i -X GET -k -u ordsadmin:adminpass
    https://node1.example.com:7080/ords/tfaml/orachk/checktfafaileduploads
    HTTP/1.1 200 OK
    Date: Thu, 19 Jul 2018 10:04:58 GMT
    Content-Type: text/html
    X-Frame-Options: SAMEORIGIN
    Transfer-Encoding: chunked

    [{"Msg":"There are no Failed collections under ORDS directory."}]

**Parent topic:** Using Oracle ORAchk or Oracle EXAchk over REST

### 2.12.10 gettfaupload

Use GET requests to report the Oracle Trace File Analyzer service upload settings.

#### Syntax

    /gettfaupload

#### Returns

Lists the values of three environment variables: `RAT_TFA_URL`, `RAT_TFA_USER`, and `RAT_TFA_PASSWORD`.

#### Usage Notes

You need not provide input to use this API.

Example 2-11 gettfaupload

    bash-4.1# curl -i -X GET -k -u ordsadmin:adminpass
    https://node1.example.com:7080/ords/tfaml/orachk/gettfaupload
    HTTP/1.1 200 OK
    Date: Thu, 19 Jul 2018 10:07:24 GMT
    Content-Type: text/html
    X-Frame-Options: SAMEORIGIN
    Transfer-Encoding: chunked

    RAT_TFA_URL =  https://tfa.us.oracle.com/tfa/ws/orachk/
    RAT_TFA_USER =  orachkadmin
    RAT_TFA_PASSWORD = ********

After `unsettfaupload` API, use the `gettfaupload` API to recheck the values:

    -bash-4.1# curl -i -X GET -k -u ordsadmin:adminpass
    https://node1.example.com:7080/ords/tfaml/orachk/gettfaupload
    HTTP/1.1 200 OK
    Date: Thu, 19 Jul 2018 10:10:10 GMT
    Content-Type: text/html
    X-Frame-Options: SAMEORIGIN
    Transfer-Encoding: chunked

    RAT_TFA_URL is not set in the wallet
    RAT_TFA_USER is not set in the wallet
    RAT_TFA_PASSWORD is not set in the wallet

**Parent topic:** Using Oracle ORAchk or Oracle EXAchk over REST

### 2.12.11 unsettfaupload

Use GET requests to unset all of the Oracle Trace File Analyzer service upload settings, or a particular setting.

#### Syntax

    /unsettfaupload/all
    /unsettfaupload/RAT_TFA_USER

#### Returns

Returns JSON showing the job ID similar to:

    [{ "ID":"ZFZLH06WOLE3L92PQI", "Status":"SUBMITTED" }]

#### Usage Notes

Specify `all` to unset all of the three environment variables, `RAT_TFA_URL`, `RAT_TFA_USER`, and `RAT_TFA_PASSWORD` or, just specify an environment variable to unset it.

Example 2-12 unsettfaupload

    -bash-4.1# curl -i -X GET -k -u ordsadmin:adminpass
    https://node1.example.com:7080/ords/tfaml/orachk/unsettfaupload/all
    HTTP/1.1 200 OK
    Date: Thu, 19 Jul 2018 10:08:30 GMT
    Content-Type: text/html
    X-Frame-Options: SAMEORIGIN
    Transfer-Encoding: chunked

    [{"ID":"Z8P9DHA8VV3PUOVQTV","Status":"SUBMITTED"}]

**Parent topic:** Using Oracle ORAchk or Oracle EXAchk over REST

### 2.12.12 uploadtfafailed

Use GET requests to reattempt to upload all previously failed uploads to Oracle Trace File Analyzer service.

#### Syntax

    /uploadtfafailed/all

#### Returns

Returns JSON showing the job ID similar to:

    [{ "ID":"ZFZLH06WOLE3L92PQI", "Status":"SUBMITTED" }]

#### Usage Notes

You need not provide input to use this API.

Example 2-13 uploadtfafailed

    -bash-4.1# curl -i -X GET -k -u ordsadmin:adminpass
    https://node1.example.com:7080/ords/tfaml/orachk/uploadtfafailed/all
    HTTP/1.1 200 OK
    Date: Thu, 19 Jul 2018 10:09:18 GMT
    Content-Type: text/html
    X-Frame-Options: SAMEORIGIN
    Transfer-Encoding: chunked

    [{"ID":"0B9O04CKSYZNUZCYZD","Status":"SUBMITTED"}]

**Parent topic:** Using Oracle ORAchk or Oracle EXAchk over REST

### 2.12.13 showrepair

Use GET requests to report the repair command for the specified check.

#### Syntax

    /showrepair/{check_id}

#### Returns

Returns JSON showing the job ID similar to:

    [{ "ID":"ZFZLH06WOLE3L92PQI", "Status":"SUBMITTED" }]

#### Usage Notes

Specify the check ID for which you want to report the repair command.

Example 2-14 showrepair

    -bash-4.1# curl -i -X GET -k -u ordsadmin:adminpass
    https://node1.example.com:7080/ords/tfaml/orachk/showrepair/9ECBA2152E92F6B1E040E50A1EC00DFB
    HTTP/1.1 200 OK
    Date: Thu, 19 Jul 2018 10:13:54 GMT
    Content-Type: text/html
    X-Frame-Options: SAMEORIGIN
    Transfer-Encoding: chunked

    [{"ID":"FJELUT7XYM3AKOE1R4","Status":"SUBMITTED"}]

    -bash-4.1# curl -i -X GET -k -u ordsadmin:adminpass
    https://node1.example.com:7080/ords/tfaml/orachk/status/FJELUT7XYM3AKOE1R4
    HTTP/1.1 200 OK
    Date: Thu, 19 Jul 2018 10:15:00 GMT
    Content-Type: text/html
    X-Frame-Options: SAMEORIGIN
    Transfer-Encoding: chunked

    [{"Msg":"Status of FJELUT7XYM3AKOE1R4 is  COMPLETED"}]

**Parent topic:** Using Oracle ORAchk or Oracle EXAchk over REST

### 2.12.14 getinfo

Use GET requests to report the status of the specified job ID.

#### Syntax

    /getinfo/{job_id}

#### Returns

Returns JSON similar to if the ID does not exist:

    [{ "Status":"Either the ID entered is invalid or the wallet has been purged." }]

Or, returns the repair command if the ID exists.

#### Usage Notes

Specify the job ID for which you want to check the status.

Example 2-15 getinfo

    -bash-4.1# curl -i -X GET -k -u ordsadmin:adminpass
    https://node1.example.com:7080/ords/tfaml/orachk/getinfo/FJELUT7XYM3AKOE1R4 HTTP/1.1 200 OK Date: Thu, 19 Jul 2018 10:15:34 GMT
    Content-Type: text/html X-Frame-Options: SAMEORIGIN Transfer-Encoding: chunked

Repair Command:

    alter database datafile '+DATAC1/RAC12C/DATAFILE/sysaux.314.936528199' autoextend on maxsize unlimited;

**Parent topic:** Using Oracle ORAchk or Oracle EXAchk over REST

### 2.12.15 start_client

Use POST requests to run a diff of the specified collection results.

#### Syntax

    /start_client

#### Returns

Returns JSON similar to:

    [{ "ID":"ZFZLH06WOLE3L92PQI", "Status":"SUBMITTED" }]

The status API can be used to query the status of the submitted job ID. Then you can use the download API to download diff report using the same job ID.

#### Usage Notes

JSON input:

    [{ "-diff":"collection_zip_1 collection_zip_2" }]

Example 2-16 start_client

    -bash-4.2$ curl -i -X POST -H "Content-Type: application/json" -k -u ordsadmin:adminpass
    https://host:7080/ords/tfaml/orachk/start_client -d '[{"-diff":"orachk_myhost69_apxcmupg_062118_025029_N1O498NX877LYO5FE3.zip
    orachk_myhost69_apxcmupg_062118_030527_ICMOWECU1UKF0R0VTO.zip"}]'

**Parent topic:** Using Oracle ORAchk or Oracle EXAchk over REST

### 2.12.16 Removing ORDS Setup

1.  To completely remove ORDS setup:
        ./orachk -ordsrmsetup ./exachk -ordsrmsetup

    The command option `-ordsrmsetup` stops the daemon if it is running and then stops the ORDS service.

**Parent topic:** Using Oracle ORAchk or Oracle EXAchk over REST
