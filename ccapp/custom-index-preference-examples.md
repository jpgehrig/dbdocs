This appendix describes a few custom index preference examples.

This appendix contains the following topics:

- Datastore Examples

- NULL_FILTER Example: Indexing HTML Documents

- PROCEDURE_FILTER Example

- BASIC_LEXER Example: Setting Printjoin Characters

- MULTI_LEXER Example: Indexing a Multi-Language Table

- BASIC_WORDLIST Example: Enabling Substring and Prefix Indexing

- BASIC_WORDLIST Example: Enabling Wildcard Index

### C.1 Datastore Examples

You can use datastore preferences to specify how your text is stored. These are the examples for setting some of the datastore preference types.

#### Specifying DIRECT_DATASTORE

This example creates a table with a `CLOB` column to store text data. It then populates two rows with text data and indexes the table by using the system-defined `CTXSYS.DEFAULT_DATASTORE` preference, which uses the `DIRECT_DATASTORE` preference type.

    create table mytable(id number primary key, docs clob);

    insert into mytable values(111555,'this text will be indexed');
    insert into mytable values(111556,'this is a default datastore example');
    commit;

    create index myindex on mytable(docs)
      indextype is ctxsys.context
      parameters ('DATASTORE CTXSYS.DEFAULT_DATASTORE');

#### Specifying MULTI_COLUMN_DATASTORE

This example creates a `MULTI_COLUMN_DATASTORE` datastore preference called `my_multi` on the three text columns to be concatenated and indexed:

    begin
    ctx_ddl.create_preference('my_multi', 'MULTI_COLUMN_DATASTORE');
    ctx_ddl.set_attribute('my_multi', 'columns', 'column1, column2, column3');
    end;

#### Specifying FILE_DATASTORE

This example creates a data storage preference by using `FILE_DATASTORE` to specify that the files to be indexed are stored in the operating system. The example uses `CTX_DDL.SET_ATTRIBUTE` to set the `PATH` attribute to the `/docs` directory.

    begin
    ctx_ddl.create_preference('mypref', 'FILE_DATASTORE');
    ctx_ddl.set_attribute('mypref', 'PATH', '/docs');
    end;

**Note:**

Starting with Oracle Database 19c, the Oracle Text type `FILE_DATASTORE` is deprecated. Use `DIRECTORY_DATASTORE` instead.

#### Specifying DIRECTORY_DATASTORE

This example creates a `DIRECTORY_DATASTORE` preference called `MYDS`. The example uses `CTX_DDL.SET_ATTRIBUTE` to set the `DIRECTORY` attribute to `myhome`, which is the Oracle directory object.

    exec ctx_ddl.create_preference('MYDS','DIRECTORY_DATASTORE')
    exec ctx_ddl.set_attribute('MYDS','DIRECTORY','myhome')

#### Specifying URL_DATASTORE

This example creates a `URL_DATASTORE` preference called `my_url` to which the `HTTP_PROXY`, `NO_PROXY`, and `TIMEOUT` attributes are set. The `TIMEOUT` attribute is set to 300 seconds. The defaults are used for the attributes that are not set.

    begin
     ctx_ddl.create_preference('my_url','URL_DATASTORE');
     ctx_ddl.set_attribute('my_url','HTTP_PROXY','www-proxy.us.example.com');
     ctx_ddl.set_attribute('my_url','NO_PROXY','us.example.com');
     ctx_ddl.set_attribute('my_url','TIMEOUT','300');
    end;

**Note:**

Starting with Oracle Database 19c, the Oracle Text type `URL_DATASTORE` is deprecated. Use `NETWORK_DATASTORE` instead.

#### Specifying NETWORK_DATASTORE

This example creates a `NETWORK_DATASTORE` preference called `NETWORK_PREF` to which the `HTTP_PROXY`, `NO_PROXY`, and `TIMEOUT` attributes are set. The `TIMEOUT` attribute is set to 300 seconds. The defaults are used for the attributes that are not set.

    begin
     ctx_ddl.create_preference('NETWORK_PREF','NETWORK_DATASTORE');
     ctx_ddl.set_attribute('NETWORK_PREF','HTTP_PROXY','www-proxy.us.example.com');
     ctx_ddl.set_attribute('NETWORK_PREF','NO_PROXY','us.example.com');
     ctx_ddl.set_attribute('NETWORK_PREF','TIMEOUT','300');
    end;
    /

**Related Topics**

- [Oracle Text Reference](../ccref/oracle-text-indexing-elements.md)

### C.2 NULL_FILTER Example: Indexing HTML Documents

If your document set is entirely in HTML, then Oracle recommends that you use `NULL_FILTER` in your filter preference because it does no filtering.

For example, to index an HTML document set, specify the system-defined preferences for `NULL_FILTER` and `HTML_SECTION_GROUP:`

    create index myindex on docs(htmlfile) indextype is ctxsys.context
      parameters('filter ctxsys.null_filter
      section group ctxsys.html_section_group');

### C.3 PROCEDURE_FILTER Example

Consider a `CTXSYS.NORMALIZE` filter procedure that you define with the following signature:

    PROCEDURE NORMALIZE(id IN ROWID, charset IN VARCHAR2, input IN CLOB,
    output IN OUT NOCOPY VARCHAR2);

To use this procedure as your filter, set up your filter preference:

    begin
    ctx_ddl.create_preference('myfilt', 'procedure_filter');
    ctx_ddl.set_attribute('myfilt', 'procedure', 'normalize');
    ctx_ddl.set_attribute('myfilt', 'input_type', 'clob');
    ctx_ddl.set_attribute('myfilt', 'output_type', 'varchar2');
    ctx_ddl.set_attribute('myfilt', 'rowid_parameter', 'TRUE');
    ctx_ddl.set_attribute('myfilt', 'charset_parameter', 'TRUE');
    end;

### C.4 BASIC_LEXER Example: Setting Printjoin Characters

Printjoin characters are nonalphanumeric characters that are to be included in index tokens, so that words such as vice-president are indexed as vice-president.

The following example sets printjoin characters to be the hyphen and underscore with `BASIC_LEXER:`

    begin
    ctx_ddl.create_preference('mylex', 'BASIC_LEXER');
    ctx_ddl.set_attribute('mylex', 'printjoins', '_-');
    end;

Create the index with printjoins characters set as previously shown:

    create index myindex on mytable ( docs )
      indextype is ctxsys.context
      parameters ( 'LEXER mylex' );

### C.5 MULTI_LEXER Example: Indexing a Multilanguage Table

Use the `MULTI_LEXER` preference type to index a column containing documents in different languages. For example, use this preference type when your text column stores documents in English, German, and French.

The first step is to create the multilanguage table with a primary key, a text column, and a language column:

    create table globaldoc (
       doc_id number primary key,
       lang varchar2(3),
       text clob
    );

Assume that the table holds mostly English documents, with some German and Japanese documents. To handle the three languages, you must create three sub-lexers, one for English, one for German, and one for Japanese:

    ctx_ddl.create_preference('english_lexer','basic_lexer');
    ctx_ddl.set_attribute('english_lexer','index_themes','yes');
    ctx_ddl.set_attribute('english_lexer','theme_language','english');

    ctx_ddl.create_preference('german_lexer','basic_lexer');
    ctx_ddl.set_attribute('german_lexer','composite','german');
    ctx_ddl.set_attribute('german_lexer','mixed_case','yes');
    ctx_ddl.set_attribute('german_lexer','alternate_spelling','german');

    ctx_ddl.create_preference('japanese_lexer','japanese_vgram_lexer');

Create the multi-lexer preference:

    ctx_ddl.create_preference('global_lexer', 'multi_lexer');

Because the stored documents are mostly English, make the English lexer the default by using `CTX_DDL.ADD_SUB_LEXER:`

    ctx_ddl.add_sub_lexer('global_lexer','default','english_lexer');

Add the German and Japanese lexers in their respective languages with the `CTX_DDL.ADD_SUB_LEXER` procedure. Also assume that the language column is expressed in the standard ISO 639-2 language codes, and add those codes as alternate values.

    ctx_ddl.add_sub_lexer('global_lexer','german','german_lexer','ger');
    ctx_ddl.add_sub_lexer('global_lexer','japanese','japanese_lexer','jpn');

Create the `globalx` index, specifying the multi-lexer preference and the language column in the parameter clause:

    create index globalx on globaldoc(text) indextype is ctxsys.context
    parameters ('lexer global_lexer language column lang');

### C.6 BASIC_WORDLIST Example: Enabling Substring and Prefix Indexing

This example improves performance for wildcard queries by setting the wordlist preference for prefix and substring indexing. For prefix indexing, the example creates token prefixes between three and four characters long.

    begin
    ctx_ddl.create_preference('mywordlist', 'BASIC_WORDLIST');
    ctx_ddl.set_attribute('mywordlist','PREFIX_INDEX','TRUE');
    ctx_ddl.set_attribute('mywordlist','PREFIX_MIN_LENGTH', '3');
    ctx_ddl.set_attribute('mywordlist','PREFIX_MAX_LENGTH', '4');
    ctx_ddl.set_attribute('mywordlist','SUBSTRING_INDEX', 'YES');
    end;

### C.7 BASIC_WORDLIST Example: Enabling Wildcard Index

Wildcard indexing supports fast and efficient wildcard search for all wildcard expressions.

This example creates a wordlist preference and enables the wildcard (“K-gram”) index. By default, the K-grams have a K value of `3:`

    begin
         ctx_ddl.create_preference('mywordlist','BASIC_WORDLIST');
         ctx_ddl.set_attribute('mywordlist','WILDCARD_INDEX','TRUE');
    end;

**See Also:**

[Oracle Text Reference](../ccref/oracle-text-indexing-elements.md) for more information about the `BASIC_WORDLIST` attributes table and the `WILDCARD_INDEX` and `WILDCARD_INDEX_K` attributes
