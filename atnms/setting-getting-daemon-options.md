Set the daemon options before you start the daemon. Reset the daemon options anytime after starting the daemon.

### To set the daemon options:

1.  Set the daemon options using the `–set` option.
    Set an option as follows:
        $ ./orachk –set "option_1=option_1_value"

        $ ./exachk –set "option_1=option_1_value"

    Set multiple options using the `name``=``value` format separated by semicolons as follows:
        $ ./orachk –set "option_1=option_1_value;option_2=option_2_value;option_n=option_n_value"

        $ ./exachk –set "option_1=option_1_value;option_2=option_2_value;option_n=option_n_value"

- AUTORUN_SCHEDULE
  Schedule recurring health check runs using the `AUTORUN_SCHEDULE` daemon option.
- AUTORUN_FLAGS
  The `AUTORUN_FLAGS` daemon option determines how health checks are run.
- NOTIFICATION_EMAIL
  Set the `NOTIFICATION_EMAIL` daemon option to send email notifications to the recipients you specify.
- collection_retention
  Set the `collection_retention` daemon option to purge health check collection results that are older than a specified number of days.
- PASSWORD_CHECK_INTERVAL
  The `PASSWORD_CHECK_INTERVAL` daemon option defines the frequency, in hours, for the daemon to validate the passwords entered when the daemon was started the first time.
- Setting Multiple Option Profiles for the Daemon
  Use only one daemon process for each server. Do not start a single daemon on multiple databases in a cluster, or multiple daemons on the same database.
- Getting Existing Options for the Daemon
  Query the values that you set for the daemon options.

**Parent topic:** [Managing the Oracle ORAchk and Oracle EXAchk Daemons](managing-daemons.md)

### 2.5.3.1 AUTORUN_SCHEDULE

Schedule recurring health check runs using the `AUTORUN_SCHEDULE` daemon option.

#### To schedule recurring health check runs:

1.  Set the `AUTORUN_SCHEDULE` option, as follows:
        AUTORUN_SCHEDULE=hour minute day month day_of_week

    where:
    - `minute` is 0-59 (Optional. If omitted, then 0 is used)

    - `hour` is 0–23

    - `day` is 1–31

    - `month` is 1–12

    - `day_of_week` is 0–6, where 0=Sunday and 6=Saturday

    Use the asterisk (\*) as a wildcard to specify multiple values separated by commas.

    Table 2-1 AUTORUN_SCHEDULE

    | Example                                     | Result                                                                        |
    |:--------------------------------------------|:------------------------------------------------------------------------------|
    | `"AUTORUN_SCHEDULE=0,15,30,45 * * * *"`     | Runs every 15 minutes.                                                        |
    | `"AUTORUN_SCHEDULE=* * * *"`                | Runs every hour.                                                              |
    | `"AUTORUN_SCHEDULE=3 * * 0"`                | Runs at 3 AM every Sunday.                                                    |
    | `"AUTORUN_SCHEDULE=2 * * 1, 3, 5"`          | Runs at 2 AM on Monday, Wednesday, and Friday.                                |
    | `"AUTORUN_SCHEDULE=4 1 * *"`                | Runs at 4 AM on the first day of every month.                                 |
    | `"AUTORUN_SCHEDULE=8,20 * * 1, 2, 3, 4, 5"` | Runs at 8 AM and 8 PM every Monday, Tuesday, Wednesday, Thursday, and Friday. |

For example:

    $ ./orachk –set "AUTORUN_SCHEDULE=3 * * 0"

    $ ./exachk –set "AUTORUN_SCHEDULE=3 * * 0"

**Parent topic:** Setting and Getting Options for the Daemon

### 2.5.3.2 AUTORUN_FLAGS

The `AUTORUN_FLAGS` daemon option determines how health checks are run.

#### To configure how health checks should run:

1.  Set the `AUTORUN_FLAGS` option as follows:
        AUTORUN_FLAGS=flags

    where, `flags` can be any combination of valid command-line flags.

    Table 2-2 AUTORUN_FLAGS

    | Example                                          | Result                                                                            |
    |:-------------------------------------------------|:----------------------------------------------------------------------------------|
    | `"AUTORUN_FLAGS=-profile dba"`                   | Runs only the `dba` profile checks.                                               |
    | `"AUTORUN_FLAGS=-profile sysadmin –tag syadmin"` | Runs only the `dba` profile checks and tags the output with the value `sysadmin`. |
    | `-excludeprofile ebs`                            | Runs all checks except the checks in the `ebs` profile.                           |

For example:

    $ ./orachk –set "AUTORUN_FLAGS=-profile sysadmin –tag sysadmin"

    $ ./exachk –set "AUTORUN_FLAGS=-profile sysadmin –tag sysadmin"

**Parent topic:** Setting and Getting Options for the Daemon

### 2.5.3.3 NOTIFICATION_EMAIL

Set the `NOTIFICATION_EMAIL` daemon option to send email notifications to the recipients you specify.

#### To configure email notifications:

The daemon notifies the recipients each time a health check run completes or when the daemon experiences a problem.

1.  Specify a comma-delimited list of email addresses, as follows:
        $ ./orachk –set "NOTIFICATION_EMAIL=some.person@acompany.com,another.person@acompany.com"

        $ ./exachk –set "NOTIFICATION_EMAIL=some.person@acompany.com,another.person@acompany.com"
2.  Test the email notification configuration using the `–testemail` option, as follows:
        $ ./orachk -testemail all

        $ ./exachk -testemail all

After the first health check run, the daemon notifies the recipients with report output attached.

For the subsequent health check runs after the first email notification, the daemon emails the summary of differences between the most recent runs to all recipients specified in the `NOTIFICATION_EMAIL` list.

**Parent topic:** Setting and Getting Options for the Daemon

### 2.5.3.4 collection_retention

Set the `collection_retention` daemon option to purge health check collection results that are older than a specified number of days.

#### To configure collection retention period:

1.  Set the `collection_retention` option, as follows:
        collection_retention=number_of_days

    If you do not set this option, then the daemon does not purge the stale collection.
2.  Set the `collection_retention` option to an appropriate number of days based on:
    - Frequency of your scheduled collections

    - Size of the collection results

    - Available disk space

For example:

    $ ./orachk –set "collection_retention=60"

    $ ./exachk –set "collection_retention=60"

**Parent topic:** Setting and Getting Options for the Daemon

### 2.5.3.5 PASSWORD_CHECK_INTERVAL

The `PASSWORD_CHECK_INTERVAL` daemon option defines the frequency, in hours, for the daemon to validate the passwords entered when the daemon was started the first time.

If an invalid password is found due to a password change, then the daemon stops, makes an entry in the daemon log, and then sends an email notification message to the recipients specified in the `NOTIFICATION_EMAIL` option.

#### To configure password validation frequency:

1.  Set the `PASSWORD_CHECK_INTERVAL` option, as follows:
        PASSWORD_CHECK_INTERVAL=number_of_hours

    If you do not set the `PASSWORD_CHECK_INTERVAL` option, then the daemon cannot actively check password validity and fails the next time the daemon tries to run after a password change. Using the `PASSWORD_CHECK_INTERVAL` option enables you to take corrective action and restart the daemon with the correct password rather than having failed collections.
2.  Set the `PASSWORD_CHECK_INTERVAL` option to an appropriate number of hours based on:
    - Frequency of your scheduled collections

    - Password change policies

For example:

    $ ./orachk –set "PASSWORD_CHECK_INTERVAL=1"

    $ ./exachk –set "PASSWORD_CHECK_INTERVAL=1"

**Parent topic:** Setting and Getting Options for the Daemon

### 2.5.3.6 Setting Multiple Option Profiles for the Daemon

Use only one daemon process for each server. Do not start a single daemon on multiple databases in a cluster, or multiple daemons on the same database.

The daemon does not start, if the daemon detects another Oracle ORAchk or Oracle EXAchk daemon process running locally.

Define multiple different run profiles using the same daemon. Defining multiple different run profiles enables you to run multiple different health checks with different daemon options, such as different schedules, email notifications, and automatic run flags. The daemon manages all profiles.

#### To set multiple option profiles for the daemon:

1.  Define daemon option profiles using the `–id ``id` option before the `–set` option.
    Where, `id` is the name of the profile

        $ ./orachk –id id –set "option=value"

        $ ./exachk –id id –set "option=value"

For example, if the database administrator wants to run checks within the `dba` profile and the system administrator wants to run checks in the `sysadmin` profile, then configure the daemon using the profiles option.

Define the database administrator profile as follows:

    $ ./orachk –id dba –set "NOTIFICATION_EMAIL=dba@example.com;\
       AUTORUN_SCHEDULE=4,8,12,16,20 * * *;AUTORUN_FLAGS=-profile dba –tag dba;\
       collection_retention=30"

    Created notification_email for ID[dba]
    Created autorun_schedule for ID[dba]
    Created autorun_flags for ID[dba]
    Created collection_retention for ID[dba]

    $ ./exachk –id dba –set "NOTIFICATION_EMAIL=dba@example.com;\
       AUTORUN_SCHEDULE=4,8,12,16,20 * * *; AUTORUN_FLAGS=-profile dba –tag dba;\
       collection_retention=30"

    Created notification_email for ID[dba]
    Created autorun_schedule for ID[dba]
    Created autorun_flags for ID[dba]
    Created collection_retention for ID[dba]

Define the system administrator profile as follows:

    $ ./orachk –id sysadmin –set "NOTIFICATION_EMAIL=sysadmin@example.com;\
       AUTORUN_SCHEDULE=3 * * 1,3,5; AUTORUN_FLAGS=-profile sysadmin –tag sysadmin;\
       collection_retention=60"

    Created notification_email for ID[sysadmin]
    Created autorun_schedule for ID[sysadmin]
    Created autorun_flags for ID[sysadmin]
    Created collection_retention for ID[sysadmin]

    $ ./exachk –id sysadmin –set "NOTIFICATION_EMAIL=sysadmin@example.com;\
       AUTORUN_SCHEDULE=3 * * 1,3,5; AUTORUN_FLAGS=-profile sysadmin –tag sysadmin;\
       collection_retention=60"

    Created notification_email for ID[sysadmin]
    Created autorun_schedule for ID[sysadmin]
    Created autorun_flags for ID[sysadmin]
    Created collection_retention for ID[sysadmin]

**Parent topic:** Setting and Getting Options for the Daemon

### 2.5.3.7 Getting Existing Options for the Daemon

Query the values that you set for the daemon options.

To query the values, use

    [-id ID] -get option | all

where:

- `ID` is a daemon option profile

- `option` is a specific daemon option you want to retrieve

- `all` returns values of all options

#### To get existing options for the daemon:

1.  To get a specific daemon option:
    For example:
        $ ./orachk –get NOTIFICATION_EMAIL

        ID: orachk.default
        ------------------------------------------
        notification_email = some.body@example.com

        $ ./exachk –get NOTIFICATION_EMAIL

        ID: exachk.default
        ------------------------------------------
        notification_email = some.body@example.com
2.  To query multiple daemon option profiles:
    For example:
        $ ./orachk –get NOTIFICATION_EMAIL

        ID: orachk.default
        ------------------------------------------
        notification_email = some.body@example.com

        ID: dba
        ------------------------------------------
        notification_email = dba@example.com

        ID: sysadmin
        ------------------------------------------
        notification_email = sysadmin@example.com

        $ ./exachk –get NOTIFICATION_EMAIL

        ID: exachk.default
        ------------------------------------------
        notification_email = some.person@example.com

        ID: dba
        ------------------------------------------
        notification_email = dba@example.com

        ID: sysadmin
        ------------------------------------------
        notification_email = sysadmin@example.com
3.  To limit the request to a specific daemon option profile, use the `–id ``ID`` -get ``option` option:
    For example:

    To get the `NOTIFICATION_EMAIL`  for a daemon profile called `dba` :

        $ ./orachk –id dba –get NOTIFICATION_EMAIL

        ID: dba
        ------------------------------------------
        notification_email = dba@example.com

        $ ./exachk –id dba –get NOTIFICATION_EMAIL

        ID: dba
        ------------------------------------------
        notification_email = dba@example.com
4.  To get all options set, use the `–get all` option:
    For example:
        $ ./orachk –get all

        ID: orachk.default
        ------------------------------------------
        notification_email = some.body@example.com
        autorun_schedule = 3 * * 0
        collection_retention = 30
        password_check_interval = 1

        $ ./exachk –get all

        ID: exachk.default
        ------------------------------------------
        notification_email = some.body@example.com
        autorun_schedule = 3 * * 0
        collection_retention = 30
        password_check_interval = 1
5.  To query all daemon option profiles:
    For example:
        $ ./orachk –get all

        ID: orachk.default
        ------------------------------------------
        notification_email = some.body@example.com
        autorun_schedule = 3 * * 0
        collection_retention = 30
        password_check_interval = 12

        ID: dba
        ------------------------------------------
        notification_email = dba@example.com
        autorun_schedule = 4,8,12,16,20 * * *
        autorun_flags = -profile dba – tag dba
        collection_retention = 30
        password_check_interval = 1

        ID: sysadmin
        ------------------------------------------
        notification_email = sysadmin@example.com
        autorun_schedule = 3 * * 1,3,5
        autorun_flags = -profile sysadmin –tag sysadmin
        collection_retension = 60
        password_check_interval = 1

        $ ./exachk –get all

        ID: exachk.default
        ------------------------------------------
        notification_email = some.body@example.com
        autorun_schedule = 3 * * 0
        collection_retention = 30
        password_check_interval = 1

        ID: dba
        ------------------------------------------
        notification_email = dba@example.com
        autorun_schedule = 4,8,12,16,20 * * *
        autorun_flags = -profile dba – tag dba
        collection_retention = 30
        password_check_interval = 1

        ID: sysadmin
        ------------------------------------------
        notification_email = sysadmin@example.com
        autorun_schedule = 3 * * 1,3,5
        autorun_flags = -profile sysadmin –tag sysadmin
        collection_retension = 60
        password_check_interval = 1
6.  To get all the options set for a daemon profile, for example, a daemon profile called `dba`:
        $ ./orachk –id dba –get all

        ID: dba
        ------------------------------------------
        notification_email = dba@example.com
        autorun_schedule = 4,8,12,16,20 * * *
        autorun_flags = -profile dba – tag dba
        collection_retention = 30
        password_check_interval = 1

        $ ./exachk –id dba –get all

        ID: dba
        ------------------------------------------
        notification_email = dba@example.com
        autorun_schedule = 4,8,12,16,20 * * *
        autorun_flags = -profile dba – tag dba
        collection_retention = 30
        password_check_interval = 1

**Parent topic:** Setting and Getting Options for the Daemon
