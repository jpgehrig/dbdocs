This preface lists changes in Oracle Autonomous Health Framework for Oracle Database 19c.

- New Features for Oracle ORAchk and EXAchk 18.2.0
  These are new features for Oracle ORAchk and EXAchk 18.2.0.
- New Features for Oracle ORAchk and EXAchk 18.3.0
  These are new features for Oracle ORAchk and EXAchk 18.3.0.
- New Features for Oracle ORAchk and EXAchk 18.4.0
  These are new features for Oracle ORAchk and EXAchk 18.4.0.
- New Features for Oracle Trace File Analyzer 18.1.1
  These are new features for Oracle Trace File Analyzer 18.1.1.
- New Features for Oracle Trace File Analyzer 18.2.0
  These are new features for Oracle Trace File Analyzer 18.2.0.
- New Features for Oracle Trace File Analyzer 18.3.0
  These are new features for Oracle Trace File Analyzer 18.3.0.
- New Features for Oracle Trace File Analyzer 18.4.1
  These are new features for Oracle Trace File Analyzer 18.4.1.

### New Features for Oracle ORAchk and EXAchk 18.2.0

These are new features for Oracle ORAchk and EXAchk 18.2.0.

- Only the Most Critical Checks Shown by Default
  By default, Oracle ORAchk and Oracle EXAchk display only the most critical checks in the report output.
- REST Interface
  Oracle ORAchk and Oracle EXAchk now include full REST support allowing invocation and query over HTTPS.
- Remote Node Connection without Passwordless SSH
  If you do not wish to use passwordless SSH to connect to remote nodes, Oracle ORAchk and Oracle EXAchk can auto-generate the private key files for the remote nodes.
- Python 3 Compatibility
  Oracle ORAchk and Oracle EXAchk now support Python 3.6.
- Support for Oracle Autonomous Database
  Oracle EXAchk now provides support for Oracle Autonomous Database.
- New Oracle Stack Health Checks
  This release includes new health checks for both Oracle ORAchk and Oracle EXAchk including a number of Oracle Exadata critical issues.
- Command-Line Options to Generate Password Protected Collection zip Files
  This release includes Oracle ORAchk and Oracle EXAchk command-line options to encrypt and decrypt diagnostic collection `zip` files.

**Parent topic:** Changes in this Release for Autonomous Health Framework Users Guide 19c

#### Only the Most Critical Checks Shown by Default

By default, Oracle ORAchk and Oracle EXAchk display only the most critical checks in the report output.

The critical checks are those which Oracle judges to have the most severe potential impact.

All other checks are still run and available in the report. You can view them by selecting appropriate option under the control Show checks with the following status.

To run only the critical checks, use appropriate profile:

    ./orachk -profile oratier1
    ./exachk -profile exatier1

**Parent topic:** New Features for Oracle ORAchk and EXAchk 18.2.0

#### REST Interface

Oracle ORAchk and Oracle EXAchk now include full REST support allowing invocation and query over HTTPS.

To facilitate REST support, Oracle REST Data Services (ORDS) is included within the install.

To enable REST, start ORDS by running the `./exachk -ordssetup` command, and then start the daemon using the `-ords` option.

    ./exachk -d start -ords

Start a full health check run by accessing the URL:

    https://host:7080/ords/tfaml/orachk/start_client

To run specific profiles:

    https://host:7080/ords/tfaml/orachk/profile/profile1,profile2

To run specific checks:

    https://host:7080/ords/tfaml/orachk/check/check_id,check_id

Any request returns a job ID that you can use to query the status or to download the result.

To query the status:

    https://host:7080/ords/tfaml/orachk/status/job_id

To download the result:

    https://host:7080/ords/tfaml/orachk/download/job_id

**Parent topic:** New Features for Oracle ORAchk and EXAchk 18.2.0

#### Remote Node Connection without Passwordless SSH

If you do not wish to use passwordless SSH to connect to remote nodes, Oracle ORAchk and Oracle EXAchk can auto-generate the private key files for the remote nodes.

The process used to generate the private key is as follows:

1.  Prompt for remote node password.

2.  Log in to the remote node, and generate private and public key pair on the remote node.

3.  Copy the contents of public key into the `.ssh/authorized_keys` file of remote node and then delete the public key from the remote node.

4.  Copy the private key of remote node into the local node, and use as identity file to make future connections.

Alternatively, you can provide the private key file yourself.

**Parent topic:** New Features for Oracle ORAchk and EXAchk 18.2.0

#### Python 3 Compatibility

Oracle ORAchk and Oracle EXAchk now support Python 3.6.

Python 3.6 provides better security and performance over the older python versions.

**Parent topic:** New Features for Oracle ORAchk and EXAchk 18.2.0

#### Support for Oracle Autonomous Database

Oracle EXAchk now provides support for Oracle Autonomous Database.

**Parent topic:** New Features for Oracle ORAchk and EXAchk 18.2.0

#### New Oracle Stack Health Checks

This release includes new health checks for both Oracle ORAchk and Oracle EXAchk including a number of Oracle Exadata critical issues.

- [Oracle ORAchk Health Check Catalog](https://support.oracle.com/epmos/main/downloadattachmentprocessor?parent=DOCUMENT&sourceId=1268927.2&attachid=1268927.1:HC_CATALOG)

- [Oracle EXAchk Health Check Catalog](https://support.oracle.com/epmos/main/downloadattachmentprocessor?parent=DOCUMENT&sourceId=1268927.2&attachid=1268927.1:EXACHK_HC_CATALOG)

The Health Check Catalog is also contained within the download.

**Parent topic:** New Features for Oracle ORAchk and EXAchk 18.2.0

#### Command-Line Options to Generate Password Protected Collection zip Files

This release includes Oracle ORAchk and Oracle EXAchk command-line options to encrypt and decrypt diagnostic collection `zip` files.

You can run these command only on Linux and Solaris platforms.

**Related Topics**

- [Command-Line Options to Generate Password Protected Collection zip Files](generate-password-protected-collection-zip-files.md)

**Parent topic:** New Features for Oracle ORAchk and EXAchk 18.2.0

### New Features for Oracle ORAchk and EXAchk 18.3.0

These are new features for Oracle ORAchk and EXAchk 18.3.0.

- Support for Oracle Private Cloud Appliance
  Oracle EXAchk now provides beta support for checks covering Oracle Private Cloud Appliance.
- Automatic Start from Oracle Trace File Analyzer Install
  Installing Oracle Trace File Analyzer as `root` on Linux or Solaris on non-engineered systems automatically sets up and runs the Oracle ORAchk daemon.
- Run Against Individual PDBs
  Oracle ORAchk and Oracle EXAchk can now be run against specific individual PDBs.
- Enhancements to User-Defined Checks
  User-defined checks can now have custom check names, pass and fail messages, all declared dynamically at run time.
- Oracle Database Role (Primary or Standby) Now Displayed in Report
  The summary section of report output now displays the role of each Oracle Database (Primary or Standby)
- Deprecation of EBS Health Checks
  Starting with 18.3.0 release, the Oracle ORAchk and Oracle EXAchk checks for EBS feature has been deprecated.
- New Oracle Stack Health Checks
  This release includes new health checks for both Oracle ORAchk and Oracle EXAchk including a number of Oracle Exadata critical issues.

**Parent topic:** Changes in this Release for Autonomous Health Framework Users Guide 19c

#### Support for Oracle Private Cloud Appliance

Oracle EXAchk now provides beta support for checks covering Oracle Private Cloud Appliance.

You can view the new checks listed in the EXAchk Health Check Catalog under Engineered systems of Private Cloud Appliance and Private Cloud Appliance Plane.

**Parent topic:** New Features for Oracle ORAchk and EXAchk 18.3.0

#### Automatic Start from Oracle Trace File Analyzer Install

Installing Oracle Trace File Analyzer as `root` on Linux or Solaris on non-engineered systems automatically sets up and runs the Oracle ORAchk daemon.

The daemon restarts at 1 am every day to discover any environment changes. The daemon runs a full local Oracle ORAchk check at 2 am every day, and a partial run of the most impactful checks every 6 hours through the `oratier1` profile.

The daemon automatically purges any collections older than 2 weeks.

You can change the daemon settings after enabling auto start. To remove auto start any time, run `tfactl run orachk -autostop`.

**Parent topic:** New Features for Oracle ORAchk and EXAchk 18.3.0

#### Run Against Individual PDBs

Oracle ORAchk and Oracle EXAchk can now be run against specific individual PDBs.

To run against specific PDBs, use:

    -pdbnames {pdb_name1,pdb_name2}

**Parent topic:** New Features for Oracle ORAchk and EXAchk 18.3.0

#### Enhancements to User-Defined Checks

User-defined checks can now have custom check names, pass and fail messages, all declared dynamically at run time.

Set the dynamic values, for example,

    ---CHECK STARTS---
    {existing_check_code}

    echo "CUSTOM_CHECK_NAME={customized_check_name}" >> CUSTOMIZE_CHECK_PARAMS
    echo "CUSTOM_PASS_MSG={customized_pass_message}" >> CUSTOMIZE_CHECK_PARAMS
    echo "CUSTOM_FAIL_MSG={customized_fail_message}" >> CUSTOMIZE_CHECK_PARAMS
    ---CHECK ENDS---

Additionally, user-defined checks that are on hold will no longer be exported by default. You can still choose to export on hold checks by selecting the relevant check boxes.

**Parent topic:** New Features for Oracle ORAchk and EXAchk 18.3.0

#### Oracle Database Role (Primary or Standby) Now Displayed in Report

The summary section of report output now displays the role of each Oracle Database (Primary or Standby)

In the DB Home - Version - Names section, click the number of databases to expand details and view the role of each Oracle Database.

**Parent topic:** New Features for Oracle ORAchk and EXAchk 18.3.0

#### Deprecation of EBS Health Checks

Starting with 18.3.0 release, the Oracle ORAchk and Oracle EXAchk checks for EBS feature has been deprecated.

This means running health checks against EBS feature is no longer enhanced, but it is still supported until the Oracle ORAchk and Oracle EXAchk 19.3.0 release (approximately one year).

In the Oracle ORAchk and Oracle EXAchk 19.3.0 release, the EBS checks feature will be desupported, meaning Oracle will no longer fix bugs in Oracle ORAchk and Oracle EXAchk related to EBS checks, and the EBS checking feature will be removed altogether.

Run all EBS health checks using the EBS Analyzers, which is available at My Oracle Support Note 1545562.1.

**Related Topics**

- [https://support.oracle.com/rs?type=doc&id=1545562.1](https://support.oracle.com/rs?type=doc&amp;id=1545562.1)

**Parent topic:** New Features for Oracle ORAchk and EXAchk 18.3.0

#### New Oracle Stack Health Checks

This release includes new health checks for both Oracle ORAchk and Oracle EXAchk including a number of Oracle Exadata critical issues.

- [Oracle ORAchk Health Check Catalog](https://support.oracle.com/epmos/main/downloadattachmentprocessor?parent=DOCUMENT&sourceId=1268927.2&attachid=1268927.1:HC_CATALOG)

- [Oracle EXAchk Health Check Catalog](https://support.oracle.com/epmos/main/downloadattachmentprocessor?parent=DOCUMENT&sourceId=1268927.2&attachid=1268927.1:EXACHK_HC_CATALOG)

The Health Check Catalog is also contained within the download.

**Parent topic:** New Features for Oracle ORAchk and EXAchk 18.3.0

### New Features for Oracle ORAchk and EXAchk 18.4.0

These are new features for Oracle ORAchk and EXAchk 18.4.0.

- Automatically Run on Oracle Exadata User Domain (DomU)
  Installing Oracle Trace File Analyzer on Oracle Exadata automatically sets up and runs the Oracle EXAchk daemon on the user domain (DomU).
- Support for Oracle Exadata 19.1.0
  This release adds Oracle EXAchk support for the latest Oracle Exadata release 19.1.0.
- Ensure That You Run Only the Up-To-Date Checks
  Starting in this release, Oracle ORAchk and Oracle EXAchk will provide only the checks that are less than a year old.
- Performance Improvement through Caching Discovery Data
  Starting in this release, Oracle ORAchk and Oracle EXAchk cache the discovery data.
- Ability to Patch Between Releases
  Starting in this release, Oracle ORAchk and Oracle EXAchk has the ability to patch between the releases. The patching allows for updates to both health checks and code.
- Check Specific Timeouts to Reduce Skipped Checks
  Health Checks are skipped sometimes because the check takes longer to run than the default timeout value.
- New Oracle Stack Health Checks
  This release includes new health checks for both Oracle ORAchk and Oracle EXAchk including a number of Oracle Exadata critical issues.

**Parent topic:** Changes in this Release for Autonomous Health Framework Users Guide 19c

#### Automatically Run on Oracle Exadata User Domain (DomU)

Installing Oracle Trace File Analyzer on Oracle Exadata automatically sets up and runs the Oracle EXAchk daemon on the user domain (DomU).

The daemon restarts at 1 am every day to discover any environment changes. The daemon runs a full local Oracle EXAchk check at 2 am every day, and a partial run of the most impactful checks every 6 hours through the exatier1 profile.

The daemon automatically purges any collections older than 2 weeks.

If you install Oracle EXAchk in stand-alone mode, then run `exachk -autostart` to enable auto start for quick setup on Oracle Exadata user domain.

You can change the daemon settings after enabling auto start. To remove auto start any time, run `exachk -autostop` or `tfactl run exachk -autostop`.

**Parent topic:** New Features for Oracle ORAchk and EXAchk 18.4.0

#### Support for Oracle Exadata 19.1.0

This release adds Oracle EXAchk support for the latest Oracle Exadata release 19.1.0.

**Parent topic:** New Features for Oracle ORAchk and EXAchk 18.4.0

#### Ensure That You Run Only the Up-To-Date Checks

Starting in this release, Oracle ORAchk and Oracle EXAchk will provide only the checks that are less than a year old.

Health Check information is constantly changing over time. What is applicable today, may not be applicable several months later. This is the reason Oracle ORAchk and Oracle EXAchk have always had a quarterly release cycle.

The older Health checks are the more risk of them containing out of date information. So from this release onwards Oracle ORAchk and Oracle EXAchk will provide only the checks that are less than a year old.

If Oracle ORAchk or Oracle EXAchk is more than six months old, then the tool (as per previous releases) presents a warning message advising you to upgrade and offers you the ability to download a new version. If Oracle ORAchk or Oracle EXAchk is more than a year old, then the tool will not run any checks.

**Parent topic:** New Features for Oracle ORAchk and EXAchk 18.4.0

#### Performance Improvement through Caching Discovery Data

Starting in this release, Oracle ORAchk and Oracle EXAchk cache the discovery data.

Internal testing on Oracle Exadata systems has shown caching of discovery data improved runtime performance by cutting the execution time of critical checks in half.

The following command options are included in this release:

- `-discovery`: Cache discovery data.
- `-checkdiscovery`: Optionally verify discovery.
- `-usediscovery`: Use discovery data.
- `-refreshdiscovery`: Refresh discovery data.
- `-rmdiscovery`: Remove discovery data.

**Related Topics**

- [Caching Discovery Data](caching-discovery-information.md)

**Parent topic:** New Features for Oracle ORAchk and EXAchk 18.4.0

#### Ability to Patch Between Releases

Starting in this release, Oracle ORAchk and Oracle EXAchk has the ability to patch between the releases. The patching allows for updates to both health checks and code.

When the patches are ready to deploy, they will be made available through the regular patching mechanisms on <https://support.oracle.com> and <https://updates.oracle.com>.

The following command options are included in this release:

- `-applypatch exachk_{bug_num}.zip | orachk_{bug_num}.zip`: Apply a new patch.
- `-querypatch all`: Find all patches installed.
- `-querypatch {bug_num}`: Find if a specific patch is installed.
- `-rollbackpatch {bug_num}`: Rollback a specific patch.

**Related Topics**

- [Applying Patch Between Releases](applying-patch-between-releases.md)

**Parent topic:** New Features for Oracle ORAchk and EXAchk 18.4.0

#### Check Specific Timeouts to Reduce Skipped Checks

Health Checks are skipped sometimes because the check takes longer to run than the default timeout value.

This release adds check specific timeout values.

When checks are written by Oracle a check specific timeout value is applied. This timeout value is based on our understanding of how long we expect that check to take to run.

If you find certain checks are still timing out, then you can override the individual check timeout value using: export `RAT_TIMEOUT={value_in_seconds}`

**Parent topic:** New Features for Oracle ORAchk and EXAchk 18.4.0

#### New Oracle Stack Health Checks

This release includes new health checks for both Oracle ORAchk and Oracle EXAchk including a number of Oracle Exadata critical issues.

- [Oracle ORAchk Health Check Catalog](https://support.oracle.com/epmos/main/downloadattachmentprocessor?parent=DOCUMENT&sourceId=1268927.2&attachid=1268927.1:HC_CATALOG)

- [Oracle EXAchk Health Check Catalog](https://support.oracle.com/epmos/main/downloadattachmentprocessor?parent=DOCUMENT&sourceId=1268927.2&attachid=1268927.1:EXACHK_HC_CATALOG)

The Health Check Catalog is also contained within the download.

**Parent topic:** New Features for Oracle ORAchk and EXAchk 18.4.0

### New Features for Oracle Trace File Analyzer 18.1.1

These are new features for Oracle Trace File Analyzer 18.1.1.

- Faster and Easier Service Request Data Collection
  Oracle Trace File Analyzer includes new One Command SRDCs (Service Request Data Collections).

**Parent topic:** Changes in this Release for Autonomous Health Framework Users Guide 19c

#### Faster and Easier Service Request Data Collection

Oracle Trace File Analyzer includes new One Command SRDCs (Service Request Data Collections).

New Service Request Data Collections (SRDC) make it fast and easy to collect exactly the right diagnostic data when you need help from Oracle Support.

**Parent topic:** New Features for Oracle Trace File Analyzer 18.1.1

### New Features for Oracle Trace File Analyzer 18.2.0

These are new features for Oracle Trace File Analyzer 18.2.0.

- REST Service
  Oracle Trace File Analyzer now includes REST support allowing invocation and query over HTTPS.
- Oracle Cluster Health Advisor Integration
  Oracle Trace File Analyzer now integrates with Oracle Cluster Health Advisor and consumes the problem events that Oracle Cluster Health Advisor detects.
- New SRDCs
  This release includes new SRDCs.
- Metadata Search Capability
  All metadata stored in the Oracle Trace File Analyzer index is now searchable using `tfactl search -showdatatypes|-json [json_details]`.

**Parent topic:** Changes in this Release for Autonomous Health Framework Users Guide 19c

#### REST Service

Oracle Trace File Analyzer now includes REST support allowing invocation and query over HTTPS.

To facilitate REST support Oracle REST Data Services (ORDS) is included within the install.

To enable REST, start ORDS: `tfactl rest -start`.

REST supports printing details, starting a diagcollect, and downloading collections.

**Parent topic:** New Features for Oracle Trace File Analyzer 18.2.0

#### Oracle Cluster Health Advisor Integration

Oracle Trace File Analyzer now integrates with Oracle Cluster Health Advisor and consumes the problem events that Oracle Cluster Health Advisor detects.

When Oracle Cluster Health Advisor detects a problem event, Oracle Trace File Analyzer automatically triggers relevant diagnostic collection and sends an email notification.

Email notification is configured through the standard Oracle Trace File Analyzer notification process.

**Parent topic:** New Features for Oracle Trace File Analyzer 18.2.0

#### New SRDCs

This release includes new SRDCs.

- `ORA-01031` for `ORA-01031` errors

- `ORA-01578` for `ORA-01578` errors

- `ORA-08102` for `ORA-08102` errors

- `ORA-08103` for `ORA-08103` errors

- `dbblockcorruption` for problems showing alert log messages of `Corrupt block relative dba`

- `dbfs` for ASM, DBFS, DNFS, and ACFS problems

- `dbpartition` for create/maintain partitioned/subpartitioned table/index problems

- `dbpartitionperf` for slow create/alter/drop commands against partitioned table/index

- `dbsqlperf` for SQL performance problems

- `dbundocorruption` for UNDO corruption problems

- `esexalogic` for Oracle Exalogic full Exalogs data collection information

- `listener_services` for listener errors: `TNS-12516`, `TNS-12518`, `TNS-12519`, and `TNS-12520`

- `naming_services` for naming service errors: `ORA-12154`, `ORA-12514`, and `ORA-12528`

- `dbaudit` standard information for Oracle Database auditing

Additionally, a number of the existing RMAN related SRDCs have been collapsed into fewer SRDCs:

- `dbrman` for RMAN related issues, such as backup, maintenance, restore and recover, `RMAN-08137` or `RMAN-08120`

- `dbrman600` for `RMAN-00600` error

- `dbrmanperf` for RMAN performance problems

As with all other SRDCs, use `tfactl diagcollect -srdc ``srdc_name`.

**Related Topics**

- [Collecting Diagnostic Data and Using One Command Service Request Data Collections](ondemand-diagnostic-collection.md)

**Parent topic:** New Features for Oracle Trace File Analyzer 18.2.0

#### Metadata Search Capability

All metadata stored in the Oracle Trace File Analyzer index is now searchable using `tfactl search -showdatatypes|-json [json_details]`.

You can search for all events for a particular Oracle Database between certain dates, for example,

    tfactl search -json
    '{
      "data_type":"event",
      "content":"oracle",
      "database":"rac11g",
      "from":"01/20/2017 00:00:00",
      "to":"12/20/2018 00:00:00"
     }'

To list all index events: `tfactl search -json '{"data_type":"event"}'`

To list all available datatypes: `tfactl search -showdatatypes`

**Parent topic:** New Features for Oracle Trace File Analyzer 18.2.0

### New Features for Oracle Trace File Analyzer 18.3.0

These are new features for Oracle Trace File Analyzer 18.3.0.

- Automatic SRDCs
  Oracle Trace File Analyzer will now automatically run the relevant SRDC when it detects the following events:
- REST Service Extensions
  The REST service API includes new run commands.
- Configuring REST Service Using Apache Tomcat
  The Oracle Trace File Analyzer install includes a Web Application Resource (WAR) file to enable the REST service via Apache Tomcat.
- New SRDCs
  This release includes new SRDCs.
- Automatic Start from Oracle Trace File Analyzer Install
  Installing Oracle Trace File Analyzer as `root` on Linux or Solaris on non-engineered systems automatically sets up and runs the Oracle ORAchk daemon.

**Parent topic:** Changes in this Release for Autonomous Health Framework Users Guide 19c

#### Automatic SRDCs

Oracle Trace File Analyzer will now automatically run the relevant SRDC when it detects the following events:

- `ORA-00600`

- `ORA-04030`

- `ORA-04031`

- `ORA-07445`

This means the diagnostic collections captured will be automatically targeted specifically to the event that occurred.

When other critical events are detected, Oracle Trace File Analyzer performs a default diagnostic collection.

Over future releases the automatic collection of specific SRDCs will be extended to cover other events.

**Parent topic:** New Features for Oracle Trace File Analyzer 18.3.0

#### REST Service Extensions

The REST service API includes new run commands.

You can access the new run commands as follows:

    https://host:port/ords/tfactl/run/alertsummary
    https://host:port/ords/tfactl/run/calog
    https://host:port/ords/tfactl/run/changes
    https://host:port/ords/tfactl/run/events
    https://host:port/ords/tfactl/run/history

There is also a new upgrade feature for the existing ORDS REST implementations.

    tfactl rest -upgrade

Running the commands `tfactl rest -upgrade` stops ORDS, upgrades it to support the latest API updates, and then restarts it again.

**Parent topic:** New Features for Oracle Trace File Analyzer 18.3.0

#### Configuring REST Service Using Apache Tomcat

The Oracle Trace File Analyzer install includes a Web Application Resource (WAR) file to enable the REST service via Apache Tomcat.

To enable the REST service using Apache Tomcat:

1.  Deploy the `WAR` file located at `TFA_HOME/jlib/tfa.war` to your Tomcat server.
2.  Change the `tfaadmin` user password.
        curl -k --user tfaadmin:tfaadmin -X POST "https://host/tfa/tfactl/user/update" '{ "password" : "some_new_password" }'
3.  Change the `tfarest` user password.
        curl -k --user tfarest:tfarest -X POST "https://host/tfa/tfactl/user/update" '{ "password" : "some_new_password" }'
4.  Add the Tomcat user to the Oracle Trace File Analyzer access list.
        tfactl access add -user tomcat_user

**Parent topic:** New Features for Oracle Trace File Analyzer 18.3.0

#### New SRDCs

This release includes new SRDCs.

- `dbimpdpperf` for Data Pump import performance problems.

- `dbsqlperf` for SQL performance problems.

- `dbtde` for Transparent Data Encryption (TDE) problems.

- `emagentperf` for Enterprise Manager Agent performance problems.

- `emomscrash` for Enterprise Manager crash problems.

- `emomsheap` for Enterprise Manager java heap usage, or performance problems.

- `emomshungcpu` for Enterprise Manager OMS crash, restart, or performance problems.

As with all other SRDCs use `tfactl diagcollect -srdc srdc_name`.

**Parent topic:** New Features for Oracle Trace File Analyzer 18.3.0

#### Automatic Start from Oracle Trace File Analyzer Install

Installing Oracle Trace File Analyzer as `root` on Linux or Solaris on non-engineered systems automatically sets up and runs the Oracle ORAchk daemon.

The daemon restarts at 1 am every day to discover any environment changes. The daemon runs a full local Oracle ORAchk check at 2 am every day, and a partial run of the most impactful checks every 6 hours through the `oratier1` profile.

The daemon automatically purges any collections older than 2 weeks.

You can change the daemon settings after enabling auto start. To remove auto start any time, run `tfactl run orachk -autostop`.

**Parent topic:** New Features for Oracle Trace File Analyzer 18.3.0

### New Features for Oracle Trace File Analyzer 18.4.1

These are new features for Oracle Trace File Analyzer 18.4.1.

- New SRDCs
  This release includes new SRDCs.
- Merging of Multiple Automatic SRDCs
  If Oracle Trace File Analyzer detects a significant event, then it waits five minutes to check any other events, which occur as a result, and collects all of these.
- Running Oracle Trace File Analyzer SRDC Commands in Silent Mode
  SRDCs have prompts for problem details, which are specific to the SRDC type.

**Parent topic:** Changes in this Release for Autonomous Health Framework Users Guide 19c

#### New SRDCs

This release includes new SRDCs.

As with all other SRDCs use `tfactl diagcollect -srdc ``srdc_name`.

- `dbdatapatch` for Datapatch issues
- `dbspatialinstall` for Oracle Spatial Installation issues
- `dbrmanperf` updated to include diagnostic data collection for RMAN Backup, RMAN Maintenance, RMAN Restore and Recover, `RMAN-08137` or `RMAN-08120`, and RMAN Performance issues
- `dbtextupgrade` for Oracle Text version 12.1.0.1 and later upgrade issues
- `ORA-04023` for `ORA-04023` issues
- `ORA-04063` for `ORA-04063` issues
- `dbspatialexportimport` for Oracle Spatial Export/Import issues
- `dbstandalonedbca` for Database Configuration Assistant issues

**Parent topic:** New Features for Oracle Trace File Analyzer 18.4.1

#### Merging of Multiple Automatic SRDCs

If Oracle Trace File Analyzer detects a significant event, then it waits five minutes to check any other events, which occur as a result, and collects all of these.

If there are multiple SRDC related events, which occur on the same database within that five minute period, then Oracle Trace File Analyzer performs one merged SRDC collection for all of them.

For example, if an `ORA-00600` event occurs and 30 seconds later an `ORA-04031` event occurs, then Oracle Trace File Analyzer performs one SRDC that collects everything necessary to resolve both the errors.

Merging of SRDCs applies to the following:

- `ORA-00600`
- `ORA-07445`
- `ORA-04030`
- `ORA-04031`

Over future releases the automatic collection of specific SRDCs will be extended to cover other events.

**Related Topics**

- [ORA-600 (ORA-00600 Internal Error) Detection, Diagnosis & Resolution](https://community.oracle.com/community/support/support-blogs/database-support-blog/blog/2018/09/19/ora-600-ora-00600-internal-error-detection-diagnosis-resolution)

**Parent topic:** New Features for Oracle Trace File Analyzer 18.4.1

#### Running Oracle Trace File Analyzer SRDC Commands in Silent Mode

SRDCs have prompts for problem details, which are specific to the SRDC type.

SRDCs can now be run in silent mode by providing answers to prompts using the command-line. This will be very useful in scenarios where a tool automatically triggers Oracle Trace File Analyzer collection.

You can view the SRDC-specific prompt by running:

    tfactl diagcollection -srdc {srdc_type} -help

**Parent topic:** New Features for Oracle Trace File Analyzer 18.4.1
