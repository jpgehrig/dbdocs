## AutoUpgrade Messages and Process Description Terms

To understand how your upgrade checks and operations are proceeding, learn about the AutoUpgrade utility messages that are generated as the utility runs.

- Overview of AutoUpgrade Job IDs
  An AutoUpgrade **Job** is a unit of work associated with an upgrade, which is identified by a job identifier (`jobid`).
- Overview of AutoUpgrade Stages
  AutoUpgrade utility jobs pass through a series of phases, called **stages**, during which specific actions are performed.
- Overview of AutoUpgrade Stage Operations and States
  In AutoUpgrade, **operation** describes actions performed during stages, and **state** indicates the status of a stage operation.

**Parent topic:** [Using AutoUpgrade for Oracle Database Upgrades](using-autoupgrade-oracle-database-upgrades.md)

### Overview of AutoUpgrade Job IDs

An AutoUpgrade **Job** is a unit of work associated with an upgrade, which is identified by a job identifier (`jobid`).

A job represents a set of actions that AutoUpgrade performs. Each job goes through a set of stages to accomplish its purpose. The job is identified by a unique positive integer, which is called a `jobid`. Each new AutoUpgrade job produces a new job ID (`jobid`) for each database found in the configuration file for the AutoUpgrade utility. If AutoUpgrade detects that a database with a `jobid` that you previously started exists on your system is incomplete, then AutoUpgrade identifies this existing `jobid` as a **resume** operation. In a resume operation, stages of a job identified by a `jobid` that did not complete during the previous AutoUpgrade run are continued from the point where they were stopped.

**Parent topic:** AutoUpgrade Messages and Process Description Terms

### Overview of AutoUpgrade Stages

AutoUpgrade utility jobs pass through a series of phases, called **stages**, during which specific actions are performed.

The actions that occur during a stage are defined by the **processing mode** that you select for AutoUpgrade: **Analyze**, **Fixups**, **Deploy**, and **Upgrade**.

AutoUpgrade has the following stages:

- SETUP: The initial stage that the AutoUpgrade utility job manager creates as part of the preparation for starting a job.
- PREUPGRADE: The stage in which AutoUpgrade performs checks of your system, based on your current system configuration to determine its readiness for upgrade, such as checking to determine if you have sufficient available disk space.
- PRECHECKS: The stage in which AutoUpgrade analyzes your source Oracle home to determine if the database meets the requirements for upgrade.
- GRP: The guaranteed restore point (GRP), which AutoUpgrade creates before starting the upgrade process. This option is only available for Oracle Database Enterprise Edition releases. It is not available for Oracle Database Standard Edition. Even though AutoUpgrade creates a GRP by default, Oracle highly recommends that you perform a backup before starting your upgrade.
- PREFIXUPS: The stage in which AutoUpgrade performs preupgrade fixups before starting the upgrade. For example, this is the stage in which AutoUpgrade gathers dictionary statistics on the source Oracle home.
- DRAIN: The stage during which AutoUpgrade shuts down the database.
- DBUPGRADE: The stage in which AutoUpgrade performs the upgrade, and compiles any invalid objects that are found after the upgrade completes.
- POSTCHECKS: The stage in which AutoUpgrade performs checks on the target Oracle home (the upgraded Oracle Database) before starting postupgrade fixups.
- POSTFIXUPS: The stage in which AutoUpgrade performs processing of postupgrade fixups, such as upgrading the time zone.
- POSTUPGRADE: The stage in which AutoUpgrade copies or merges the source Oracle home configuration files (`tnsnames.ora`, `sqlnet.ora`, and other files) to the target Oracle home.
- SYSUPDATES: The stage in which AutoUpgrade will bring up the Oracle RAC or an individual database for patching or upgrade.

**Parent topic:** AutoUpgrade Messages and Process Description Terms

### Overview of AutoUpgrade Stage Operations and States

In AutoUpgrade, **operation** describes actions performed during stages, and **state** indicates the status of a stage operation.

#### Understanding Operation Messages

An operation message is an internal phase message that describes what is happening during an AutoUpgrade state. There are two types of operation messages.

PREPARING: An AutoUpgrade instance is being created, initialized, or called, in preparation for completing an AutoUpgrade stage. This is an information message. When you see this message, there is no action for you to perform.

EXECUTING: AutoUpgrade is in the process of performing the main workflow of a stage. This is an information message. There is no action for you to perform.

#### Understanding State Messages

State messages indicate the status of the current workflow of the stage for which the message is displayed. There are four state messages:

- ABORTED: AutoUpgrade stopped performing the stage workflow, in response to a user request.

- ERROR: An error was encountered while the stage workflow was being performed. Review the cause of the error.

- FINISHED: AutoUpgrade successfully completed the workflow for the stage.

- RUNNING: AutoUpgrade is performing the stage workflow.

**Parent topic:** AutoUpgrade Messages and Process Description Terms
