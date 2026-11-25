## Glossary

The following are selected terms relevant to the Oracle Database implementation of RDF Semantic Graph support. This is not a comprehensive RDF and OWL glossary.

### apply pattern

Part of a data access constraint defines additional graph patterns to be applied on the resources that match the match pattern before they can be used to construct the query results. See also: match pattern

**Parent topic:** Glossary

### basic graph pattern (BGP)

A set of triple patterns. From the W3C SPARQL Query Language for RDF Recommendation: "SPARQL graph pattern matching is defined in terms of combining the results from matching basic graph patterns. A sequence of triple patterns interrupted by a filter comprises a single basic graph pattern. Any graph pattern terminates a basic graph pattern."

**Parent topic:** Glossary

### clique

A graph in which every node of it is connected to, bidirectionally, every other node in the same graph.

**Parent topic:** Glossary

### Cytoscape

An open source bioinformatics software platform for visualizing molecular interaction networks and integrating these interactions with gene expression profiles and other state data. (See [`http://www.cytoscape.org/`](http://www.cytoscape.org/).) An RDF viewer (available for download) is provided as a Cytoscape plug-in.

**Parent topic:** Glossary

### entailment

An object containing precomputed triples that can be inferred from applying a specified set of rulebases to a specified set of models. See also: rulebase

**Parent topic:** Glossary

### extractor policy

A named dictionary entity that determines the characteristics of a semantic index that is created using the policy. Each extractor policy refers, directly or indirectly, to an instance of an extractor type.

**Parent topic:** Glossary

### graph pattern

A combination of triples constructed by combining triple patterns in various ways, including conjunction of triple patterns into groups, optionally using filter conditions, and then combining such groups using connectors similar to disjunctions, outer-joins, and so on. SPARQL querying is based around graph pattern matching.

**Parent topic:** Glossary

### inferencing

The ability to make logical deductions based on rules. Inferencing enables you to construct queries that perform semantic matching based on meaningful relationships among pieces of data, as opposed to just syntactic matching based on string or other values. Inferencing involves the use of rules, either supplied by Oracle or user-defined, placed in rulebases.

**Parent topic:** Glossary

### information extractor

An application that processes unstructured documents and extract meaningful information from them, often using natural-language processing engines with the aid of ontologies.

**Parent topic:** Glossary

### match pattern

Part of a constraint that determines the type of access restriction it enforces and binds one or more variables to the corresponding data instances accessed in the user query. See also: apply pattern

**Parent topic:** Glossary

### model

A user-created semantic structure that has a model name, and refers to triples stored in a specified table column. Examples in this manual are the Articles and Family models.

**Parent topic:** Glossary

### ontology

A shared conceptualization of knowledge in a particular domain. It consists of a collection of classes, properties, and optionally instances. Classes are typically related by class hierarchy (subclass/ superclass relationship). Similarly, the properties can be related by property hierarchy (subproperty/ superproperty relationship). Properties can be symmetric or transitive, or both. Properties can also have domain, ranges, and cardinality constraints specified for them.

**Parent topic:** Glossary

### OWLPrime

An Oracle-defined subset of OWL capabilities; refers to the elements of the OWL standard supported by the RDF Semantic Graph native inferencing engine.

**Parent topic:** Glossary

### RDF Semantic Graph support for Apache Jena

An Oracle-supplied adapter (available for download) for Apache Jena, which is a Java framework for building Semantic Web applications.

**Parent topic:** Glossary

### reasoning

See inferencing

**Parent topic:** Glossary

### rule

An object that can be applied to draw inferences from semantic data.

**Parent topic:** Glossary

### rulebase

An object that can contain rules. See also: rule

**Parent topic:** Glossary

### rules index

See: entailment

**Parent topic:** Glossary

### semantic index

An index of type MDSYS.SEMCONTEXT, created on textual documents stored in a column of a table, and used with information extractors to locate and extract meaningful information from unstructured documents. See also: information extractor

**Parent topic:** Glossary

### Simple Knowledge Organization System (SKOS)

A data model that is especially useful for representing thesauri, classification schemes, taxonomies, and other types of controlled vocabulary. SKOS is based on standard semantic web technologies including RDF and OWL, which makes it easy to define the formal semantics for those knowledge organization systems and to share the semantics across applications.

**Parent topic:** Glossary

### triple pattern

Similar to an RDF triple, but allows use of a variable in place of any of the three components (subject, predicate, or object). Triple patterns are basic elements in graph patterns used in SPARQL queries. A triple pattern used in a query against an RDF graph is said to match if, substitution of RDF terms for the variables present in the triple pattern, creates a triple that is present in the RDF graph. See also: graph pattern

**Parent topic:** Glossary
