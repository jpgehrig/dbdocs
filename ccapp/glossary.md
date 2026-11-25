### alternate spelling

The use of spelling variations in German, Swedish, and Dutch; you can index these variations if you specify the `BASIC_LEXER` attribute named `ALTERNATE_SPELLING.`

### attribute

An optional parameter associated with a preference. For example, the `BASIC_LEXER` preference includes the `base_letter` attribute, which can have either the value of `YES` (perform base-letter conversions) or `NO` (do not perform such conversions). Set attributes with the `CTX_DDL.SET_ATTRIBUTE` procedure or with the `ALTER INDEX` statement. See also: preference, base-letter conversion.

### attribute section

A user-defined section, that represents an attribute of an XML document, such as `AUTHOR` or `TITLE.` Add attribute sections to section groups with `CTX_DDL.ADD_ATTR_SECTION` or with the `ALTER INDEX` statement. See also: AUTO_SECTION_GROUP, section, XML_SECTION_GROUP.

### AUTO_SECTION_GROUP

A section group used to automatically crate a zone section for each start-tag and end-tag pair in an XML document; attribute sections are automatically created for XML tags that have attributes. See also: attribute section, section, section group, XML_SECTION_GROUP, zone section.

### base-letter conversion

The conversion of a letter with alternate forms (such as accents, umlauts, or cedillas) to its basic form (for example, without an accent).

### BASIC_SECTION_GROUP

A section group used to define sections where the start and end tags are of the form `<tag>` and` </tag>.` It does not support nonbasic tags, such as comment tags or those with attributes or unbalanced parentheses. See also: HTML_SECTION_GROUP, section, section group.

### case

The capitalization of a word or letter, where uppercase letters are capitals (M instead of m, for example). Not all languages have case. Mixed-case indexing is supported for some languages, notably those of Western Europe.

### classification

Also known as document classification. The conceptual separation of source documents into groups, or clusters, based on their content. For example, a group of documents might be separated into clusters for medicine, finance, and sports.

Oracle Text includes rule-based classification, in which a person writes the rules for classifying documents (in the form of queries), and Oracle Text performs the document classification according to the rules; supervised classification, in which Oracle Text creates classification rules based on a set of sample documents; and clustering (also known as unsupervised classification), in which the clusters and rules are both created by Oracle Text.

### clustering

Also known as unsupervised classification. See: classification.

### composite domain index

Also known as CDI type of index. An Oracle Text index that not only indexes and processes a specified text column, but also indexes and processes `FILTER` `BY` and `ORDER` `BY` structured columns that are specified during index creation. See also: domain index.

### CONTEXT index

The basic type of Oracle Text index; an index on a text column. A `CONTEXT` index is useful when your source text consists of many large, coherent documents. Applications making use of `CONTEXT` indexes use the `CONTAINS` query operator to retrieve text.

### CTXAPP role

A role for application developers that enables a user to create Oracle Text indexes and index preferences and to use PL/SQL packages. This role must be granted to Oracle Text users.

### CTXCAT index

A combined index on a text column and one or more other columns. Typically used to index small documents or text fragments, such as item names, prices, and descriptions typically found in catalogs. The `CTXCAT` index typically has better mixed-query performance than the `CONTEXT` index.

Applications query this index with the `CATSEARCH` operator. This index is transactional, which means that it automatically updates itself when you make inserts, updates, or deletes to the base table.

### CTXRULE index

Used to build a document classification application. The `CTXRULE` index is an index created on a table of queries, where the queries serve as rules to define the classification criteria. This index is queried with the `MATCHES` operator.

### CTXSYS user

Created at install time. The `CTXSYS` user can view all indexes; synchronize all indexes; run `ctxkbtc`, the knowledge base extension compiler; query all system-defined views; and perform all tasks of a user with the `CTXAPP` role.

### datastore

The method of storing text. The method is determined by specifying a storage preference of a particular type. For example, the `DIRECT_DATASTORE` type stores data directly into the text column, whereas the `URL_DATASTORE` specifies that data is stored externally in a location specified by a URL.

### document services

Services that work at the document level, such as highlighting query terms in a document, marking up a document, or producing a document snippet during the query operation. The `CTX_DOC` PL/SQL package provides procedures and functions for requesting document services. See also: knowledge base.

### domain index

An Oracle Database domain index that indexes and processes a specified text column. See also: composite domain index.

### endjoin

One or more nonalphanumeric characters that, when encountered as the last character in a token, explicitly identify the end of the token. The characters, as well as any startjoin characters that immediately follow it, are included in the Oracle Text index entry for the token. For example, if you specify ++ as an endjoin, then C++ is recognized and indexed as a single token. See also: printjoin, skipjoin, startjoin.

### entity extraction

The identification and extraction of named entities within a text. Entities are mainly nouns and noun phrases, such as names, places, times, coded strings (such as phone numbers and zip codes), percentages, and monetary amounts. The `CTX_ENTITY` package implements entity extraction with a built-in dictionary and set of rules for English text. You can use user-provided add-on dictionaries and rule sets to extend the capabilities for English or for other languages.

### field section

Similar to a zone section, with the main difference being that you can index the content between the start and end tags of a field section separately from the rest of the document. This separate indexing enables field section content to be "hidden" from a normal query. (The `INPATH` and `WITHIN` operators may be used to find the term in such a section.) Field sections are useful when a section occurs once in a document, such as a field in a news header. Add field sections to section groups with the `CTX_DDL.ADD_FIELD_SECTION` procedure or with the `ALTER INDEX` statement. See also: INPATH operator, section, WITHIN operator, zone section.

### filtering

A step in the Oracle Text index-creation process. Depending on the filtering preferences associated with the creation of the index, one of three things happens during filtering: Formatted documents are filtered into marked-up text; text is converted from a non-database character set to a database character set; or no filtering takes place (HTML, XML, and plain-text documents are not filtered).

### fuzzy matching

Expanded query that includes words which are spelled similarly to the specified term. This type of expansion is helpful for finding more accurate results when there are frequent misspellings in a document set. Invoke fuzzy matching with the `FUZZY` query operator.

### HASPATH operator

A `CONTAINS` query operator used to find XML documents that contain a section path exactly as specified in the query. See also: PATH_SECTION_GROUP.

### highlighting

A generated version of a document or document fragments, with query terms displayed or called out in a special way.

Highlighting takes three forms. The `CTX_DOC.MARKUP` procedure returns a document with the query term surrounded by plain-text or HTML tags. The `CTX_DOC.HIGHLIGHT` procedure returns offsets for the query terms, so that the user can mark up the document. The `CTX_DOC.SNIPPET` procedure produces a concordance, with the query term displayed in fragments of surrounding text. See also: markup.

### HTML_SECTION_GROUP

A section group type used for defining sections in HTML documents. See also: BASIC_SECTION_GROUP, section, section group.

### INPATH operator

A `CONTAINS` query operator used to search within tags, or paths, of an XML document. It enables more generic path denomination than the `WITHIN` operator. See also: WITHIN operator.

### Key Word in Context (KWIC)

A presentation of a query term with the text that surrounds it in the source document. This presentation may consist of a single instance of the query term, several instances, or every instance in the source document. The `CTX_DOC.SNIPPET` procedure produces such a presentation.

### knowledge base

A hierarchical tree of concepts used for theme indexing, `ABOUT` queries, and derived themes for document services. You can create your own knowledge base or you can extend the standard Oracle Text knowledge base.

### lexer

A software program that breaks source text into tokens—usually words—in accordance with a specified language. To extract tokens, the lexer uses parameters as defined by a lexer preference. These parameters include the definitions for the characters that separate tokens, such as whitespace, and to the rules for converting text to all uppercase or not. When you enable theme indexing, the lexer analyzes text to create theme tokens.

When an application needs to index a table containing documents in more than one language, it can use `MULTI_LEXER` (the multilingual lexer) and create sub-lexers to handle each language. Add each sub-lexer to the main multi-lexer with the `CTX_DDl.ADD_SUB_LEXER` procedure. See also: sub-lexer.

### markup

A form of highlighting. The `CTX_DOC.MARKUP` and `CTX_DOC.POLICY_MARKUP` procedures take a query term and a document, and return the document with the query terms marked up; that is, surrounded either by plain-text characters or HTML tags. You can use predefined markup tags or specify your own. In comparison, `CTX_DOC.HIGHLIGHT` and `CTX_DOC.POLICY_HIGHLIGHT` return offsets for query terms, so that you can add your own highlighting tags. See also: highlighting.

### MDATA

See: metadata.

### MDATA section

User-defined index metadata. Using this metadata can speed up mixed `CONTAINS` queries. See also: metadata, mixed query, section.

### metadata

Information about a document that is not part of a document's regular content. For example, if an HTML document contains `<author>Smith</author>`, author is considered the metadata type and Smith is considered the value for `author`.

Use the `CTX_DDL.ADD_MDATA_SECTION` procedure to add sections containing metadata, known as `MDATA` sections, to a document. Metadata can speed up mixed queries. Such queries can be made with the `MDATA` operator. See also: mixed query, section.

### mixed query

A query that searches for two different types of information; for example, text content and document type. For example, a search for Jones in `<title>` metadata is a mixed query.

### name search

A solution to match proper names that might differ in spelling due to orthographic variation. It also enables you to search for somewhat inaccurate data, such as might occur when a record's first name and surname are not properly segmented. Also called name matching.

### NEWS_SECTION_GROUP

A section group type used for defining sections in newsgroup-formatted documents as defined by RFC 1036. See also: section, section group.

### normalized word

The form of a word after it has been transformed for indexing, according to the transformational rules in effect. Depending on the rules in effect, the normalized form of a word may be the same as the form found in the source document. The normalized form of a word may also include both the original and transformed versions. For example, if you specify New German Spelling, then the word Potential is normalized to both Potenzial and Potential.

### NULL_SECTION_GROUP

The default section group type when no sections are defined or when only `SENTENCE` or `PARAGRAPH` sections are defined. See also: section, section group, special section.

### PATH_SECTION_GROUP

A section group type used for indexing XML documents. It is similar to the `AUTO_SECTION_GROUP` type, except that it enables the use of the `HASPATH` and `INPATH` operators. See also: AUTO_SECTION_GROUP, HASPATH operator, INPATH operator, section, section group.

### preference

An optional parameter that affects how Oracle Text creates an index. For example, a lexer preference specifies the lexer to use when processing documents, such as `JAPANESE_VGRAM_LEXER.` There are preferences for storage, filtering, lexers, classifiers, wordlists, section types, and more. A preference may or may not be associated with attributes. Set preferences with the `CTX_DDL.CREATE_PREFERENCE` procedure. See also: attribute.

### printjoin

One or more nonalphanumeric characters that, whether they appear in the beginning, middle, or end of a word, are processed alphanumerically and are included with the token in an Oracle Text index. Also includes consecutive printjoins.

For example, if you define the hyphen (-) and underscore (\_) characters as printjoins, terms such as pseudo-intellectual and \_file\_ are stored in the Oracle Text index as pseudo-intellectual and \_file\_.

Printjoins differ from endjoins and startjoins in that position does not matter. For example, \$35 is indexed as one token if \$ is defined as a startjoin or a printjoin, but as two tokens if it is defined as an endjoin. See also: endjoin, printjoin, startjoin.

### result set

An interface that improves performance by sharing overhead. It enables you to produce, all at once, the disparate elements (such as metadata of the first few documents, total hit counts, and per-word hit counts) needed for a page of search results. You can also return data views that are difficult to express in SQL.

Generating these results in earlier versions of Oracle Text required several queries and calls. Each extra call takes time to reparse the query and look up index metadata. Moreover, some search operations, such as iterative query refinement are difficult for SQL.

### rule-based classification

See: classification.

### structured/sort data (SDATA) section

A section type that supports equality and range searches. By default, all `FILTER` `BY` and `ORDER` `BY` columns are mapped as `SDATA` sections. An `SDATA` section contains user-defined index metadata. Use of this type of section can speed up mixed `CONTAINS` queries. See also: mixed query, section.

### section

A subdivision of a document; for example, everything within an `...` section of an HTML page. The various section types include attribute, field, HTML, MDATA, special, stop, XML, and zone sections.

By dividing a document into sections and then searching within sections, you can to narrow text queries down to blocks of text within documents. Section searching is useful when your documents have internal structure, such as HTML and XML documents. You can also search for text at the sentence and paragraph level.

Perform section searching with the `HASPATH,` `ISPATH,` or `WITHIN` operator. When indexing, use the section group to enable section searching. See Also: section group.

### section group

A group that identifies a type of document set and implicitly indicates the tag structure for indexing. For instance, to index HTML-tagged documents, use the `HTML_SECTION_GROUP` section group type. Likewise, to index XML-tagged documents, the `XML_SECTION_GROUP` section group type. Declare section groups with the `CTX_DDL.CREATE_SECTION_GROUP` procedure or with the `ALTER INDEX` statement. See also: section.

### skipjoin

A non-alphanumeric character that, when it appears within a word, identifies the word as a single token; however, the character is not stored with the token in the Oracle Text index. For example, if you define the hyphen character (-) as a skipjoin, then the word pseudo-intellectual is stored in the Oracle Text index as pseudointellectual. See also: endjoin, printjoin, startjoin.

### startjoin

One or more non-alphanumeric characters that, when encountered as the first character in a token, explicitly identify the start of the token. The characters, as well as any other `startjoins` characters that immediately follow it, are included in the Oracle Text index entry for the token. For example, if you define '\$' as a startjoin, then \$35 is indexed as a single token. In addition, the first `startjoins` character in a string of `startjoins` characters implicitly ends the previous token. See also: endjoin, printjoin, skipjoin.

### stemming

The expansion of a query term to include all terms having the same root word. For example, stemming the verb talk yields talking, talks, and talked, as well as talk (but not talkie). Stemming is distinct from wildcard expansion, in which results are related only through spelling, not through morphology. See also: wildcard expansion.

### special section

A document section that is not bounded by tags. Instead, sections are formed by plaintext document structures such as sentences and paragraphs. Special sections are added to a section group with the `CTX_DDL.ADD_SPECIAL_SECTION` procedure. See also: section, section group.

### stop section

A section that, when added to `AUTO_SECTION_GROUP,` causes the information for document sections of that type to be ignored during indexing; however, the section content may still be searched. Add stop sections to section groups with the `CTX_DDL.ADD_STOP_SECTION` procedure. See also: AUTO_SECTION_GROUP, section, section group.

### stopclass

A class of tokens, such as `NUMBER`s, that are to be skipped over during indexing. To specify stopclasses, add them to stoplists with `CTX_DDL.ADD_STOPCLASS.` See also: stoplist.

### stoplist

A list of words, known as stopwords, themes (stopthemes), and data classes (stopclasses) that are not to be indexed. By default, the system indexes text by using the system-supplied stoplist that corresponds to a given database language.

Oracle Text provides default stoplists for most common languages, including English, French, German, Spanish, Chinese, Dutch, and Danish. These default stoplists contain only stopwords. Create stoplists with the `CTX_DDL.CREATE_STOPLIST` procedure or with the `ALTER INDEX` statement. See also: stopclass, stoptheme, stopword.

### stoptheme

A theme to be skipped over during indexing. Specify stopthemes by adding them to stoplists with the `CTX_DDL.ADD_STOPTHEMES` procedure. See also: stoplist.

### stopword

A word to be skipped during indexing. Specify stopwords by adding them to stoplists with the `CTX_DDL.ADD_STOPWORD` procedure. You can also dynamically add them to an index by using the `ALTER INDEX` statement. See also: stoplist.

### sub-lexer

See: lexer.

### supervised classification

See: classification.

### theme

A topic associated with a given document. A document may have many themes. A theme does not have to appear in a document; for example, a document containing the words San Francisco may have California as one of its themes.

Add theme components to indexes with the `INDEX_THEMES` attribute of the `BASIC_LEXER` preference; extract them from a document with the `CTX_DOC.THEMES` procedure and query them with the `ABOUT` operator.

### unsupervised classification

Also known as clustering. See: classification.

### wildcard expansion

The expansion of a query term to return words that fit a given pattern. For example, expansion of the query term %rot% returns both trot and rotten. Wildcard expansion is distinct from stemming. See also: stemming.

### whitespace

Characters that are treated as blank spaces between tokens. The predefined default values for whitespace are 'space' and 'tab'. The `BASIC_LEXER` uses whitespace characters (in conjunction with `punctuations` and `newline` characters) to identify character strings that serve as sentence delimiters for sentence and paragraph searching.

### WITHIN operator

A `CONTAINS` query operator used to search for query terms within a given XML document section. It is similar to the `INPATH` operator, but less generic. See also: INPATH operator.

### wordlist

An Oracle Text preference that enables features such as fuzzy, stemming, and prefix indexing for better wildcard searching, as well as substring and prefix indexing. The wordlist preference improves performance for wildcard queries with `CONTAINS` and `CATSEARCH.` Create wordlists with the `CTX_DDL.ADD_WORDLIST` procedure or with the `ALTER INDEX` statement. See also: preference.

### XML section

A section that is defined by XML tags, enabling XML section searching. Indexing with XML sections allows automatic sectioning and creating document-type-sensitive sections. XML section searching includes attribute searching and path section searching with the `INPATH,` `HASPATH,` and `WITHIN` operators. See also: section.

### XML_SECTION_GROUP

A section group used to identify XML documents for indexing. See also: section, section group.

### zone section

The basic type of document section; a body of text delimited by start and end tags in a document. Zone sections are well suited for defining sections in HTML and XML documents. Add zone sections to section groups with the `CTX_DDL.ADD_ZONE_SECTION` procedure or with the `ALTER INDEX` statement. See also: field section, section, section group.
