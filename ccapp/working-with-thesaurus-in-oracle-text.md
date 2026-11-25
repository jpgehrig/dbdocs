You can improve your query application with a thesaurus.

This chapter contains the following topics:

- Overview of Oracle Text Thesaurus Features

- Defining Terms in a Thesaurus

- Using a Thesaurus in a Query Application

- Loading a Custom Thesaurus and Issuing Thesaurus-Based Queries

- Augmenting the Knowledge Base with a Custom Thesaurus

- Linking New Terms to Existing Terms

- Example of Loading a Thesaurus with ctxload

- Example of Loading a Thesaurus with the CTX_THES.IMPORT_THESAURUS PL/SQL procedure

- Compiling a Loaded Thesaurus

- About the Supplied Knowledge Base

### 13.1 Overview of Oracle Text Thesaurus Features

Users of your query application looking for information on a given topic might not know which words have been used in documents that refer to that topic.

Oracle Text enables you to create case-sensitive or case-insensitive thesauruses that define synonym and hierarchical relationships between words and phrases. You can then retrieve documents that contain relevant text by expanding queries to include similar or related terms as defined in the thesaurus.

You can create a thesaurus and load it into the system.

This section contains the following topics.

- Oracle Text Thesaurus Creation and Maintenance

- Using a Case-sensitive Thesaurus

- Using a Case-insensitive Thesaurus

- Default Thesaurus

- Supplied Thesaurus

**Note:**

Oracle Text thesaurus formats and functionality are compliant with both the ISO-2788 and ANSI Z39.19 (1993) standards.

#### 13.1.1 Oracle Text Thesaurus Creation and Maintenance

If you have the `CTXAPP` role, you can create, modify, delete, import, and export thesauruses and thesaurus entries.

This section contains the following topics.

- CTX_THES Package: To maintain and browse your thesaurus programatically, you can use the `CTX_THES` PL/SQL package. With this package, you can browse terms and hierarchical relationships, add and delete terms, add and remove thesaurus relations, and import and export thesauruses in and out of the thesaurus tables.

- Thesaurus Operators: To expand query terms according to your loaded thesaurus, you can use the thesaurus operators in the `CONTAINS` clause. For example, use the `SYN` operator to expand a term such as dog to its synonyms:

  `'syn(dog)'`

- ctxload Utility: You can use the `ctxload` utility to load thesauruses from a plain-text file into the thesaurus tables, and to dump thesauruses from the tables into output (or dump) files.

  You can print the thesaurus dump files, you can use them as input for other applications, and you can use them to load a thesaurus into the thesaurus tables (useful when you want to use an existing thesaurus as the basis for a new thesaurus).

  **WARNING:**

  To ensure sound security practices, Oracle recommends that you enter the password for `ctxload` by using the interactive mode, which prompts you for the user password. Oracle strongly recommends that you do not enter a password on the command line.

  **Note:**

  You can also programatically import and export thesauruses in and out of the thesaurus tables using the PL/SQL package `CTX_THES` procedures `IMPORT_THESAURUS` and `EXPORT_THESAURUS`.

  Refer to [Oracle Text Reference](../ccref/CTX_THES-package.md) for more information about these procedures.

#### 13.1.2 Using a Case-Sensitive Thesaurus

In a case-sensitive thesaurus, terms (words and phrases) are stored exactly as you enter them. For example, if you enter a term in mixed case (using either the `CTX_THES` package or a thesaurus load file), then the thesaurus stores the entry in mixed case.

**Note:**

To take full advantage of query expansions that result from a case-sensitive thesaurus, your index must also be case-sensitive.

When loading a thesaurus, you can specify a case-sensitive thesaurus by using the `-thescase` parameter.

When creating a thesaurus with either `CTX_THES.CREATE_THESAURUS` or `CTX_THES.IMPORT_THESAURUS,` you can specify a case-sensitive thesaurus.

In addition, when you specify a case-sensitive thesaurus in a query, the thesaurus lookup uses the query terms exactly as you enter them in the query. Therefore, queries that use case-sensitive thesauruses allow for a higher level of precision in the query expansion, which helps lookup when and only when you have a case-sensitive index.

For example, a case-sensitive thesaurus is created with different entries for the distinct meanings of the terms Turkey (the country) and turkey (the type of bird). Using the thesaurus, a query for Turkey expands to include only the entries associated with Turkey.

#### 13.1.3 Using a Case-Insensitive Thesaurus

In a case-insensitive thesaurus, terms are stored in all uppercase, regardless of the case in which they were originally entered.

The `ctxload` program loads a thesaurus in case-insensitive mode by default.

When creating a thesaurus with either `CTX_THES`.`CREATE_THESAURUS` or `CTX_THES.IMPORT_THESAURUS,` the thesaurus is created as case-insensitive by default.

In addition, when you specify a case-insensitive thesaurus in a query, the query terms are converted to all uppercase for thesaurus lookup. As a result, Oracle Text is unable to distinguish between terms that have different meanings when they are in mixed case.

For example, a case-insensitive thesaurus is created with different entries for the two distinct meanings of the term TURKEY (the country or the type of bird). Using the thesaurus, a query for either Turkey or turkey is converted to TURKEY for thesaurus lookup and then expanded to include all the entries associated with both meanings.

#### 13.1.4 Default Thesaurus

If you do not specify a thesaurus by name in a query, by default, the thesaurus operators use a thesaurus named DEFAULT. However, Oracle Text does not provide a DEFAULT thesaurus.

As a result, if you want to use a default thesaurus for the thesaurus operators, you must create a thesaurus named DEFAULT. You can create the thesaurus through any of the thesaurus creation methods supported by Oracle Text:

- `CTX_THES`.`CREATE_THESAURUS` (PL/SQL)

- `CTX_THES`.`IMPORT_THESAURUS` (PL/SQL)

- `ctxload` utility

  **See Also:**

  [Oracle Text Reference](../ccref/CTX_THES-package.md) to learn more about using `ctxload` and the `CTX_THES` package

#### 13.1.5 Supplied Thesaurus

Although Oracle Text does not provide a default thesaurus, Oracle Text does supply a thesaurus, in the form of a file that you load with `ctxload,` you can use to create a general-purpose, English-language thesaurus.

You can use the thesaurus load file to create a default thesaurus for Oracle Text, or you can use it as the basis for thesauruses tailored to a specific subject or range of subjects.

- Supplied Thesaurus Structure and Content: The supplied thesaurus is similar to a traditional thesaurus, such as Roget's Thesaurus, in that it provides a list of synonymous and semantically related terms.

  It provides additional value by organizing the terms into a hierarchy that defines real-world, practical relationships between narrower terms and their broader terms.

  Additionally, cross-references are established between terms in different areas of the hierarchy.

- Supplied Thesaurus Location: The exact name and location of the thesaurus load file depends on the operating system; however, the file is generally named `dr0thsus` (with an appropriate extension for text files) and is generally located in the following directory structure:

      <Oracle_home_directory>
          <Oracle_Text_directory>
             sample
                 thes

**See Also:**

- [Oracle Database Installation Guide](../install-and-upgrade.md) for the installation documentation specific to your operating system for more information about the directory structure of Oracle Text

- [Oracle Text Reference](../ccref/CTX_THES-package.md) to learn more about using `ctxload` and the `CTX_THES` package

### 13.2 Defining Terms in a Thesaurus

You can create synonyms, related terms, and hierarchical relationships with a thesaurus.

This section contains the following topics.

- Defining Synonyms

- Defining Hierarchical Relations

#### 13.2.1 Defining Synonyms

If you have a thesaurus of computer science terms, then you might define a synonym for the term XML as extensible markup language. This synonym enables queries on either of these terms to return the same documents.

    XML

    SYN Extensible Markup Language

You can use the `SYN` operator to expand XML into its synonyms:

    'SYN(XML)'

is expanded to:

    'XML, Extensible Markup Language'

#### 13.2.2 Defining Hierarchical Relations

If your document set consists of news articles, you can use a thesaurus to define a hierarchy of geographical terms. Consider the following that describes a geographical hierarchy for the state of California:

    California
       NT Northern California
           NT San Francisco
           NT San Jose
       NT Central Valley
           NT Fresno
       NT Southern California
           NT Los Angeles

You can use the `NT` operator to expand a query on California:

    'NT(California)'

is expanded to:

    'California, Northern California, San Francisco, San Jose, Central Valley,
      Fresno, Southern California, Los Angeles'

The resulting hitlist shows all documents related to the state of California regions and cities.

### 13.3 Using a Thesaurus in a Query Application

When you define a custom thesaurus, you can process queries more intelligently. Because users of your application might not know which words represent a topic, you can define synonyms or narrower terms for likely query terms. You can use the thesaurus operators to expand your query into your thesaurus terms.

There are two ways that you can enhance your query application with a custom thesaurus so that you can process queries more intelligently. Each approach has its advantages and disadvantages.

- Load your custom thesaurus and enter queries with thesaurus operators

- Augment the knowledge base with your custom thesaurus (English only) and use the `ABOUT` operator to expand your query.

### 13.4 Loading a Custom Thesaurus and Issuing Thesaurus-Based Queries

You can build and load a custom thesaurus.

The advantage of this method is that you can modify the thesaurus after indexing.

The limitation of this method is that you must use thesaurus expansion operators in your query. Long queries can cause extra overhead in the thesaurus expansion and slow your query down.

To build a custom thesaurus:

1.  Create your thesaurus. See "Defining Terms in a Thesaurus".
2.  Load the thesaurus with `ctxload.` The following example imports a thesaurus named `tech_doc` from an import file named `tech_thesaurus.txt:`
        ctxload -thes -name tech_doc -file tech_thesaurus.txt
3.  At the prompt, enter your user name and password. To ensure security, do not enter a password at the command line.
4.  Use `THES` operators to query. For example, you can find all documents that contain XML and its synonyms as defined in `tech_doc:`
        'SYN(XML, tech_doc)'

### 13.5 Augmenting the Knowledge Base with a Custom Thesaurus

You can add your custom thesaurus to a branch in the existing knowledge base. The knowledge base is a hierarchical tree of concepts used for theme indexing, `ABOUT` queries, and derived themes for document services.

When you augment the existing knowledge base with your new thesaurus, you query with the `ABOUT` operator. The query implicitly expands to synonyms and narrower terms. You do not query with the thesaurus operators.

To augment the existing knowledge base with your custom thesaurus:

1.  Create your custom thesaurus, linking new terms to existing knowledge base terms.
2.  Load the thesaurus one of the following ways:
    - Using the `ctxload` utility. See "Example of Loading a Thesaurus with ctxload".

    - Using the PL/SQL procedure `CTX_THES.IMPORT_THESAURUS.` See "Example of Loading a Thesaurus with the CTX_THES.IMPORT_THESAURUS PL/SQL procedure".
3.  Compile the loaded thesaurus with the `ctxkbtc` compiler.
4.  Index your documents. By default the system creates a theme component for your index.
5.  Use the `ABOUT` operator to query. For example, to find all documents that are related to the term politics, including any synonyms or narrower terms as defined in the knowledge base, enter this query:
        'about(politics)'

    **See Also:**

    - "Defining Terms in a Thesaurus" and "Linking New Terms to Existing Terms"

    - "Compiling a Loaded Thesaurus"

#### 13.5.1 Advantages

Compiling your custom thesaurus with the existing knowledge base before indexing enables faster and simpler queries with the `ABOUT` operator. Document services can also take full advantage of the customized information to create theme summaries and gists.

#### 13.5.2 Limitations

Use of the `ABOUT` operator requires a theme component in the index, which requires slightly more disk space. You must also define the thesaurus before indexing your documents. If you change the thesaurus, you must recompile your thesaurus and reindex your documents.

### 13.6 Linking New Terms to Existing Terms

When you add terms to the knowledge base, for best results in theme proving, Oracle recommends that you links new terms to one of the categories in the knowledge base.

**See Also:**

[Oracle Text Reference](../ccref/oracle-text-utilities.md) for more information about the supplied English knowledge base

If you keep new terms separate from existing categories, fewer themes from new terms are proven. The result is poor precision and recall with `ABOUT` queries, as well as poor quality of gists and theme highlighting.

You link new terms to existing terms by making an existing term the broader term for the new terms.

Consider the example: You purchase a `medthes` medical thesaurus containing a hierarchy of medical terms. The following are the top four terms in the thesaurus:

- Anesthesia and Analgesia

- Anti-Allergic and Respiratory System Agents

- Anti-Inflammatory Agents, Antirheumatic Agents, and Inflammation Mediators

- Antineoplastic and Immunosuppressive Agents

To map these terms to the existing health and medicine branch in the knowledge base, add the following entries to the medical thesaurus:

    health and medicine
     NT Anesthesia and Analgesia
     NT Anti-Allergic and Respiratory System Agents
     NT Anti-Inflamammatory Agents, Antirheumatic Agents, and Inflamation Mediators
     NT Antineoplastic and Immunosuppressive Agents

### 13.7 Example of Loading a Thesaurus with ctxload

Assuming the medical thesaurus is in the `med.thes` file, you load the thesaurus as `medthes` with `ctxload` as follows:

    ctxload -thes -thescase y -name medthes -file med.thes -user ctxsys

When you enter the `ctxload` command line, you are prompted for the user password. For best security practices, never enter the password at the command line. Alternatively, you may omit `-user` and let `ctxload` prompt you for your user name and password.

### 13.8 Example of Loading a Thesaurus with the CTX_THES.IMPORT_THESAURUS PL/SQL procedure

This example creates a case-sensitive thesaurus named `mythesaurus` and imports the thesaurus content in `myclob` into the Oracle Text thesaurus tables:

    declare
     myclob clob;
    begin
     myclob := to_clob('peking SYN beijing BT capital country NT beijing tokyo');
     ctx_thes.import_thesaurus(‘mythesaurus', myclob, ‘Y');
    end;

The format of the thesaurus to be imported (`myclob` in this example) should be the same as the format in the `ctxload` utility. If the format of the thesaurus to be imported is not correct, then `IMPORT_THESAURUS` raises an exception.

### 13.9 Compiling a Loaded Thesaurus

To link the loaded `medthes` thesaurus to the knowledge base, use `ctxkbtc` as follows:

    ctxkbtc -user ctxsys -name medthes

When you enter the `ctxkbtc` command line, you are prompted for the user password. As with `ctxload,` for best security practices, do not enter the password at the command line.

**WARNING:**

To ensure sound security practices, Oracle recommends that you enter the password for `ctxload` and `ctxkbtc` in the interactive mode. This mode prompts you for the user password. Oracle strongly recommends that you do not enter a password on the command line.

### 13.10 About the Supplied Knowledge Base

Oracle Text supplies a knowledge base for English and French. The supplied knowledge contains the information used to perform theme analysis. Theme analysis includes theme indexing, `ABOUT` queries, and theme extraction with the `CTX_DOC` package.

The knowledge base is a hierarchical tree of concepts and categories. It has six main branches:

- Science and technology

- Business and economics

- Government and military

- Social environment

- Geography

- Abstract ideas and concepts

The supplied knowledge base is like a thesaurus in that it is hierarchical and contains broader terms, narrower terms, and related terms. As such, to improve the accuracy of theme analysis, augment the knowledge base with your industry-specific thesaurus by linking new terms to existing terms.

**See Also:**

"Augmenting Knowledge Base with Custom Thesaurus"

You can also extend theme functionality to other languages by compiling a language-specific thesaurus into a knowledge base.

**See Also:**

"Adding a Language-Specific Knowledge Base"

Knowledge bases can be in any single-byte character set. Supplied knowledge bases are in WE8ISO8859P1. You can store an extended knowledge base in another character set such as US7ASCII.

This section contains the following topics:

- Adding a Language-Specific Knowledge Base

- Limitations for Adding Knowledge Bases

#### 13.10.1 Adding a Language-Specific Knowledge Base

You can extend theme functionality to languages other than English or French by loading your own knowledge base for any single-byte whitespace-delimited language, including Spanish.

You can extend theme functionality to languages other than English or French by loading your own knowledge base for any single-byte whitespace-delimited language, including Spanish.

Theme functionality includes theme indexing, `ABOUT` queries, theme highlighting, and the generation of themes, gists, and theme summaries with `CTX_DOC.`

You extend theme functionality by adding a user-defined knowledge base. For example, you can create a Spanish knowledge base from a Spanish thesaurus.

To load your language-specific knowledge base:

1.  Load your custom thesaurus by using `ctxload.`
2.  Set `NLS_LANG` so that the language portion is the target language. The charset portion must be a single-byte character set.
3.  Compile the loaded thesaurus by using `ctxkbtc` and then enter the password for -user when you are prompted. This statement compiles your language-specific knowledge base from the loaded thesaurus.
        ctxkbtc -user ctxsys -name my_lang_thes

To use this knowledge base for theme analysis during indexing and `ABOUT` queries, specify the `NLS_LANG` language as the `THEME_LANGUAGE` attribute value for the `BASIC_LEXER` preference.

**See Also:**

- "Example of Loading a Thesaurus with ctxload"

- "Compiling a Loaded Thesaurus"

#### 13.10.2 Limitations for Adding Knowledge Bases

Here are the limitations for adding knowledge bases:

- Oracle supplies knowledge bases only in English and French. You must provide your own thesaurus for any other language.

- You can add knowledge bases only for languages with single-byte character sets. You cannot create a knowledge base for languages that can be expressed only in multibyte character sets. If the database is a multibyte universal character set, such as UTF-8, you must still set the `NLS_LANG` parameter to a compatible single-byte character set when you compile the thesaurus.

- Adding a knowledge base works best for whitespace-delimited languages.

- Only one knowledge base is allowed for each `NLS_LANG` language.

- Obtaining hierarchical query feedback information (for example, broader terms, narrower terms, and related terms) does not work in languages other than English and French. In other languages, the knowledge bases are derived entirely from your thesauruses. In such cases, Oracle recommends that you obtain hierarchical information directly from your thesauruses.

  **See Also:**

  [Oracle Text Reference](../ccref/oracle-text-utilities.md) for more information about theme indexing, `ABOUT` queries, using the `CTX_DOC` package, and the supplied English knowledge base
