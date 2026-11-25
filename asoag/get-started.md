## 2 Quick-start Setup Guide for Wallet Based Transparent Data Encryption

1.  Create the directories that will hold the TDE wallet (a PKCS#12 container that is encrypted with a key that is derived from the TDE wallet password).

    The last two commands change the ownership of the directories to `oracle:oinstall` and reduce the file privileges to the minimum:

    The `ORACLE_SID` in this example is `finance`:
        mkdir -pv /etc/ORACLE/KEYSTORES/finance/tde_seps
        chown -Rv oracle:oinstall /etc/ORACLE
        chmod -Rv 700 /etc/ORACLE

2.  Set static system parameter `WALLET_ROOT` to the directory that you just created:

        SYS> alter system set WALLET_ROOT = '/etc/ORACLE/KEYSTORES/$ORACLE_SID' scope = spfile;

3.  Set the static `TABLESPACE_ENCRYPTION` parameter to `AUTO_ENABLE`, so that all new tablespaces are encrypted, even if the `encryption` key-words are not part of the `create tablespace` commands:

        SYS> alter system set TABLESPACE_ENCRYPTION = AUTO_ENABLE scope = spfile;

4.  Restart the database to activate those two parameters.

5.  The next parameter defines AES256 as the default encryption encryption algorithm (it needs to be executed before the `create keystore` command, otherwise the default encryption algorithm remains AES128).

        SYS> alter system set "_TABLESPACE_ENCRYPTION_DEFAULT_ALGORITHM" = 'AES256' scope = both;

6.  The last parameter configures the database to use a TDE wallet for file-based TDE setup:

        SYS> alter system set TDE_CONFIGURATION = "KEYSTORE_CONFIGURATION=FILE" scope = both;

7.  Create a new password-protected and local auto-open TDE wallet; the local auto-open wallet enables automatic database restarts without DBA intervention to open the password-protected TDE wallet:

    (N.B.: This command also creates the `<WALLET_ROOT>/tde directory`)

        SYSKM> administer key management CREATE KEYSTORE identified by <wallet-pwd>;

        SYSKM> administer key management CREATE LOCAL AUTO_LOGIN KEYSTORE from keystore identified by <wallet-pwd>;

8.  Add the TDE wallet password as a secret into another (local) auto-open wallet in `<WALLET_ROOT>/tde_seps`. This allows you to hide the TDE wallet password from the SQL\*Plus command line and replace it with `EXTERNAL STORE`:

        SYSKM> administer key management ADD SECRET '<wallet-pwd>' for client 'TDE_WALLET' to LOCAL auto_login keystore '/etc/ORACLE/KEYSTORES/finance/tde_seps';

9.  In the root container database, set the first TDE master key:

        SYSKM> administer key management SET KEY force keystore identified by EXTERNAL STORE with backup container = current;

10. Create either a united or isolated PDB:
    - United PDBIn the PDB, set the first TDE master key:

          SYSKM:FINPDB19C> administer key management SET KEY force keystore identified by EXTERNAL STORE with backup;

    - Isolated PDB
      1.  : Create an isolated PDB with its own individual keystore and keystore password:

              SYSKM:FINPDB19C> administer key management CREATE KEYSTORE identified by <PDB-wallet-pwd>;

          This next command does three things:
          1.  It sets `TDE_CONFIGURATION` to `FILE` for the isolated PDB
          2.  It creates the `<PDB_GUID>/tde` directories under` <WALLET_ROOT>`
          3.  It creates an individual wallet for the PDB, with its own TDE wallet password (that is potentially unknown to the DBA of the root container)

      2.  Create a (local) auto-open wallet for the isolated PDB:

              SYSKM:FINPDB19C> administer key management CREATE LOCAL AUTO_LOGIN KEYSTORE from keystore identified by <PDB-wallet-pwd>;

      3.  Create the directory `<WALLET_ROOT>/<PDB_GUID>/tde_seps` by executing the output of the following command:

              SYS:FINPDB19C> select ' host mkdir -pvm700 '''||v.value||'/'||guid||'/tde_seps'';' from v$pdbs, v$parameter v where v.name like '%root%';

      4.  Add the TDE wallet password as a secret into the wallet in `<WALLET_ROOT>/<PDB_GUID>/tde_seps` by executing the output of the following command. This allows you to hide the TDE wallet password of the isolated PDB from the SQL\*Plus command line and replace it with `EXTERNAL STORE`:

              SYS:FINPDB19C> select ' administer key management ADD SECRET ''<PDB-wallet-pwd>'' for client ''TDE_WALLET'' to LOCAL auto_login keystore '''||v.value||'/'||guid||'/tde_seps/'';' from v$pdbs, v$parameter v where v.name like '%root%';

11. Encrypt the tablespaces in the PDB:

        SYS:FINPDB19C> alter tablespace USERS encryption ONLINE encrypt;
        SYS:FINPDB19C> alter tablespace SYSTEM encryption ONLINE encrypt;
        SYS:FINPDB19C> alter tablespace SYSAUX encryption ONLINE encrypt;

12. Confirm:

        SYS> select c.name as PDB_NAME, t.name as TBS_NAME, e.ENCRYPTIONALG as ALG, e.STATUS from v$tablespace t, v$encrypted_tablespaces e, v$containers c where e.ts# = t.ts# and e.con_id = t.con_id and e.con_id = c.con_id order by e.con_id, t.name;

        PDB_NAME        TBS_NAME             ALG     STATUS
        --------------- -------------------- ------- -------
        FINPDB19C       SYSAUX               AES256  NORMAL
        FINPDB19C       SYSTEM               AES256  NORMAL
        FINPDB19C       USERS                AES256  NORMAL

**Parent topic:** [Using Transparent Data Encryption](asopart1.md)
