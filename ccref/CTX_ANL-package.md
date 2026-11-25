## 6  CTX_ANL Package

This chapter contains the following topics.

- About CTX_ANL Package Procedures

- ADD_DICTIONARY

- DROP_DICTIONARY

### 6.1 About CTX_ANL Package Procedures

The `CTX_ANL` PL/SQL package is used with [AUTO_LEXER](oracle-text-indexing-elements.md) and provides procedures for adding and dropping a custom dictionary from the lexer. A custom dictionary might be one that you develop for a special field of study or for your industry. In most cases, the dictionaries supplied with Oracle Text are more than sufficient to handle your requirements.

**See Also:**

"[AUTO_LEXER](oracle-text-indexing-elements.md)" for a discussion of AUTO_LEXER and supported languages

The `CTX_ANL` package contains the following stored procedures.

| Name            | Description                               |
|:----------------|:------------------------------------------|
| ADD_DICTIONARY  | Adds a custom dictionary to the lexer.    |
| DROP_DICTIONARY | Drops a custom dictionary from the lexer. |

**Note:**

Only the `CTXSYS` user can use the procedures in `CTX_ANL`.

The APIs in the `CTX_ANL` package do not support identifiers that are prefixed with the schema or the owner name.

### 6.2 ADD_DICTIONARY

Use the CTX_ANL.ADD_DICTIONARY procedure to add a custom dictionary to be used by "[AUTO_LEXER](oracle-text-indexing-elements.md)".

**Note:**

The dictionary data is not processed until index/policy creation time or ALTER INDEX time. Errors in dictionary data format are detected at index/policy creation time or ALTER INDEX time and result in error: DRG-13710: Syntax Error in Dictionary.

#### Syntax

    CTX_ANL.ADD_DICTIONARY(
      name          in VARCHAR2,
      language      in VARCHAR2,
      dictionary    in CLOB
      );

name
The unique name for the user-created custom dictionary.

**Note:**

The unique name may not be prefixed by the schema or the owner name as this syntax is not supported.

language
The language used by the custom dictionary.

dictionary
The CLOB containing the custom dictionary. The custom dictionary comprises a list of definitions, which are declared separated by a tab or one per line as described in "Custom Dictionary Format and Syntax".

#### Custom Dictionary Format and Syntax

The custom dictionary enables you to define a new stem or redefine an existing stem to add words to [AUTO_LEXER](oracle-text-indexing-elements.md) for your language.

Define a new stem or redefine an existing one using the following syntax:

    COMPOUND<tab>word|word<tab>STEM<tab>word<tab>parts-of-speech<tab>features

COMPOUND
Use `COMPOUND` to create a compound word by joining two whole words with a pipe (\|). The `word` is a simple text string that you want to join to another word to create one compound word to add to the language you specify in [AUTO_LEXER](oracle-text-indexing-elements.md).

Note that `COMPOUND` supports a maximum of 8 component words for a compound word.

<!-- -->

STEM
Use `STEM` to add the root for a new word.

<!-- -->

word
For `COMPOUND` and `STEM`, the `word` value is a simple text string respresenting a word that you want to join with another word to create a new word; or a word root or stem that you want to add to the language dictionary in AUTO_LEXER.

<!-- -->

parts-of-speech
The `parts-of-speech` value is a list of valid parts of speech, separated by a comma. Table 6-1 lists the names for `parts-of-speech` value. At least one `parts-of-speech` value is required.

<!-- -->

features
The `features` represent a list of valid linguistic features, as shown in Table 6-2. Multiple features are separated by a comma. Features are optional. If the word is already defined in the supplied language dictionary, then this definition overrides it. It is an error to have an invalid value for `parts-of-speech` or `features`.

Table 6-1 Custom Dictionary Valid Parts-of-Speech (case sensitive)

| Part-of-Speech | Description                                                                                                                                                         |
|:---------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| noun           | A simple noun, like table, book, or procedure.                                                                                                                      |
| nounProper     | A proper name, for person, place, etc., typically capitalized, like Zachary, Supidito, Susquehanna                                                                  |
| adjective      | Modifiers of nouns, which typically can be compared (green, greener, greenest), like fast, trenchant, pendulous.                                                    |
| adverb         | Any general modifier of a sentence that may modify an adjective or verb or may stand alone, like slowly, yet, perhaps.                                              |
| preposition    | A word that forms a prepositional phrase with a noun, like off, beside, from. Used for postpositions too, in languages that have postpositions of similar function. |

Table 6-2 lists the features and their usage. The specified language determines whether these are relevant and necessary. Note that declension refers to the inflection some languages use to determine number (singular or plural), case, and gender. The features are relevant depending on the language for the custom dictionary.

Table 6-2 Custom Dictionary Valid Features

| Feature (case sensitive) | Description     |
|:-------------------------|:----------------|
| genderMasculine          | masculine       |
| genderFeminine           | feminine        |
| genderNeuter             | neuter          |
| declensionHard           | hard declension |
| declensionSoft           | soft declension |

#### Examples

    exec CTX_DDL.CREATE_PREFERENCE('A_LEX', 'AUTO_LEXER');
    exec CTX_ANL. ADD_DICTIONARY('my_dict1', 'ENGLISH', lobloc);
    select * from CTX_USR_ANL_DICTS;
    exec CTX_DDL.SET_ATTRIBUTE('A_LEX', 'english_dictionary', 'MY_ENGLISH');

The following example creates a custom dictionary named `d1` to be added to AUTO_LEXER for the English language.

    declare
     dict clob;
    begin
     dict := '# compounds
    COMPOUND        help|desk
    COMPOUND        help|desks
    COMPOUND        book|shelf
    COMPOUND        book|shelves
    COMPOUND        back|woods|man
    '||
    '# define company abbreviations
    STEM    comp.   noun
    STEM    ltd.    noun
    STEM    co.     noun
    STEM    oracle  nounProper
    STEM    make    verb
    STEM    unkword noun
    STEM    unkword verb
    ';
     ctx_anl.add_dictionary('d1','ENGLISH',dict);
    end;
    /

#### Related Topics

"[AUTO_LEXER](oracle-text-indexing-elements.md)"

"[CREATE_PREFERENCE](CTX_DDL-package.md) "

"[SET_ATTRIBUTE](CTX_DDL-package.md) "

"DROP_DICTIONARY"

### 6.3 DROP_DICTIONARY

Use this procedure to drop a custom dictionary from [AUTO_LEXER](oracle-text-indexing-elements.md).

#### Syntax

    CTX_ANL.DROP_DICTIONARY(
      name          in VARCHAR2,
      language      in VARCHAR2,
      dictionary    in CLOB
      );

name
The unique name for the user-created custom dictionary.

**Note:**

The unique name may not be prefixed by the schema or the owner name as this syntax is not supported.

language
The language for the custom dictionary.

dictionary
The CLOB representing the custom dictionary.

#### Example

    begin
       CTX_ANL.DROP_DICTIONARY('dict1', 'english', 'dictionary');
    end;

#### Related Topic

"[AUTO_LEXER](oracle-text-indexing-elements.md)"

"ADD_DICTIONARY"
