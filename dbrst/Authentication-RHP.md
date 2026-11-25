For using Fleet Patching and Provisioning REST APIs, perform the following steps:

1.  Register a REST user

    To register a REST user associated to the CRS user, run the following command:

    `rhpctl register user -user <restUserName> -restuser -email <useremail> -rhpuser <crsUser>`

    In response to the preceding command, you will be prompted for a password.
    **Note:**

    CRS user is the user you used to setup Fleet Patching and Provisioning or any user with similar role and permission.
    Where:
    - The `<restUserName> ` option is the name used to authenticate each REST request sent to the Fleet Patching and Provisioning Server.

    - The `<useremail> `option is the email address where the notifications will be sent if enabled.

    - The `<crsUser> `option is the name of a user with similar role and permissions to perform the Fleet Patching and Provisioning operations.

    Example:

    To register a REST user called` rest` with the email id `rest@email.com` associated to the CRS user, log on to the Fleet Patching and Provisioning server as the CRS user, and run the following command:

    `$ $ORACLE_HOME/bin/rhpctl register user -user rest -restuser -email rest@email.com -rhpuser $USER`

2.  Enable HTTPS on the Fleet Patching and Provisioning server.:

    For Fleet Patching and Provisioning REST APIs, the certificate is obtained directly from the Fleet Patching and Provisioning server. HTTPS is enabled by default on the Fleet Patching and Provisioning server.

    If HTTPS is not enabled on the Fleet Patching and Provisioning server, then log on to the Fleet Patching and Provisioning server and perform the following steps:

    1.  Stop Fleet Patching and Provisioning server.

        `$ $ORACLE_HOME/bin/srvctl stop rhpserver`

    2.  Enable HTTPS on the Fleet Patching and Provisioning server.

        `$ $ORACLE_HOME/bin/srvctl modify rhpserver -enableHTTPS YES`

    3.  Start Fleet Patching and Provisioning server.

        ` $ $ORACLE_HOME/bin/srvctl start rhpserver`

3.  Export Fleet Patching and Provisioning REST API certificate if HTTPS is enabled.

    You can perform this task if you are logged on to the Fleet Patching and Provisioning server as the `CRS User` or any user with similar role or permissions.

    1.  Change directory to a path where the user has write permissions to export the certificate.

        `$ cd ~`

    2.  Run the following command:

        `$ $ORACLE_HOME/bin/crskeytoolctl -printrootcert`

        Cluster root public certificate is printed to file: `<ClusterGUID.pem>`.

        **Note:**

        The certificate is created every time the Fleet Patching and Provisioning server is started. All clients must update its certificate every time the Fleet Patching and Provisioning server is started.

4.   Verify the working of Fleet Patching and Provisioning REST API.

    To verify the working of Fleet Patching and Provisioning REST API, you will need the Fleet Patching and Provisioning server host name which will be used in all REST requests, and the user and password of the registered user (as explained in Step 2).

    1.  Set the environment variable `CURL_CA_BUNDLE` with the absolute path to the `pem` certificate exported using the following command:

        `$ export CURL_CA_BUNDLE=/home/crsUser/<clusterGUID>.pem`
        **Note:**

        To remove the environment variable run the following command :
        `$ unset CURL_CA_BUNDLE`

    2.  If you want to find the name of the node where Fleet Patching and Provisioning server is running, then run the following command:

        `$ $ORACLE_HOME/bin/srvctl status rhpserver`

        In response, you will get the name of the node and the status of Fleet Patching and Provisioning server.

    3.  Using the following cURL command, query the working copies. This will prompt you for the user password:

        `curl -u <restUser> http://<RHPServerHostName>:8894/rhp-restapi/rhp/workingcopies`

        Example:

        To get the names of the working copies, log on to the Fleet Patching and Provisioning server and run the following command:

        `$ curl -u rest https://$HOSTNAME:8894/rhp-restapi/rhp/workingcopies`

        This will prompt you for the password:

        `Enter host password for user "rest":`

        Enter the password, and in response you get the names of the working copies available in the Fleet Patching and Provisioning server. If there are no working copies, then you get an empty items array in response:

        `{"items":[ ]}`.
