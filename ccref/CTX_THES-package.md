## 14  CTX_THES Package

This chapter provides reference information for using the `CTX_THES` package to manage and browse thesauri. These thesaurus functions are based on the ISO-2788 and ANSI Z39.19 standards except where noted.

Knowing how information is stored in your thesaurus helps in writing queries with thesaurus operators. You can also use a thesaurus to extend the knowledge base, which is used for `ABOUT` queries in English and French and for generating document themes.

`CTX_THES` contains the following stored procedures and functions:

| Name               | Description                                                                                                 |
|:-------------------|:------------------------------------------------------------------------------------------------------------|
| ALTER_PHRASE       | Alters thesaurus phrase.                                                                                    |
| ALTER_THESAURUS    | Renames or truncates a thesaurus.                                                                           |
| BT                 | Returns all broader terms of a phrase.                                                                      |
| BTG                | Returns all broader terms generic of a phrase.                                                              |
| BTI                | Returns all broader terms instance of a phrase.                                                             |
| BTP                | Returns all broader terms partitive of a phrase.                                                            |
| CREATE_PHRASE      | Adds a phrase to the specified thesaurus.                                                                   |
| CREATE_RELATION    | Creates a relation between two phrases.                                                                     |
| CREATE_THESAURUS   | Creates the specified thesaurus.                                                                            |
| CREATE_TRANSLATION | Creates a new translation for a phrase.                                                                     |
| DROP_PHRASE        | Removes a phrase from thesaurus.                                                                            |
| DROP_RELATION      | Removes a relation between two phrases.                                                                     |
| DROP_THESAURUS     | Drops the specified thesaurus from the thesaurus tables.                                                    |
| DROP_TRANSLATION   | Drops a translation for a phrase.                                                                           |
| EXPORT_THESAURUS   | Exports a thesaurus from the thesaurus tables.                                                              |
| HAS_RELATION       | Tests for the existence of a thesaurus relation.                                                            |
| IMPORT_THESAURUS   | Imports a thesaurus into the thesaurus tables.                                                              |
| NT                 | Returns all narrower terms of a phrase.                                                                     |
| NTG                | Returns all narrower terms generic of a phrase.                                                             |
| NTI                | Returns all narrower terms instance of a phrase.                                                            |
| NTP                | Returns all narrower terms partitive of a phrase.                                                           |
| OUTPUT_STYLE       | Sets the output style for the expansion functions.                                                          |
| PT                 | Returns the preferred term of a phrase.                                                                     |
| RT                 | Returns the related terms of a phrase                                                                       |
| SN                 | Returns scope note for phrase.                                                                              |
| SYN                | Returns the synonym terms of a phrase                                                                       |
| THES_TT            | Returns all top terms for phrase.                                                                           |
| TR                 | Returns the foreign equivalent of a phrase.                                                                 |
| TRSYN              | Returns the foreign equivalent of a phrase, synonyms of the phrase, and foreign equivalent of the synonyms. |
| TT                 | Returns the top term of a phrase.                                                                           |
| UPDATE_TRANSLATION | Updates an existing translation.                                                                            |

**Note:**

The APIs in the `CTX_THES` package do not support identifiers that are prefixed with the schema or the owner name.

**See Also:**

[Oracle Text CONTAINS Query Operators](oracle-text-CONTAINS-query-operators.md) for more information about the thesaurus operators.

### 14.1 ALTER_PHRASE

Alters an existing phrase in the thesaurus. Only `CTXSYS` or thesaurus owner can alter a phrase.

#### Syntax

    CTX_THES.ALTER_PHRASE(tname      in varchar2,
                           phrase     in varchar2,
                           op         in varchar2,
                           operand    in varchar2 default null);

tname
Specify the thesaurus name.

phrase
Specify a phrase to alter.

op (alter operation)
Specify the alter operation as a string or symbol. You can specify one of the following operations with the `op` and `operand` pair:

| op (or alter operation)                | meaning                                                                                                     | operand                                                                                             |
|:---------------------------------------|:------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------|
| `RENAME`<br>or<br>`CTX_THES.OP_RENAME` | Rename phrase. If the new phrase already exists in the thesaurus, this procedure raises an exception.       | Specify a new phrase. You can include qualifiers to change, add, or remove qualifiers from phrases. |
| `PT`<br>or<br>`CTX_THES.OP_PT`         | Make phrase the preferred term. Existing preferred terms in the synonym ring becomes non-preferred synonym. | (none)                                                                                              |
| `SN`<br>or<br>`CTX_THES.OP_SN`         | Change the scope note on the phrase.                                                                        | Specify a new scope note.                                                                           |

operand
Specify an argument to the alter operation. See table for ""op (alter operation)"".

#### Examples

Correct misspelled word in thesaurus:

    ctx_thes.alter_phrase('thes1', 'tee', 'rename', 'tea');

Remove qualifier from mercury (metal):

    ctx_thes.alter_phrase('thes1', 'mercury (metal)', 'rename', 'mercury');

Add qualifier to mercury:

    ctx_thes.alter_phrase('thes1', 'mercury', 'rename', 'mercury (planet)');

Make Kowalski the preferred term in its synonym ring:

    ctx_thes.alter_phrase('thes1', 'Kowalski', 'pt');

Change scope note for view cameras:

    ctx_thes.alter_phrase('thes1', 'view cameras', 'sn', 'Cameras with lens focusing');

### 14.2 ALTER_THESAURUS

Use this procedure to rename or truncate an existing thesaurus. Only the thesaurus owner or `CTXSYS` can invoke this function on a given thesaurus.

#### Syntax

    CTX_THES.ALTER_THESAURUS(tname     in   varchar2,
                              op       in   varchar2,
                              operand  in   varchar2 default null);

tname
Specify the thesaurus name.

op
Specify the alter operation as a string or symbol. You can specify one of two operations:

| op                                         | Meaning                                                            | operand                       |
|:-------------------------------------------|:-------------------------------------------------------------------|:------------------------------|
| `RENAME`<br>or<br>`CTX_THES.OP_RENAME`     | Rename thesaurus. Returns an error if the new name already exists. | Specify a new thesaurus name. |
| `TRUNCATE`<br>or<br>`CTX_THES.OP_TRUNCATE` | Truncate thesaurus.                                                | None.                         |

operand
Specify the argument to the alter operation. See table for `op`.

#### Examples

Rename thesaurus `THES1` to `MEDICAL`:

    ctx_thes.alter_thesaurus('thes1', 'rename', 'medical');

or

    ctx_thes.alter_thesaurus('thes1', ctx_thes.op_rename, 'medical');

You can use symbols for any op argument, but all further examples will use strings.

Remove all phrases and relations from thesaurus `THES1`:

    ctx_thes.alter_thesaurus('thes1', 'truncate');

### 14.3 BT

This function returns all broader terms of a phrase as recorded in the specified thesaurus.

#### Syntax 1: Table Result

    CTX_THES.BT(restab IN OUT NOCOPY EXP_TAB,
                phrase IN VARCHAR2,
                lvl    IN NUMBER DEFAULT 1,
                tname  IN VARCHAR2 DEFAULT 'DEFAULT');

#### Syntax 2: String Result

    CTX_THES.BT(phrase IN VARCHAR2,
                lvl    IN NUMBER DEFAULT 1,
                tname  IN VARCHAR2 DEFAULT 'DEFAULT')
    RETURN VARCHAR2;

restab
Optionally, specify the name of the expansion table to store the results. This table must be of type `EXP_TAB` which the system defines as follows:

    type exp_rec is record (
        xrel varchar2(12),
        xlevel number,
        xphrase varchar2(256)
    );
    type exp_tab is table of exp_rec index by binary_integer;

**See Also:**

"[CTX_THES Result Tables and Data Types](oracle-text-result-tables.md)" in [Oracle Text Result Tables](oracle-text-result-tables.md) for more information about `EXP_TAB`

phrase
Specify a phrase to lookup in thesaurus.

lvl
Specify how many levels of broader terms to return. For example 2 means get the broader terms of the broader terms of the phrase.

tname
Specify a thesaurus name. If not specified, system default thesaurus is used.

#### Returns

This function returns a string of broader terms in the form:

     {bt1}|{bt2}|{bt3} ...

#### Example

String Result

Consider a thesaurus named `MY_THES` that has an entry for cat as follows:

    cat
       BT1 feline
         BT2 mammal
           BT3 vertebrate
             BT4 animal

To look up the broader terms for cat up to two levels, enter the following statements:

    set serveroutput on

    declare
      terms varchar2(2000);
    begin
      terms := ctx_thes.bt('CAT', 2, 'MY_THES');
      dbms_output.put_line('The broader expansion for CAT is: '||terms);
    end;

This code produces the following output:

    The broader expansion for CAT is: {cat}|{feline}|{mammal}

Table Result

The following example performs a broader term lookup for brown wolf using the table result:

    set serveroutput on

    declare
      xtab ctx_thes.exp_tab;
    begin
      ctx_thes.bt(xtab, 'brown wolf', 2, 'my_thesaurus');
      for i in 1..xtab.count loop
        dbms_output.put_line(xtab(i).rel||' '||xtab(i).phrase);
      end loop;
    end;

This code produces the following output:

    PHRASE BROWN WOLF
    BT WOLF
    BT CANINE
    BT ANIMAL

#### Related Topics

OUTPUT_STYLE

[Broader Term (BT\_ BTG\_ BTP\_ BTI)](oracle-text-CONTAINS-query-operators.md)

### 14.4 BTG

This function returns all broader terms generic of a phrase as recorded in the specified thesaurus.

#### Syntax 1: Table Result

    CTX_THES.BTG(restab IN OUT NOCOPY EXP_TAB,
                 phrase IN VARCHAR2,
                 lvl    IN NUMBER DEFAULT 1,
                 tname  IN VARCHAR2 DEFAULT 'DEFAULT');

#### Syntax 2: String Result

    CTX_THES.BTG(phrase IN VARCHAR2,
                 lvl    IN NUMBER DEFAULT 1,
                 tname  IN VARCHAR2 DEFAULT 'DEFAULT')
    RETURN VARCHAR2;

restab
Optionally, specify the name of the expansion table to store the results. This table must be of type `EXP_TAB` which the system defines as follows:

    type exp_rec is record (
        xrel varchar2(12),
        xlevel number,
        xphrase varchar2(256)
    );
    type exp_tab is table of exp_rec index by binary_integer;

**See Also:**

"[CTX_THES Result Tables and Data Types](oracle-text-result-tables.md)" in [Oracle Text Result Tables](oracle-text-result-tables.md) for more information about `EXP_TAB`.

phrase
Specify a phrase to lookup in thesaurus.

lvl
Specify how many levels of broader terms to return. For example 2 means get the broader terms of the broader terms of the phrase.

tname
Specify thesaurus name. If not specified, system default thesaurus is used.

#### Returns

This function returns a string of broader terms generic in the form:

     {bt1}|{bt2}|{bt3} ...

#### Example

To look up the broader terms generic for cat up to two levels, enter the following statements:

    set serveroutput on
    declare
      terms varchar2(2000);
    begin
      terms := ctx_thes.btg('CAT', 2, 'MY_THES');
      dbms_output.put_line('the broader expansion for CAT is: '||terms);
    end;

#### Related Topics

"OUTPUT_STYLE "

"[Broader Term (BT\_ BTG\_ BTP\_ BTI)](oracle-text-CONTAINS-query-operators.md)"

### 14.5 BTI

This function returns all broader terms instance of a phrase as recorded in the specified thesaurus.

#### Syntax 1: Table Result

    CTX_THES.BTI(restab IN OUT NOCOPY EXP_TAB,
                 phrase IN VARCHAR2,
                 lvl    IN NUMBER DEFAULT 1,
                 tname  IN VARCHAR2 DEFAULT 'DEFAULT');

#### Syntax 2: String Result

    CTX_THES.BTI(phrase IN VARCHAR2,
                 lvl    IN NUMBER DEFAULT 1,
                 tname  IN VARCHAR2 DEFAULT 'DEFAULT')
    RETURN VARCHAR2;

restab
Optionally, specify the name of the expansion table to store the results. This table must be of type `EXP_TAB` which the system defines as follows:

    type exp_rec is record (
        xrel varchar2(12),
        xlevel number,
        xphrase varchar2(256)
    );
    type exp_tab is table of exp_rec index by binary_integer;

**See Also:**

"[CTX_THES Result Tables and Data Types](oracle-text-result-tables.md)" in [Oracle Text Result Tables](oracle-text-result-tables.md) for more information about `EXP_TAB`.

phrase
Specify a phrase to lookup in thesaurus.

lvl
Specify how many levels of broader terms to return. For example 2 means get the broader terms of the broader terms of the phrase.

tname
Specify a thesaurus name. If not specified, system default thesaurus is used.

#### Returns

This function returns a string of broader terms instance in the form:

     {bt1}|{bt2}|{bt3} ...

#### Example

To look up the broader terms instance for cat up to two levels, enter the following statements:

    set serveroutput on
    declare
      terms varchar2(2000);
    begin
      terms := ctx_thes.bti('CAT', 2, 'MY_THES');
      dbms_output.put_line('the broader expansion for CAT is: '||terms);
    end;

#### Related Topics

"OUTPUT_STYLE "

"[Broader Term (BT\_ BTG\_ BTP\_ BTI)](oracle-text-CONTAINS-query-operators.md)"

### 14.6 BTP

This function returns all broader terms partitive of a phrase as recorded in the specified thesaurus.

#### Syntax 1: Table Result

    CTX_THES.BTP(restab IN OUT NOCOPY EXP_TAB,
                 phrase IN VARCHAR2,
                 lvl    IN NUMBER DEFAULT 1,
                 tname  IN VARCHAR2 DEFAULT 'DEFAULT');

#### Syntax 2: String Result

    CTX_THES.BTP(phrase IN VARCHAR2,
                 lvl    IN NUMBER DEFAULT 1,
                 tname  IN VARCHAR2 DEFAULT 'DEFAULT')
    RETURN VARCHAR2;

restab
Optionally, specify the name of the expansion table to store the results. This table must be of type `EXP_TAB` which the system defines as follows:

    type exp_rec is record (
        xrel varchar2(12),
        xlevel number,
        xphrase varchar2(256)
    );
    type exp_tab is table of exp_rec index by binary_integer;

**See Also:**

"[CTX_THES Result Tables and Data Types](oracle-text-result-tables.md)" in [Oracle Text Result Tables](oracle-text-result-tables.md) for more information about `EXP_TAB`.

phrase
Specify a phrase to lookup in thesaurus.

lvl
Specify how many levels of broader terms to return. For example 2 means get the broader terms of the broader terms of the phrase.

tname
Specify a thesaurus name. If not specified, the system default thesaurus is used.

#### Returns

This function returns a string of broader terms in the form:

     {bt1}|{bt2}|{bt3} ...

#### Example

To look up the two broader terms partitive for cat, enter the following statements:

    declare
      terms varchar2(2000);
    begin
      terms := ctx_thes.btp('CAT', 2, 'MY_THES');
      dbms_output.put_line('the broader expansion for CAT is: '||terms);
    end;

#### Related Topics

"OUTPUT_STYLE "

"[Broader Term (BT\_ BTG\_ BTP\_ BTI)](oracle-text-CONTAINS-query-operators.md)"

### 14.7 CREATE_PHRASE

The `CREATE_PHRASE` procedure adds a new phrase to the specified thesaurus.

**Note:**

Even though you can create thesaurus relations with this procedure, Oracle recommends that you use `CTX_THES.CREATE_RELATION` rather than `CTX_THES.CREATE_PHRASE` to create relations in a thesaurus.

#### Syntax

    CTX_THES.CREATE_PHRASE(tname   IN VARCHAR2,
                           phrase  IN VARCHAR2,
                           rel     IN VARCHAR2 DEFAULT NULL,
                           relname IN VARCHAR2 DEFAULT NULL);

tname
Specify the name of the thesaurus in which the new phrase is added or the existing phrase is located.

phrase
Specify the phrase to be added to a thesaurus or the phrase for which a new relationship is created.

rel
Specify the new relationship between phrase and relname. This parameter is supported only for backward compatibility. Use CTX_THES.CREATE_RELATION to create new relations in a thesaurus.

relname
Specify the existing phrase that is related to phrase. This parameter is supported only for backward compatibility. Use CTX_THES.CREATE_RELATION to create new relations in a thesaurus.

#### Returns

The ID for the entry.

#### Example

In this example, two new phrases (os and operating system) are created in a thesaurus named `tech_thes`.

    begin
       ctx_thes.create_phrase('tech_thes','os');
       ctx_thes.create_phrase('tech_thes','operating system');
    end;

### 14.8 CREATE_RELATION

Creates a relation between two phrases in the thesaurus. The synonym ring is limited in length to about 4000 synonyms, depending on word length.

**Note:**

Oracle recommends that you use `CTX_THES.CREATE_RELATION` rather than `CTX_THES.CREATE_PHRASE` to create relations in a thesaurus.

Only thesaurus owner and `CTXSYS` can invoke this procedure on a given thesaurus.

#### Syntax

    CTX_THES.CREATE_RELATION(tname      in    varchar2,
                             phrase     in    varchar2,
                             rel        in    varchar2,
                             relphrase  in    varchar2);

tname
Specify the thesaurus name

phrase
Specify the phrase to alter or create. If `phrase` is a disambiguated homograph, you must specify the qualifier. If `phrase` does not exist in the thesaurus, it is created.

rel
Specify the relation to create. The relation is from `phrase` to `relphrase`. You can specify one of the following relations:

| relation         | meaning                       | relphrase                                                                             |
|:-----------------|:------------------------------|:--------------------------------------------------------------------------------------|
| BT\*/NT\*        | Add hierarchical relation.    | Specify the related phrase. The relationship is interpreted from phrase to relphrase. |
| RT               | Add associative relation.     | Specify the phrase to associate.                                                      |
| SYN              | Add phrase to a synonym ring. | Specify an existing phrase in the synonym ring.                                       |
| Specify language | Add translation for a phrase. | Specify a new translation phrase.                                                     |

relphrase
Specify the related phrase. If relphrase does not exist in `tname`, relphrase is created. See table for `rel`.

#### Notes

The relation you specify for rel is interpreted as from phrase to relphrase. For example, consider dog with broader term animal:

    dog
      BT animal

To add this relation, specify the arguments as follows:

    begin
    CTX_THES.CREATE_RELATION('thes','dog','BT','animal');
    end;

**Note:**

The order in which you specify arguments for `CTX_THES.CREATE_RELATION` is different from the order you specify them with `CTX_THES.CREATE_PHRASE`.

#### Examples

Create relation VEHICLE NT CAR:

    ctx_thes.create_relation('thes1', 'vehicle', 'NT', 'car');

Create Japanese translation for you:

    ctx_thes.create_relation('thes1', 'you', 'JAPANESE:', 'kimi');

### 14.9 CREATE_THESAURUS

The `CREATE_THESAURUS` procedure creates an empty thesaurus with the specified name in the thesaurus tables.

#### Syntax

    CTX_THES.CREATE_THESAURUS(name           IN VARCHAR2,
                              casesens       IN BOOLEAN DEFAULT FALSE);

name
Specify the name of the thesaurus to be created. The name of the thesaurus must be unique. If a thesaurus with the specified name already exists, `CREATE_THESAURUS` returns an error and does not create the thesaurus.

casesens
Specify whether the thesaurus to be created is case-sensitive. If `casesens` is true, Oracle Text retains the cases of all terms entered in the specified thesaurus. As a result, queries that use the thesaurus are case-sensitive.

#### Example

    begin
       ctx_thes.create_thesaurus('tech_thes', FALSE);
    end;

### 14.10 CREATE_TRANSLATION

Use this procedure to create a new translation for a phrase in a specified language.

#### Syntax

    CTX_THES.CREATE_TRANSLATION(tname       in    varchar2,
                                phrase      in    varchar2,
                                language    in    varchar2,
                                translation in    varchar2);

tname
Specify the name of the thesaurus, using no more than 30 characters.

phrase
Specify the phrase in the thesaurus to which to add a translation. Phrase must already exist in the thesaurus, or an error is raised.

language
Specify the language of the translation, using no more than 10 characters.

translation
Specify the translated term, using no more than 256 characters.

If a translation for this phrase already exists, this new translation is added without removing that original translation, so long as that original translation is not the same. Adding the same translation twice results in an error.

#### Example

The following code adds the Spanish translation for dog to my_thes:

    begin
       ctx_thes.create_translation('my_thes', 'dog', 'SPANISH', 'PERRO');
    end;

### 14.11 DROP_PHRASE

Removes a phrase from the thesaurus. Only thesaurus owner and `CTXSYS` can invoke this procedure on a given thesaurus.

#### Syntax

    CTX_THES.DROP_PHRASE(tname      in varchar2,
                         phrase     in varchar2);

tname
Specify thesaurus name.

phrase
Specify a phrase to drop. If the `phrase` is a disambiguated homograph, then you must include the qualifier. If the phrase does not exist in `tname`, then this procedure raises an exception.

BT\* / NT\* relations are patched around the dropped phrase. For example, if A has a BT B, and B has BT C, after B is dropped, A has BT C.

When a word has multiple broader terms, then a relationship is established for each narrower term to each broader term.

Note that BT, BTG, BTP, and BTI are separate hierarchies, so if A has BTG B, and B has BTI C, when B is dropped, there is no relation implicitly created between A and C.

RT relations are not patched. For example, if A has RT B, and B has RT C, then if B is dropped, there is no associative relation created between A and C.

#### Example

Assume you have the following relations defined in mythes:

    wolf
       BT canine
    canine
       BT animal

You drop phrase canine:

    begin
    ctx_thes.drop_phrase('mythes', 'canine');
    end;

The resulting thesaurus is patched and looks like:

    wolf
       BT animal

### 14.12 DROP_RELATION

Removes a relation between two phrases from the thesaurus.

**Note:**

`CTX_THES.DROP_RELATION` removes only the relation between two phrases. Phrases are never removed by this call.

Only thesaurus owner and `CTXSYS` can invoke this procedure on a given thesaurus.

#### Syntax

    CTX_THES.DROP_RELATION(tname     in    varchar2,
                            phrase    in    varchar2,
                            rel       in    varchar2,
                            relphrase in    varchar2 default null);

tname
Specify the thesaurus name.

phrase
Specify the filing phrase.

rel
Specify the relation to drop. The relation is from `phrase` to `relphrase`. You can specify one of the following relations:

| relation  | meaning                                                                                    | relphrase                                                                                                                                                                                                                                                       |
|:----------|:-------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| BT\*/NT\* | Remove hierarchical relation.                                                              | Optional specify relphrase. If not provided, all relations of that type for the phrase are removed.                                                                                                                                                             |
| RT        | Remove associative relation.                                                               | Optionally specify relphrase. If not provided, all RT relations for the phrase are removed.                                                                                                                                                                     |
| SYN       | Remove phrase from its synonym ring.                                                       | (none)                                                                                                                                                                                                                                                          |
| PT        | Remove preferred term designation from the phrase. The phrase remains in the synonym ring. | (none)                                                                                                                                                                                                                                                          |
| language  | Remove a translation from a phrase.                                                        | Optionally specify relphrase. You can specify relphrase when there are multiple translations for a phrase for the language, and you want to remove just one translation.<br>If relphrase is NULL, all translations for the phrase for the language are removed. |

relphrase
Specify the related phrase.

#### Notes

The relation you specify for rel is interpreted as from phrase to relphrase. For example, consider dog with broader term animal:

    dog
      BT animal

To remove this relation, specify the arguments as follows:

    begin
    CTX_THES.DROP_RELATION('thes','dog','BT','animal');
    end;

You can also remove this relation using NT as follows:

    begin
    CTX_THES.DROP_RELATION('thes','animal','NT','dog');
    end;

#### Example

Remove relation VEHICLE NT CAR:

    ctx_thes.drop_relation('thes1', 'vehicle', 'NT', 'car');

Remove all narrower term relations for vehicle:

    ctx_thes.drop_relation('thes1', 'vehicle', 'NT');

Remove Japanese translations for me:

    ctx_thes.drop_relation('thes1', 'me', 'JAPANESE:');

Remove a specific Japanese translation for me:

    ctx_thes.drop_relation('thes1', 'me', 'JAPANESE:', 'boku')

### 14.13 DROP_THESAURUS

The `DROP_THESAURUS` procedure deletes the specified thesaurus and all of its entries from the thesaurus tables.

#### Syntax

    CTX_THES.DROP_THESAURUS(name IN VARCHAR2);

name
Specify the name of the thesaurus to be dropped.

#### Example

    begin
    ctx_thes.drop_thesaurus('tech_thes');
    end;

### 14.14 DROP_TRANSLATION

Use this procedure to remove one or more translations for a phrase.

#### Syntax

    CTX_THES.DROP_TRANSLATION (tname       in    varchar2,
                               phrase      in    varchar2,
                               language    in    varchar2 default null,
                               translation in    varchar2 default null);

tname
Specify the name of the thesaurus, using no more than 30 characters.

phrase
Specify the phrase in the thesaurus to which to remove a translation. The phrase must already exist in the thesaurus or an error is raised.

language
Optionally, specify the language of the translation, using no more than 10 characters. If not specified, the translation must also not be specified and all translations in all languages for the phrase are removed. An error is raised if the phrase has no translations.

translation
Optionally, specify the translated term to remove, using no more than 256 characters. If no such translation exists, an error is raised.

#### Example

The following code removes the Spanish translation for dog:

    begin
       ctx_thes.drop_translation('my_thes', 'dog', 'SPANISH', 'PERRO');
    end;

To remove all translations for dog in all languages:

    begin
       ctx_thes.drop_translation('my_thes', 'dog');
    end;

### 14.15 EXPORT_THESAURUS

Use this procedure to export a thesaurus as a clob from the Oracle Text thesaurus tables. The format of the exported thesaurus is same as that of the format of the thesaurus file that is used by the `ctxload` utility to import thesaurus into the Oracle Text thesaurus tables.

**See Also:**

"[Thesaurus Loader (ctxload)](oracle-text-utilities.md)" in [Oracle Text Utilities](oracle-text-utilities.md) for more information about the `ctxload` utility.

Only the owner of the thesaurus, or the `sys` user, or the `ctxsys` user can export a thesaurus from the Oracle Text thesaurus tables using `export_thesaurus`.

You should call `ctx_output.start_log` before calling `export_thesaurus` to log the operations done by `export_thesaurus`.

#### Syntax

    CTX_THES.EXPORT_THESAURUS(name in varchar2,
                              thesdump in out nocopy CLOB);

name
Specify the name of the thesaurus in the Oracle Text thesaurus tables that you want to export. If the specified thesaurus does not exists in the Oracle Text thesaurus tables, then this procedure raises an exception.

thedump
Specify the name of the clob where you want to store the thesaurus that is exported from the Oracle Text thesaurus tables.

#### Example

The following example copies the thesaurus named `mythesaurus` from the Oracle Text thesaurus tables into the clob `mythesdump`:

    declare
     mythesdump clob;
    begin
     ctx_thes.export_thesaurus('mythesaurus', mythesdump);
    end;

### 14.16 HAS_RELATION

`HAS_RELATION` tests that a thesaurus relation exists without actually performing the expansion. The function returns `TRUE` if the phrase has any of the relations in the specified list.

#### Syntax

    CTX_THES.HAS_RELATION(phrase in varchar2,
                          rel in varchar2,
                          tname in varchar2 default 'DEFAULT')
      returns boolean;

phrase
Specify the phrase.

rel
Specify a single thesaural relation or a comma-delimited list of relations, except `PT`. Specify `'ANY'` for any relation.

tname
Specify the thesaurus name.

#### Example

The following example returns `TRUE` if the phrase cat in the `DEFAULT` thesaurus has any broader terms or broader generic terms:

    set serveroutput on
    result boolean;

    begin
     result := ctx_thes.has_relation('cat','BT,BTG');
     if (result) then dbms_output.put_line('TRUE');
      else  dbms_output.put_line('FALSE');
     end if;
    end;

### 14.17 IMPORT_THESAURUS

Use this procedure to import a thesaurus into the Oracle Text thesaurus tables. You should call `ctx_output.start_log` before calling `import_thesaurus` to log the operations done by `import_thesaurus`.

#### Syntax

    CTX_THES.IMPORT_THESAURUS(name in varchar2,
                              content in CLOB,
                              thescase in varchar2 default 'N');

name
Specify the name of the thesaurus to be created. If the name of the thesaurus specified in the `name` parameter already exists in the Oracle Text thesaurus tables, then this procedure raises an exception.

content
Specify the thesaurus content to be imported in the Oracle Text thesaurus tables. The format of the thesaurus to be imported should be the same as used by the `ctxload` utility. If the format of the thesaurus to be imported is not correct, then this procedure raises an exception.

**See Also:**

"[Thesaurus Loader (ctxload)](oracle-text-utilities.md)" in [Oracle Text Utilities](oracle-text-utilities.md) for more information about the `ctxload` utility.

thecase
Specify `'Y'` to create a case-sensitive thesaurus and `'N'` to create a case-insensitive thesaurus. The default is `'N'`.

#### Example

The following example creates a case-sensitive thesaurus named `mythesaurus` and imports the thesaurus content present in `myclob` into the Oracle Text thesaurus tables:

    declare
     myclob clob;
    begin
     myclob := to_clob('peking SYN beijing BT capital country NT beijing tokyo');
     ctx_thes.import_thesaurus('mythesaurus', myclob, 'Y');
    end;

### 14.18 NT

This function returns all narrower terms of a phrase as recorded in the specified thesaurus.

#### Syntax 1: Table Result

    CTX_THES.NT(restab IN OUT NOCOPY EXP_TAB,
                 phrase IN VARCHAR2,
                 lvl    IN NUMBER DEFAULT 1,
                 tname  IN VARCHAR2 DEFAULT 'DEFAULT');

#### Syntax 2: String Result

    CTX_THES.NT(phrase IN VARCHAR2,
                 lvl    IN NUMBER DEFAULT 1,
                 tname  IN VARCHAR2 DEFAULT 'DEFAULT')
    RETURN VARCHAR2;

restab
Optionally, specify the name of the expansion table to store the results. This table must be of type `EXP_TAB` which the system defines as follows:

    type exp_rec is record (
        xrel varchar2(12),
        xlevel number,
        xphrase varchar2(256)
    );
    type exp_tab is table of exp_rec index by binary_integer;

**See Also:**

"[CTX_THES Result Tables and Data Types](oracle-text-result-tables.md)" in [Oracle Text Result Tables](oracle-text-result-tables.md) for more information about `EXP_TAB`.

phrase
Specify a phrase to lookup in thesaurus.

lvl
Specify how many levels of narrower terms to return. For example 2 means get the narrower terms of the narrower terms of the phrase.

tname
Specify thesaurus name. If not specified, system default thesaurus is used.

#### Returns

This function returns a string of narrower terms in the form:

     {nt1}|{nt2}|{nt3} ...

#### Example

String Result

Consider a thesaurus named `MY_THES` that has an entry for cat as follows:

    cat
     NT domestic cat
     NT wild cat
     BT mammal
    mammal
     BT animal
    domestic cat
     NT Persian cat
     NT Siamese cat

To look up the narrower terms for cat down to two levels, enter the following statements:

    declare
      terms varchar2(2000);
    begin
      terms := ctx_thes.nt('CAT', 2, 'MY_THES');
      dbms_output.put_line('the narrower expansion for CAT is: '||terms);
    end;

This code produces the following output:

    the narrower expansion for CAT is: {cat}|{domestic cat}|{Persian cat}|{Siamese cat}| {wild cat}

Table Result

The following code does an narrower term lookup for canine using the table result:

    declare
      xtab ctx_thes.exp_tab;
    begin
      ctx_thes.nt(xtab, 'canine', 2, 'my_thesaurus');
      for i in 1..xtab.count loop
        dbms_output.put_line(lpad(' ', 2*xtab(i).xlevel) ||
        xtab(i).xrel || ' ' || xtab(i).xphrase);
      end loop;
    end;

This code produces the following output:

    PHRASE CANINE
     NT WOLF (Canis lupus)
       NT BROWN WOLF
       NT GREY WOLF
     NT DOG (Canis familiaris)
       NT PIT BULL
       NT DASCHUND
       NT CHIHUAHUA
    NT HYENA (Canis mesomelas)
    NT COYOTE (Canis latrans)

#### Related Topics

OUTPUT_STYLE

[Narrower Term (NT\_ NTG\_ NTP\_ NTI)](oracle-text-CONTAINS-query-operators.md)

### 14.19 NTG

This function returns all narrower terms generic of a phrase as recorded in the specified thesaurus.

#### Syntax 1: Table Result

    CTX_THES.NTG(restab IN OUT NOCOPY EXP_TAB,
                 phrase IN VARCHAR2,
                 lvl    IN NUMBER DEFAULT 1,
                 tname  IN VARCHAR2 DEFAULT 'DEFAULT');

#### Syntax 2: String Result

    CTX_THES.NTG(phrase IN VARCHAR2,
                 lvl    IN NUMBER DEFAULT 1,
                 tname  IN VARCHAR2 DEFAULT 'DEFAULT')
    RETURN VARCHAR2;

restab
Optionally, specify the name of the expansion table to store the results. This table must be of type `EXP_TAB` which the system defines as follows:

    type exp_rec is record (
        xrel varchar2(12),
        xlevel number,
        xphrase varchar2(256)
    );
    type exp_tab is table of exp_rec index by binary_integer;

**See Also:**

"[CTX_THES Result Tables and Data Types](oracle-text-result-tables.md)" in [Oracle Text Result Tables](oracle-text-result-tables.md) for more information about `EXP_TAB`.

phrase
Specify a phrase to lookup in thesaurus.

lvl
Specify how many levels of narrower terms to return. For example 2 means get the narrower terms of the narrower terms of the phrase.

tname
Specify the thesaurus name. If not specified, system default thesaurus is used.

#### Returns

This function returns a string of narrower terms generic in the form:

     {nt1}|{nt2}|{nt3} ...

#### Example

To look up the narrower terms generic for cat down to two levels, enter the following statements:

    declare
      terms varchar2(2000);
    begin
      terms := ctx_thes.ntg('CAT', 2, 'MY_THES');
      dbms_output.put_line('the narrower expansion for CAT is: '||terms);
    end;

#### Related Topics

"OUTPUT_STYLE "

"[Narrower Term (NT\_ NTG\_ NTP\_ NTI)](oracle-text-CONTAINS-query-operators.md)"

### 14.20 NTI

This function returns all narrower terms instance of a phrase as recorded in the specified thesaurus.

#### Syntax 1: Table Result

    CTX_THES.NTI(restab IN OUT NOCOPY EXP_TAB,
                 phrase IN VARCHAR2,
                 lvl    IN NUMBER DEFAULT 1,
                 tname  IN VARCHAR2 DEFAULT 'DEFAULT');

#### Syntax 2: String Result

    CTX_THES.NTI(phrase IN VARCHAR2,
                 lvl    IN NUMBER DEFAULT 1,
                 tname  IN VARCHAR2 DEFAULT 'DEFAULT')
    RETURN VARCHAR2;

restab
Optionally, specify the name of the expansion table to store the results. This table must be of type `EXP_TAB` which the system defines as follows:

    type exp_rec is record (
        xrel varchar2(12),
        xlevel number,
        xphrase varchar2(256)
    );
    type exp_tab is table of exp_rec index by binary_integer;

**See Also:**

"[CTX_THES Result Tables and Data Types](oracle-text-result-tables.md)" in [Oracle Text Result Tables](oracle-text-result-tables.md) for more information about `EXP_TAB`.

phrase
Specify a phrase to lookup in thesaurus.

lvl
Specify how many levels of narrower terms to return. For example 2 means get the narrower terms of the narrower terms of the phrase.

tname
Specify the thesaurus name. If not specified, system default thesaurus is used.

#### Returns

This function returns a string of narrower terms instance in the form:

     {nt1}|{nt2}|{nt3} ...

#### Example

To look up the narrower terms instance for cat down to two levels, enter the following statements:

    declare
      terms varchar2(2000);
    begin
      terms := ctx_thes.nti('CAT', 2, 'MY_THES');
      dbms_output.put_line('the narrower expansion for CAT is: '||terms);
    end;

#### Related Topics

"OUTPUT_STYLE "

"[Narrower Term (NT\_ NTG\_ NTP\_ NTI)](oracle-text-CONTAINS-query-operators.md)"

### 14.21 NTP

This function returns all narrower terms partitive of a phrase as recorded in the specified thesaurus.

#### Syntax 1: Table Result

    CTX_THES.NTP(restab IN OUT NOCOPY EXP_TAB,
                 phrase IN VARCHAR2,
                 lvl    IN NUMBER DEFAULT 1,
                 tname  IN VARCHAR2 DEFAULT 'DEFAULT');

#### Syntax 2: String Result

    CTX_THES.NTP(phrase IN VARCHAR2,
                 lvl    IN NUMBER DEFAULT 1,
                 tname  IN VARCHAR2 DEFAULT 'DEFAULT')
    RETURN VARCHAR2;

restab
Optionally, specify the name of the expansion table to store the results. This table must be of type `EXP_TAB` which the system defines as follows:

    type exp_rec is record (
        xrel varchar2(12),
        xlevel number,
        xphrase varchar2(256)
    );
    type exp_tab is table of exp_rec index by binary_integer;

**See Also:**

"[CTX_THES Result Tables and Data Types](oracle-text-result-tables.md)" in [Oracle Text Result Tables](oracle-text-result-tables.md) for more information about `EXP_TAB`.

phrase
Specify a phrase to lookup in thesaurus.

lvl
Specify how many levels of narrower terms to return. For example 2 means get the narrower terms of the narrower terms of the phrase.

tname
Specify the thesaurus name. If not specified, system default thesaurus is used.

#### Returns

This function returns a string of narrower terms partitive in the form:

     {nt1}|{nt2}|{nt3} ...

#### Example

To look up the narrower terms partitive for cat down to two levels, enter the following statements:

    declare
      terms varchar2(2000);
    begin
      terms := ctx_thes.ntp('CAT', 2, 'MY_THES');
      dbms_output.put_line('the narrower expansion for CAT is: '||terms);
    end;

#### Related Topics

"OUTPUT_STYLE "

"[Narrower Term (NT\_ NTG\_ NTP\_ NTI)](oracle-text-CONTAINS-query-operators.md)"

### 14.22 OUTPUT_STYLE

Sets the output style for the return string of the `CTX_THES` expansion functions. This procedure has no effect on the table results to the `CTX_THES` expansion functions.

#### Syntax

    CTX_THES.OUTPUT_STYLE (
          showlevel     IN BOOLEAN DEFAULT FALSE,
          showqualify   IN BOOLEAN DEFAULT FALSE,
          showpt        IN BOOLEAN DEFAULT FALSE,
          showid        IN BOOLEAN DEFAULT FALSE
    );

showlevel
Specify `TRUE` to show level in `BT/NT` expansions.

showqualify
Specify `TRUE` to show phrase qualifiers.

showpt
Specify `TRUE` to show preferred terms with an asterisk \*.

showid
Specify `TRUE` to show phrase ids.

#### Notes

The general syntax of the return string for `CTX_THES` expansion functions is:

    {pt indicator:phrase (qualifier):level:phraseid}

Preferred term indicator is an asterisk then a colon at the start of the phrase. The qualifier is in parentheses after a space at the end of the phrase. Level is a number.

The following is an example return string for turkey the bird:

    *:TURKEY (BIRD):1:1234

### 14.23 PT

This function returns the preferred term of a phrase as recorded in the specified thesaurus.

#### Syntax 1: Table Result

    CTX_THES.PT(restab IN OUT NOCOPY EXP_TAB,
                phrase IN VARCHAR2,
                tname  IN VARCHAR2 DEFAULT 'DEFAULT')
    RETURN varchar2;

#### Syntax 2: String Result

    CTX_THES.PT(phrase IN VARCHAR2,
                tname  IN VARCHAR2 DEFAULT 'DEFAULT')
    RETURN varchar2;

restab
Optionally, specify the name of the expansion table to store the results. This table must be of type `EXP_TAB` which the system defines as follows:

    type exp_rec is record (
        xrel varchar2(12),
        xlevel number,
        xphrase varchar2(256)
    );
    type exp_tab is table of exp_rec index by binary_integer;

**See Also:**

"[CTX_THES Result Tables and Data Types](oracle-text-result-tables.md)" in [Oracle Text Result Tables](oracle-text-result-tables.md) for more information about EXP_TAB.

phrase
Specify a phrase to lookup in thesaurus.

tname
Specify thesaurus name. If not specified, system default thesaurus is used.

#### Returns

This function returns the preferred term as a string in the form:

    {pt}

#### Example

Consider a thesaurus `MY_THES` with the following preferred term definition for automobile:

    AUTOMOBILE
      PT CAR

To look up the preferred term for automobile, execute the following code:

    declare
      terms varchar2(2000);
    begin
      terms := ctx_thes.pt('AUTOMOBILE','MY_THES');
      dbms_output.put_line('The preferred term for automobile is: '||terms);
    end;

#### Related Topics

"OUTPUT_STYLE "

"[Preferred Term (PT)](oracle-text-CONTAINS-query-operators.md)"

### 14.24 RT

This function returns the related terms of a term in the specified thesaurus.

#### Syntax 1: Table Result

    CTX_THES.RT(restab IN OUT NOCOPY EXP_TAB,
                phrase IN VARCHAR2,
                tname  IN VARCHAR2 DEFAULT 'DEFAULT');

#### Syntax 2: String Result

    CTX_THES.RT(phrase IN VARCHAR2,
                tname  IN VARCHAR2 DEFAULT 'DEFAULT')
    RETURN varchar2;

restab
Optionally, specify the name of the expansion table to store the results. This table must be of type `EXP_TAB` which the system defines as follows:

    type exp_rec is record (
        xrel varchar2(12),
        xlevel number,
        xphrase varchar2(256)
    );
    type exp_tab is table of exp_rec index by binary_integer;

**See Also:**

"[CTX_THES Result Tables and Data Types](oracle-text-result-tables.md)" in [Oracle Text Result Tables](oracle-text-result-tables.md) for more information about `EXP_TAB`.

phrase
Specify a phrase to lookup in thesaurus.

tname
Specify the thesaurus name. If not specified, system default thesaurus is used.

#### Returns

This function returns a string of related terms in the form:

    {rt1}|{rt2}|{rt3}| ...

#### Example

Consider a thesaurus `MY_THES` with the following related term definition for dog:

    DOG
      RT WOLF
      RT HYENA

To look up the related terms for dog, execute the following code:

    declare
      terms varchar2(2000);
    begin
      terms := ctx_thes.rt('DOG','MY_THES');
      dbms_output.put_line('The related terms for dog are: '||terms);
    end;

This codes produces the following output:

    The related terms for dog are: {dog}|{wolf}|{hyena}

#### Related Topics

"OUTPUT_STYLE "

"[Related Term (RT)](oracle-text-CONTAINS-query-operators.md)"

### 14.25 SN

This function returns the scope note of the given phrase.

#### Syntax

    CTX_THES.SN(phrase IN VARCHAR2,
                tname  IN VARCHAR2 DEFAULT 'DEFAULT')
    RETURN VARCHAR2;

phrase
Specify a phrase to lookup in thesaurus.

tname
Specify the thesaurus name. If not specified, system default thesaurus is used.

#### Returns

This function returns the scope note as a string.

#### Example

    declare
      note varchar2(80);
    begin
      note := ctx_thes.sn('camera','mythes');
      dbms_output.put_line('CAMERA');
      dbms_output.put_line(' SN ' || note);
    end;

    sample output:

    CAMERA
     SN Optical cameras

### 14.26 SYN

This function returns all synonyms of a phrase as recorded in the specified thesaurus.

#### Syntax 1: Table Result

    CTX_THES.SYN(restab IN OUT NOCOPY EXP_TAB,
                 phrase IN VARCHAR2,
                 tname  IN VARCHAR2 DEFAULT 'DEFAULT');

#### Syntax 2: String Result

    CTX_THES.SYN(phrase IN VARCHAR2,
                 tname  IN VARCHAR2 DEFAULT 'DEFAULT')
    RETURN VARCHAR2;

restab
Optionally, specify the name of the expansion table to store the results. This table must be of type `EXP_TAB` which the system defines as follows:

    type exp_rec is record (
        xrel varchar2(12),
        xlevel number,
        xphrase varchar2(256)
    );
    type exp_tab is table of exp_rec index by binary_integer;

**See Also:**

"[CTX_THES Result Tables and Data Types](oracle-text-result-tables.md)" in [Oracle Text Result Tables](oracle-text-result-tables.md) for more information about `EXP_TAB`.

phrase
Specify a phrase to lookup in thesaurus.

tname
Specify the thesaurus name. If not specified, system default thesaurus is used.

#### Returns

This function returns a string of the form:

     {syn1}|{syn2}|{syn3} ...

#### Example

String Result

Consider a thesaurus named `ANIMALS` that has an entry for cat as follows:

    CAT
      SYN KITTY
      SYN FELINE


To look-up the synonym for cat and obtain the result as a string, enter the following statements:

    declare
      synonyms varchar2(2000);
    begin
      synonyms := ctx_thes.syn('CAT','ANIMALS');
      dbms_output.put_line('the synonym expansion for CAT is: '||synonyms);
    end;

This code produces the following output:

    the synonym expansion for CAT is: {CAT}|{KITTY}|{FELINE}

Table Result

The following code looks up the synonyms for canine and obtains the results in a table. The contents of the table are printed to the standard output.

    declare
      xtab ctx_thes.exp_tab;
    begin
      ctx_thes.syn(xtab, 'canine', 'my_thesaurus');
      for i in 1..xtab.count loop
        dbms_output.put_line(lpad(' ', 2*xtab(i).xlevel) ||
        xtab(i).xrel || ' ' || xtab(i).xphrase);
      end loop;
    end;


This code produces the following output:

    PHRASE CANINE
     PT DOG
    SYN PUPPY
    SYN MUTT
    SYN MONGREL

#### Related Topics

"OUTPUT_STYLE "

"[SYNonym (SYN)](oracle-text-CONTAINS-query-operators.md)"

### 14.27 THES_TT

This procedure finds and returns all top terms of a thesaurus. A top term is defined as any term which has a narrower term but has no broader terms.

This procedure differs from `TT` in that `TT` takes in a phrase and finds the top term for that phrase, but `THES_TT` searches the whole thesaurus and finds all top terms.

#### Large Thesauri

Because this procedure searches the whole thesaurus, it can take some time on large thesauri. Oracle recommends that you not call this often for such thesauri. Instead, your application should call this once, store the results in a separate table, and use those stored results.

#### Syntax

    CTX_THES.THES_TT(restab IN OUT NOCOPY EXP_TAB,
                     tname  IN VARCHAR2 DEFAULT 'DEFAULT');

restab
Specify the name of the expansion table to store the results. This table must be of type `EXP_TAB` which the system defines as follows:

    type exp_rec is record (
        xrel varchar2(12),
        xlevel number,
        xphrase varchar2(256)
    );
    type exp_tab is table of exp_rec index by binary_integer;

**See Also:**

"[CTX_THES Result Tables and Data Types](oracle-text-result-tables.md)" in [Oracle Text Result Tables](oracle-text-result-tables.md) for more information about `EXP_TAB`.

tname
Specify the thesaurus name. If not specified, system default thesaurus is used.

#### Returns

This procedure returns all top terms and stores them in `restab`.

### 14.28 TR

For a given mono-lingual thesaurus, this function returns the foreign language equivalent of a phrase as recorded in the thesaurus.

**Note:**

Foreign language translation is not part of the ISO-2788 or ANSI Z39.19 thesaural standards. The behavior of TR is specific to Oracle Text.

#### Syntax 1: Table Result

    CTX_THES.TR(restab IN OUT NOCOPY EXP_TAB,
                phrase IN VARCHAR2,
                lang   IN VARCHAR2 DEFAULT NULL,
                tname  IN VARCHAR2 DEFAULT 'DEFAULT')

#### Syntax 2: String Result

    CTX_THES.TR(phrase IN VARCHAR2,
                lang   IN VARCHAR2 DEFAULT NULL,
                tname  IN VARCHAR2 DEFAULT 'DEFAULT')
    RETURN VARCHAR2;

restab
Optionally, specify the name of the expansion table to store the results. This table must be of type `EXP_TAB` which the system defines as follows:

    type exp_rec is record (
        xrel varchar2(12),
        xlevel number,
        xphrase varchar2(256)
    );
    type exp_tab is table of exp_rec index by binary_integer;

**See Also:**

"[CTX_THES Result Tables and Data Types](oracle-text-result-tables.md)" in [Oracle Text Result Tables](oracle-text-result-tables.md) for more information about `EXP_TAB`.

phrase
Specify a phrase to lookup in thesaurus.

lang
Specify the foreign language. Specify `'ALL'` for all translations of `phrase`.

tname
Specify the thesaurus name. If not specified, system default thesaurus is used.

#### Returns

This function returns a string of foreign terms in the form:

     {ft1}|{ft2}|{ft3} ...

#### Example

Consider a thesaurus `MY_THES` with the following entries for cat:

    cat
      SPANISH: gato
      FRENCH:  chat
      SYN lion
        SPANISH: leon

To look up the translation for cat, enter the following statements:

    declare
      trans      varchar2(2000);
      span_trans varchar2(2000);
    begin
      trans := ctx_thes.tr('CAT','ALL','MY_THES');
      span_trans := ctx_thes.tr('CAT','SPANISH','MY_THES')
      dbms_output.put_line('the translations for CAT are: '||trans);
      dbms_output.put_line('the Spanish translations for CAT are: '||span_trans);
    end;


This codes produces the following output:

    the translations for CAT are: {CAT}|{CHAT}|{GATO}
    the Spanish translations for CAT are: {CAT}|{GATO}

#### Related Topics

"OUTPUT_STYLE "

"[Translation Term (TR)](oracle-text-CONTAINS-query-operators.md)"

### 14.29 TRSYN

For a given mono-lingual thesaurus, this function returns the foreign equivalent of a phrase, synonyms of the phrase, and foreign equivalent of the synonyms as recorded in the specified thesaurus.

**Note:**

Foreign language translation is not part of the ISO-2788 or ANSI Z39.19 thesaural standards. The behavior of `TRSYN` is specific to Oracle Text.

#### Syntax 1: Table Result

    CTX_THES.TRSYN(restab IN OUT NOCOPY EXP_TAB,
                   phrase IN VARCHAR2,
                   lang   IN VARCHAR2 DEFAULT NULL,
                   tname  IN VARCHAR2 DEFAULT 'DEFAULT');

#### Syntax 2: String Result

    CTX_THES.TRSYN(phrase IN VARCHAR2,
                lang   IN VARCHAR2 DEFAULT NULL,
                tname  IN VARCHAR2 DEFAULT 'DEFAULT')
    RETURN VARCHAR2;

restab
Optionally, specify the name of the expansion table to store the results. This table must be of type `EXP_TAB` which the system defines as follows:

    type exp_rec is record (
        xrel varchar2(12),
        xlevel number,
        xphrase varchar2(256)
    );
    type exp_tab is table of exp_rec index by binary_integer;

**See Also:**

"[CTX_THES Result Tables and Data Types](oracle-text-result-tables.md)" in [Oracle Text Result Tables](oracle-text-result-tables.md) for more information about `EXP_TAB`.

phrase
Specify a phrase to lookup in thesaurus.

lang
Specify the foreign language. Specify `'ALL'` for all translations of phrase.

tname
Specify the thesaurus name. If not specified, system default thesaurus is used.

#### Returns

This function returns a string of foreign terms in the form:

     {ft1}|{ft2}|{ft3} ...

#### Example

Consider a thesaurus `MY_THES` with the following entries for cat:

    cat
      SPANISH: gato
      FRENCH:  chat
      SYN lion
        SPANISH: leon

To look up the translation and synonyms for cat, enter the following statements:

    declare
      synonyms   varchar2(2000);
      span_syn   varchar2(2000);
    begin
      synonyms := ctx_thes.trsyn('CAT','ALL','MY_THES');
      span_syn := ctx_thes.trsyn('CAT','SPANISH','MY_THES')
      dbms_output.put_line('all synonyms for CAT are: '||synonyms);
      dbms_output.put_line('the Spanish synonyms for CAT are: '||span_syn);
    end;


This codes produces the following output:

    all synonyms for CAT are: {CAT}|{CHAT}|{GATO}|{LION}|{LEON}
    the Spanish synonyms for CAT are: {CAT}|{GATO}|{LION}|{LEON}

#### Related Topics

"OUTPUT_STYLE "

"[Translation Term Synonym (TRSYN)](oracle-text-CONTAINS-query-operators.md)"

### 14.30 TT

This function returns the top term of a phrase as recorded in the specified thesaurus.

#### Syntax 1: Table Result

    CTX_THES.TT(restab IN OUT NOCOPY EXP_TAB,
                phrase IN VARCHAR2,
                tname  IN VARCHAR2 DEFAULT 'DEFAULT');

#### Syntax 2: String Result

    CTX_THES.TT(phrase IN VARCHAR2,
                tname  IN VARCHAR2 DEFAULT 'DEFAULT')
    RETURN varchar2;

restab
Optionally, specify the name of the expansion table to store the results. This table must be of type `EXP_TAB` which the system defines as follows:

    type exp_rec is record (
        xrel varchar2(12),
        xlevel number,
        xphrase varchar2(256)
    );
    type exp_tab is table of exp_rec index by binary_integer;

**See Also:**

"[CTX_THES Result Tables and Data Types](oracle-text-result-tables.md)" in [Oracle Text Result Tables](oracle-text-result-tables.md) for more information about `EXP_TAB`.

phrase
Specify a phrase to lookup in thesaurus.

tname
Specify the thesaurus name. If not specified, system default thesaurus is used.

#### Returns

This function returns the top term string in the form:

    {tt}

#### Example

Consider a thesaurus `MY_THES` with the following broader term entries for dog:

    DOG
       BT1 CANINE
         BT2 MAMMAL
           BT3 VERTEBRATE
             BT4 ANIMAL

To look up the top term for DOG, execute the following code:

    declare
      terms varchar2(2000);
    begin
      terms := ctx_thes.tt('DOG','MY_THES');
      dbms_output.put_line('The top term for DOG is: '||terms);
    end;

This code produces the following output:

    The top term for dog is: {ANIMAL}

#### Related Topics

"OUTPUT_STYLE "

"[Top Term (TT)](oracle-text-CONTAINS-query-operators.md)"

### 14.31 UPDATE_TRANSLATION

Use this procedure to update an existing translation.

#### Syntax

    CTX_THES.UPDATE_TRANSLATION(tname       in     varchar2,
                                 phrase      in     varchar2,
                                 language    in     varchar2,
                                 translation in     varchar2,
                                 new_translation in varchar2);

tname
Specify the name of the thesaurus, using no more than 30 characters.

phrase
Specify the phrase in the thesaurus to which to update a translation. The phrase must already exist in the thesaurus or an error is raised.

language
Specify the language of the translation, using no more than 10 characters.

translation
Specify the translated term to update. If no such translation exists, an error is raised.

You can specify `NULL` if there is only one translation for the phrase. An error is raised if there is more than one translation for the term in the specified language.

new_translation
Optionally, specify the new form of the translated term.

#### Example

The following code updates the Spanish translation for dog:

    begin
       ctx_thes.update_translation('my_thes', 'dog', 'SPANISH:', 'PERRO', 'CAN');
    end;
