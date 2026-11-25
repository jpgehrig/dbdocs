## 17  Oracle Text Alternative Spelling

This chapter describes various ways that Oracle Text handles alternative spelling of words. It also documents the alternative spelling conventions that Oracle Text uses in the German, Danish, and Swedish languages.

The following topics are covered:

- Overview of Alternative Spelling Features

- Overriding Alternative Spelling Features

- Alternative Spelling Conventions

### 17.1 Overview of Alternative Spelling Features

Some languages have alternative spelling forms for certain words. For example, the German word Schoen can also be spelled as Schön.

The form of a word is either original or normalized. The original form of the word is how it appears in the source document. The normalized form is how it is transformed, if it is transformed at all. Depending on the word being indexed and which system preferences are in effect (these are discussed in this chapter), the normalized form of a word may be the same as the original form. Also, the normalized form may comprise more than one spelling. For example, the normalized form of Schoen is both Schoen and Schön.

Oracle Text handles indexing of alternative word forms in the following ways:

- Alternate Spelling—indexing of alternative forms is enabled

- Base-Letter Conversion—accented letters are transformed into non-accented representations

- New German Spelling—reformed German spelling is accepted

Enable these features by specifying the appropriate attribute to the `BASIC_LEXER`. For instance, enable alternate spelling by specifying either `GERMAN`, `DANISH`, or `SWEDISH` for the `ALTERNATE_SPELLING` attribute. As an example, here is how to enable alternate spelling in German:

    begin
    ctx_ddl.create_preference('GERMAN_LEX', 'BASIC_LEXER');
    ctx_ddl.set_attribute('GERMAN_LEX', 'ALTERNATE_SPELLING', 'GERMAN');
    end;

To disable alternate spelling, use the `CTX_DDL.UNSET_ATTRIBUTE` procedure as follows:

    begin
    ctx_ddl.unset_attribute('GERMAN_LEX', 'ALTERNATE_SPELLING');
    end;

Oracle Text converts query terms to their normalized forms before lookup. As a result, users can query words with either spelling. If Schoen has been indexed as both Schoen and Schön, a query with Schön returns documents containing either form.

This section contains the following topics.

- Alternate Spelling

- Base-Letter Conversion

- New German Spelling

#### 17.1.1 Alternate Spelling

When Swedish, German, or Danish has more than one way of spelling a word, Oracle Text normally indexes the word in its original form; that is, as it appears in the source document.

When Alternate Spelling is enabled, Oracle Text indexes words in their normalized form. So, for example, Schoen is indexed both as Schoen and as Schön, and a query on Schoen will return documents containing either spelling. (The same is true of a query on Schön.)

To enable Alternate Spelling, set the `BASIC_LEXER` attribute `ALTERNATE_SPELLING` to `GERMAN`, `DANISH`, or `SWEDISH`. See "[BASIC_LEXER](oracle-text-indexing-elements.md)" for more information.

#### 17.1.2 Base-Letter Conversion

Besides alternative spelling, Oracle Text also handles base-letter conversions. With base-letter conversions enabled, letters with umlauts, acute accents, cedillas, and the like are converted to their basic forms for indexing, so fiancé is indexed both as fiancé and as fiance, and a query of fiancé returns documents containing either form.

To enable base-letter conversions, set the `BASIC_LEXER` attribute `BASE_LETTER` to `YES`. See "[BASIC_LEXER](oracle-text-indexing-elements.md)" for more information.

When Alternate Spelling is also enabled, Base-Letter Conversion may need to be overridden to prevent unexpected results. See "Overriding Alternative Spelling Features" for more information.

##### Generic Versus Language-Specific Base-Letter Conversions

The `BASE_LETTER_TYPE` attribute affects the way base-letter conversions take place. It has two possible values: `GENERIC` or `SPECIFIC`.

The `GENERIC` value is the default and specifies that base letter transformation uses one transformation table that applies to all languages.

The `SPECIFIC` value means that a base-letter transformation that has been specifically defined for your language will be used. This enables you to use accent-sensitive searches for words in your own language, while ignoring accents that are from other languages.

For example, both the `GENERIC` and the Spanish `SPECIFIC` tables will transform é into e. However, they treat the letter ñ distinctly. The `GENERIC` table treats ñ as an n with an accent (actually, a tilde), and so transforms ñ to n. The Spanish `SPECIFIC` table treats ñ as a separate letter of the alphabet, and thus does not transform it.

#### 17.1.3 New German Spelling

In 1996, new spelling rules for German were approved by representatives from all German-speaking countries. For example, under the spelling reforms, Potential becomes Potenzial, Schiffahrt becomes Schifffahrt, and schneuzen becomes schnäuzen.

When the `BASIC_LEXER` attribute `NEW_GERMAN_SPELLING` is set to `YES`, then a `CONTAINS` query on a German word that has both new and traditional forms will return documents matching both forms. For example, a query on Potential returns documents containing both Potential and Potenzial. The default setting is `NO`.

**Note:**

Under reformed German spelling, many words traditionally spelled as one word, such as soviel, are now spelled as two (so viel). Currently, Oracle Text does not make these conversions, nor conversions from two words to one (for example, weh tun to wehtun).

The case of the transformed word is determined from the first two characters of the word in the source document; that is, schiffahrt becomes schifffahrt, Schiffahrt becomes Schifffahrt, and SCHIFFAHRT becomes SCHIFFFAHRT.

As many new German spellings include hyphens, it is recommended that users choosing `NEW_GERMAN_SPELLING` define hyphens as `printjoin`s.

See "[BASIC_LEXER](oracle-text-indexing-elements.md)" for more information on setting this attribute.

### 17.2 Overriding Alternative Spelling Features

Even when alternative spelling features have been specified by lexer preference, it is possible to override them.

You can override base-letter conversion when Alternate Spelling is used, to prevent characters with alternate spelling forms, such as ü, ö, and ä, from also being transformed to the base letter forms.

#### Overriding Base-Letter Transformations with Alternate Spelling

Transformations caused by turning on `alternate_spelling` are performed before those of `base_letter`, which can sometimes cause unexpected results when both are enabled.

When Alternate Spelling is enabled, Oracle Text converts two-letter forms to single-letter forms (for example, ue to ü), so that words can be searched in both their base and alternate forms. Therefore, with Alternate Spelling enabled, a search for Schoen will return documents with both Schoen and Schön.

However, when Base-letter Transformation is also enabled, the ü in Schlüssel is transformed into a u, producing the non-existent word (in German, anyway) Schlussel, and the word is indexed in all three forms.

To prevent this secondary conversion, set the `OVERRIDE_BASE_LETTER` attribute to TRUE.

`OVERRIDE_BASE_LETTER` only affects letters with umlauts; accented letters, for example, are still transformed into their base forms.

For more on `BASE_LETTER`, see "Base-Letter Conversion".

### 17.3 Alternative Spelling Conventions

The following sections show the alternative spelling substitutions used by Oracle Text.

- German Alternate Spelling Conventions

- Danish Alternate Spelling Conventions

- Swedish Alternate Spelling Conventions

#### 17.3.1 German Alternate Spelling Conventions

The German alphabet is the English alphabet plus the additional characters: ä ö ü ß. Table 17-1 lists the alternate spelling conventions Oracle Text uses for these characters.

Table 17-1 German Alternate Spelling Conventions

| Character | Alternate Spelling Substitution |
|:----------|:--------------------------------|
| ä         | ae                              |
| ü         | ue                              |
| ö         | oe                              |
| Ä         | AE                              |
| Ü         | UE                              |
| Ö         | OE                              |
| ß         | ss                              |

#### 17.3.2 Danish Alternate Spelling Conventions

The Danish alphabet is the Latin alphabet without the w, plus the special characters: ø æ å. Table 17-2 lists the alternate spelling conventions Oracle Text uses for these characters.

Table 17-2 Danish Alternate Spelling Conventions

| Character | Alternate Spelling Substitution |
|:----------|:--------------------------------|
| æ         | ae                              |
| ø         | oe                              |
| å         | aa                              |
| Æ         | AE                              |
| Ø         | OE                              |
| Å         | AA                              |

#### 17.3.3 Swedish Alternate Spelling Conventions

The Swedish alphabet is the English alphabet without the w, plus the additional characters: å ä ö. Table 17-3 lists the alternate spelling conventions Oracle Text uses for these characters.

Table 17-3 Swedish Alternate Spelling Conventions

| Character | Alternate Spelling Convention |
|:----------|:------------------------------|
| ä         | ae                            |
| å         | aa                            |
| ö         | oe                            |
| Ä         | AE                            |
| Å         | AA                            |
| Ö         | OE                            |
