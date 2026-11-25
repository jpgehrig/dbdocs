Oracle Database Provider for DRDA provides command-line utility.

### 10.1 Command-line Utility

The command-line utility `drdactl` enables the user to control the Oracle DRDA Application Sever. It controls startup, shutdown, status and operational changes of the AS. The `drdactl` utility may be invoked with command arguments for immediate execution, or without arguments (the utility will prompt for commands).

#### 10.1.1 START

This command starts the designated instance.

##### Syntax

    START {instance_name}

#### 10.1.2 STOP

This command stops the designated running instance.

##### Syntax

    STOP {instance_name}

#### 10.1.3 STATUS

This command displays the current status of the designated running instance, and any currently connected session information.

##### Syntax

    STATUS {instance_name} {DETAIL}

#### 10.1.4 TRACE

This command disables or enables tracing at a specified level, for the specified session id.

##### Syntax

`TRACE {<instance_name>} <OFF|Level> {SESSION {<session_id>|ALL}}`

#### 10.1.5 PAUSE

This command pauses the session with the specified session id.

##### Syntax

    PAUSE {instance_name} SESSION <session_id>

#### 10.1.6 RESUME

This command resumes the session with the specified session id.

##### Syntax

    RESUME {instance_name} SESSION <session_id>

#### 10.1.7 RELOAD

This command causes the server to reload the instance configuration.

##### Syntax

    RELOAD {instance_name}

#### 10.1.8 EXIT

This command exits the utility and returns to the operating system.

##### Syntax

    EXIT
