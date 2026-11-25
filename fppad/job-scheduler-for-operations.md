## Job Scheduler for Operations

The Oracle Fleet Patching and Provisioning job scheduler provides you with a mechanism to submit operations at a scheduled time instead of running the command immediately, querying the metadata of the job, and then deleting the job from the repository.

The Oracle Fleet Patching and Provisioning job scheduler includes the following features:

- Enables you to schedule a command to run at a specific point in time by providing the time value

- Performs the job and stores the metadata for the job, along with the current status of the job

- Stores the logs for each of the jobs that have run or are running

- Enables you to query job details ( for all jobs or for specific jobs, based on the user roles)

- Deletes jobs

- Authorizes the running, querying, and deleting of jobs, based on role-based access for users

Use the `-schedule ``timer_value` command parameter with any of the following RHPCTL commands to schedule certain Rapid Hope Provisioning operations:

- `rhpctl add workingcopy`

- `rhpctl import image`

- `rhpctl delete image`

- `rhpctl add database`

- `rhpctl move gihome`

- `rhpctl move database`

- `rhpctl upgrade database`

- `rhpctl addnode database`

- `rhpctl deletenode database`

- `rhpctl delete workingcopy`

For example:

    $ rhpctl add workingcopy -workingcopy 18_3 -image 18_3_Base -oraclebase /u01/app/oracle -schedule 2016-12-21T19:13:17+05

All commands are run in reference with the time zone of the server, according to the ISO-8601 value, and RHPCTL displays the command result by specifying the same time zone.

Command Results

RHPCTL stores any command that is run from the command queue on the Oracle Fleet Patching and Provisioning Server. When you query a command result by specifying the command identifier, then RHPCTL returns the path to the job output file, along with the results.

Job Operation

When you run an RHPCTL command with the `-schedule` parameter, the operation creates a job with a unique job ID that you can query to obtain the status of the job.

Job Status

At any point in time, a job can be in any of the following states:

    EXECUTED | TIMER_RUNNING | EXECUTING | UNKNOWN | TERMINATED

- `EXECUTED`: The job is complete.

- `TIMER_RUNNING`: The timer for the job is still running.

- `EXECUTING`: The timer for the job has expired and the job is running.

- `UNKNOWN`: There is an unexpected failure due to issues such as a target going down, nodes going down, or any resource failures.

- `TERMINATED`: There is an abrupt failure or the operation has stopped.

**Related Topics**

- [rhpctl delete job](job-commands.md)
- [rhpctl query job](job-commands.md)

**Parent topic:** [Advanced Oracle Fleet Patching and Provisioning Configurations](advanced-oracle-fpp-configurations.md)
