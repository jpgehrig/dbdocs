## 33 Oracle Secure Backup Cloud Module for Amazon S3

The Oracle Secure Backup (OSB) Cloud Module enables you to take advantage of internet-based data storage services offered by Amazon Simple Storage Service (S3) for RMAN backup and recovery tasks.

### 33.1 About Backup on the Cloud Using Oracle Secure Backup Cloud Module

The Oracle Secure Backup Cloud Module is part of the Oracle Secure Backup product family and provides the flexibility to back up your Oracle Database to the Amazon S3 Cloud and to tape. With this cloud offering, local disk backups are sent directly to Amazon S3 for offsite storage and are fully integrated with Recovery Manager (RMAN) features.

The Oracle Secure Backup Cloud Module efficiently handles the backing up of Oracle Databases to S3 storage. In addition, Oracle Secure Backup Cloud Module backups work with tools like Oracle Enterprise Manager and your customized RMAN scripts. The Oracle Secure Backup Cloud Module does not back up operating system files.

The Oracle Secure Backup Cloud Module uses the RMAN SBT (System Backup to Tape) interface to extend the Amazon S3 functionality for Oracle backup operations. The Oracle Secure Backup Cloud Module offers an easy-to-manage, cost efficient, and scalable alternative to maintaining in-house data storage and managing a local, fully configured backup infrastructure.

The Oracle Secure Backup Cloud Module has several advantages over traditional tape-based off site backups:

- Continuous Accessibility

  Oracle Secure Backup Cloud Module backups stored on Amazon S3 storage are always accessible. The cloud storage services availability and access model helps an organization to streamline recovery operations. For example, there is no need to ship or load tapes before a restore can be performed. You can still use familiar and standard tools like Enterprise Manager and your organization's current scripts continue to execute backup and restore tasks. With the ability to continually and easily access backups, the time spent restoring backups may be substantially reduced.

- Improved Reliability

  Because S3 storage is disk based, it is inherently more reliable than tape media. Internet storage service providers keep multiple, redundant copies of your data for availability and scalability purposes and the benefit of this practice to your organization and your data is increased reliability.

**Note:**

The Oracle Secure Backup Cloud Module for Amazon S3 is compatible with Oracle Databases deployed on-premises or on Amazon EC2. Support for writing backups to Amazon S3 for Oracle Database Cloud Services is not available.

**Related Topics**

- [FAQs about the Oracle Secure Backup Cloud Module - My Oracle Support Note 740226.1](https://support.oracle.com/epmos/faces/DocumentDisplay?_afrLoop=308982001105082&id=740226.1&_afrWindowMode=0&_adf.ctrl-state=16uqntsdf0_4)

### 33.2 Sign-up for an Amazon S3 - AWS Account

Before you can use the Oracle Secure Backup Cloud Backup Module and access Amazon S3, you must create an AWS account. The account requires that you provide a means of payment for Amazon to charge for your AWS S3 usage.

Use this procedure to create an AWS account and obtain the AWS account credentials.

1.  Visit <https://aws.amazon.com/> to create an AWS account.
2.  After you log in to your AWS account, click My Account and select Security Credentials to obtain your account details.
3.  Use one of these methods to authenticate and access Amazon S3.
    - AWS Identifiers

      You obtain these credentials by going to the AWS website at [`http://aws.amazon.com`](http://aws.amazon.com), selecting My Account, and then AWS Management Console.

      You need the following mandatory AWS identifiers that are assigned when you create your AWS account: Access Key ID and Secret Access Key.

      Note: It is a good idea to secure these credentials since they authorize charges for all Amazon Web Services and enable access to RMAN backups stored on Amazon S3.

    - AWS IAM Role

      Enables Amazon Elastic Cloud Compute (EC2) instance users to leverage the metadata service. When the EC2 instance is configured with an IAM role, applications running on EC2 can use temporary credentials associated with the IAM role to create backups to Amazon S3. EC2 stores the temporary credentials in a predetermined location in JSON format. The installer retrieves the temporary credentials and stores them in the Oracle wallet.

      The IAM role must have the privileges required to access Amazon S3.

      Provide the following parameters to use IAM roles:
      - `IAMRole` (mandatory) - The AWS IAM Role name
      - `IAMRoleMetaURI` (optional) - Metadata URI for the specified IAM Role

      The OSB Cloud Module uses the Instance Metadata Service (IMDS) to access the instance metadata from an Amazon EC2 instance. IMDS is available in two versions: `IMDSv1` and `IMDSv2`. By default, the OSB Cloud Module uses `IMDSv2` to support enhanced security for metadata access. If `IMDSv2` is not accessible, then the OSB Cloud Module automatically falls back to use `IMDSv1`.

    **Note:**

    See [IAM Roles for Amazon EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html) for more information.

### 33.3 Installing the Oracle Secure Backup Cloud Module

Before you backup to Amazon S3 Cloud, you need to install the Oracle Secure Backup (OSB) Cloud Module on the target database server. The backup module installer file `osbws_installer.zip` is available in the Oracle home directory after you install the Oracle Database.

Table 33-1 File Name and Location of the OSB Cloud Module Installer

| OSB Cloud Module Installer File Name | Location on UNIX and Linux Systems | Location on Windows Systems |
|:-------------------------------------|:-----------------------------------|:----------------------------|
| `osbws_installer.zip`                | `$ORACLE_HOME/lib`                 | `%ORACLE_HOME%\lib`         |

**Note:**

For Oracle Database 19c Release Update version 26 (19.26) and earlier versions, download the operating system-specific cloud backup modules from [My Oracle Support Patch Number 37855779](https://support.oracle.com/epmos/faces/ui/patch/PatchDetail.jspx?patchId=37855779).

Run the backup module installer to set up the authentication required for RMAN to access the cloud storage. You must use the SBT library included with the patch instead of downloading the library while running the installer.

#### 33.3.1 Prerequisites for Oracle Secure Backup Cloud Module

You can backup Oracle Database 9i Release 2 and higher to Amazon S3 Cloud.

The following table lists the supported database versions, operating systems, and prerequisites for using the Oracle Secure Backup Cloud Module.

Table 33-2 Software Prerequisites for the Oracle Secure Backup Cloud Module

| Hardware/Software             | Version                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|:------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Java SE Development Kit (JDK) | Default JDK version supported by the target Oracle Database release.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| Oracle Database               | You can backup databases starting with Oracle Database 9`i` Release 2 or later to Amazon S3 Cloud.<br>Note: Operating system files cannot be backed up with RMAN or the RMAN SBT interface.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| S3 Backup Installer File      | `osbws_install.jar`<br>The installer creates the configuration file and the Oracle wallet to store the AWS credentials.<br>After you install Oracle Database 23ai, you can access the OSB Cloud Module installer file `osbws_installer.zip` from the Oracle home directory (See Table 33-1).<br>However, if you are using Oracle provided Amazon Machine Images (AMIs) to run the Oracle Database on Amazon's Elastic Compute Cloud (EC2), then the installer can be found in the `/home/oracle/scripts` directory.<br>Oracle recommends that users include any of the command-line options in a file and secure the file with appropriate operating system permissions. The S3 Backup Installer can then read the file, invoke the options, and prohibit unauthorized users from reading the file. |
| Oracle Wallet Directory       | The Oracle Wallet Directory stores your AWS identifiers and must exist before you can run the S3 Backup installer. If you have not set up a wallet directory then you must create one.<br>Here are the suggested platform-specific locations for the wallet directory:<br>• Linux: `$ORACLE_HOME/dbs/osbws_wallet`<br>• Windows: `%ORACLE_HOME%\database\osbws_wallet`                                                                                                                                                                                                                                                                                                                                                                                                                              |
| System Time                   | The authentication method used by Amazon S3 relies on the client system time being similar to the Amazon S3 time. In this case, the client is the computer where you run the OSB Cloud Module. S3 time is Coordinated Universal Time (UTC), so you must ensure that the system time on your client is within a few minutes of UTC.                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |

#### 33.3.2 Parameters for Installing the Oracle Secure Backup Cloud Module

Review the mandatory parameters and compile their values before installing the Oracle Secure Backup Cloud Module.

After you install the Oracle Database, the OSB Cloud Module installer zip file `osbws_installer.zip ` is available in the Oracle home directory (see Table 33-1).

Extract the `osbws_installer.zip` file to a subdirectory of your choice and preview the installation parameters.

Example 33-1 Extracting the OSB Cloud Module Installer Files and Previewing the Installation Parameters (on UNIX and Linux Systems)

In this example, you extract the contents of the `osbws_installer.zip` file to a subdirectory of your choice.

    $ mkdir -p $ORACLE_HOME/lib/osbws_1
    $ cd $ORACLE_HOME/lib/osbws_1
    unzip -q $ORACLE_HOME/lib/osbws_installer.zip

To preview the installation parameters, run this command from the subdirectory that contains the extracted installer files.

    % java -jar osbws_install.jar

Table 33-3 Parameters Used when Installing the OSB Cloud Module Library

| Parameter Name   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | Mandatory?                                                      |
|:-----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------|
| `AWSID`          | Access Key ID for the Amazon Web Services account that is used to store RMAN backups.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Yes, if you use AWS identifiers to authenticate with Amazon S3. |
| `AWSKey`         | Secret access key for the Amazon Web Services account specified in `-AWSID`.<br>Note: To authenticate with Amazon S3, you must provide one of the following values:<br>• `AWSID` along with `AWSKey`<br>• `IAMRole`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Yes, if you use AWS identifiers to authenticate with Amazon S3. |
| `IAMRole`        | AWS IAM (Identity and Access Management) role name that contains the temporary credentials that RMAN will use for backup and recovery operations. This role must be assigned the appropriate privilege to access your S3 account.<br>Note: To authenticate with Amazon S3, you must provide one of the following:<br>• `IAMRole`<br>• `AWSID` along with `AWSKey`<br>The OSB Cloud Module uses the Instance Metadata Service (IMDS) to access the instance metadata from an Amazon EC2 instance. IMDS is available in two versions: `IMDSv1` and `IMDSv2`. By default, the OSB Cloud Module uses `IMDSv2` to support enhanced security for metadata access. If `IMDSv2` cannot be accessed, then the OSB Cloud Module automatically falls back to use `IMDSv1`.<br>See [IAM roles for Amazon EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html) for more information. | Yes, if you use IAM roles to authenticate with Amazon S3.       |
| `IAMRoleMetaURI` | Metadata URI where temporary credentials for the specified IAM role are stored. For Amazon EC2 users, specifying the metadata URI is optional. If this parameter is omitted, the temporary credentials are retrieved from the instance metadata.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | No                                                              |
| `awsEndpoint`    | Host name to which backups must be sent. If this parameter is omitted, backups will be stored on the default host.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | No                                                              |
| `awsPort`        | Non-default HTTP/HTTPS connection port number. The default port number for HTTP is 80 and HTTPS is 443.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | No                                                              |
| `location`       | Amazon S3 location where the RMAN backups must be stored. If specified, the value must match the location of the value of `awsEndPoint`. For third-party S3-compatible services, if a location is not required, set location to “us”.<br>Refer to the Amazon S3 documentation for a list of valid locations..                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | No                                                              |
| `walletDir`      | Location that stores the Oracle wallet that contains S3 credentials and proxy information.<br>The Oracle wallet directory must exist before running the S3 Backup installer.<br>Consult Prerequisites for Oracle Secure Backup Cloud Module for more information.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | Yes                                                             |
| `configFile`     | Name, with the complete path, of the configuration file that will be created by the installer. The parameters that are used while running RMAN jobs are obtained from this configuration file.<br>If this parameter is omitted, the installer creates the configuration file and places it in a default system-dependent location.<br>Default Linux location: `$ORACLE_HOME/dbs/osbsws``ORACLE_SID``.ora`<br>Default Windows location: `%ORACLE_HOME%\database\osbsws``ORACLE_SID``.ora`                                                                                                                                                                                                                                                                                                                                                                                                                   | No                                                              |
| `proxyHost`      | Name of the HTTP proxy server, if required.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | No                                                              |
| `proxyPort`      | Port number of the HTTP proxy server.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | No                                                              |
| `proxyID`        | User name for the HTTP proxy server.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | No                                                              |
| `proxyPass`      | Password for the HTTP proxy server user                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | No                                                              |
| `trustedCerts`   | List of SSL certificate to be imported into the Oracle wallet.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | No                                                              |
| `argFile`        | Name of the file from which arguments must be read during installation. To read arguments from the standard input, specify “-”.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | No                                                              |
| `useHttps`       | Sets up an HTTPS connection. If omitted, HTTP connection is used.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | No                                                              |
| `useSigV2`       | Sets up an authentication scheme. If this parameter is specified, Signature Version 2 authentication is set up; else Signature Version 4 is set up. The recommended scheme is Signature Version 4.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | No                                                              |

#### 33.3.3 Running the OSB Cloud Module Installer

Oracle recommends that you run the Oracle Secure Backup installer in a secure mode, and avoid running the installer directly from the command line.

Before you begin, ensure that you have verified the prerequisites and compiled the parameter values required to run the Oracle Secure Backup Cloud Module installer.

- Prerequisites for Oracle Secure Backup Cloud Module
- Parameters for Installing the Oracle Secure Backup Cloud Module

1.  The OSB Cloud Module installer file `osbws_installer.zip` is available in the Oracle home directory. (See Table 33-1). Extract the contents of `osbws_installer.zip` to a subdirectory of your choice.
    In this example, you extract the zip file to the `osbws_1` subdirectory.

        $ mkdir -p $ORACLE_HOME/lib/osbws_1
        $ cd $ORACLE_HOME/lib/osbws_1
        unzip -q $ORACLE_HOME/lib/osbws_installer.zip
2.  Navigate to the directory where you have extracted the OSB Cloud Module installer files.
    In this example, you go to the `osbws_1` subdirectory which contains the `osbws_install.jar` installer file and the README file `osbws_readme.txt`.
        $ cd $ORACLE_HOME/lib/osbws_1
3.  Run the OSB Cloud Module installer using one of these methods.
    1.  Include the parameters and values in a file and secure the file. Run the OSB Cloud Module installer using the parameters specified in the file.
            % java -jar osbws_install.jar -ARGFILE filename
    2.  Alternatively, use these steps to embed the run command, parameters, and values in a file. Run the file as a shell script or as a Windows batch file.
        1.  Create a file that contains the installer invocation line.

                % touch osbws.sh
                % chmod 700 osbws.sh

            Set file permissions to grant exclusive access only to the owner of the file. It is critical to restrict access to the file that contains the AWS credentials.

        2.  Edit the file to contain a single line with the installer run command and the mandatory parameters. You can compose a one-line invocation by populating the parameters with the information you obtained in the previous section.

            This example shows that the AWS identifiers are specified to authenticate RMAN operations with Amazon S3.

                java -jar osbws_install.jar -AWSID access key ID
                -AWSKey secret key -walletDir $ORACLE_HOME/dbs/osbws_wallet
                -proxyHost www-proxy.example.com

            This example shows that an IAM role name `s3access` is specified to authenticate RMAN operations with Amazon S3.

                java -jar osbws_install.jar
                —IAMRole s3access -walletDir $ORACLE_HOME/dbs/osbws_wallet
                -proxyHost www-proxy.example.com

        3.  Run the file.

                % ./osbws.sh

    Review the sample output of the OSB Cloud Module installer.

        Oracle Secure Backup Web Service Install Tool, build 23.0.0.0.0_2024-11-04
        AWS credentials are valid.
        Oracle Secure Backup Web Service wallet created in directory /orc1/dbs/hsbtwallet.
        Oracle Secure Backup Web Service initialization file /orc1home/dbs/osbwssbt.ora created.
        Skipping library download because option -libDir is not specified.

    The OSB Cloud Module installer creates these files on your system:
    - The configuration file `osbws<``ORACLE_SID``>.ora`.
    - The OSB Web Services Wallet

### 33.4 Configuration Parameters for the Oracle Secure Backup Cloud Module

Use configuration parameters to specify the settings that are used when performing backups with the Oracle Secure Backup Cloud Module.

Configuration parameters can be set in one of the following locations:

- Configuration file for the Oracle Secure Backup Cloud Module

  The name of the configuration file is specified in the `OSB_WS_PFILE` parameter

- `ENV` variable when configuring SBT channels

  **Note:**

  On Windows, Oracle recommends that you use the `SBT_PARMS` parameter to specify the environment variables, instead of the `ENV` parameter.

The following table describes the configuration parameters that can be set when using the Oracle Secure Backup Cloud Module.

| Parameter Name             | Mandatory?                            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:---------------------------|:--------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OSB_WS_PFILE`             | No                                    | Indicates the configuration file for the SBT library. The default location for the configuration file is:<br>Linux: `$ORACLE_HOME/dbs/osbws``ORACLE_SID``.ora`<br>Windows: `%ORACLE_HOME%\database\osbws``ORACLE_SID``.ora`<br>`ORACLE_SID` represents the `SID` of the target database.                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `OSB_WS_HOST`              | Yes                                   | Specifies the name of the host to which the backups are sent.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `OSB_WS_PROXY`             | No                                    | Specifies the proxy server and port when the target database is behind a firewall. It is specified in the \<host\>:\<port\> format.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `OSB_WS_BUCKET`            | No                                    | Specifies the bucket in which the SBT library stores backups. If this parameter is not specified, then the SBT library first attempts to find an existing bucket whose location matches the specified location from buckets whose names are prefixed with `oracle-data-``account name``-`. If no such bucket exists, then the SBT library creates a unique bucket with the above prefix.                                                                                                                                                                                                                                                                                                                                 |
| `OSB_WS_LOCATION`          | No                                    | Specifies the Amazon S3 location where the backups must be stored. This value must match the location of the specified `OSB_WS_HOST` and the location of the `OSB_WS_BUCKET` (if specified). If this parameter is not specified, then the default Amazon S3 region is used.<br>Refer to the Amazon S3 documentation for a list of valid pairs of endpoints and locations.                                                                                                                                                                                                                                                                                                                                                |
| `OSB_WS_CHUNK_SIZE`        | No                                    | Specifies the object size, in bytes, that will used when storing backups to Amazon S3. The default size is 100MB.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `OSB_WS_WALLET`            | Yes                                   | Defines the wallet location, alias, and proxy authentication alias through which the SBT library reads credentials.<br>The format of this parameter is:<br>`LOCATION=<filename> CREDENTIAL_ALIAS=<alias> PROXY_AUTH_ALIAS=<alias>`<br>`LOCATION` defines the location of wallet, `CREDENTIAL_ALIAS` defines the alias in the wallet from which AWS credentials are retrieved, and `PROXY_AUTH_ALIAS` defines the alias in the wallet from which the proxy authentication credentials are retrieved. `PROXY_AUTH_ALIAS` is optional, the others are mandatory.                                                                                                                                                            |
| `OSB_WS_VIRTUAL_HOST`      | No                                    | Specifies the format of the host. The default value is TRUE.<br>When set to TRUE, the format is http\[s\]://\<bucket\>.\<host\>. When set to FALSE, the format is http\[s\]://\<host\>/\<bucket\>. Use FALSE when the storage provider is not Amazon S3, but is compatible with S3.                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `OSB_WS_IAM_ROLE`          | Yes, when using the metadata service. | Specifies the name of the IAM role that can be used to back up to Amazon S3. The Amazon Elastic Cloud Compute (EC2) instance must be configured with the specified IAM role.<br>The OSB Cloud Module uses the Instance Metadata Service (IMDS) to access the instance metadata from an Amazon EC2 instance. IMDS is available in two versions: `IMDSv1` and `IMDSv2`.<br>By default, the OSB Cloud Module uses `IMDSv2` to support enhanced security for metadata access. If `IMDSv2` cannot be accessed, then the OSB Cloud Module automatically falls back to use `IMDSv1`.<br>See [IAM roles for Amazon EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html) for more information. |
| `OSB_WS_IAM_ROLE_META_URI` | No                                    | Specifies the name of the metadata URI where temporary credentials for the IAM role are stored.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |

### 33.5 Configuring SBT Channel for Amazon S3

Configure an RMAN automatic SBT (tape) channel and specify the `oracle.osbws` SBT library that corresponds to Amazon Web Services. You can optionally configure the SBT channel as the default channel so that RMAN can directly make all backups to Amazon S3 storage.

1.  Start RMAN and connect to the target database.
2.  Use the `CONFIGURE` command to configure an automatic SBT channel. Use the `SBT_LIBRARY` parameter to specify the `oracle.osbws` library which is the Oracle-supplied native SBT library for RMAN operations with Amazon S3. You can optionally specify the native SBT library path instead of the library alias.
    - UNIX and Linux
    - Windows

    <!-- -->

        RMAN> CONFIGURE CHANNEL DEVICE TYPE 'SBT'
        PARMS 'SBT_LIBRARY=oracle.osbws,
        ENV=(OSB_WS_PFILE=/myfiles/osbsws<ORACLE_SID>.ora)';

    You can optionally specify the native SBT library path instead of the library alias, as shown below.

        RMAN> CONFIGURE CHANNEL DEVICE TYPE 'SBT'
        PARMS 'SBT_LIBRARY=$ORACLE_HOME/lib/libosbws.so,
        ENV=(OSB_WS_PFILE=/myfiles/osbsws<ORACLE_SID>.ora)';

        RMAN> CONFIGURE CHANNEL DEVICE TYPE 'SBT'
        PARMS 'SBT_LIBRARY=oracle.osbws,
        SBT_PARMS=(OSB_WS_PFILE=C:\myfiles\osbsws<ORACLE_SID>.ora)';

    You can optionally specify the native SBT library path instead of the library alias, as shown below.

        RMAN> CONFIGURE CHANNEL DEVICE TYPE 'SBT'
        PARMS 'SBT_LIBRARY=%ORACLE_HOME%\bin\oraosbws.dll,
        SBT_PARMS=(OSB_WS_PFILE=C:\myfiles\osbsws<ORACLE_SID>.ora)';

    This example configures an automatic SBT channel to send backups to Amazon S3. The `SBT_LIBRARY` parameter specifies the alias name (`oracle.osbws`) of the native SBT library that corresponds to Amazon S3 Cloud. `osbsws``ORACLE_SID``.ora` is the Oracle Secure Backup configuration file that is created when you install the Oracle Secure Backup Cloud module. `<ORACLE_SID>` is the system identifier of the target Oracle Database which you want to back up to AWS Cloud.

    **Note:**

    - On Windows systems, use the `SBT_PARMS` parameter instead of the `ENV` parameter to specify the configuration file.
    - You can skip the `ENV` or `SBT_PARMS` parameter if the configuration file is created in the default directory chosen by the backup module installer.
    - An automatic SBT channel creates a persistent default SBT device setting that applies to all backup and recovery operations. Alternatively, you can use the `ALLOCATE CHANNEL` command to manually allocate a one-time SBT channel before each backup or restore operation.

    Review the sample output of the `CONFIGURE` command.
        CONFIGURE CHANNEL DEVICE TYPE 'SBT_TAPE' PARMS  'SBT_LIBRARY=oracle.osbws, ENV=(OSB_WS_PFILE=/myfiles/osbwssbt.ora)';
        new RMAN configuration parameters are successfully stored
3.  Configure `SBT` as the default device type if you want to create all backups to Amazon S3 by default.
        RMAN> CONFIGURE DEFAULT DEVICE TYPE TO SBT;

        CONFIGURE DEFAULT DEVICE TYPE TO SBT;
        new RMAN configuration parameters:
        CONFIGURE DEFAULT DEVICE TYPE TO 'SBT_TAPE';
        new RMAN configuration parameters are successfully stored
4.  Use the `SHOW` `ALL CHANGED` command to review the RMAN configuration and to confirm that you have set Amazon S3 as the backup destination.
        RMAN> SHOW ALL CHANGED;

        SHOW ALL CHANGED;
        RMAN configuration parameters for database with db_unique_name TEST are:
        CONFIGURE DEFAULT DEVICE TYPE TO 'SBT_TAPE';
        CONFIGURE CHANNEL DEVICE TYPE 'SBT_TAPE' PARMS  'SBT_LIBRARY=oracle.osbws, ENV=(OSB_WS_PFILE=/myfiles/osbwssbt.ora)';

### 33.6 Backup and Recover with Amazon S3 Cloud

Connect RMAN to your target database and perform backup and restores with Amazon S3 Cloud.

Before you begin, ensure that you have installed the Oracle Secure Backup (OSB) Cloud Module and configured an Amazon S3-specific SBT channel.

1.  Start RMAN and connect to the target database.
2.  Run the `SHOW ALL CHANGED` command to verify that the RMAN environment is configured for backups with Amazon S3.
        RMAN> SHOW ALL CHANGED;

    This sample RMAN configuration shows that the SBT channel specifies the `oracle.osbws` SBT library which corresponds to Amazon S3 Cloud. The default device type is set to `SBT_TAPE` which indicates that all backups are directly sent to Amazon S3.
        SHOW ALL CHANGED;
        RMAN configuration parameters for database with db_unique_name TEST are:
        CONFIGURE DEFAULT DEVICE TYPE TO 'SBT_TAPE';
        CONFIGURE CHANNEL DEVICE TYPE 'SBT_TAPE' PARMS  'SBT_LIBRARY=oracle.osbws, ENV=(OSB_WS_PFILE=/oracle/dbs/osbwssbt.ora)';
3.  Use RMAN to backup the database to Amazon S3 Cloud using RMAN.
        BACKUP DATABASE;

        RMAN> backup database;
        backup database;
        Starting backup at 11-MAR-25
        allocated channel: ORA_SBT_TAPE_1
        channel ORA_SBT_TAPE_1: SID=211 device type=SBT_TAPE
        channel ORA_SBT_TAPE_1: Oracle Secure Backup Web Services Library VER = 26.0.0.1
        allocated channel: ORA_SBT_TAPE_2
        channel ORA_SBT_TAPE_2: SID=25 device type=SBT_TAPE
        channel ORA_SBT_TAPE_2: Oracle Secure Backup Web Services Library VER = 26.0.0.1
        allocated channel: ORA_SBT_TAPE_3
        channel ORA_SBT_TAPE_3: SID=212 device type=SBT_TAPE
        channel ORA_SBT_TAPE_3: Oracle Secure Backup Web Services Library VER = 26.0.0.1
        channel ORA_SBT_TAPE_1: starting full datafile backup set
        .
        .
        .
        channel ORA_SBT_TAPE_1: backup set complete, elapsed time: 00:01:01
        channel ORA_SBT_TAPE_2: finished piece 1 at 11-MAR-25
        piece handle=1j8qmc28_51_1_1 tag=TAG20250311T063959 comment=API Version 2.0,MMS Version 26.0.0.1
        channel ORA_SBT_TAPE_2: backup set complete, elapsed time: 00:00:45
        channel ORA_SBT_TAPE_3: finished piece 1 at 11-MAR-25
        piece handle=1e0mmbu0_46_1_1 tag=TAG20250311T063959 comment=API Version 2.0,MMS Version 26.0.0.1
        channel ORA_SBT_TAPE_3: backup set complete, elapsed time: 00:03:01
        Finished backup at 11-MAR-25
        Starting Control File Autobackup at 11-MAR-25
        piece handle=c-3829255431-20250311-01 comment=API Version 2.0,MMS Version 26.0.0.1
        Finished Control File Autobackup at 11-MAR-25
4.  Restore and recover the database with Amazon S3 using RMAN.
        RESTORE DATABASE;
        RECOVER DATABASE;

### 33.7 Troubleshooting the OSB Cloud Module

This section lists potential issues that may affect the installation or the operation of the Oracle Secure Backup Cloud Module.

| Symptoms                                                                | Error Messages                                     | Resolution                                                                                                                                                                                                                                                                                        |
|:------------------------------------------------------------------------|:---------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| The S3 Backup installation cannot create the license file on Amazon S3. | `Time-out waiting for license file to be created.` | The first time you run the S3 Backup installer for a set of AWS identifiers, the installer creates a license file on Amazon S3. If there are problems preventing its creation the time-out error message is displayed in the installation output.<br>Contact Oracle support to resolve the issue. |
