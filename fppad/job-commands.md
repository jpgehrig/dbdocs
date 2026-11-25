## job Commands

Use commands with the `job` keyword to delete or query schedule jobs.

- rhpctl delete job
  Deletes a specific scheduled job from the repository.
- rhpctl query job
  Queries the current status of a scheduled job with a specific job ID.

**Parent topic:** [RHPCTL Command Reference](rhpctl-command-reference.md)

### rhpctl delete job

Deletes a specific scheduled job from the repository.

#### Syntax

    rhpctl delete job [-jobid job_id] [-force]

#### Parameters

Table A-40 rhpctl delete job Command Parameters

| Parameter         | Description                                                                                                                                                                                    |
|:------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-jobid ``job_id` | Optionally, you can specify the job ID value for the job you want to delete that you obtained while scheduling the job. If you choose not to use this parameter, then RHPCTL deletes all jobs. |
| `–force`          | Use this parameter to forcibly delete a job.                                                                                                                                                   |

#### Usage Notes

You must run this command on the Fleet Patching and Provisioning Server.

#### Example

To delete a job with a job ID of `1`:

    $ rhpctl delete job –jobid 1

**Parent topic:** job Commands

### rhpctl query job

Queries the current status of a scheduled job with a specific job ID.

#### Syntax

    rhpctl query job [-jobid job_id] [-status {FAILED | SUCCEEDED | SCHEDULED
       | EXECUTING | UNKNOWN | TERMINATED }] [-client client_name] [-user user_name]
      [-since timer_value] [-summary] [-eval] [-migrate]

#### Parameters

Table A-41 rhpctl query job Command Parameters

| Parameter                                                                | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:-------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-jobid ``job_id`                                                        | Optionally, you can specify the job ID value for the job you want to query. The job Id is obtained while scheduling the job.<br>If you choose this parameter, then the only other option you can specify is `-summary`. If you do not choose this parameter, then all jobs are queried.                                                                                                                                                                                            |
| `-status {EXECUTED | TIMER_RUNNING | EXECUTING | UNKNOWN | TERMINATED }` | Optionally, you can specify any of the following states of a job that you want to query:<br>• `EXECUTED`: The job is complete.<br>• `TIMER_RUNNING`: The timer for the job is still running.<br>• `EXECUTING`: The timer for the job has expired and is running.<br>• `UNKNOWN`: There is an unexpected failure due to issues such as a server going down, nodes going down, or any resource failures.<br>• `TERMINATED`: There is an abrupt failure or the operation has stopped. |
| `-client ``client_name``k`                                               | Optionally, you can specify the name of a client cluster for which you want to query jobs.                                                                                                                                                                                                                                                                                                                                                                                         |
| `-user ``user_name`                                                      | Optionally, you can specify the user name of the user for whom a software home is being provisioned.                                                                                                                                                                                                                                                                                                                                                                               |
| `-since ``timer_value`                                                   | Optionally, you can specify a date from which to query the jobs, in ISO-8601 format, as in the following example:<br>`2018-07-25T19:13:17+05`                                                                                                                                                                                                                                                                                                                                      |
| `-summary`                                                               | Optionally, you can use this parameter to return only job details.                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-eval`                                                                  | Optionally, you can use this parameter to query only evaluation jobs.                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-migrate`                                                               | Optionally, you can use this parameter to query only migration jobs.                                                                                                                                                                                                                                                                                                                                                                                                               |

#### Usage Notes

You must run this command on the Fleet Patching and Provisioning Server.

#### Example

To query a specified scheduled job:

    $ rhpctl query job –jobid 1

This command returns output similar to the following:

    Job ID: 1
    User: fred
    Client: fredlinux4
    Scheduled job command: "rhpctl import image -image DB-Image1 -imagetype ORACLEDBSOFTWARE -path /ade/fred_linux4/esw1 -schedule 2018-07-27T13:38:57Z"
    Scheduled job execution start time: 2018-07-27T05:38:57-08. Equivalent local time: 2018-07-27 05:38:57
    Current status: EXECUTED
    Result file path: "/scratch/rhp_storage/chkbase/scheduled/job-1-2017-11-27-05:39:14.log"
    Job execution start time: 2018-07-27 05:39:14
    Job execution end time: 2018-07-27 05:43:09
    Job execution elapsed time: 3 minutes 55 seconds

    Result file "/scratch/rhp_storage/chkbase/scheduled/job-1-2018-07-27-05:39:14.log" contents:
    slc05amw.example.com: Audit ID: 4
    slc05amw.example.com: Creating a new ACFS file system for image "DB-Image1" ...
    slc05amw.example.com: Copying files...
    slc05amw.example.com: Copying home contents...
    slc05amw.example.com: Changing the home ownership to user fred...
    slc05amw.example.com: Changing the home ownership to user fred...

**Parent topic:** job Commands
