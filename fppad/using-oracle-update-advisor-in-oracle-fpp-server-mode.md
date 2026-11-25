## Using Oracle Update Advisor in Oracle FPP Server Mode

Understand how to use the Oracle Update Advisor in Oracle FPP Server Mode to evaluate the gold image or Oracle home and download the patched gold image.

1.  Register a user for the Oracle Update Advisor on the Oracle FPP Server.
        $ rhpctl manage updateadvisor -registeruser -ssousername abc.xyz@example.com -csi 18890944
        Enter user "abc.xyz@example.com" REDACTED: *****
        mbcluster-1: Audit ID: 97
        Registering user to Oracle update advisor ...
        Successfully registered user to Oracle update advisor.

    **Note:**

    You must specify the Customer Support Identifier (CSI) to be able to download the patched gold image.
2.  Evaluate the current patches applied to your gold image or Oracle home and get recommendations for the best patching strategy from the Oracle Update Advisor.
        $ rhpctl evaluate patch -image DB192600 -updatelag LATEST
        Performing software health check for image "DB192600".
        Software health status: "RED"
        Software health comment: "More than one cycle behind your policy.."
        Software Type: "DB"
        Current version: "19.26.0.0.0"
        Recommended version: "19.28"
        updateLag policy: latest(default)
        applyFrequency policy: quarterly (default)
3.  Download the gold image based on the input policy and additional patches or bug numbers requested. The Oracle Update Advisor directly downloads the patched image into an Oracle Advanced Cluster File System (Oracle ACFS) volume and Oracle FPP imports the patched image to an existing gold image.
        $ rhpctl evaluate patch -image DB192600 -generateimage -importtoimage DB192800
        Operation "rhpctl evaluate patch" scheduled with the job ID "53".

    The `-path` can be either an Oracle Grid Infrastructure home or an Oracle Database home, which you want to evaluate.
4.  Check the job status. If the current status is `EXECUTING`, then check again after the estimated time.
        $ rhpctl query job -jobid 53
        Job ID: 53
        User: grid
        Client: abc-rac1
        Scheduled job command: "rhpctl evaluate patch -image DB192600 -generateimage -importtoimage DB192800"
        Scheduled job execution start time: 2025-07-01T09:33:44Z. Equivalent local time: 2025-07-01 09:33:44
        Current status: EXECUTING
        Result file path: "/u01/app/obase/rhp_storage/chkbase/scheduled/job-53-2025-07-01-09:33:53.log"
        Metrics file path: "/u01/app/obase/rhp_storage/chkbase/scheduled/job-53-2025-07-01-09:33:53.json"
        Job execution start time: 2025-07-01 09:33:53

        Result file "/u01/app/obase/rhp_storage/chkbase/scheduled/job-53-2025-07-01-09:33:53.log" contents:
        ======================JOB_EXECUTION_DETAILS_START======================
        User: grid
        Client: abc-rac1
        Scheduled job command: "rhpctl evaluate patch -image DB192600 -generateimage -importtoimage DB192800"
        Job execution start time: 2025-07-01 09:33:53
        Current status: EXECUTING
        =======================JOB_EXECUTION_DETAILS_END=======================
        ...
        Software health status: "RED"
        Software health comment: "More than one cycle behind your policy."
        Software Type: "DB"
        Current version: "19.26.0.0.0"
        Recommended version: "19.28"
        updateLag policy: latest (default)
        applyFrequency policy: quarterly (default)
        ...
        Downloading image...
        Downloaded "1,442,775,040" bytes so far, continuing download...
        Downloaded "2,786,754,560" bytes so far, continuing download...
        Downloaded "3,961,995,124" bytes so far, continuing download...
        Image downloaded succesfully at location "/u01/app/obase/rhp_storage/images/ipatchplanimage405412/swhome".
        Importing image "DB192800"...

        Creating a new ACFS file system for image "DB192800" ...
        ...
        Executing detach home operation...
        ========================================
        Starting Oracle Universal Installer...
        ...
        Successfully executed detach home operation.
5.  Patch the Oracle Database home and Oracle Grid Infrastructure home by following the steps described in Patching and Upgrading Oracle Database and Patching and Upgrading Oracle Grid Infrastructure.

**Related Topics**

- [patch Commands](patch-commands.md)
- [updateadvisor Commands](updateadvisor-commands.md)
- [Patching and Upgrading Oracle Database](patching-and-upgrading-oracle-database.md)
- [Patching and Upgrading Oracle Grid Infrastructure](patching-and-upgrading-oracle-grid-infrastructure.md)

**Parent topic:** [Patching and Upgrading Oracle Grid Infrastructure](patching-and-upgrading-oracle-grid-infrastructure.md)
