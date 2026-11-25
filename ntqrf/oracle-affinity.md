Enables the scheduling of class threads on more than one processor group for systems with more than 64 CPUs.

This parameter must be manually added. Oracle recommends consulting Oracle Support Services before changing this parameter. The format is:

    namen:[[processorgroup0][processorgroup1][..2][..3],]{cpumask0[ cpumask1 cpumask2 cpumask3] | ALL};
    name1:[[0][1][2][3],]{cpumask0[ cpumask1 cpumask2 cpumask3] | ALL};
    name2:[[0][1][2][3],]{cpumask0[ cpumask1 cpumask2 cpumask3] | ALL};

Where, `processorgroup` is an optional parameter designating Windows CPU group. On systems with 64+ logical CPUs, Windows divides all available CPUs into 4 groups (0,1,2,3) with each group containing no more than 64 logical CPUs. By default, a process utilizes single processor group. The `processorgroup` parameter enables Oracle to use more than 64 logical CPUs. Refer to the specific hardware configuration to determine the valid processor groups.

**Note:**

You should not use the `ORACLE_AFFINITY` parameter with multiple processor groups on a system with fewer than 64 logical cores. On production servers any system with fewer than 64 logical CPUs can have only one processor group.

Each `name``n` setting must be the name of a background thread, `USER` for non-background (shadow) threads, or `DEF` for any thread type not handled specifically. Valid background thread names include `DBW0`, `LGWR`, `PMON`, `SMON`, `ARCH`, `RECO`, `CKPT`, `TRWR`, `J000` through `J999`, `P000` through `P481`, and any other name found in the `NAME` column of the `v$bgprocess` data dictionary view.

The cpumask sets the affinity mask of the Oracle Database process. Each affinity setting must be a valid affinity mask or its numeric equivalent for the corresponding thread name. Process affinity masks are used only when Oracle Services are first started. Each thread's affinity is set only when the individual thread is started (for example, at database startup time for the background threads).

Few examples, to use multiple processor groups in a system with 160 logical CPUs, `ORACLE_AFFINITY` registry key in `HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\KEY_HOMENAME` may be defined as follows:

The following examples show how set the `ORACLE_AFFINITY` registry key in `HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\KEY_HOMENAME` to use multiple processor groups in a system with 160 logical CPUs. In the following examples, it is assumed that: `USER`, `DEF` are thread class names; `0,1,2,3` are valid CPU groups in the system; and `4294967295` is a valid affinity mask in the corresponding CPU group.

- Affinitize `USER` (foreground) threads to all CPUs in `processorgroup1` or to all CPUs in `processorgroup2` or to all CPUs in `processorgroup3` while alternating between the processor groups for each new foreground thread. Also, affinitize `DEF` class threads to CPUs `0-31` in `processorgroup0`.

      USER:123,ALL;DEF:0,4294967295;

- Affinitize `USER` class threads either to CPUs `0-19` in `processorgroup0` or to CPUs `16-31` in `processorgroup2`. Also, affinitize `DEF` class threads to CPUs 0-19 in `processorgroup1`.

      USER:02,1048575 4294901760;DEF:1,1048575;

- Affinitize `USER` class threads to all the CPUs of all processor groups while alternating between the processor groups for each new foreground thread. Also, affinitize `DEF` class threads to CPUs `0-31` in all the processor groups while alternating between the processor groups for each new `DEF` class thread.

      USER:0123,ALL;DEF:0123,4294967295;

- Affinitize `USER` class threads to CPUs `0-31` in `processorgroup0`, CPUs `0-19` in `processorgroup1` and CPUs `0-19` in `processorgroup2` while alternating between the processor groups for each new foreground thread.

      USER:012,4294967295 1048575 1048575;

**Parent topic:** [About HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\KEY_HOMENAME](about-hkey-local-machine.md)
