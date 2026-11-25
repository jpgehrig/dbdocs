## 10  CTX_ENTITY Package

The `CTX_ENTITY` PL/SQL package is used to locate and classify words and phrases into categories, such as persons or companies.

`CTX_ENTITY` contains the following stored procedures and functions.

| Name                  | Description                                                                   |
|:----------------------|:------------------------------------------------------------------------------|
| ADD_EXTRACT_RULE      | Adds a single extraction rule to an extraction policy.                        |
| ADD_STOP_ENTITY       | Marks certain entity mentions or entity types as not to be extracted.         |
| COMPILE               | Compiles added extraction rules into an extraction policy.                    |
| CREATE_EXTRACT_POLICY | Creates an extraction policy to use.                                          |
| DROP_EXTRACT_POLICY   | Drops an extraction policy.                                                   |
| EXTRACT               | Generates an XML document describing the entities found in an input document. |
| REMOVE_EXTRACT_RULE   | Removes a single extraction rule from an extraction policy.                   |
| REMOVE_STOP_ENTITY    | Removes a stop entity from an extraction policy.                              |

**Note:**

The APIs in the `CTX_ENTITY` package do not support identifiers that are prefixed with the schema or the owner name.

### 10.1 ADD_EXTRACT_RULE

The `ADD_EXTRACT_RULE` procedure adds a single extraction rule to extract policy. Invokers add rules into their own extraction policy.

Extraction rules have sentence-wide scopes. Extraction rules have to be case-sensitive except for entity types and rule operators in the rule expression. Order of rule addition is not important. Addition of a rule will not be effective until `CTX_ENTITY.COMPILE` is executed. This procedure issues a commit.

#### Syntax

    CTX_ENTITY.ADD_EXTRACT_RULE(
      policy_name                 IN VARCHAR2,
      rule_id                     IN INTEGER,
      extraction_rule             IN VARCHAR2);

policy_name
Specify the policy name.

rule_id
Specify a unique rule ID within an extraction policy. The rule ID must be greater than 0.

extraction_rule
The rule text in XML format specifies the language, expression, and entities to be extracted. The rule text follows the XML schema as follows:

    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">
    <xsd:element name="rule">
      <xsd:sequence>
        <xsd:element name="expression" type="xsd:string"/>
        <xsd:complexType>
          <xsd:attribute name="refid" type="xsd:positiveInteger"/>
        </xsd:complexType>
        <xsd:element name="comments type="xsd:string" default="\0"/>
      </xsd:sequence>
      </xsd:attribute name="language" type="xsd:string" default="ALL"/>
    </xsd:element>
    </xsd:schema>

Where:

- The language attribute of the rule tag specifies the applied language for the rule. The rule will only be applied to documents that are of the specified languages. The language attribute can be left out, or set to "ALL" if the rule is to match on all documents.

- The expression tag contains the posix regular expression that will be used in the matching.

- The comments tag allows users to associate any comments with this user rule.

- The type tag assigns the extracted entity text to a given entity type. The `refid` attribute of the type tag specifies which backreference in the regular expression corresponds to the actual entity. The entity type can be one of the Oracle supplied types, listed in Table 10-1, or it can be a user-defined type, which must be prefixed with the letter "x".

Table 10-1 Supplied Entity Types

| Supplied Entity Type | Explanation                           | Example                                        |
|:---------------------|:--------------------------------------|:-----------------------------------------------|
| `building`           | Name of a building                    | Gallery House                                  |
| `city`               | Name of a city                        | New York                                       |
| `company`            | Name of a company                     | Oracle Corporation                             |
| `country`            | Name of a country                     | United States                                  |
| `currency`           | Currency                              | Dollar                                         |
| `date`               | Date                                  | July 4                                         |
| `day`                | Day                                   | Monday, Tuesday                                |
| `email_address`      | Email address                         | person@example.com                             |
| `geo_political`      | A political or strategic organization | United Nations                                 |
| `holiday`            | Name of a country holiday             | Labor Day                                      |
| `location_other`     | Other types of locations              | Atlantic Ocean                                 |
| `month`              | Month                                 | June, July                                     |
| `non_profit`         | Non-profit organization               | Red Cross                                      |
| `organization_other` | Other types of organizations          | Supreme Court                                  |
| `percent`            | Expressed as number and %             | 10%                                            |
| `person_jobtitle`    | Person referred to by title           | President, Professor                           |
| `person_name`        | Person referred to by name            | John Doe                                       |
| `person_other`       | Other types of persons                | Other types of persons (for example, criminal) |
| `phone_number`       | Phone number                          | (123)-456-7890                                 |
| `postal_address`     | Postal address                        | Redwood Shores, CA                             |
| `product`            | Name of a product                     | Oracle Text                                    |
| `region`             | Name of a region                      | North America                                  |
| `ssn`                | Social Security Number                | 123-45-6789                                    |
| `state`              | A state or province                   | California                                     |
| `time_duration`      | A length of time                      | 10 seconds                                     |
| `tod`                | Time of day                           | 8:00 AM                                        |
| `url`                | Web address                           | www.example.com                                |
| `zip_code`           | Zip Code                              | CA 94065                                       |

#### Example 1

The following example shows how to define an extraction rule and associate it with an entity extraction policy. The following rule defines a simple extraction rule for finding email addresses in documents.

    begin
      ctx_entity.add_extract_rule('pol1', 1,
      '<rule>
        <expression>email is (\w+@\w+\.\w+)</expression>
        <type refid = "1">email_address</type>
       </rule>');
    end;
    /

Where:

- Given the sentence: "My email address is jdoe@example.com", this extraction rule will extract "jdoe@example.com" as an entity of type `email_address`.

- The rule is added to the extraction policy called `pol1`.

- The rule is added with rule ID of 1.

- This XML description of the rule is as follows:

  - The language attribute of the rule tag is left empty, so the rule will apply to all languages.

  - The expression tag contains the regular expression to use in the extraction.

  - The value of the type element and the `refid` attribute of the type tag specify that the first backreference corresponds to the text of the entity.

#### Example 2

The following rule defines a simple extraction rule for finding phone numbers in documents:

    begin
      ctx_entity.add_extract_rule('pol1', 2,
      '<rule language="english">
         <expression>(\(d{3}\) \d{3}-\d{3}-\d{4})</expression>
         <comments>Rule for phone numbers</comments>
         <type refid="1">email_address</type>
       </rule>';
    end;
    /

Where:

- Given the sentence: "I can be contacted at (123) 456-7890", this extraction rule will extract "(123) 456-7890" as an entity of type `phone_number`.

- The rule is added to the extraction policy called `pol1`.

- The rule is added with rule ID of 2.

- The XML description of the rule is as follows:

  - The language attribute of the rule tag is set to english, so the rule will only apply to English documents.

  - The expression tag contains the regular expression to use in the extraction.

  - The value of the type element and the `refid` attribute of the type tag specify that the first backreference corresponds to the text of the entity.

  - Explanatory comments are associated with this rule.

### 10.2 ADD_STOP_ENTITY

This procedure is used to mark certain entity mentions or entity types as not to be extracted. Invokers add stop entities to their own extraction policy. It does not take effect until after `CTX_ENTITY.COMPILE` is run. Either `entity_name` or `entity_type` can be `NULL`, but not both. If one stop entity is a subset of another, it will be marked as a subset after `CTX_ENTITY.COMPILE`, and not used in extraction. This procedure issues a commit.

#### Syntax

    CTX_ENTITY.ADD_STOP_ENTITY(
      policy_name                 IN VARCHAR2,
      entity_name                 IN INTEGER,
      entity_type                 IN VARCHAR2 DEFAULT NULL,
      comments                    IN VARCHAR2 DEFAULT NULL);

policy_name
Specify the policy name of the stop entity that is to be added.

entity_name
Specify the entity name to be listed as a stop entity. If `entity_type` is `NULL`, all mentions with this `entity_name` will be listed as stop entities. It is case-sensitive.

entity_type
If `entity_name` is `NULL`, this will specify an entire entity type to be listed as stop entity. If `entity_name` is not `NULL`, this will specify only the mention `<entity_type, entity_name>` as a stop entity. It is case-insensitive. The maximum byte length is 4000 bytes.

comments
The maximum byte length is 4000 bytes.

#### Example

The following example adds a stop entity corresponding to all persons. After compilation, extraction will not report any mentions of entity type `person`.

    exec ctx_entity.add_stop_entity('pol1', NULL, 'person');

The following example adds a stop entity corresponding to `<'person', 'john doe'>`. After compilation, extraction will not report any mentions of the pair `<'person', 'john doe'>`. This stop entity is actually a subset of the first stop entity added. It will be marked subset in the [`CTX_USER_EXTRACT_STOP_ENTITIES`](oracle-text-views.md) view, and will not be used in extraction.

    exec ctx_entity.add_stop_entity('pol1', 'john doe', 'person');

The following example adds a stop entity corresponding to all mentions of `ford`. After compilation, extraction will not report any mentions of the entity `ford`, irrespective of the entity type of the mention. For example, if a rule matches `ford` to a person, the extraction will not report this match. If a rule matches ford to a company, the extraction will again not report this match.

    exec ctx_entity.add_stop_entity('pol1', 'ford', NULL);

#### Related Topics

"COMPILE"

"[CTX_USER_EXTRACT_STOP_ENTITIES](oracle-text-views.md)"

### 10.3 COMPILE

This procedure compiles added extraction rules into an extraction policy. It can also be used to compile added stop entities into an extraction policy. Users have to invoke this procedure if they have added any rules or stop entities to their policy.

Invokers compile rules and stop entities into their own extraction policy. Users can choose to compile added rules, added stop entities, or both.

After compilation, the [`CTX_USER_EXTRACT_RULES`](oracle-text-views.md) and [`CTX_USER_EXTRACT_STOP_ENTITIES`](oracle-text-views.md) views will show which rules and stop entities are being used in the entity extraction.

#### Syntax

    CTX_ENTITY.COMPILE(
      policy_name                 IN VARCHAR2,
      compile_choice              IN NUMBER DEFAULT COMPILE_ALL,
      locking                     IN NUMBER DEFAULT LOCK_NOWAIT_ERROR);

policy_name
Specify the policy name that is to be compiled.

compile_choice
Specify the entity name to be listed as a stop entity. If `entity_type` is `NULL`, all mentions with this `entity_name` will be listed as stop entities. It is case-sensitive.

The options are `COMPILE_ALL`, `COMPILE_RULES`, and `COMPILE_STOP_ENTITIES`. `COMPILE_ALL` compiles both rules and stop entities. `COMPILE_RULES` compiles only rules. `COMPILE_STOP_ENTITIES` compiles only stop entities.

locking
The maximum byte length is 4000 bytes. Configure how `COMPILE` deals with the situation where another `COMPILE` is already running on the same policy.

The options for locking are:

- `CTX_ENTITY.LOCK_WAIT`

  If another compile is running, wait until the running compile is complete, then begin compile. (In the event of not being able to get a lock, it will wait forever and ignore the maxtime setting.).

- `CTX_ENTITY.LOCK_NOWAIT`

  If another compile is running, immediately returns without error.

- `CTX_ENTITY.LOCK_NOWAIT_ERROR`

  If another sync is running, error "DRG-51313: timeout while waiting for DML or optimize lock" is raised.

#### Example

The following example compiles the policy using the default setting:

    exec ctx_entity.compile('pol1');

The following example compiles only the stop entities for the policy:

    exec ctx_entity.compile('pol1', CTX_ENTITY.COMPILE_STOP_ENTITIES);

The following example compiles both rules and stop entities. If a lock exists, the function returns immediately, but does not raise an error.

    exec ctx_entity.compile('pol1', CTX_ENTITY.COMPILE_ALL,
                                    CTX_ENTITY.LOCK_NOWAIT);

#### Related Topics

"[CTX_USER_EXTRACT_RULES](oracle-text-views.md)"

"[CTX_USER_EXTRACT_STOP_ENTITIES](oracle-text-views.md)"

### 10.4 CREATE_EXTRACT_POLICY

The `CREATE_EXTRACT_POLICY` procedure creates an extraction policy to use. This policy can only be used by the policy owner.

#### Syntax

    CTX_ENTITY.CREATE_EXTRACT_POLICY(
      policy_name                   IN VARCHAR2,
      lexer                         IN VARCHAR2 DEFAULT NULL,
      include_supplied_rules        IN BOOLEAN DEFAULT TRUE,
      include_supplied_dictionary   IN BOOLEAN DEFAULT TRUE
    );

policy_name
Specify the name of the new extraction policy.

lexer
Specify the name of the lexer preference. Only [AUTO_LEXER](oracle-text-indexing-elements.md) is supported. If not specified, [`CTXSYS.DEFAULT_EXTRACT_LEXER`](oracle-text-indexing-elements.md) will be used. The attributes `index_stems` and `deriv_stems` are not allowed.

include_supplied_rules
Specify whether Oracle-supplied rules are included in entity extraction. If false, automatic acronym resolution will be turned off. The default is `true`.

include_supplied_dictionary
Specify whether the Oracle-supplied dictionary is included in entity extraction. The default is `true`.

#### Examples

The following example creates an extraction policy using the default settings. By default, the Oracle-supplied features, such as rules and dictionary, are enabled.

    exec CTX_ENTITY.CREATE_EXTRACT_POLICY('pol1');

The following example creates an extraction policy that explicitly specifies certain parameters. It specifies the lexer to be used as `mylex`, which must be an [AUTO_LEXER](oracle-text-indexing-elements.md) preference. It also includes the Oracle-supplied rules, but disables the Oracle-supplied dictionary.

    exec CTX_ENTITY.CREATE_EXTRACT_POLICY('pol2', 'mylex', TRUE, FALSE);

#### Related Topics

"[AUTO_LEXER](oracle-text-indexing-elements.md)"

"[CTXSYS.DEFAULT_EXTRACT_LEXER](oracle-text-indexing-elements.md)"

### 10.5 DROP_EXTRACT_POLICY

The `DROP_EXTRACT_POLICY` procedure drops an extraction policy. These policies can only be dropped by the policy owner. This procedure issues a commit.

#### Syntax

    CTX_ENTITY.DROP_EXTRACT_POLICY(
      policy_name                 IN VARCHAR2
    );

policy_name
Specify the name of the extraction policy to be dropped.

#### Example

The following example drops the extraction policy `pol2`:

    exec ctx_entity.drop_extract_policy('pol2');

### 10.6 EXTRACT

The `EXTRACT` procedure runs entity extraction on a given document and generates an XML document describing the entities found in the document.

The XML document will give the entity text, type, and location of the entity in the document. The extraction will use the settings (rules, stop entities, and dictionary) defined in the given extraction policy.

Entity type names in the result will be uppercased. Invokers can run extraction using their own extraction policy.

Before execution, you have to issue `CTX_ENTITY.COMPILE`.

#### Syntax

    CTX_ENTITY.EXTRACT(
      policy_name                 IN VARCHAR2,
      document                    IN CLOB,
      language                    IN VARCHAR2,
      result                      IN OUT NOCOPY CLOB,
      entity_type_list            IN CLOB DEFAULT NULL
    );

policy_name
Run extraction using the given policy.

document
The input document to run extraction on.

If `entity_type` is `NULL`, all mentions with this `entity_name` will be listed as stop entities. It is case-sensitive.

language
Only English is supported.

result
A `CLOB` containing the XML description of the entities extracted from the document.

If `entity_type` is `NULL`, all mentions with this `entity_name` will be listed as stop entities. It is case-sensitive.

entity_type_list
Specify that extraction will only consider a subset of entity types. The `entity_type_list` is a comma-delimited list. If the `entity_type_list` is not specified, the entity extraction will consider all entity types.

#### Example

The following example shows the results of entity extraction on an example document. Suppose that we have created an extraction policy called `pol1`, and we are given the input document:

    Sam A. Schwartz retired as executive vice president of Org Inc. in New York.

We then call the `ctx_entity.extract` procedure to generate an XML document containing the entities in this document. We insert the results `CLOB` into a table called `entities` for future viewing.

    declare
      myresults clob;
    begin
      select txt into mydoc from docs where id=1;
      ctx_entity.extract('p1', mydoc, null, myresults);
      insert into entities values(1, myresults);
      commit;
      end;
    /

Then we can examine the extracted entities from the `entities` table. Note that each entity is tagged with its location in the input document, as well as the source used to classify the entity.

    <entities>
    <entity id="0" offset="75" length="8" source="SuppliedDictionary">
    <text>New York</text>
    <type>city</type>
    </entity>
    <entity id="1" offset="55" length="16" source="SuppliedRule">
    <text>Org Inc.</text>
    <type>company</type>
    </entity>
    <entity id="2" offset="27" length="24" source="SuppliedDictionary">
    <text>Sam A. Schwartz</text>
    <type>person_name</type>
    </entity>
    <entity id="4" offset="75" length="8" source="SuppliedDictionary">
    <text>New York</text>
    <type>state</type>
    </entity>
    </entities>

### 10.7 REMOVE_EXTRACT_RULE

The `REMOVE_EXTRACT_RULE` procedure removes an extraction rule from the specified policy given a `rule_id`. Only the owner of the specified policy can remove an extraction rule from the policy. Removal of the extraction rule will be in effect after running `CTX_ENTITY.COMPILE`.

#### Syntax

    CTX_ENTITY.REMOVE_EXTRACT_RULE(
      policy_name                 IN VARCHAR2,
      rule_id                     IN INTEGER
    );

policy_name
Remove the extraction rule from the specified policy.

rule_id
Specify the rule ID of the extraction rule to be removed.

#### Example

The following example removes the extraction rule with ID 1 from the policy `pol1`:

    exec ctx_entity.remove_extract_rule('pol1', 1);

### 10.8 REMOVE_STOP_ENTITY

The `REMOVE_STOP_ENTITY` procedure removes a stop entity from an extraction policy. Only the owner of the specified policy can remove a stop entity from the policy. Removal of the stop entity will be in effect after running `CTX_ENTITY.COMPILE`. Either the `entity_name` or `entity_type` can be null, but not both.

#### Syntax

    CTX_ENTITY.REMOVE_STOP_ENTITY(
      policy_name                 IN VARCHAR2,
      entity_name                 IN INTEGER DEFAULT NULL,
      entity_type                 IN VARCHAR2 DEFAULT NULL
    );

policy_name
Remove the `stop_entity` from the specified policy.

entity_name
Specify the name to be removed from the stop entity list. The `stop_entity` must have already been added to the `stop_entity` list using `CTX_ENTITY.ADD_STOP_ENTITY`.

entity_type
Specify the type of entity to be removed from the stop entity list. The `stop_entity` must have already been added to the stop entity list using `CTX_ENTITY.ADD_STOP_ENTITY`.

#### Example

    exec ctx_entity.remove_stop_entity('pol1', NULL, 'person_name');

The example statement removes the stop entity corresponding to all mentions of the `entity_type` `person_name` from the policy `pol1`. After execution, this stop entity will be marked as "to be deleted" in the [`CTX_USER_EXTRACT_STOP_ENTITIES`](oracle-text-views.md) view. The removal of the stop entity will take effect once the user runs `CTX_ENTITY.COMPILE`.

#### Related Topics

"COMPILE"

"ADD_STOP_ENTITY"

"[CTX_USER_EXTRACT_STOP_ENTITIES](oracle-text-views.md)"
