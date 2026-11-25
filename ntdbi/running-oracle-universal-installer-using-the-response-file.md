## Running Oracle Universal Installer Using the Response File

At this stage, you are ready to run Oracle Universal Installer at the command line, specifying the response file you created, to perform the installation.

On Windows, open the command prompt with Administrator privileges. The Oracle Universal Installer executable, `setup.exe`, provides several options. For help information about the full set of these options, run `setup.exe` with the `-help` option, for example:

    DRIVE_LETTER:\setup.exe_location setup -help

A new command window with the "Preparing to launch..." message appears.

To run Oracle Universal Installer, and specify a response file:

1.  Place the response file on the computer where you want to install Oracle Database.
2.  At a command prompt, run Oracle Universal Installer with the appropriate response file. On Windows, you must open command prompt with the Administrator privileges. For example:
        DRIVE_LETTER:\setup.exe_location setup [-silent] "variable=setting" [-nowelcome] [-noconfig] [-nowait] -responseFile
         filename

    where:

    - `filename`: Identifies the full path of the response file.

    - `setup.exe_location`: Indicates the location of `setup.exe`.

    - `-silent`: Runs Oracle Universal Installer in silent mode and suppresses the Welcome window.

    - `"``variable``=``setting``"` refers to a variable within the response file that you may prefer to run at the command line rather than set in the response file. Enclose the variable and its setting in quotes.

    - `-noconfig`: Suppresses running the configuration assistants during installation, performing a software-only installation instead.

    - `-nowait`: Closes the console window when the silent installation completes.

    If you save a response file during a silent installation, then Oracle Universal Installer saves the variable values that were specified in the original source response file into the new response file.

**Parent topic:** [Installing and Configuring Oracle Database Using Response Files](advance.md)
