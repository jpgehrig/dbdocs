The following examples illustrate how to use Oracle JMS Types to [dequeue](glossary.md) and [enqueue](glossary.md) Oracle Database Advanced Queuing (AQ) messages.

- How to Setup the Oracle Database Advanced Queuing JMS Type Examples

- JMS BytesMessage Examples

- JMS StreamMessage Examples

- JMS MapMessage Examples

- More Oracle Database Advanced Queuing JMS Examples

### How to Set Up the Oracle Database Advanced Queuing JMS Type Examples

To run Example 16-3 through Example 16-8 follow these steps:

1.  Copy and save Example 16-1 as `setup.sql`.
2.  Run `setup.sql` as follows:
        sqlplus /NOLOG @setup.sql
3.  Log in to SQL\*Plus as `jmsuser/jmsuser`.
4.  Run the corresponding pair of SQL scripts for each type of [message](glossary.md).
    For JMS `BytesMessage`, for example, run Example 16-3 and Example 16-4.
5.  Ensure that your database parameter `java_pool-size` is large enough. For example, you can use `java_pool_size`=20M.

Example 16-1 Setting Up Environment for Running JMS Types Examples

    connect sys;
    enter password: password

    Rem
    Rem Create the JMS user: jmsuser
    Rem

    DROP USER jmsuser CASCADE;
    CREATE USER jmsuser IDENTIFIED BY jmsuser;
    GRANT EXECUTE ON DBMS_AQADM TO jmsuser;
    GRANT EXECUTE ON DBMS_AQ TO jmsuser;
    GRANT EXECUTE ON DBMS_LOB TO jmsuser;
    GRANT EXECUTE ON DBMS_JMS_PLSQL TO jmsuser;

    set echo offset verify offconnect sysDROP USER jmsuser CASCADE;ACCEPT password CHAR PROMPT 'Enter the password for JMSUSER: ' HIDECREATE USER jmsuser IDENTIFIED BY &password;GRANT DBA, AQ_ADMINISTRATOR_ROLE, AQ_USER_ROLE to jmsuser;GRANT EXECUTE ON DBMS_AQADM TO jmsuser;GRANT EXECUTE ON DBMS_AQ TO jmsuser;GRANT EXECUTE ON DBMS_LOB TO jmsuser;GRANT EXECUTE ON DBMS_JMS_PLSQL TO jmsuser;connect jmsuser/&password

    Rem
    Rem Creating five AQ queue tables and five queues for five payloads:
    Rem SYS.AQ$_JMS_TEXT_MESSAGE
    Rem SYS.AQ$_JMS_BYTES_MESSAGE
    Rem SYS.AQ$_JMS_STREAM_MESSAG
    Rem SYS.AQ$_JMS_MAP_MESSAGE
    Rem SYS.AQ$_JMS_MESSAGE
    Rem

    EXECUTE DBMS_AQADM.CREATE_QUEUE_TABLE (Queue_table => 'jmsuser.jms_qtt_text',
        Queue_payload_type => 'SYS.AQ$_JMS_TEXT_MESSAGE', compatible => '8.1.0');
    EXECUTE DBMS_AQADM.CREATE_QUEUE_TABLE (Queue_table => 'jmsuser.jms_qtt_bytes',
        Queue_payload_type => 'SYS.AQ$_JMS_BYTES_MESSAGE', compatible => '8.1.0');
    EXECUTE DBMS_AQADM.CREATE_QUEUE_TABLE (Queue_table => 'jmsuser.jms_qtt_stream',
        Queue_payload_type => 'SYS.AQ$_JMS_STREAM_MESSAGE', compatible => '8.1.0');
    EXECUTE DBMS_AQADM.CREATE_QUEUE_TABLE (Queue_table => 'jmsuser.jms_qtt_map',
        Queue_payload_type => 'SYS.AQ$_JMS_MAP_MESSAGE', compatible => '8.1.0');
    EXECUTE DBMS_AQADM.CREATE_QUEUE_TABLE (Queue_table => 'jmsuser.jms_qtt_general',
        Queue_payload_type => 'SYS.AQ$_JMS_MESSAGE', compatible => '8.1.0');
    EXECUTE DBMS_AQADM.CREATE_QUEUE (Queue_name => 'jmsuser.jms_text_que',
        Queue_table => 'jmsuser.jms_qtt_text');
    EXECUTE DBMS_AQADM.CREATE_QUEUE (Queue_name => 'jmsuser.jms_bytes_que',
        Queue_table => 'jmsuser.jms_qtt_bytes');
    EXECUTE DBMS_AQADM.CREATE_QUEUE (Queue_name => 'jmsuser.jms_stream_que',
        Queue_table => 'jmsuser.jms_qtt_stream');
    EXECUTE DBMS_AQADM.CREATE_QUEUE (Queue_name => 'jmsuser.jms_map_que',
        Queue_table => 'jmsuser.jms_qtt_map');
    EXECUTE DBMS_AQADM.CREATE_QUEUE (Queue_name => 'jmsuser.jms_general_que',
        Queue_table => 'jmsuser.jms_qtt_general');

    Rem
    Rem Starting the queues and enable both enqueue and dequeue
    Rem
    EXECUTE DBMS_AQADM.START_QUEUE (Queue_name => 'jmsuser.jms_text_que');
    EXECUTE DBMS_AQADM.START_QUEUE (Queue_name => 'jmsuser.jms_bytes_que');
    EXECUTE DBMS_AQADM.START_QUEUE (Queue_name => 'jmsuser.jms_stream_que');
    EXECUTE DBMS_AQADM.START_QUEUE (Queue_name => 'jmsuser.jms_map_que');
    EXECUTE DBMS_AQADM.START_QUEUE (Queue_name => 'jmsuser.jms_general_que');

    Rem The supporting utility used in the example to help display results in SQLPLUS enviroment

    Rem
    Rem Display a RAW data in SQLPLUS
    Rem
    create or replace procedure display_raw(rdata raw)
    IS
        pos                 pls_integer;
        length              pls_integer;
    BEGIN
        pos := 1;
        length := UTL_RAW.LENGTH(rdata);

        WHILE pos <= length LOOP
          IF pos+20 > length+1 THEN
            dbms_output.put_line(UTL_RAW.SUBSTR(rdata, pos, length-pos+1));
          ELSE
            dbms_output.put_line(UTL_RAW.SUBSTR(rdata, pos, 20));
          END IF;
          pos := pos+20;
        END LOOP;

    END display_raw;
    /

    show errors;

    Rem
    Rem Display a BLOB data in SQLPLUS
    Rem
    create or replace procedure display_blob(bdata blob)
    IS
        pos                 pls_integer;
        length              pls_integer;
    BEGIN
        length :=  dbms_lob.getlength(bdata);
        pos := 1;
        WHILE pos <= length LOOP
          display_raw(DBMS_LOB.SUBSTR(bdata, 2000, pos));
          pos := pos+2000;
        END LOOP;
    END display_blob;
    /

    show errors;

    Rem
    Rem Display a VARCHAR data in SQLPLUS
    Rem
    create or replace procedure display_varchar(vdata varchar)
    IS
        pos                 pls_integer;
        text_len            pls_integer;
    BEGIN
        text_len :=  length(vdata);
        pos := 1;

        WHILE pos <= text_len LOOP
          IF pos+20 > text_len+1 THEN
            dbms_output.put_line(SUBSTR(vdata, pos, text_len-pos+1));
          ELSE
            dbms_output.put_line(SUBSTR(vdata, pos, 20));
          END IF;
          pos := pos+20;
        END LOOP;

    END display_varchar;
    /

    show errors;

    Rem
    Rem Display a CLOB data in SQLPLUS
    Rem
    create or replace procedure display_clob(cdata clob)
    IS
        pos                 pls_integer;
        length              pls_integer;
    BEGIN
        length :=  dbms_lob.getlength(cdata);
        pos := 1;
        WHILE pos <= length LOOP
          display_varchar(DBMS_LOB.SUBSTR(cdata, 2000, pos));
          pos := pos+2000;
        END LOOP;
    END display_clob;
    /

    show errors;

    Rem
    Rem Display a SYS.AQ$_JMS_EXCEPTION data in SQLPLUS
    Rem
    Rem When application receives an ORA-24197 error, It means the JAVA stored
    Rem procedures has thrown some exceptions that could not be catergorized. The
    Rem user can use GET_EXCEPTION procedure of SYS.AQ$_JMS_BYTES_MESSAGE,
    Rem SYS.AQ$_JMS_STREAM_MESSAG or SYS.AQ$_JMS_MAP_MESSAGE
    Rem to retrieve a SYS.AQ$_JMS_EXCEPTION object which contains more detailed
    Rem information on this JAVA exception including the exception name, JAVA error
    Rem message and stack trace.
    Rem
    Rem This utility function is to help display the SYS.AQ$_JMS_EXCEPTION object in
    Rem SQLPLUS
    Rem
    create or replace procedure display_exp(exp SYS.AQ$_JMS_EXCEPTION)
    IS
        pos1                pls_integer;
        pos2                pls_integer;
        text_data           varchar(2000);
    BEGIN
        dbms_output.put_line('exception:'||exp.exp_name);
        dbms_output.put_line('err_msg:'||exp.err_msg);
        dbms_output.put_line('stack:'||length(exp.stack));
        pos1 := 1;
        LOOP
          pos2 := INSTR(exp.stack, chr(10), pos1);
          IF pos2 = 0 THEN
            pos2 := length(exp.stack)+1;
          END IF;

          dbms_output.put_line(SUBSTR(exp.stack, pos1, pos2-pos1));

          IF pos2 > length(exp.stack) THEN
            EXIT;
          END IF;

          pos1 := pos2+1;
        END LOOP;

    END display_exp;
    /

    show errors;

    EXIT;

Example 16-2 Setting Up the Examples

Example 16-1 performs the necessary setup for the JMS types examples. Copy and save it as `setup.sql`.

### JMS BytesMessage Examples

This section includes examples that illustrate enqueuing and dequeuing of a JMS `BytesMessage`.

Example 16-3 shows how to use JMS type member functions with `DBMS_AQ` functions to populate and enqueue a JMS `BytesMessage` represented as `sys.aq$_jms_bytes_message` type in the database. This message later can be dequeued by a JAVA [Oracle Java Message Service](glossary.md) (Oracle JMS) client.

Example 16-4 illustrates how to use JMS type member functions with `DBMS_AQ` functions to dequeue and retrieve data from a JMS `BytesMessage` represented as `sys.aq$_jms_bytes_message` type in the database. This message might be enqueued by an Oracle JMS client.

Example 16-3 Populating and Enqueuing a BytesMessage

    set echo offset verify offconnect sysDROP USER jmsuser CASCADE;ACCEPT password CHAR PROMPT 'Enter the password for JMSUSER: ' HIDECREATE USER jmsuser IDENTIFIED BY &password;GRANT DBA, AQ_ADMINISTRATOR_ROLE, AQ_USER_ROLE to jmsuser;GRANT EXECUTE ON DBMS_AQADM TO jmsuser;GRANT EXECUTE ON DBMS_AQ TO jmsuser;GRANT EXECUTE ON DBMS_LOB TO jmsuser;GRANT EXECUTE ON DBMS_JMS_PLSQL TO jmsuser;connect jmsuser/&password

    SET ECHO ON
    set serveroutput on

    DECLARE

        id                 pls_integer;
        agent              sys.aq$_agent := sys.aq$_agent(' ', null, 0);
        message            sys.aq$_jms_bytes_message;
        enqueue_options    dbms_aq.enqueue_options_t;
        message_properties dbms_aq.message_properties_t;
        msgid raw(16);

        java_exp           exception;
        pragma EXCEPTION_INIT(java_exp, -24197);
    BEGIN

        -- Consturct a empty BytesMessage object
        message := sys.aq$_jms_bytes_message.construct;

        -- Shows how to set the JMS header
        message.set_replyto(agent);
        message.set_type('tkaqpet1');
        message.set_userid('jmsuser');
        message.set_appid('plsql_enq');
        message.set_groupid('st');
        message.set_groupseq(1);

        -- Shows how to set JMS user properties
        message.set_string_property('color', 'RED');
        message.set_int_property('year', 1999);
        message.set_float_property('price', 16999.99);
        message.set_long_property('mileage', 300000);
        message.set_boolean_property('import', True);
        message.set_byte_property('password', -127);

        -- Shows how to populate the message payload of aq$_jms_bytes_message

        -- Passing -1 reserve a new slot within the message store of sys.aq$_jms_bytes_message.
        -- The maximum number of sys.aq$_jms_bytes_message type of messges to be operated at
        -- the same time within a session is 20. Calling clean_body function with parameter -1
        -- might result a ORA-24199 error if the messages currently operated is already 20.
        -- The user is responsible to call clean or clean_all function to clean up message store.
        id := message.clear_body(-1);

        -- Write data into the BytesMessage paylaod. These functions are analogy of JMS JAVA api's.
        -- See the document for detail.

        -- Write a byte to the BytesMessage payload
        message.write_byte(id, 10);

        -- Write a RAW data as byte array to the BytesMessage payload
        message.write_bytes(id, UTL_RAW.XRANGE(HEXTORAW('00'), HEXTORAW('FF')));

        -- Write a portion of the RAW data as byte array to BytesMessage payload
        -- Note the offset follows JAVA convention, starting from 0
        message.write_bytes(id, UTL_RAW.XRANGE(HEXTORAW('00'), HEXTORAW('FF')), 0, 16);

        -- Write a char to the BytesMessage payload
        message.write_char(id, 'A');

        -- Write a double to the BytesMessage payload
        message.write_double(id, 9999.99);

        -- Write a float to the BytesMessage payload
        message.write_float(id, 99.99);

        -- Write a int to the BytesMessage payload
        message.write_int(id, 12345);

        -- Write a long to the BytesMessage payload
        message.write_long(id, 1234567);

        -- Write a short to the BytesMessage payload
        message.write_short(id, 123);

        -- Write a String to the BytesMessage payload,
        -- the String is encoded in UTF8 in the message payload
        message.write_utf(id, 'Hello World!');

        -- Flush the data from JAVA stored procedure (JServ) to PL/SQL side
        -- Without doing this, the PL/SQL message is still empty.
        message.flush(id);

        -- Use either clean_all or clean to clean up the message store when the user
        -- do not plan to do paylaod population on this message anymore
        sys.aq$_jms_bytes_message.clean_all();
        --message.clean(id);

        -- Enqueue this message into AQ queue using DBMS_AQ package
        dbms_aq.enqueue(queue_name => 'jmsuser.jms_bytes_que',
                        enqueue_options => enqueue_options,
                        message_properties => message_properties,
                        payload => message,
                        msgid => msgid);

        EXCEPTION
        WHEN java_exp THEN
          dbms_output.put_line('exception information:');
          display_exp(sys.aq$_jms_stream_message.get_exception());

    END;
    /

    commit;

Example 16-4 Dequeuing and Retrieving JMS BytesMessage Data

    set echo off
    set verify off

    DROP USER jmsuser CASCADE;

    ACCEPT password CHAR PROMPT 'Enter the password for JMSUSER: ' HIDE

    CREATE USER jmsuser IDENTIFIED BY &password;
    GRANT EXECUTE ON DBMS_AQADM TO jmsuser;
    GRANT EXECUTE ON DBMS_AQ TO jmsuser;
    GRANT EXECUTE ON DBMS_LOB TO jmsuser;
    GRANT EXECUTE ON DBMS_JMS_PLSQL TO jmsuser;
    connect jmsuser/&password
    set echo on
    set serveroutput on size 20000

    DECLARE

        id                 pls_integer;
        blob_data          blob;
        clob_data          clob;
        blob_len           pls_integer;
        message            sys.aq$_jms_bytes_message;
        agent              sys.aq$_agent;
        dequeue_options    dbms_aq.dequeue_options_t;
        message_properties dbms_aq.message_properties_t;
        msgid raw(16);
        gdata              sys.aq$_jms_value;

        java_exp           exception;
        pragma EXCEPTION_INIT(java_exp, -24197);
    BEGIN
        DBMS_OUTPUT.ENABLE (20000);

        -- Dequeue this message from AQ queue using DBMS_AQ package
        dbms_aq.dequeue(queue_name => 'jmsuser.jms_bytes_que',
                        dequeue_options => dequeue_options,
                        message_properties => message_properties,
                        payload => message,
                        msgid => msgid);

        -- Retrieve the header
        agent := message.get_replyto;

        dbms_output.put_line('Type: ' || message.get_type ||
                             ' UserId: ' || message.get_userid ||
                             ' AppId: ' || message.get_appid ||
                             ' GroupId: ' || message.get_groupid ||
                             ' GroupSeq: ' || message.get_groupseq);

        -- Retrieve the user properties
        dbms_output.put_line('price: ' || message.get_float_property('price'));
        dbms_output.put_line('color: ' || message.get_string_property('color'));
        IF message.get_boolean_property('import') = TRUE THEN
           dbms_output.put_line('import: Yes' );
        ELSIF message.get_boolean_property('import') = FALSE THEN
           dbms_output.put_line('import: No' );
        END IF;
        dbms_output.put_line('year: ' || message.get_int_property('year'));
        dbms_output.put_line('mileage: ' || message.get_long_property('mileage'));
        dbms_output.put_line('password: ' || message.get_byte_property('password'));

    -- Shows how to retrieve the message payload of aq$_jms_bytes_message

    -- Prepare call, send the content in the PL/SQL aq$_jms_bytes_message object to
       -- Java stored procedure(Jserv) in the form of a byte array.
       -- Passing -1 reserves a new slot in msg store of sys.aq$_jms_bytes_message.
       -- Max number of sys.aq$_jms_bytes_message type of messges to be operated at
       -- the same time in a session is 20. Call clean_body fn. with parameter -1
       -- might result in ORA-24199 error if messages operated on are already 20.
       -- You must call clean or clean_all function to clean up message store.
        id := message.prepare(-1);

    -- Read data from BytesMessage paylaod. These fns. are analogy of JMS Java
    -- API's. See the JMS Types chapter for detail.
        dbms_output.put_line('Payload:');

        -- read a byte from the BytesMessage payload
        dbms_output.put_line('read_byte:' || message.read_byte(id));

        -- read a byte array into a blob object from the BytesMessage payload
        dbms_output.put_line('read_bytes:');
        blob_len := message.read_bytes(id, blob_data, 272);
        display_blob(blob_data);

        -- read a char from the BytesMessage payload
        dbms_output.put_line('read_char:'|| message.read_char(id));

        -- read a double from the BytesMessage payload
        dbms_output.put_line('read_double:'|| message.read_double(id));

        -- read a float from the BytesMessage payload
        dbms_output.put_line('read_float:'|| message.read_float(id));

        -- read a int from the BytesMessage payload
        dbms_output.put_line('read_int:'|| message.read_int(id));

        -- read a long from the BytesMessage payload
        dbms_output.put_line('read_long:'|| message.read_long(id));

        -- read a short from the BytesMessage payload
        dbms_output.put_line('read_short:'|| message.read_short(id));

        -- read a String from the BytesMessage payload.
        -- the String is in UTF8 encoding in the message payload
        dbms_output.put_line('read_utf:');
        message.read_utf(id, clob_data);
        display_clob(clob_data);

        -- Use either clean_all or clean to clean up the message store when the user
        -- do not plan to do paylaod retrieving on this message anymore
        message.clean(id);
        -- sys.aq$_jms_bytes_message.clean_all();

        EXCEPTION
        WHEN java_exp THEN
          dbms_output.put_line('exception information:');
          display_exp(sys.aq$_jms_bytes_message.get_exception());

    END;
    /

    commit;

### JMS StreamMessage Examples

This section includes examples that illustrate enqueuing and dequeuing of a JMS `StreamMessage`.

Example 16-5 shows how to use JMS type member functions with `DBMS_AQ` functions to populate and enqueue a JMS `StreamMessage` represented as `sys.aq$_jms_stream_message` type in the database. This message later can be dequeued by an Oracle JMS client.

Example 16-6 shows how to use JMS type member functions with `DBMS_AQ` functions to dequeue and retrieve data from a JMS `StreamMessage` represented as `sys.aq$_jms_stream_message` type in the database. This message might be enqueued by an Oracle JMS client.

Example 16-5 Populating and Enqueuing a JMS StreamMessage

    set echo off
    set verify off


    DROP USER jmsuser CASCADE;

    ACCEPT password CHAR PROMPT 'Enter the password for JMSUSER: ' HIDE

    CREATE USER jmsuser IDENTIFIED BY &password;
    GRANT EXECUTE ON DBMS_AQADM TO jmsuser;
    GRANT EXECUTE ON DBMS_AQ TO jmsuser;
    GRANT EXECUTE ON DBMS_LOB TO jmsuser;
    GRANT EXECUTE ON DBMS_JMS_PLSQL TO jmsuser;
    connect jmsuser/&password
    SET ECHO ON
    set serveroutput on

    DECLARE

        id                 pls_integer;
        agent              sys.aq$_agent := sys.aq$_agent(' ', null, 0);
        message            sys.aq$_jms_stream_message;
        enqueue_options    dbms_aq.enqueue_options_t;
        message_properties dbms_aq.message_properties_t;
        msgid raw(16);

        java_exp           exception;
        pragma EXCEPTION_INIT(java_exp, -24197);
    BEGIN

        -- Consturct a empty StreamMessage object
        message := sys.aq$_jms_stream_message.construct;

        -- Shows how to set the JMS header
        message.set_replyto(agent);
        message.set_type('tkaqpet1');
        message.set_userid('jmsuser');
        message.set_appid('plsql_enq');
        message.set_groupid('st');
        message.set_groupseq(1);

        -- Shows how to set JMS user properties
        message.set_string_property('color', 'RED');
        message.set_int_property('year', 1999);
        message.set_float_property('price', 16999.99);
        message.set_long_property('mileage', 300000);
        message.set_boolean_property('import', True);
        message.set_byte_property('password', -127);

        -- Shows how to populate the message payload of aq$_jms_stream_message

        -- Passing -1 reserve a new slot within the message store of sys.aq$_jms_stream_message.
        -- The maximum number of sys.aq$_jms_stream_message type of messges to be operated at
        -- the same time within a session is 20. Calling clean_body function with parameter -1
        -- might result a ORA-24199 error if the messages currently operated is already 20.
        -- The user is responsible to call clean or clean_all function to clean up message store.
        id := message.clear_body(-1);

        -- Write data into the message paylaod. These functions are analogy of JMS JAVA api's.
        -- See the document for detail.

        -- Write a byte to the StreamMessage payload
        message.write_byte(id, 10);

        -- Write a RAW data as byte array to the StreamMessage payload
        message.write_bytes(id, UTL_RAW.XRANGE(HEXTORAW('00'), HEXTORAW('FF')));

        -- Write a portion of the RAW data as byte array to the StreamMessage payload
        -- Note the offset follows JAVA convention, starting from 0
        message.write_bytes(id, UTL_RAW.XRANGE(HEXTORAW('00'), HEXTORAW('FF')), 0, 16);

        -- Write a char to the StreamMessage payload
        message.write_char(id, 'A');

        -- Write a double to the StreamMessage payload
        message.write_double(id, 9999.99);

        -- Write a float to the StreamMessage payload
        message.write_float(id, 99.99);

        -- Write a int to the StreamMessage payload
        message.write_int(id, 12345);

        -- Write a long to the StreamMessage payload
        message.write_long(id, 1234567);

        -- Write a short to the StreamMessage payload
        message.write_short(id, 123);

        -- Write a String to the StreamMessage payload
        message.write_string(id, 'Hello World!');

        -- Flush the data from JAVA stored procedure (JServ) to PL/SQL side
        -- Without doing this, the PL/SQL message is still empty.
        message.flush(id);

        -- Use either clean_all or clean to clean up the message store when the user
        -- do not plan to do paylaod population on this message anymore
        sys.aq$_jms_stream_message.clean_all();
        --message.clean(id);

        -- Enqueue this message into AQ queue using DBMS_AQ package
        dbms_aq.enqueue(queue_name => 'jmsuser.jms_stream_que',
                        enqueue_options => enqueue_options,
                        message_properties => message_properties,
                        payload => message,
                        msgid => msgid);

        EXCEPTION
        WHEN java_exp THEN
          dbms_output.put_line('exception information:');
          display_exp(sys.aq$_jms_stream_message.get_exception());

    END;
    /

    commit;

Example 16-6 Dequeuing and Retrieving Data From a JMS StreamMessage

    set echo off
    set verify off


    DROP USER jmsuser CASCADE;

    ACCEPT password CHAR PROMPT 'Enter the password for JMSUSER: ' HIDE

    CREATE USER jmsuser IDENTIFIED BY &password;
    GRANT EXECUTE ON DBMS_AQADM TO jmsuser;
    GRANT EXECUTE ON DBMS_AQ TO jmsuser;
    GRANT EXECUTE ON DBMS_LOB TO jmsuser;
    GRANT EXECUTE ON DBMS_JMS_PLSQL TO jmsuser;
    connect jmsuser/&password
    set echo on
    set serveroutput on

    DECLARE

        id                 pls_integer;
        blob_data          blob;
        clob_data          clob;
        message            sys.aq$_jms_stream_message;
        agent              sys.aq$_agent;
        dequeue_options    dbms_aq.dequeue_options_t;
        message_properties dbms_aq.message_properties_t;
        msgid raw(16);
        gdata              sys.aq$_jms_value;

        java_exp           exception;
        pragma EXCEPTION_INIT(java_exp, -24197);
    BEGIN
        DBMS_OUTPUT.ENABLE (20000);

        -- Dequeue this message from AQ queue using DBMS_AQ package
        dbms_aq.dequeue(queue_name => 'jmsuser.jms_stream_que',
                        dequeue_options => dequeue_options,
                        message_properties => message_properties,
                        payload => message,
                        msgid => msgid);

        -- Retrieve the header
        agent := message.get_replyto;

        dbms_output.put_line('Type: ' || message.get_type ||
                             ' UserId: ' || message.get_userid ||
                             ' AppId: ' || message.get_appid ||
                             ' GroupId: ' || message.get_groupid ||
                             ' GroupSeq: ' || message.get_groupseq);

        -- Retrieve the user properties
        dbms_output.put_line('price: ' || message.get_float_property('price'));
        dbms_output.put_line('color: ' || message.get_string_property('color'));
        IF message.get_boolean_property('import') = TRUE THEN
           dbms_output.put_line('import: Yes' );
        ELSIF message.get_boolean_property('import') = FALSE THEN
           dbms_output.put_line('import: No' );
        END IF;
        dbms_output.put_line('year: ' || message.get_int_property('year'));
        dbms_output.put_line('mileage: ' || message.get_long_property('mileage'));
        dbms_output.put_line('password: ' || message.get_byte_property('password'));

        -- Shows how to retrieve the message payload of aq$_jms_stream_message

        -- The prepare call send the content in the PL/SQL aq$_jms_stream_message object to
        -- JAVA stored procedure(Jserv) in the form of byte array.
        -- Passing -1 reserve a new slot within the message store of sys.aq$_jms_stream_message.
        -- The maximum number of sys.aq$_jms_stream_message type of messges to be operated at
        -- the same time within a session is 20. Calling clean_body function with parameter -1
        -- might result a ORA-24199 error if the messages currently operated is already 20.
        -- The user is responsible to call clean or clean_all function to clean up message store.
        id := message.prepare(-1);

        -- Assume the users know the types of data in the StreamMessage payload.
        -- The user can use the specific read function corresponding with the data type.
        -- These functions are analogy of JMS JAVA api's. See the document for detail.
        dbms_output.put_line('Retrieve payload by Type:');

        -- Read a byte from the StreamMessage payload
        dbms_output.put_line('read_byte:' || message.read_byte(id));

        -- Read a byte array into a blob object from the StreamMessage payload
        dbms_output.put_line('read_bytes:');
        message.read_bytes(id, blob_data);
        display_blob(blob_data);

        -- Read another byte array into a blob object from the StreamMessage payload
        dbms_output.put_line('read_bytes:');
        message.read_bytes(id, blob_data);
        display_blob(blob_data);

        -- Read a char from the StreamMessage payload
        dbms_output.put_line('read_char:'|| message.read_char(id));

        -- Read a double from the StreamMessage payload
        dbms_output.put_line('read_double:'|| message.read_double(id));

        -- Read a float from the StreamMessage payload
        dbms_output.put_line('read_float:'|| message.read_float(id));

        -- Read a int from the StreamMessage payload
        dbms_output.put_line('read_int:'|| message.read_int(id));

        -- Read a long from the StreamMessage payload
        dbms_output.put_line('read_long:'|| message.read_long(id));

        -- Read a short from the StreamMessage payload
        dbms_output.put_line('read_short:'|| message.read_short(id));

        -- Read a String into a clob data from the StreamMessage payload
        dbms_output.put_line('read_string:');
        message.read_string(id, clob_data);
        display_clob(clob_data);

        -- Assume the users do not know the types of data in the StreamMessage payload.
        -- The user can use read_object method to read the data into a sys.aq$_jms_value object
        -- These functions are analogy of JMS JAVA api's. See the document for detail.

        -- Reset the stream pointer to the begining of the message so that we can read throught
        -- the message payload again.
        message.reset(id);

        LOOP
          message.read_object(id, gdata);
          IF gdata IS NULL THEN
            EXIT;
          END IF;

          CASE gdata.type
            WHEN sys.dbms_jms_plsql.DATA_TYPE_BYTE      THEN
                     dbms_output.put_line('read_object/byte:' || gdata.num_val);
            WHEN sys.dbms_jms_plsql.DATA_TYPE_SHORT     THEN
                     dbms_output.put_line('read_object/short:' || gdata.num_val);
            WHEN sys.dbms_jms_plsql.DATA_TYPE_INTEGER   THEN
                     dbms_output.put_line('read_object/int:' || gdata.num_val);
            WHEN sys.dbms_jms_plsql.DATA_TYPE_LONG      THEN
                     dbms_output.put_line('read_object/long:' || gdata.num_val);
            WHEN sys.dbms_jms_plsql.DATA_TYPE_FLOAT     THEN
                     dbms_output.put_line('read_object/float:' || gdata.num_val);
            WHEN sys.dbms_jms_plsql.DATA_TYPE_DOUBLE    THEN
                     dbms_output.put_line('read_object/double:' || gdata.num_val);
            WHEN sys.dbms_jms_plsql.DATA_TYPE_BOOLEAN   THEN
                     dbms_output.put_line('read_object/boolean:' || gdata.num_val);
            WHEN sys.dbms_jms_plsql.DATA_TYPE_CHARACTER THEN
                     dbms_output.put_line('read_object/char:' || gdata.char_val);
            WHEN sys.dbms_jms_plsql.DATA_TYPE_STRING    THEN
                     dbms_output.put_line('read_object/string:');
                     display_clob(gdata.text_val);
            WHEN sys.dbms_jms_plsql.DATA_TYPE_BYTES     THEN
                     dbms_output.put_line('read_object/bytes:');
                     display_blob(gdata.bytes_val);
            ELSE dbms_output.put_line('No such data type');
          END CASE;

        END LOOP;

        -- Use either clean_all or clean to clean up the message store when the user
        -- do not plan to do paylaod retrieving on this message anymore
        message.clean(id);
        -- sys.aq$_jms_stream_message.clean_all();

        EXCEPTION
        WHEN java_exp THEN
          dbms_output.put_line('exception information:');
          display_exp(sys.aq$_jms_stream_message.get_exception());

    END;
    /

    commit;

### JMS MapMessage Examples

This section includes examples that illustrate enqueuing and dequeuing of a JMS `MapMessage`.

Example 16-7 shows how to use JMS type member functions with `DBMS_AQ` functions to populate and enqueue a JMS `MapMessage` represented as `sys.aq$_jms_map_message` type in the database. This message later can be dequeued by an Oracle JMS client.

Example 16-8 illustrates how to use JMS type member functions with `DBMS_AQ` functions to dequeue and retrieve data from a JMS `MapMessage` represented as `sys.aq$_jms_map_message` type in the database. This message can be enqueued by an Oracle JMS client.

Example 16-7 Populating and Enqueuing a JMS MapMessage

    set echo off
    set verify off


    DROP USER jmsuser CASCADE;

    ACCEPT password CHAR PROMPT 'Enter the password for JMSUSER: ' HIDE

    CREATE USER jmsuser IDENTIFIED BY &password;
    GRANT EXECUTE ON DBMS_AQADM TO jmsuser;
    GRANT EXECUTE ON DBMS_AQ TO jmsuser;
    GRANT EXECUTE ON DBMS_LOB TO jmsuser;
    GRANT EXECUTE ON DBMS_JMS_PLSQL TO jmsuser;
    connect jmsuser/&password

    SET ECHO ON
    set serveroutput on

    DECLARE

        id                 pls_integer;
        agent              sys.aq$_agent := sys.aq$_agent(' ', null, 0);
        message            sys.aq$_jms_map_message;
        enqueue_options    dbms_aq.enqueue_options_t;
        message_properties dbms_aq.message_properties_t;
        msgid raw(16);

        java_exp           exception;
        pragma EXCEPTION_INIT(java_exp, -24197);
    BEGIN

        -- Consturct a empty map message object
        message := sys.aq$_jms_map_message.construct;

        -- Shows how to set the JMS header
        message.set_replyto(agent);
        message.set_type('tkaqpet1');
        message.set_userid('jmsuser');
        message.set_appid('plsql_enq');
        message.set_groupid('st');
        message.set_groupseq(1);

        -- Shows how to set JMS user properties
        message.set_string_property('color', 'RED');
        message.set_int_property('year', 1999);
        message.set_float_property('price', 16999.99);
        message.set_long_property('mileage', 300000);
        message.set_boolean_property('import', True);
        message.set_byte_property('password', -127);

        -- Shows how to populate the message payload of aq$_jms_map_message

        -- Passing -1 reserve a new slot within the message store of sys.aq$_jms_map_message.
        -- The maximum number of sys.aq$_jms_map_message type of messges to be operated at
        -- the same time within a session is 20. Calling clean_body function with parameter -1
        -- might result a ORA-24199 error if the messages currently operated is already 20.
        -- The user is responsible to call clean or clean_all function to clean up message store.
        id := message.clear_body(-1);

        -- Write data into the message paylaod. These functions are analogy of JMS JAVA api's.
        -- See the document for detail.

        -- Set a byte entry in map message payload
        message.set_byte(id, 'BYTE', 10);

        -- Set a byte array entry using RAW data in map message payload
        message.set_bytes(id, 'BYTES', UTL_RAW.XRANGE(HEXTORAW('00'), HEXTORAW('FF')));

        -- Set a byte array entry using only a portion of the RAW data in map message payload
        -- Note the offset follows JAVA convention, starting from 0
        message.set_bytes(id, 'BYTES_PART', UTL_RAW.XRANGE(HEXTORAW('00'), HEXTORAW('FF')), 0, 16);

        -- Set a char entry in map message payload
        message.set_char(id, 'CHAR', 'A');

        -- Set a double entry in map message payload
        message.set_double(id, 'DOUBLE', 9999.99);

        -- Set a float entry in map message payload
        message.set_float(id, 'FLOAT', 99.99);

        -- Set a int entry in map message payload
        message.set_int(id, 'INT', 12345);

        -- Set a long entry in map message payload
        message.set_long(id, 'LONG', 1234567);

        -- Set a short entry in map message payload
        message.set_short(id, 'SHORT', 123);

        -- Set a String entry in map message payload
        message.set_string(id, 'STRING', 'Hello World!');

        -- Flush the data from JAVA stored procedure (JServ) to PL/SQL side
        -- Without doing this, the PL/SQL message is still empty.
        message.flush(id);

        -- Use either clean_all or clean to clean up the message store when the user
        -- do not plan to do paylaod population on this message anymore
        sys.aq$_jms_map_message.clean_all();
        --message.clean(id);

        -- Enqueue this message into AQ queue using DBMS_AQ package
        dbms_aq.enqueue(queue_name => 'jmsuser.jms_map_que',
                        enqueue_options => enqueue_options,
                        message_properties => message_properties,
                        payload => message,
                        msgid => msgid);

    END;
    /

    commit;

Example 16-8 Dequeuing and Retrieving Data From a JMS MapMessage

    set echo off
    set verify off


    DROP USER jmsuser CASCADE;

    ACCEPT password CHAR PROMPT 'Enter the password for JMSUSER: ' HIDE

    CREATE USER jmsuser IDENTIFIED BY &password;
    GRANT EXECUTE ON DBMS_AQADM TO jmsuser;
    GRANT EXECUTE ON DBMS_AQ TO jmsuser;
    GRANT EXECUTE ON DBMS_LOB TO jmsuser;
    GRANT EXECUTE ON DBMS_JMS_PLSQL TO jmsuser;
    connect jmsuser/&password

    set echo on
    set serveroutput on

    DECLARE

        id                 pls_integer;
        blob_data          blob;
        clob_data          clob;
        message            sys.aq$_jms_map_message;
        agent              sys.aq$_agent;
        dequeue_options    dbms_aq.dequeue_options_t;
        message_properties dbms_aq.message_properties_t;
        msgid              raw(16);
        name_arr           sys.aq$_jms_namearray;
        gdata              sys.aq$_jms_value;

        java_exp           exception;
        pragma EXCEPTION_INIT(java_exp, -24197);
    BEGIN
        DBMS_OUTPUT.ENABLE (20000);

        -- Dequeue this message from AQ queue using DBMS_AQ package
        dbms_aq.dequeue(queue_name => 'jmsuser.jms_map_que',
                        dequeue_options => dequeue_options,
                        message_properties => message_properties,
                        payload => message,
                        msgid => msgid);

        -- Retrieve the header
        agent := message.get_replyto;

        dbms_output.put_line('Type: ' || message.get_type ||
                             ' UserId: ' || message.get_userid ||
                             ' AppId: ' || message.get_appid ||
                             ' GroupId: ' || message.get_groupid ||
                             ' GroupSeq: ' || message.get_groupseq);

        -- Retrieve the user properties
        dbms_output.put_line('price: ' || message.get_float_property('price'));
        dbms_output.put_line('color: ' || message.get_string_property('color'));
        IF message.get_boolean_property('import') = TRUE THEN
           dbms_output.put_line('import: Yes' );
        ELSIF message.get_boolean_property('import') = FALSE THEN
           dbms_output.put_line('import: No' );
        END IF;
        dbms_output.put_line('year: ' || message.get_int_property('year'));
        dbms_output.put_line('mileage: ' || message.get_long_property('mileage'));
        dbms_output.put_line('password: ' || message.get_byte_property('password'));

        -- Shows how to retrieve the message payload of aq$_jms_map_message

        -- 'Prepare' sends the content in the PL/SQL aq$_jms_map_message object to
        -- Java stored procedure(Jserv) in the form of byte array.
        -- Passing -1 reserve a new slot within the message store of
        -- sys.aq$_jms_map_message. The maximum number of sys.aq$_jms_map_message
        -- type of messges to be operated at the same time within a session is 20.
        -- Calling clean_body function with parameter -1
        -- might result a ORA-24199 error if the messages currently operated is
        -- already 20. The user is responsible to call clean or clean_all function
        -- to clean up message store.
        id := message.prepare(-1);

        -- Assume the users know the names and types in the map message payload.
        -- The user can use names to get the corresponsing values.
        -- These functions are analogous to JMS Java API's. See JMS Types chapter
        -- for detail.
        dbms_output.put_line('Retrieve payload by Name:');

        -- Get a byte entry from the map message payload
        dbms_output.put_line('get_byte:' || message.get_byte(id, 'BYTE'));

        -- Get a byte array entry from the map message payload
        dbms_output.put_line('get_bytes:');
        message.get_bytes(id, 'BYTES', blob_data);
        display_blob(blob_data);

        -- Get another byte array entry from the map message payload
        dbms_output.put_line('get_bytes:');
        message.get_bytes(id, 'BYTES_PART', blob_data);
        display_blob(blob_data);

        -- Get a char entry from the map message payload
        dbms_output.put_line('get_char:'|| message.get_char(id, 'CHAR'));

        -- get a double entry from the map message payload
        dbms_output.put_line('get_double:'|| message.get_double(id, 'DOUBLE'));

        -- Get a float entry from the map message payload
        dbms_output.put_line('get_float:'|| message.get_float(id, 'FLOAT'));

        -- Get a int entry from the map message payload
        dbms_output.put_line('get_int:'|| message.get_int(id, 'INT'));

        -- Get a long entry from the map message payload
        dbms_output.put_line('get_long:'|| message.get_long(id, 'LONG'));

        -- Get a short entry from the map message payload
        dbms_output.put_line('get_short:'|| message.get_short(id, 'SHORT'));

        -- Get a String entry from the map message payload
        dbms_output.put_line('get_string:');
        message.get_string(id, 'STRING', clob_data);
        display_clob(clob_data);

        -- Assume users do not know names and types in map message payload.
        -- User can first retrieve the name array containing all names in the
        -- payload and iterate through the name list and get the corresponding
        -- value. These functions are analogous to JMS Java API's.
        -- See JMS Type chapter for detail.
        dbms_output.put_line('Retrieve payload by iteration:');

        -- Get the name array from the map message payload
        name_arr := message.get_names(id);

        -- Iterate through the name array to retrieve the value for each of the name.
        FOR i IN name_arr.FIRST..name_arr.LAST LOOP

        -- Test if a name exist in the map message payload
        -- (It is not necessary in this case, just a demostration on how to use it)
          IF message.item_exists(id, name_arr(i)) THEN
            dbms_output.put_line('item exists:'||name_arr(i));

        -- Because we do not know the type of entry, we must use sys.aq$_jms_value
        -- type object for the data returned
           message.get_object(id, name_arr(i), gdata);
           IF gdata IS NOT NULL THEN
            CASE gdata.type
            WHEN   sys.dbms_jms_plsql.DATA_TYPE_BYTE
              THEN dbms_output.put_line('get_object/byte:' || gdata.num_val);
            WHEN   sys.dbms_jms_plsql.DATA_TYPE_SHORT
              THEN dbms_output.put_line('get_object/short:' || gdata.num_val);
            WHEN   sys.dbms_jms_plsql.DATA_TYPE_INTEGER
              THEN dbms_output.put_line('get_object/int:' || gdata.num_val);
            WHEN   sys.dbms_jms_plsql.DATA_TYPE_LONG
              THEN dbms_output.put_line('get_object/long:' || gdata.num_val);
            WHEN   sys.dbms_jms_plsql.DATA_TYPE_FLOAT
              THEN dbms_output.put_line('get_object/float:' || gdata.num_val);
            WHEN   sys.dbms_jms_plsql.DATA_TYPE_DOUBLE
              THEN dbms_output.put_line('get_object/double:' || gdata.num_val);
            WHEN   sys.dbms_jms_plsql.DATA_TYPE_BOOLEAN
              THEN dbms_output.put_line('get_object/boolean:' || gdata.num_val);
            WHEN   sys.dbms_jms_plsql.DATA_TYPE_CHARACTER
              THEN dbms_output.put_line('get_object/char:' || gdata.char_val);
            WHEN   sys.dbms_jms_plsql.DATA_TYPE_STRING
              THEN dbms_output.put_line('get_object/string:');
                   display_clob(gdata.text_val);
            WHEN sys.dbms_jms_plsql.DATA_TYPE_BYTES
            THEN
                 dbms_output.put_line('get_object/bytes:');
                 display_blob(gdata.bytes_val);
              ELSE dbms_output.put_line('No such data type');
              END CASE;
            END IF;
          ELSE
            dbms_output.put_line('item not exists:'||name_arr(i));
          END IF;

        END LOOP;

        -- Use either clean_all or clean to clean up the message store when the user
        -- do not plan to do paylaod population on this message anymore
        message.clean(id);
        -- sys.aq$_jms_map_message.clean_all();

        EXCEPTION
        WHEN java_exp THEN
          dbms_output.put_line('exception information:');
          display_exp(sys.aq$_jms_stream_message.get_exception());

    END;
    /

    commit;

### More Oracle Database Advanced Queuing JMS Examples

The sample program in Example 16-9 enqueues a large `TextMessage` (along with JMS user properties) in an Oracle Database Advanced Queuing queue created through the Oracle JMS administrative interfaces to hold JMS `TEXT` messages. Both the `TextMessage` and `BytesMessage` enqueued in this example can be dequeued using Oracle JMS clients.

The sample program in Example 16-10 enqueues a large `BytesMessage`.

Example 16-9 Enqueuing a Large TextMessage

    DECLARE

        text        varchar2(32767);
        agent       sys.aq$_agent   := sys.aq$_agent(' ', null, 0);
        message     sys.aq$_jms_text_message;

        enqueue_options    dbms_aq.enqueue_options_t;
        message_properties dbms_aq.message_properties_t;
        msgid               raw(16);

    BEGIN

        message := sys.aq$_jms_text_message.construct;

        message.set_replyto(agent);
        message.set_type('tkaqpet2');
        message.set_userid('jmsuser');
        message.set_appid('plsql_enq');
        message.set_groupid('st');
        message.set_groupseq(1);

        message.set_boolean_property('import', True);
        message.set_string_property('color', 'RED');
        message.set_short_property('year', 1999);
        message.set_long_property('mileage', 300000);
        message.set_double_property('price', 16999.99);
        message.set_byte_property('password', 127);

        FOR i IN 1..500 LOOP
            text := CONCAT (text, '1234567890');
        END LOOP;

        message.set_text(text);

        dbms_aq.enqueue(queue_name => 'jmsuser.jms_text_t1',
                           enqueue_options => enqueue_options,
                           message_properties => message_properties,
                           payload => message,
                           msgid => msgid);

    END;

Example 16-10 Enqueuing a Large BytesMessage

    DECLARE

        text        VARCHAR2(32767);
        bytes       RAW(32767);
        agent       sys.aq$_agent   := sys.aq$_agent(' ', null, 0);
        message     sys.aq$_jms_bytes_message;
        body        BLOB;
        position    INT;

        enqueue_options    dbms_aq.enqueue_options_t;
        message_properties dbms_aq.message_properties_t;
        msgid raw(16);

    BEGIN

        message := sys.aq$_jms_bytes_message.construct;

        message.set_replyto(agent);
        message.set_type('tkaqper4');
        message.set_userid('jmsuser');
        message.set_appid('plsql_enq_raw');
        message.set_groupid('st');
        message.set_groupseq(1);

        message.set_boolean_property('import', True);
        message.set_string_property('color', 'RED');
        message.set_short_property('year', 1999);
        message.set_long_property('mileage', 300000);
        message.set_double_property('price', 16999.99);

    --  prepare a huge payload into a blob

        FOR i IN 1..1000 LOOP
            text := CONCAT (text, '0123456789ABCDEF');
        END LOOP;

        bytes := HEXTORAW(text);

        dbms_lob.createtemporary(lob_loc => body, cache => TRUE);
        dbms_lob.open (body, DBMS_LOB.LOB_READWRITE);
        position := 1 ;
        FOR i IN 1..10 LOOP
            dbms_lob.write ( lob_loc => body,
                    amount => FLOOR((LENGTH(bytes)+1)/2),
                    offset => position,
                    buffer => bytes);
            position := position + FLOOR((LENGTH(bytes)+1)/2) ;
        END LOOP;

    -- end of the preparation

        message.set_bytes(body);
        dbms_aq.enqueue(queue_name => 'jmsuser.jms_bytes_t1',
                           enqueue_options => enqueue_options,
                           message_properties => message_properties,
                           payload => message,
                           msgid => msgid);

        dbms_lob.freetemporary(lob_loc => body);
    END;
