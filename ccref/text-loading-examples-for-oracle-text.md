## C  Text Loading Examples for Oracle Text

This appendix provides examples of how to load text into a text column, and the structure of `ctxload` import files. This appendix contains these topics:

- SQL INSERT Example

- SQL\*Loader Example

- Structure of ctxload Thesaurus Import File

### C.1 SQL INSERT Example

A simple way to populate a text table is to create a table with two columns, `id` and `text`, using `CREATE` `TABLE` and then use the `INSERT` statement to load the data. This example makes the `id` column the primary key, which is optional. The `text` column is `VARCHAR2`:

    create table docs (id number primary key, text varchar2(80));

To populate the `text` column, use the `INSERT` statement as follows:

    insert into docs values(1, 'this is the text of the first document');
    insert into docs values(12, 'this is the text of the second document');

### C.2 SQL\*Loader Example

The following example shows how to use SQL\*Loader to load mixed format documents from the operating system to a `BLOB` column. The example has two steps:

- Creating the Table

- Issuing the SQL\*Loader Command

  The SQL\*Loader command reads the control file and loads data into table

**See Also:**

For a complete discussion on using SQL\*Loader, see [Oracle Database Utilities](../sutil/oracle-sql-loader-concepts.md)

#### C.2.1 Creating the Table

This example loads a table `articles_formatted` created as follows:

    CREATE TABLE articles_formatted (
      ARTICLE_ID   NUMBER PRIMARY KEY ,
      AUTHOR       VARCHAR2(30),
      FORMAT       VARCHAR2(30),
      PUB_DATE     DATE,
      TITLE        VARCHAR2(256),
      TEXT         BLOB
    );

The `article_id` column is the primary key. Documents are loaded in the `text` column, which is of type `BLOB`.

#### C.2.2 Issuing the SQL\*Loader Command

The following command starts the loader, which reads the control file `LOADER1.DAT`:

    sqlldr userid=demo/password control=loader1.dat log=loader.log

- Example Control File: loader1.dat

- Example Data File: loader2.dat

##### C.2.2.1 Example Control File: `loader1.dat`

This SQL\*Loader control file defines the columns to be loaded and instructs the loader to load the data line by line from `loader2.dat` into the `articles_formatted` table. Each line in `loader2.dat` holds a comma-delimited list of fields to be loaded.

    -- load file example
    load data
    INFILE 'loader2.dat'
    INTO TABLE articles_formatted
    APPEND
    FIELDS TERMINATED BY ','
    (article_id SEQUENCE (MAX,1),
     author CHAR(30),
     format,
     pub_date SYSDATE,
     title,
     ext_fname FILLER CHAR(80),
     text LOBFILE(ext_fname) TERMINATED BY EOF)

This control file instructs the loader to load data from `loader2.dat` to the `articles_formatted` table in the following way:

1.  The ordinal position of the line describing the document fields in `loader2.dat` is written to the `article_id` column.

2.  The first field on the line is written to `author` column.

3.  The second field on the line is written to the `format` column.

4.  The current date given by `SYSDATE` is written to the `pub_date` column.

5.  The title of the document, which is the third field on the line, is written to the `title` column.

6.  The name of each document to be loaded is read into the `ext_fname`temporary variable, and the actual document is loaded in the `text` BLOB column:

##### C.2.2.2 Example Data File: `loader2.dat`

This file contains the data to be loaded into each row of the table, `articles_formatted`.

Each line contains a comma-delimited list of the fields to be loaded in `articles_formatted`. The last field of every line names the file to be loaded in to the text column:

    Ben Kanobi, plaintext,Kawasaki news article,../sample_docs/kawasaki.txt,
    Joe Bloggs, plaintext,Java plug-in,../sample_docs/javaplugin.txt,
    John Hancock, plaintext,Declaration of Independence,../sample_docs/indep.txt,
    M. S. Developer, Word7,Newsletter example,../sample_docs/newsletter.doc,
    M. S. Developer, Word7,Resume example,../sample_docs/resume.doc,
    X. L. Developer, Excel7,Common example,../sample_docs/common.xls,
    X. L. Developer, Excel7,Complex example,../sample_docs/solvsamp.xls,
    Pow R. Point, Powerpoint7,Generic presentation,../sample_docs/generic.ppt,
    Pow R. Point, Powerpoint7,Meeting presentation,../sample_docs/meeting.ppt,
    Java Man, PDF,Java Beans paper,../sample_docs/j_bean.pdf,
    Java Man, PDF,Java on the server paper,../sample_docs/j_svr.pdf,
    Ora Webmaster, HTML,Oracle home page,../sample_docs/oramnu97.html,
    Ora Webmaster, HTML,Oracle Company Overview,../sample_docs/oraoverview.html,
    John Constable, GIF,Laurence J. Ellison : portrait,../sample_docs/larry.gif,
    Alan Greenspan, GIF,Oracle revenues : Graph,../sample_docs/oragraph97.gif,
    Giorgio Armani, GIF,Oracle Revenues : Trend,../sample_docs/oratrend.gif,

### C.3 Structure of ctxload Thesaurus Import File

This section discusses the structure of the `ctxload` thesaurus import file in the following topics.

- Import File Format

- Alternate Hierarchy Structure

- Usage Notes for Terms in Import Files

- Usage Notes for Relationships in Import Files

- Examples of Import Files

#### C.3.1 Import File Format

The import file must use the following format for entries in the thesaurus:

    phrase
    BT broader_term
    NT narrower_term1
    NT narrower_term2
    . . .
     NT narrower_termN

     BTG broader_term
     NTG narrower_term1
     NTG narrower_term2
    . . .
     NTG narrower_termN

     BTP broader_term
     NTP narrower_term1
     NTP narrower_term2
    . . .
     NTP narrower_termN

     BTI broader_term
     NTI narrower_term1
     NTI narrower_term2
    . . .
     NTI narrower_termN

     SYN synonym1
     SYN synonym2
    . . .
     SYN synonymN

     USE synonym1  or  SEE synonym1 or  PT  synonym1

     RT related_term1
     RT related_term2
    . . .
     RT related_termN

     SN text

     language_key: term

phrase
is a word or phrase that is defined as having synonyms, broader terms, narrower terms, or related terms.

In compliance with ISO-2788 standards, a TT marker can be placed before a phrase to indicate that the phrase is the top term in a hierarchy; however, the TT marker is not required. In fact, ctxload ignores TT markers during import.

A top term is identified as any phrase that does not have a broader term (BT, BTG, BTP, or BTI).

**Note:**

The thesaurus query operators (`SYN`, `PT`, `BT`, `BTG`, `BTP`, `BTI`, `NT`, `NTG`, `NTP`, `NTI`, and `RT`) are reserved words and, thus, cannot be used as phrases in thesaurus entries.

BT, BTG, BTP, BTI broader_termN
are the markers that indicate `broader_termN` is a broader (generic\|partitive\|instance) term for `phrase`.

`broader_termN`is a word or phrase that conceptually provides a more general description or category for `phrase`. For example, the word elephant could have a broader term of land mammal.

NT, NTG, NTP, NTI narrower_termN
are the markers that indicate `narrower_termN` is a narrower (generic\|partitive\|instance) term for `phrase`.

If `phrase` does not have a broader (generic\|partitive\|instance) term, but has one or more narrower (generic\|partitive\|instance) terms, `phrase` is created as a top term in the respective hierarchy (in an Oracle Text thesaurus, the BT/NT, BTG/NTG, BTP/NTP, and BTI/NTI hierarchies are separate structures).

`narrower_termN` is a word or phrase that conceptually provides a more specific description for `phrase`. For example, the word elephant could have a narrower terms of indianelephant and african elephant.

SYN synonymN
is a marker that indicates `phrase` and `synonymN` are synonyms within a synonym ring.

`synonymN` is a word or phrase that has the same meaning for `phrase`. For example, the word dog could have a synonym of canine.

**Note:**

Synonym rings are not defined explicitly in Oracle Text thesauri. They are created by the transitive nature of synonyms.

USE SEE PT synonym1
are markers that indicate `phrase` and `synonym1` are synonyms within a synonym ring (similar to SYN).

The markers USE, SEE or PT also indicate `synonym1` is the preferred term for the synonym ring. Any of these markers can be used to define the preferred term for a synonym ring.

**Note:**

If the user-defined thesaurus is to be used for compiling the knowledge base, then you must specify the preferred term when a synonym ring is declared. Use one of the keywords USE, SEE, or PT to specify which synonym to use when reporting query matches. Only one term can be a preferred term.

Not using one of these keywords may result in the failure to return results defined by a word's synonym. When compiling two or more thesauri that declare elements of the same synonym ring, the preferred term must be the same in both files, which ensures that only one word is defined as the preferred word in a synonym ring.

RT related_termN
is the marker that indicates `related_termN` is a related term for `phrase`.

`related_termN` is a word or phrase that has a meaning related to, but not necessarily synonymous with `phrase`. For example, the word dog could have a related term of wolf.

**Note:**

Related terms are not transitive. If a phrase has two or more related terms, the terms are related only to the parent phrase and not to each other.

SN text
is the marker that indicates the following `text` is a scope note (for example, comment) for the preceding entry.

language_key term
`term` is the translation of phrase into the language specified by `language_key`.

#### C.3.2 Alternate Hierarchy Structure

In compliance with thesauri standards, the load file supports formatting hierarchies (BT/NT, BTG/NTG, BTP, NTP, BTI/NTI) by indenting the terms under the top term and using NT (or NTG, NTP, NTI) markers that include the level for the term:

    phrase
       NT1 narrower_term1
          NT2 narrower_term1.1
          NT2 narrower_term1.2
              NT3 narrower_term1.2.1
              NT3 narrower_term1.2.2
       NT1 narrower_term2
       . . .
       NT1 narrower_termN

Using this method, the entire branch for a top term can be represented hierarchically in the load file.

#### C.3.3 Usage Notes for Terms in Import Files

The following conditions apply to the structure of the entries in the import file:

- Each entry (`phrase`, `BT, NT`, or `SYN`) must be on a single line followed by a newline character.

- Entries can consist of a single word or phrases.

- The maximum length of an entry (`phrase, BT, NT,` or `SYN`) is 255 bytes, not including the `BT, NT,` and `SYN` markers or the newline characters.

- Entries cannot contain parentheses or plus signs.

- Each line of the file that starts with a relationship (`BT, NT`, and so on) must begin with at least one space.

- A `phrase` can occur more than once in the file.

- Each `phrase` can have one or more narrower term entries (`NT, NTG, NTP`), broader term entries (`BT, BTG, BTP`), synonym entries, and related term entries.

- Each broader term, narrower term, synonym, and preferred term entry must start with the appropriate marker and the markers must be in capital letters.

- The broader terms, narrower terms, and synonyms for a `phrase` can be in any order.

- Homographs must be followed by parenthetical disambiguators everywhere they are used.

  For example: `cranes (birds), cranes (lifting equipment)`

- Compound terms are signified by a plus sign between each factor (for example, buildings + construction).

- Compound terms are allowed only as synonyms or preferred terms for other terms, never as terms by themselves, or in hierarchical relations.

- Terms can be followed by a scope note (`SN`), total maximum length of 2000 bytes, on subsequent lines.

- Multi-line scope notes are allowed, but require an `SN` marker on each line of the note.

Example of Incorrect SN usage:

    VIEW CAMERAS
     SN Cameras with through-the lens focusing and a
    range of movements of the lens plane relative to
    the film plane

Example of Correct SN usage:

    VIEW CAMERAS
     SN Cameras with through-the lens focusing and a
     SN range of movements of the lens plane relative
     SN to the film plane

- Multi-word terms cannot start with reserved words (for example, use is a reserved word, so use other door is not an allowed term; however, use is an allowed term).

#### C.3.4 Usage Notes for Relationships in Import Files

The following conditions apply to the relationships defined for the entries in the import file:

- related term entries must follow a phrase or another related term entry

- related term entries start with one or more spaces, the `RT` marker, followed by white space, then the related term on the same line

- multiple related terms require multiple `RT` markers

  Example of incorrect `RT` usage:

      MOVING PICTURE CAMERAS
       RT CINE CAMERAS
      TELEVISION CAMERAS

  Example of correct `RT` usage:

      MOVING PICTURE CAMERAS
       RT CINE CAMERAS
       RT TELEVISION CAMERAS

- Terms are allowed to have multiple broader terms, narrower terms, and related terms

#### C.3.5 Examples of Import Files

This section provides three examples of correctly formatted thesaurus import files.

- Example 1 (Flat Structure)

- Example 2 (Hierarchical)

- Example 3

##### C.3.5.1 Example 1 (Flat Structure)

    cat
     SYN feline
     NT domestic cat
     NT wild cat
     BT mammal
    mammal
     BT animal
    domestic cat
     NT Persian cat
     NT Siamese cat
    wild cat
     NT tiger
    tiger
     NT Bengal tiger
    dog
     BT mammal
     NT domestic dog
     NT wild dog
     SYN canine
    domestic dog
     NT German Shepard
    wild dog
     NT Dingo

##### C.3.5.2 Example 2 (Hierarchical)

    animal
       NT1 mammal
            NT2 cat
                 NT3 domestic cat
                      NT4 Persian cat
                      NT4 Siamese cat
                 NT3 wild cat
                      NT4 tiger
                           NT5 Bengal tiger
            NT2 dog
                 NT3 domestic dog
                      NT4 German Shepard
                 NT3 wild dog
                      NT4 Dingo
    cat
     SYN feline
    dog
     SYN canine

##### C.3.5.3 Example 3

    35MM CAMERAS
     BT MINIATURE CAMERAS
    CAMERAS
     BT OPTICAL EQUIPMENT
     NT MOVING PICTURE CAMERAS
     NT STEREO CAMERAS
    LAND CAMERAS
     USE VIEW CAMERAS
    VIEW CAMERAS
     SN Cameras with through-the lens focusing and a range of
     SN movements of the lens plane relative to the film plane
     UF LAND CAMERAS
     BT STILL CAMERAS
