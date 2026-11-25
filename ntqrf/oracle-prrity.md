Determines Windows scheduling priorities of the threads within the Oracle Database management system process.

The format is:

    name1:priority1;name2:priority2 . . .

The `name` class sets the `priority` class of the Oracle Database process. Threads can be assigned a priority either collectively or individually. The collective name `user` designates non-background (shadow) threads; the collective name `def` designates any thread type not handled specifically. Valid individual background thread names include `DBW0`, `LGWR`, `PMON`, `SMON`, `ARCH0`, `RECO`, `CKPT`, `TRWR`, `SNP0` through `SNP9`, and any other name found in the `NAME` column of the `v$bgprocess` data dictionary view.

The default value is `class:normal; def:normal`.

**Note:**

`ORACLE_PRRITY` is not automatically created for you in the registry. When it is not defined in the registry, Windows default values are used for thread priorities.

**Parent topic:** [About HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\KEY_HOMENAME](about-hkey-local-machine.md)
