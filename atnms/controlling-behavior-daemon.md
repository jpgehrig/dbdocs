Use the list of commands in this section to control the behavior of the daemon.

### Syntax

    [-id id] –set daemon_option
    [-id id] -unset daemon_option | all
    [-id id] -get parameter | all
    [-d start]
    [-d start -debug]
    [-d stop]
    [-d stop_client]
    [-d status]
    [-d info]
    [-id id] -d nextautorun
    [-initsetup]
    [-initrmsetup]
    [-initcheck]

### Parameters

Table A-5 Daemon Options

| Option                                        | Description                                                                                                                         |
|:----------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------|
| `[-id ``id``] –set ``daemon_option`           | Optionally use `id` with the `set` command to set specific daemon usage profiles.                                                   |
| `[-id ``id``] -unset ``daemon_option`` | all` | Unsets the parameter.<br>Use with `–id ``id` to set a daemon profile-specific value.                                                |
| `[-id ``id``] -get ``parameter`` | all`       | Displays the value of the specified parameter or all the parameters.<br>Use with `–id ``id` to set a daemon profile-specific value. |
| `-d start`                                    | Starts the daemon.                                                                                                                  |
| `-d start —debug`                             | Starts the daemon in debug mode.                                                                                                    |
| `-d stop`                                     | Stops the daemon.                                                                                                                   |
| `-d stop_client`                              | Forces a running daemon client to stop.                                                                                             |
| `-d status`                                   | Checks the current status of the daemon.                                                                                            |
| `-d info`                                     | Displays details about the daemon.<br>The details include installation and when the daemon was started.                             |
| `[-id ``id``] -d nextautorun`                 | Displays details about when the next scheduled automatic run occurs.                                                                |
| `-initsetup`                                  | Sets the daemon auto restart function that starts the daemon when the node starts.                                                  |
| `-initrmsetup`                                | Removes the automatic restart functionality.                                                                                        |
| `-initcheck`                                  | Checks if the automatic restart functionality is set up.                                                                            |

**Parent topic:** [Oracle ORAchk and Oracle EXAchk Command-Line Options](orachk-and-exachk-command-line-options.md)
