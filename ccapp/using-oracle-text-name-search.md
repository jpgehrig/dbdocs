Oracle Text provides a name search feature to handle inaccurate data and misspelled names.

This chapter contains the following topics:

- Overview of Name Search

- Examples of Using Name Search

### 12.1 Overview of Name Search

Someone accustomed to the spelling rules of one culture can have difficulty applying those same rules to a name from a different culture. Name searching (also called name matching) provides a solution to match proper names that might differ in spelling due to orthographic variation. It also enables you to search for somewhat inaccurate data, such as might occur when a record's first name and surname are not properly segmented. The main advantage of name searching is the ability to handle somewhat inaccurate data.

### 12.2 Name Search Examples

These examples illustrate how to use `NDATA` sections to search on names.

    drop table people;

    create table people (
      full_name varchar2(2000)
    );

    insert into people values
    ('John Doe Smith');

    -- multi_column datastore is a convenient way of adding section tags around our data
    exec ctx_ddl.drop_preference('name_ds')
    begin
      ctx_ddl.create_preference('name_ds', 'MULTI_COLUMN_DATASTORE');
      ctx_ddl.set_attribute('name_ds', 'COLUMNS', 'full_name');
    end;
    /

    exec ctx_ddl.drop_section_group('name_sg');
    begin
      ctx_ddl.create_section_group('name_sg', 'BASIC_SECTION_GROUP');
      ctx_ddl.add_ndata_section('name_sg', 'full_name', 'full_name');
    end;
    /
    -- You can optionally load a thesaurus of nicknames
    -- HOST ctxload -thes -name nicknames -file nicknames.txt

    exec ctx_ddl.drop_preference('name_wl');
    begin
      ctx_ddl.create_preference('name_wl', 'BASIC_WORDLIST');
      ctx_ddl.set_attribute('name_wl', 'NDATA_ALTERNATE_SPELLING', 'FALSE');
      ctx_ddl.set_attribute('name_wl', 'NDATA_BASE_LETTER', 'TRUE');
      -- Include the following line only if you have loaded the thesaurus
      -- file nicknames.txt:
      -- ctx_ddl.set_attribute('name_wl', 'NDATA_THESAURUS', 'nicknames');
      ctx_ddl.set_attribute('name_wl', 'NDATA_JOIN_PARTICLES',
       'de:di:la:da:el:del:qi:abd:los:la:dos:do:an:li:yi:yu:van:jon:un:sai:ben:al');
    end;
    /

    create index people_idx on people(full_name) indextype is ctxsys.context
      parameters ('datastore name_ds section group name_sg wordlist name_wl');

    -- Now you can do name searches with the following SQL:

    var name varchar2(80);
    exec :name := 'Jon Doesmith'

    select /*+ FIRST_ROWS */ full_name, score(1)
      from people
      where contains(full_name,  'ndata( full_name, '||:name||') ',1)>0
      order by score(1) desc
    /

The following example illustrates a more complicated version of using `NDATA` sections to search on names:

    create table emp (
        first_name    varchar2(30),
        middle_name   varchar2(30),
        last_name     varchar2(30),
        email         varchar2(30),
        phone         varchar2(30));

    insert into emp values
    ('John', 'Doe', 'Smith', 'john.smith@example.org', '123-456-7890');

    -- user datastore procedure
    create or replace procedure empuds_proc
       (rid in rowid, tlob in out nocopy clob) is
         tag varchar2(30);
         phone varchar2(30);
    begin
      for c1 in (select FIRST_NAME, MIDDLE_NAME, LAST_NAME, EMAIL, PHONE
                 from emp
                 where rowid = rid)
      loop
         tag :='<email>';
         dbms_lob.writeappend(tlob, length(tag), tag);
         if (c1.EMAIL is not null) then
             dbms_lob.writeappend(tlob, length(c1.EMAIL), c1.EMAIL);
         end if;
         tag :='</email>';
         dbms_lob.writeappend(tlob, length(tag), tag);
         tag :='<phone>';
         dbms_lob.writeappend(tlob, length(tag), tag);
         if (c1.PHONE is not null) then
           phone := nvl(REGEXP_SUBSTR(c1.PHONE, '\d\d\d\d($|\s)'), ' ');
           dbms_lob.writeappend(tlob, length(phone), phone);
         end if;
         tag :='</phone>';
         dbms_lob.writeappend(tlob, length(tag), tag);
         tag :='<fullname>';
         dbms_lob.writeappend(tlob, length(tag), tag);
         if (c1.FIRST_NAME is not null) then
           dbms_lob.writeappend(tlob, length(c1.FIRST_NAME), c1.FIRST_NAME);
           dbms_lob.writeappend(tlob, length(' '), ' ');
         end if;
         if (c1.MIDDLE_NAME is not null) then
           dbms_lob.writeappend(tlob, length(c1.MIDDLE_NAME), c1.MIDDLE_NAME);
           dbms_lob.writeappend(tlob, length(' '), ' ');
         end if;
         if (c1.LAST_NAME is not null) then
           dbms_lob.writeappend(tlob, length(c1.LAST_NAME), c1.LAST_NAME);
         end if;
         tag :='</fullname>';
         dbms_lob.writeappend(tlob, length(tag), tag);
       end loop;
      end;
      /

    --list
    show errors

    exec ctx_ddl.drop_preference('empuds');
    begin
      ctx_ddl.create_preference('empuds', 'user_datastore');
      ctx_ddl.set_attribute('empuds', 'procedure', 'empuds_proc');
      ctx_ddl.set_attribute('empuds', 'output_type', 'CLOB');
    end;
    /

    exec ctx_ddl.drop_section_group('namegroup');
    begin
      ctx_ddl.create_section_group('namegroup', 'BASIC_SECTION_GROUP');
      ctx_ddl.add_ndata_section('namegroup', 'fullname', 'fullname');
      ctx_ddl.add_ndata_section('namegroup', 'phone', 'phone');
      ctx_ddl.add_ndata_section('namegroup', 'email', 'email');
    end;
    /

    -- Need to load nicknames thesaurus
    -- ctxload -thes -name nicknames -file dr0thsnames.txt
    -- You can find sample nicknames thesaurus file, dr0thsnames.txt, under
    -- $ORACLE_HOME/ctx/sample/thes directory.

    exec ctx_ddl.drop_preference('ndata_wl');
    begin
       ctx_ddl.create_preference('NDATA_WL', 'BASIC_WORDLIST');
       ctx_ddl.set_attribute('NDATA_WL', 'NDATA_ALTERNATE_SPELLING', 'FALSE');
       ctx_ddl.set_attribute('NDATA_WL', 'NDATA_BASE_LETTER', 'TRUE');
       ctx_ddl.set_attribute('NDATA_WL', 'NDATA_THESAURUS', 'NICKNAMES');
       ctx_ddl.set_attribute('NDATA_WL', 'NDATA_JOIN_PARTICLES',
        'de:di:la:da:el:del:qi:abd:los:la:dos:do:an:li:yi:yu:van:jon:un:sai:ben:al');
    end;
    /

    exec ctx_output.start_log('emp_log');
    create index name_idx on emp(first_name) indextype is ctxsys.context
    parameters ('datastore empuds section group namegroup wordlist ndata_wl
      memory 500M');

    exec ctx_output.end_log;

    -- Now you can do name searches with the following SQL:
    var name varchar2(80);
    exec :name := 'Jon Doesmith'

    select first_name, middle_name, last_name, phone, email, scr from
       (select /*+ FIRST_ROWS */
              first_name, middle_name, last_name, phone, email, score(1) scr
        from emp
        where contains(first_name,
              'ndata(phone, '||:name||') OR  ndata(email,'||:name||') OR
               ndata(fullname, '||:name||') ',1)>0
        order by score(1) desc
       ) where rownum <= 10;
