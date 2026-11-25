Use the Oracle ORAchk and Oracle EXAchk `-fileattr` option and command flags to record and track file attribute settings, and compare snapshots.

### Syntax

    [-fileattr start]
    [-fileattr check]
    [-fileattr remove]
    [-fileattr [start|check] -includedir directories]
    [-fileattr [start|check] -excludediscovery]
    [-fileattr check -baseline baseline snapshot path]
    [-fileattr check –fileattronly]

Table A-6 List of Oracle ORAchk and Oracle EXAchk File Attribute Tracking Options

| Option                                               | Description                                                                                                                                                                                                                                                                                                                                                                                          |
|:-----------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-fileattr start`                                    | Takes file attribute snapshots of discovered directories, and stores the snapshots in the output directory.<br>By default, this option takes snapshots of Oracle Grid Infrastructure homes, and all the installed Oracle Database homes. If a user does not own a particular directory, then the tool does not take snapshots of the directory.                                                      |
| `-fileattr check`                                    | Takes a new snapshot of discovered directories, and compares it with the previous snapshot.                                                                                                                                                                                                                                                                                                          |
| `-fileattr remove`                                   | Removes file attribute snapshots and related files.                                                                                                                                                                                                                                                                                                                                                  |
| `-fileattr [start|check] -includedir ``directories`  | Specify a comma-delimited list of directories to check file attributes.<br>For example:<br>`./orachk -fileattr start -includedir "/root/home,/etc"`<br>`./orachk -fileattr check -includedir "/root/home,/etc"`                                                                                                                                                                                      |
| `-fileattr [start|check] -excludediscovery`          | Excludes the discovered directories.<br>For example:<br>`./orachk -fileattr start -includedir "/root/home,/etc" -excludediscovery    `                                                                                                                                                                                                                                                               |
| `-fileattr check -baseline ``baseline snapshot path` | Uses a snapshot that you designate as the baseline for a snapshot comparison. Provide the path to the snapshot that you want to use as the baseline.<br>A baseline is the starting file attributes that you want to compare to at later times. Current file attributes are compared to the baseline and a delta is reported.<br>For example:<br>`./orachk -fileattr check -baseline "/tmp/Snapshot"` |
| `-fileattr check –fileattronly`                      | Performs only file attributes check, and then exits Oracle ORAchk.<br>For example:<br>`./orachk -fileattr check -fileattronly`                                                                                                                                                                                                                                                                       |

**Parent topic:** [Oracle ORAchk and Oracle EXAchk Command-Line Options](orachk-and-exachk-command-line-options.md)
