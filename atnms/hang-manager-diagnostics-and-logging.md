Hang Manager autonomously resolves hangs and continuously logs the resolutions in the database alert logs and the diagnostics in the trace files.

Hang Manager logs the resolutions in the database alert logs as Automatic Diagnostic Repository (ADR) incidents with incident code `ORA–32701`.

You also get detailed diagnostics about the hang detection in the trace files. Trace files and alert logs have file names starting with `database instance``_dia0_`.

- The trace files are stored in the `$ ``ADR_BASE``/diag/rdbms/``database name``/``database instance``/incident/``incdir_xxxxxx` directory

- The alert logs are stored in the `$ ``ADR_BASE``/diag/rdbms/``database name``/``database instance``/trace` directory

Example 12-1 Hang Manager Trace File for a Local Instance

This example shows an example of the output you see for Hang Manager for the local database instance

    Trace Log File .../oracle/log/diag/rdbms/hm1/hm11/incident/incdir_111/hm11_dia0_11111_i111.trc
    Oracle Database 12c Enterprise Edition Release 12.2.0.1.0 - 64bit Production
    ...
    *** 2016-07-16T12:39:02.715475-07:00
    HM: Hang Statistics - only statistics with non-zero values are listed

                current number of active sessions 3
                  current number of hung sessions 1
      instance health (in terms of hung sessions) 66.67%
           number of cluster-wide active sessions 9
             number of cluster-wide hung sessions 5
       cluster health (in terms of hung sessions) 44.45%

    *** 2016-07-16T12:39:02.715681-07:00
    Resolvable Hangs in the System
                          Root       Chain Total               Hang
       Hang Hang          Inst Root  #hung #hung  Hang   Hang  Resolution
         ID Type Status   Num  Sess   Sess  Sess  Conf   Span  Action
      ----- ---- -------- ---- ----- ----- ----- ------ ------ -------------------
          1 HANG RSLNPEND    3    44     3     5   HIGH GLOBAL Terminate Process
      Hang Resolution Reason: Although hangs of this root type are typically
        self-resolving, the previously ignored hang was automatically resolved.

    kjznshngtbldmp: Hang's QoS Policy and Multiplier Checksum 0x0

      Inst  Sess   Ser             Proc  Wait
       Num    ID    Num      OSPID  Name Event
      ----- ------ ----- --------- ----- -----
          1    111  1234     34567    FG gc buffer busy acquire
          1     22 12345     34568    FG gc current request
          3     44 23456     34569    FG not in wait

Example 12-2 Error Message in the Alert Log Indicating a Hung Session

This example shows an example of a Hang Manager alert log on the master instance

    2016-07-16T12:39:02.616573-07:00
    Errors in file .../oracle/log/diag/rdbms/hm1/hm1/trace/hm1_dia0_i1111.trc  (incident=1111):
    ORA-32701: Possible hangs up to hang ID=1 detected
    Incident details in: .../oracle/log/diag/rdbms/hm1/hm1/incident/incdir_1111/hm1_dia0_11111_i1111.trc
    2016-07-16T12:39:02.674061-07:00
    DIA0 requesting termination of session sid:44 with serial # 23456 (ospid:34569) on instance 3
         due to a GLOBAL, HIGH confidence hang with ID=1.
         Hang Resolution Reason: Although hangs of this root type are typically
        self-resolving, the previously ignored hang was automatically resolved.
    DIA0: Examine the alert log on instance 3 for session termination status of hang with ID=1.

Example 12-3 Error Message in the Alert Log Showing a Session Hang Resolved by Hang Manager

This example shows an example of a Hang Manager alert log on the local instance for resolved hangs

    2016-07-16T12:39:02.707822-07:00
    Errors in file .../oracle/log/diag/rdbms/hm1/hm11/trace/hm11_dia0_11111.trc  (incident=169):
    ORA-32701: Possible hangs up to hang ID=1 detected
    Incident details in: .../oracle/log/diag/rdbms/hm1/hm11/incident/incdir_169/hm11_dia0_30676_i169.trc
    2016-07-16T12:39:05.086593-07:00
    DIA0 terminating blocker (ospid: 30872 sid: 44 ser#: 23456) of hang with ID = 1
         requested by master DIA0 process on instance 1
         Hang Resolution Reason: Although hangs of this root type are typically
        self-resolving, the previously ignored hang was automatically resolved.
         by terminating session sid:44 with serial # 23456 (ospid:34569)
    ...
    DIA0 successfully terminated session sid:44 with serial # 23456 (ospid:34569) with status 0.

**Parent topic:** [Resolving Database and Database Instance Hangs](purpose-hang-manager.md)
