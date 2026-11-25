Oracle Database Provider for DRDA needs several scripts to establish a proper environment.

### A.1 catdrdaas.sql

The script `catdrdaas.sql` creates Oracle Database Provider for DRDA catalog objects.

    Rem catdrdaas.sql
    Rem
    Rem Copyright (c) 2011, Oracle and/or its affiliates. All rights reserved.
    Rem
    Rem    NAME
    Rem      catdrdaas.sql - CATalog Oracle Database Provider for DRDA
    Rem
    Rem =====================================================================
    Rem Exit immediately if there are errors in the initial checks
    Rem =====================================================================

    WHENEVER SQLERROR EXIT;

    DOC
    #######################################################################
      Customer should create the SYSIBM tablespace

    Eg:
      create tablespace SYSIBM datafile 'sysibm01.dbf'
       size 70M reuse
       extent management local
       segment space management auto
       online;

    #######################################################################
    #

    @@prvtdpsadrda.plb

### A.2 catnodrdaas.sql

The script `catnodrdaas.sql` removes Oracle Database Provider for DRDA catalog objects

    Rem catnodrdaas.sql
    Rem
    Rem Copyright (c) 2011, 2013, Oracle and/or its affiliates.
    Rem All rights reserved.
    Rem
    Rem    NAME
    Rem      catnodrdaas.sql - CATalog NO Oracle Database Provider for DRDA
    Rem

    drop public synonym DBMS_DRDAAS;
    drop public synonym DBMS_DRDAAS_ADMIN;

    drop public synonym USER_DRDAASTRACE;
    drop public synonym DBA_DRDAASTRACE;

    drop public synonym ALL_DRDAASPACKAGE;
    drop public synonym USER_DRDAASPACKAGE;
    drop public synonym DBA_DRDAASPACKAGE;

    drop public synonym USER_DRDAASPACKSTMT;
    drop public synonym DBA_DRDAASPACKSTMT;

    drop public synonym ALL_DRDAASPACKAUTH;
    drop public synonym USER_DRDAASPACKAUTH;
    drop public synonym DBA_DRDAASPACKAUTH;

    drop public synonym ALL_DRDAASPACKSIDE;
    drop public synonym USER_DRDAASPACKSIDE;
    drop public synonym DBA_DRDAASPACKSIDE;


    drop role DRDAAS_USER_ROLE;
    drop role DRDAAS_ADMIN_ROLE;

    drop user SYSIBM cascade;

    commit;
    DOC
    #######################################################################
      Customer should drop the SYSIBM tablespace.

    Eg:
      drop tablespace SYSIBM;

    #######################################################################

### A.3 drdapkg_db2.sql

    Rem drdapkg_db2.sql
    Rem
    Rem Copyright (c) 2012, Oracle and/or its affiliates. All rights reserved.
    Rem
    Rem    NAME
    Rem      drdapkg_db2.sql  - Initialize DRDA-AS environment so that
    Rem                          packages can be bound and correct datatypes
    Rem                          are returned for various SQL constructs
    Rem
    Rem    DESCRIPTION
    Rem      The DRDA-AS environment needs to be initialized so that the initial
    Rem      packages (usually with an RDBCOLID of NULLID) can be bound.
    Rem      Using the DataDirect driver, those package names look like
    Rem          NULLID.DDOC510A, NULLID.DDOC510B, and NULLID.DDOC510C
    Rem      Using the IBM driver (libdb2.so), the package names look like
    Rem          NULLID.SYSTAT and NULLID.SYSshyxx (where s is one of L or S,
    Rem                    h is one of H or N, y is 1, 2, 3, or 4 and
    Rem                                          xx is somwhere in 00 through FF)
    Rem      Also, various columns must be TYPEMAPped -- their normal
    Rem      attributes must be altered.
    Rem
    Rem      The initial package bindings should be done under the id that runs
    Rem      this script. That is, if we run this script under the Oracle ID
    Rem      of xxxx, then the initial connection through an ODBC driver should be
    Rem      using that same id, namely xxxx.
    Rem
    Rem    NOTES
    Rem      The following is relevant when using the IBM driver: libdb2.so ...
    Rem        Note that the normal set of packages produced by the jdbcbinder
    Rem        process (db2jdbcbinder in DB2/LUW) defines packages with names like
    Rem        SYSSTAT and SYSLNmnn and SYSLHmnn. Thus, before running the
    Rem        jdbcbinder on DB2/LUW specifying the Oracle Id accepted in the prompt
    Rem        for this script, one needs to inform DRDA-AS that the id has the
    Rem        required privilege, namely to create ANY package in the NULLID
    Rem        schema. That is part of what we are doing here.
    Rem
    Rem      This script can be run ONLY by a user that has the ability to use
    Rem      the DRDAAS_ADMIN_ROLE which must be GRANTed to the user; also this
    Rem      role must be active either by being set as a default ROLE or
    Rem      by actively doing a SET ROLE DRDAAS_ADMIN_ROLE.

    SET ECHO ON
    SET FEEDBACK 1
    SET NUMWIDTH 10
    SET LINESIZE 80
    SET TRIMSPOOL ON
    SET TAB OFF
    SET PAGESIZE 100

    SET SERVEROUTPUT ON

    SHOW USER

    /* The following  will work even if DRDAAS_ADMIN_ROLE is not one of the */
    /* DEFAULT Roles, but HAS been GRANTed to the user running this script. */
    /* (A prerequisite of setting a DEFAULT ROLE for a user is that the user*/
    /*  has been GRANTed that ROLE).                                        */

    SET ROLE DRDAAS_ADMIN_ROLE;

    Prompt Enter the OracleID under which the initial package BINDs will be made
    Prompt Use quotes (') if needed.
    Accept OracleID
    Define BindID = &OracleID
    Prompt Enter default collection ID for package binding (usually NULLID)
    Prompt Use quotes (') if needed.
    Accept DefaultCollection
    Define DfltCollid = &DefaultCollection

    declare
     id_passed CONSTANT VARCHAR2(128) := '&&BindId';
     collid_passed CONSTANT VARCHAR2(128) := '&&DfltCollid';
     id_to_use VARCHAR2(128);
     collid_to_use VARCHAR2(128);
     id_len PLS_INTEGER;
     collid_len PLS_INTEGER;
     quote CONSTANT CHAR := '''';
    begin
     id_len := LENGTH(id_passed);
     collid_len := LENGTH(collid_passed);

     IF SUBSTR(id_passed, 1, 1) = quote AND SUBSTR(id_passed, id_len, 1) = quote
          THEN
        /* Use Id exactly as passed */
        id_to_use := SUBSTR(id_passed, 2, id_len - 2);
     ELSE
        id_to_use := UPPER(id_passed) ;
     END IF;
     IF SUBSTR(collid_passed, 1, 1) = quote AND
        SUBSTR(collid_passed, collid_len, 1) = quote THEN
        /* Use Collection ID  exactly as passed */
        collid_to_use :=  SUBSTR(collid_passed, 2, collid_len-2) ;
     ELSE
        collid_to_use :=  UPPER(collid_passed) ;
     END IF;

     -- The following section is pertinent to ALL flavors of DB2
     -- =========================================================

      -- The id of the specified  user will have ALL privileges for ANY Package in
      -- RDBCOLID=collid_to_use

      DBMS_DRDAAS_ADMIN.GRANT_PRIVILEGE( DBMS_DRDAAS_ADMIN.ALL_PRIVILEGE,
                                         collid_to_use,'*', id_to_use);

      commit;

      -- If you might want the id specified to create packages in rcbcolid= SCOTT,
      -- then you need to do the following:

      -- DBMS_DRDAAS_ADMIN.GRANT_PRIVILEGE(DBMS_DRDAAS_ADMIN.ALL_PRIVILEGE,
      --                                   'SCOTT','*', id_to_use);
      -- commit;

      -- Typemaps ...

      -- The described "type" for "COUNT(*)" columns in any package in the
      -- collid_to_use schema should be INTEGER

      -- General "COUNT(*)" case
      DBMS_DRDAAS_ADMIN.SET_TYPEMAP(collid_to_use,'*','COUNT(*)',
                                   'NUMBER=INTEGER');



      -- ==================================================
      -- The following section is pertinent ONLY to DB2/zOS
      -- ==================================================

      -- To use DB2 z/OS SPUFI asgainst DRDAAS, the given oracle-id must be able to
      -- define packages in the DSNESPCS and DSNESPRR schemas
      --
      -- DB2 z/OS SPUFI Packages

      DBMS_DRDAAS_ADMIN.GRANT_PRIVILEGE( DBMS_DRDAAS_ADMIN.ALL_PRIVILEGE,
                                        'DSNESPCS','*', id_to_use);
      DBMS_DRDAAS_ADMIN.GRANT_PRIVILEGE( DBMS_DRDAAS_ADMIN.ALL_PRIVILEGE,
                                        'DSNESPRR','*', id_to_use);
      commit;

      -- ======================================================================
      -- Specific DataDirect ODBC package discovery queries for DB2 z/OS

      -- When accessing the collid_to_use.DDOC510A package, the
      -- "column" MAX(SECTNO) referencing table SYSIBM.SYSPACKSTMT (which is a
      --  NUMBER in Oracle terms) should be described as a SMALLINT to the
      -- application

      DBMS_DRDAAS_ADMIN.SET_TYPEMAP(collid_to_use,'DDOC510A',
                                    'SYSIBM.SYSPACKSTMT:MAX(SECTNO)',
                                    'NUMBER=SMALL');

      -- Same as above but for package collid_to_use.DDOC510B

      DBMS_DRDAAS_ADMIN.SET_TYPEMAP(collid_to_use,'DDOC510B',
                                    'SYSIBM.SYSPACKSTMT:MAX(SECTNO)',
                                    'NUMBER=SMALL');


      -- When accessing the collid_to_use.DDOC510A  package, the
      -- "column" COUNT(DISTINCT(NAME)) referencing table SYSIBM.SYSPACKSTMT
      -- (which is  a NUMBER in Oracle terms) should be described as a SMALLINT to
      --  the  application

      DBMS_DRDAAS_ADMIN.SET_TYPEMAP(collid_to_use,'DDOC510A',
                                    'SYSIBM.SYSPACKSTMT:COUNT(DISTINCT(NAME))',
                                    'NUMBER=INTEGER');

      -- Same as above but for package collid_to_use.DDOC510B

      DBMS_DRDAAS_ADMIN.SET_TYPEMAP(collid_to_use,'DDOC510B',
                                    'SYSIBM.SYSPACKSTMT:COUNT(DISTINCT(NAME))',
                                    'NUMBER=INTEGER');
      commit;

      -- ======================================================================
      -- Specific DataDirect JDBC package discovery queries for DB2 z/OS

      -- When accessing the collid_to_use.DDJC360B package, the "column"
      -- COUNT(*)-1 referencing table SYSIBM.SYSPACKSTMT (which is  a NUMBER in
      -- Oracle terms) should be described as an INTEGER to the application

      DBMS_DRDAAS_ADMIN.SET_TYPEMAP(collid_to_use,'DDJC360B',
                                   'SYSIBM.SYSPACKSTMT:COUNT(*)-1',
                                   'NUMBER=INTEGER');

      -- When accessing the collid_to_use.DDJC360B package, the "column"
      -- COUNT(*)-1 referencing table SYSIBM.SYSPACKSTMT (which  might be described
      -- as NUMBER(0,-127) in Oracle terms) describe the column as an INTEGER
      -- to the application.

      DBMS_DRDAAS_ADMIN.SET_TYPEMAP(collid_to_use,'DDJC360B',
                                    'SYSIBM.SYSPACKSTMT:COUNT(*)-1',
                                    'NUMBER(0,-127)=INTEGER');
      commit;


      -- ==================================================
      --  the following section is pertinent ONLY to DB2/luw
      -- ==================================================

      -- ======================================================================
      -- Specific DataDirect ODBC package discovery queries for DB2/LUW

      DBMS_DRDAAS_ADMIN.SET_TYPEMAP(collid_to_use,'DDOC510A',
                                    'SYSIBM.SYSPLAN:MIN(TOTALSECT)',
                                    'NUMBER=SMALL');

      DBMS_DRDAAS_ADMIN.SET_TYPEMAP(collid_to_use,'DDOC510A',
                                    'SYSIBM.SYSPLAN:COUNT(*)',
                                    'NUMBER=INTEGER');
      --  DBMS_DRDAAS_ADMIN.SET_TYPEMAP(collid_to_use,'DDOC510A',
      --                                'MIN(TOTALSECT)', 'NUMBER=SMALL');
      commit;

      --  ==================================================
      --  The following section is pertinent ONLY to DB2/iOS
      --  ==================================================

      --  Currently empty!
    end;
    /

### A.4 drdasqtt_translator_setup.sql

    Rem drdasqtt_translator_setup.sql
    Rem
    Rem Copyright (c) 2012, Oracle and/or its affiliates. All rights reserved.
    Rem
    Rem    NAME
    Rem      drdasqtt_translator_setup.sql - Generalized script for setting up an
    Rem                                      external SQL translator
    Rem
    Rem
    Rem    DESCRIPTION
    Rem      This script can be used to set up any external SQL translator.
    Rem      Some translators, e.g., BableFish, may need extra customizations.
    Rem      For BabelFish, that would include the source/target SQL text for
    Rem      the fingerprint translations (to be inserted into
    Rem      DBA_SQL_TRANSLATIONS).
    Rem
    Rem    NOTES
    Rem      Should be run "/ as sysdba"
    Rem

    SET ECHO ON
    SET FEEDBACK 1
    SET NUMWIDTH 10
    SET LINESIZE 80
    SET TRIMSPOOL ON
    SET TAB OFF
    SET PAGESIZE 100
    SET SERVEROUTPUT ON

    show user

    Prompt Enter schema in which the SQL Translator Interface Package will be created as well
    Prompt as into which the third-party SQL translator will be loaded (usually SYSIBM).
    Accept  TRANS_PKG_SCHEMA_ Prompt 'SQL Translator Interface Package Schema:'
    DEFINE TRANSLATOR_PACKAGE_SCHEMA =  &TRANS_PKG_SCHEMA_

    Prompt Enter unqualified name of the SQL Translator Interface Package
    Accept  TRANS_PKG_NAME_ Prompt 'SQL Translator Interface Package Name:'
    DEFINE TRANSLATOR_PACKAGE_NAME = &TRANS_PKG_NAME_

    Prompt Enter schema in which the Translation Profile will be created:
    Accept  TRANS_PROFILE_SCHEMA_ Prompt 'Translation Profile Schema:'
    DEFINE TRANS_PROFILE_SCHEMA = &TRANS_PROFILE_SCHEMA_

    Prompt Enter the unqualified name of the translation profile:
    Accept  TRANS_PROFILE_NAME_ Prompt 'Translation Profile Name:'
    DEFINE TRANS_PROFILE_NAME =  &TRANS_PROFILE_NAME_

    Prompt Enter the "language" type of the translator: C, java, etc
    Accept TRANS_LANG_ Prompt 'Translator Language:'
    DEFINE TRANS_LANG = &TRANS_LANG_

    Prompt Enter the names of the third-party SQL Translator objects;
    Prompt They should be available through rdbms/drdaas/jlib/..
    Prompt If there is more than one object, enclose the entire set
    Prompt in four quotes, such as  ''''object_a object_b''''.
    Accept  EXTERNAL_CODE_ Prompt 'SQL Translator object(s):'
    DEFINE EXTERNAL_CODE  = '''&EXTERNAL_CODE_'''
    DEFINE EXTERNAL_CODE


    Prompt Enter the signature for the entry for 'translateSQL' in one of the
    Prompt  previously entered SQL Translator objects:
    Accept CALLOUT_TRANSLATE_SQL_ Prompt 'Entry for translateSQL:'
    DEFINE CALLOUT_TRANSLATE_SQL = '''&CALLOUT_TRANSLATE_SQL_'''

    Prompt Enter the signature for the entry for 'translateError' in one of the
    Prompt previously entered SQL Translator objects
    Accept CALLOUT_TRANSLATE_ERROR_ Prompt 'Callout for translateError:'
    DEFINE CALLOUT_TRANSLATE_ERROR = '''&CALLOUT_TRANSLATE_ERROR_'''


    Rem Create the SQL Translator Interface Package ...

    create or replace package &&TRANSLATOR_PACKAGE_SCHEMA..&&TRANSLATOR_PACKAGE_NAME as

      procedure translate_sql(sql_text              in  clob,
                              translated_text       out clob);

      procedure translate_error(error_code          in  binary_integer,
                                translated_code     out binary_integer,
                                translated_sqlstate out varchar2);

    end;
    /
    show errors

    declare
      COMP_ERROR exception;
      pragma EXCEPTION_INIT(COMP_ERROR, -24344);
      translateSQLcode CONSTANT VARCHAR2(1024) := &&CALLOUT_TRANSLATE_SQL;
      translateErrorcode CONSTANT VARCHAR2(1024) := &&CALLOUT_TRANSLATE_ERROR;
      translateSQLToUse VARCHAR2(1024);
      translateErrorToUse VARCHAR2(1024);
      ln NUMBER;
      quote CONSTANT CHAR := '''';
      my_cursor BINARY_INTEGER;
      n BINARY_INTEGER;
      i BINARY_INTEGER;
      package_body   VARCHAR2(1024);
      /* we can't use bind variables to substitute for the "name" part of the */
      /* procedures in the package body declaration; the "name" part MUST be a*/
      /* single-quoted string!!! ARGHHH !!!                                   */
      package_body_1 VARCHAR2(400) :=
           'create or replace package ' ||
              'body &&TRANSLATOR_PACKAGE_SCHEMA..&&TRANSLATOR_PACKAGE_NAME as '  ||
                'procedure translate_sql(sql_text              in  clob, '       ||
                                      '  translated_text       out clob) as '    ||
                  'language &&TRANS_LANG '                                       ||
                  'name ''';
      package_body_2 VARCHAR2(400) := ''' ;'                                    ||
                'procedure translate_error(error_code  in  binary_integer, '     ||
                                         ' translated_code out binary_integer,'  ||
                                        ' translated_sqlstate out varchar2) as ' ||
                  'language &&TRANS_LANG '                                       ||
                  'name ''';
      package_body_end VARCHAR2(10) := '''; end;';
    begin
      ln := LENGTH(translateSQLcode);
      IF SUBSTR(translateSQLCode,1,1) = quote AND
         SUBSTR(translateSQLCode,ln,1) = quote THEN
        translateSQLToUse := SUBSTR(translateSQLCode, 2, ln-2);
      ELSE
        translateSQLToUse := translateSQLCode;
      END IF;
      ln := LENGTH(translateErrorcode);
      IF SUBSTR(translateErrorCode,1,1) = quote AND
         SUBSTR(translateErrorCode,ln,1) = quote THEN
        translateErrorToUse := SUBSTR(translateErrorCode, 2, ln-2);
      ELSE
        translateErrorToUse := translateErrorCode;
      END IF;
      my_cursor := DBMS_SQL.OPEN_CURSOR;
      package_body := package_body_1 || translateSQLToUse || package_body_2 ||
                      translateErrorToUse || package_body_end;
      BEGIN
        DBMS_SQL.PARSE(my_cursor, package_body, DBMS_SQL.NATIVE);
      EXCEPTION
        when COMP_ERROR THEN DBMS_OUTPUT.PUT_LINE('SQLCODE=' || SQLCODE || ':' ||
                                                  SQLERRM);
      END;
      n := DBMS_SQL.EXECUTE(my_cursor);
      DBMS_SQL.CLOSE_CURSOR(my_cursor);
    end;
    /

    show errors

    Rem Load the Java code
    Rem CALL DBMS_JAVA.LOADJAVA('-definer -genmissing -schema SYSIBM
    Rem rdbms/drdaas/jlib/DBTooSQLAPI.jar rdbms/drdaas/jlib/DBTooTranslator.class',
    Rem '((* SYSIBM)(* PUBLIC)(* -))');
    Rem DBTooSQLAPI.jar and DBTooSQLTranslator.class are fictional names

    set serveroutput on

    show user

    Rem Load the .class and .jar objects as specified ...

    declare
      extcode VARCHAR2(4096) := &&EXTERNAL_CODE;
      real_extcode VARCHAR2(4096);
      first_parm_first_part VARCHAR2(128) :=
                     '-definer -genmissing -schema &&TRANSLATOR_PACKAGE_SCHEMA ';
      first_parm VARCHAR2(4096);
      ln NUMBER;
    begin
      ln := LENGTH(extcode);
      /* We might have a beginning and ending aprostrophe --*/
      /* we need to delete them                             */
      IF SUBSTR(extcode,1,1) = '''' AND SUBSTR(extcode,ln,1) = '''' THEN
         real_extcode := SUBSTR(extcode, 2, ln-2);
      ELSE
         real_extcode := extcode;
      END IF;
      first_parm := first_parm_first_part || ' ' || real_extcode;
    /*DBMS_OUTPUT.PUT_LINE('First parm ' || first_parm); */
      DBMS_JAVA.LOADJAVA(first_parm ,
                         '((* &&TRANSLATOR_PACKAGE_SCHEMA)(* PUBLIC)(* -))');
    end;
    /

    GRANT EXECUTE ON &&TRANSLATOR_PACKAGE_SCHEMA..&&TRANSLATOR_PACKAGE_NAME  to PUBLIC;

    GRANT CREATE SQL TRANSLATION PROFILE TO &&TRANS_PROFILE_SCHEMA;
    GRANT TRANSLATE ANY SQL TO &&TRANS_PROFILE_SCHEMA WITH ADMIN OPTION;

    CALL DBMS_SQL_TRANSLATOR.DROP_PROFILE('&&TRANS_PROFILE_SCHEMA..&&TRANS_PROFILE_NAME');
    CALL DBMS_SQL_TRANSLATOR.CREATE_PROFILE('&&TRANS_PROFILE_SCHEMA..&&TRANS_PROFILE_NAME');


    begin
        dbms_sql_translator.set_attribute('&&TRANS_PROFILE_SCHEMA..&&TRANS_PROFILE_NAME',
                            dbms_sql_translator.attr_translator,
                                        '&&TRANSLATOR_PACKAGE_SCHEMA..&&TRANSLATOR_PACKAGE_NAME');

     dbms_sql_translator.set_attribute('&&TRANS_PROFILE_SCHEMA..&&TRANS_PROFILE_NAME',
                            dbms_sql_translator.attr_translate_new_sql,
                                            dbms_sql_translator.attr_value_true);
    end;
    /

    GRANT ALL ON SQL TRANSLATION PROFILE &&TRANS_PROFILE_SCHEMA..
       &&TRANS_PROFILE_NAME TO &&TRANSLATOR_PACKAGE_SCHEMA ;
    GRANT USE ON SQL TRANSLATION PROFILE &&TRANS_PROFILE_SCHEMA..
       &&TRANS_PROFILE_NAME TO DRDAAS_USER_ROLE;

### A.5 drdasqt_set_profile_dd.sql

    Rem drdasqt_set_profile_dd.sql
    Rem
    Rem Copyright (c) 2012, Oracle and/or its affiliates. All rights reserved.
    Rem
    Rem    NAME
    Rem      drdasqt_set_profile_dd.sql - Set a sqllangprofile for each of
    Rem                                   the DataDirect (dd) packages.
    Rem

    SET ECHO ON
    SET FEEDBACK 1
    SET NUMWIDTH 10
    SET LINESIZE 80
    SET TRIMSPOOL ON
    SET TAB OFF
    SET PAGESIZE 100

    Rem You will be prompted for the profile name.
    Rem Must be run under an id that has access to the DRDAAS_ADMIN_ROLE role.

    Rem set echo on
    set serveroutput on


    SET ROLE DRDAAS_ADMIN_ROLE;

    prompt Enter the (qualified) profile name to use for DataDirect packages
    Accept SQLPROFILENAME
    Define PROFILE_NAMEX = &SQLPROFILENAME
    prompt Enter the default Package Collection (usually NULLID)
    Prompt Use quotes (') if needed
    Accept DefaultCollection
    Define PACKAGE_COLLECTIONX = &DefaultCollection

    declare
      TYPE FIRST_CHAR  IS VARRAY(4) of CHAR(1);
      TYPE SECOND_CHAR IS VARRAY(3) of CHAR(1);

      first_chr  FIRST_CHAR := FIRST_CHAR();
      second_chr SECOND_CHAR := SECOND_CHAR();
      package_name VARCHAR2(128);
      profile_name CONSTANT VARCHAR2(128) := '&&PROFILE_NAMEX';
      package_collection_as_passed CONSTANT VARCHAR2(128) :=
                                             '&&PACKAGE_COLLECTIONX';
      package_collection VARCHAR2(128);
      cmd VARCHAR2(255);
      quote CONSTANT CHAR := '''';
      ln BINARY_INTEGER;
    begin

      ln := LENGTH(package_collection_as_passed);
      IF SUBSTR(package_collection_as_passed, 1,  1) = quote AND
         SUBSTR(package_collection_as_passed, ln, 1) = quote THEN
        /* Use package_collection exactly as passed */
         package_collection := SUBSTR(package_collection_as_passed, 2, ln - 2);
      ELSE
         package_collection := UPPER(package_collection_as_passed) ;
      END IF;

      first_chr.EXTEND(4);
      first_chr(1) := 'C'; first_chr(2) := 'S';
      first_chr(3) := 'U'; first_chr(4) := 'R';
      second_chr.EXTEND(3);
      second_chr(1) := 'A'; second_chr(2) := 'B'; second_chr(3) := 'C';

      FOR f IN 1..first_chr.COUNT
      LOOP
        FOR s IN 1..second_chr.COUNT
        LOOP
           package_name := 'DDO' || first_chr(f) || '510' || second_chr(s);

           cmd := 'DBMS_DRDAAS_ADMIN.SET_PROFILE(' || package_collection || ',' ||
                                                      package_name  || ',' ||
                                                      profile_name  || ')';
           DBMS_OUTPUT.PUT_LINE('Doing ' || cmd);
           DBMS_DRDAAS_ADMIN.SET_PROFILE(package_collection, package_name,
                                          profile_name);

        END LOOP;
      END LOOP;
    end;
    /
