The following sections detail how to configure the OLTP.

- If your communications protocol is SNA: proceed to Configuring the OLTP for Your SNA EnvironmentConfiguring the OLTP for Your SNA Environment.

- If your communications protocol is TCP/IP: proceed to Configuring the OLTP for Your TCP/IP EnvironmentConfiguring the OLTP for Your TCP/IP Environment.

  **Note:**

  On a gateway using TCP/IP support for IMS Connect, you must specify `EDIT=ULC` in the IMS `TRANSACT` macro if you need input case sensitivity. When using SNA support, you need not specify `EDIT=ULC` in the IMS `TRANSACT` macro.

### Configuring the OLTP for Your SNA Environment

The steps for configuring your OLTP to communicate with the Oracle Database Gateway for APPC vary, depending on which OLTP you are using and on which platform the OLTP is running. CICS Transaction Server for z/OS, IMS/TM, APPC/MVS, and z/OS are the currently supported OLTPs. Choose the instructions suitable to your OLTP from the following sections:

- "Configuring CICS Transaction Server for z/OS"

- "Configuring IMS/TM"

- "Configuring APPC/MVS"

  **Note:**

  You need only perform the configuration steps for an OLTP if this is a first-time configuration for that OLTP.

#### Configuring CICS Transaction Server for z/OS

If your OLTP is CICS Transaction Server for z/OS, then perform the following steps to configure it for communication with the gateway:

1.  Configure MVS VTAM for the SNA Server that will make the APPC connection to your system. At least one independent LU must be available to the gateway.

2.  Check the VTAM logmode table used by the CICS Transaction Server for z/OS. (The table name is specified in the `MODETAB` parameter in the VTAM APPL definition for CICS.) Ensure that an entry exists for APPC sessions with parallel session and sync-level support.

    The `oraplu62.asm `file in the `%ORACLE_HOME%\dg4appc\sna` directory contains a sample mode entry, including comments that indicate the required values in the mode entry.

3.  Using your file transfer facility, transfer the following files from the `%ORACLE_HOME%\dg4appc\demo\CICS `directory to the z/OS system on which you run CICS Transaction Server for z/OS:

    - `dfhcsdup.jcl` - JCL to run the CICS `DFHCSDUP` utility

    - `pgaflip.asm` - assembler source for the CICS `FLIP` transaction

    - `pgaflip.jcl` - JCL to assemble and linkedit the CICS `FLIP` transaction

4.  Using the comments in the `dfhcsdup.jcl` file, tailor the JCL and input statements to match your system setup, and submit it for batch execution. Performing this step updates your Transaction Server for z/OS system definitions.

5.  Using the instructions in the `pgaflip.jcl` file comments, tailor the JCL to match your system setup, and submit it for batch execution. Performing this step assembles and linkedits the `pgaflip.asm` file into a load module library accessible to your Transaction Server for z/OS through the `DFHRPL` DD statement in the CICS startup procedure.

6.  Log on to your CICS Transaction Server for z/OS and enter the following transaction:

        CEDA INSTALL GROUP(ORAPGA)

    This transaction installs the CICS connection and session definitions for APPC communication with the gateway on Windows. It also installs definitions for the sample CICS programs and transactions provided with the gateway.

Your CICS Transaction Server for z/OS configuration is now complete.

#### Configuring IMS/TM

If your OLTP is IMS/TM, then perform the following steps to configure IMS/TM and z/OS for communication with the gateway:

1.  Configure the IMS system for use with APPC.

2.  Configure MVS VTAM for the SNA APPC connection to Windows. At least one independent LU must be available for use by the gateway, unless you are using the IMS LU6.1 Adapter for LU6.2 applications. In this case, you must have one dependent LU defined for each concurrent session. For example, if you want to support 10 concurrent sessions, then you must have 10 dependent LUs defined.

3.  Check the VTAM logmode table used by IMS/TM. The table name is specified by the `MODETAB` parameter in the VTAM APPL definition.

    For APPC/IMS, ensure that an entry exists for APPC sessions with sync-level support and parallel session support. The `oralu62.asm` and `oraplu62.asm` files in the `%ORACLE_HOME%\dg4appc\sna` directory contain sample mode entries for single session and parallel session support, respectively. The samples include comments that indicate the required values in the mode entries.

4.  Using your file transfer facility, transfer the following files from the `%ORACLE_HOME%\dg4appc\demo\IMS `directory to the z/OS system on which you run IMS/TM:

    - `pgaflip.asm` is assembler source for IMS `FLIP` transaction;

    - `pgaflip.jcl` is JCL to assemble and linkedit IMS `FLIP` transaction;

    - `imsgen.asm` is IMS stage 1 gen definitions for the IMS `FLIP` transaction.

5.  Add the statements in the` imsgen.asm` file to your IMS stage 1 gen and run your IMS stage 1 and stage 2 gens. Use the online change utility to enable the new transaction definition.

6.  Using the comments in the `pgaflip.jcl` file, tailor the JCL to match your system setup and submit it for batch execution. This assembles and linkedits the `pgaflip.asm `file into a load module library that is accessible to your IMS/TM system and creates a PSB and an ACB for the `FLIP` transaction.

7.  Perform the tasks necessary on your system to make the new transaction available to IMS/TM. Depending on your system setup, you might have to restart IMS.

    The IMS/TM configuration is now complete.

#### Configuring APPC/MVS

If your OLTP is APPC/MVS, then perform the following steps to configure APPC/MVS for communication with the gateway:

1.  Configure MVS VTAM for the SNA APPC connection to Windows. At least one independent LU must be available for use by the gateway.

2.  Check the VTAM logmode table used by APPC/MVS. (The table name is specified by the `MODETAB` parameter in the VTAM APPL definition for APPC/MVS.) Ensure that an entry exists for APPC sessions with `SYNCLEVEL` and parallel session support. The `oraplu62.asm` file in the `%ORACLE_HOME%\dg4appc\sna` directory contains a sample mode entry, including comments that indicate the required values in the mode entry.

3.  Allocate a partitioned dataset (PDS) on your z/OS system where the sample files are placed. The PDS should be allocated with `RECFM=FB`, `LRECL=80`, and a `BLKSIZE` suitable for the device type on which it resides. Approximately two tracks of `3390` disk space are required with one directory block. Oracle suggests naming this partitioned dataset (PDS) `ORAPGA.APPCMVS.SAMPLIB`.

4.  Using the file transfer facility, transfer the following files from the `%ORACLE_HOME%\dg4appc\demo\MVS `directory to the z/OS PDS you allocated in the previous step, using the following specified member names:

    - `pgaflip.jcl` is JCL to add an APPC/MVS TP profile and to define the execution environment for the transaction. Store this file in your z/OS PDS as member `PGAFLIPJ`.

    - `pgaflip.rex` is the REXX source for the APPC/MVS `PGAFLIP` transaction. Store this file in your z/OS PDS as member `PGAFLIP`.

5.  Using the comments in the `pgaflip.jcl` file, tailor the JCL to match your system setup and submit it for batch execution. Performing this step defines the APPC/MVS TP profile for the `PGAFLIP` transaction and stores it in the APPC/MVS profile dataset. Ensure that you change the dataset name in the JCL to match the name of the z/OS PDS allocated in Step 3.

The APPC/MVS configuration is now complete.

- Now that you have completed configuration of the network on a gateway using the SNA protocol, proceed to [Gateway Configuration Using SNA Communication Protocol](configure-appc-gateway-using-sna.md) .

- If you wish to configure commit-confirm, then instructions for this configuration can be found in [Configuring Commit-Confirm](configure-appc-gateway-using-sna.md).

### Configuring the OLTP for Your TCP/IP Environment

These are the steps for configuring the OLTP to communicate with Oracle Database Gateway for APPC using TCP/IP for IMS Connect. IMS/TM, through IMS Connect, is the only supported OLTP for this release of the gateway.

Perform the following steps to configure IMS/TM and z/OS for communication with the gateway:

1.  Configure the IMS system.
2.  Configure IMS Connect.
    For information on how to configure IMS Connect, refer to the IBM IMS Connect Guide and Reference.
3.  Using your file transfer facility, transfer the following files from the `%ORACLE_HOME%\dg4appc\demo\IMS` directory to the z/OS system on which you run IMS/TM:
    - `pgaflip.asm` is assembler source for IMS `FLIP` transaction;

    - `pgaflip.jcl` is JCL to assemble and linkedit IMS `FLIP` transaction;

    - `imsgen.asm` is IMS stage 1 gen definitions for the IMS `FLIP` transaction.
4.  Add the statements in the `imsgen.asm `file to the IMS stage 1 gen and run your IMS stage 1 and stage 2 gens. Use the online change utility to enable the new transaction definition.
5.  Using the comments in the `pgaflip.jcl` file, tailor the JCL to match your system setup and submit it for batch execution. This assembles and linkedits the pgaflip.asm file into a load module library that is accessible to your IMS/TM system and creates a PSB and an ACB for the `FLIP` transaction.
6.  Perform the tasks necessary on your system to make the new transaction available to IMS/TM. Depending on your system setup, you might have to restart IMS.

The IMS/TM configuration is now complete.

- At this point, proceed to [Gateway Configuration Using TCP/IP Communication Protocol](configure-appc-gateway-using-tcp-ip.md) to complete configuration of the gateway and its components.
