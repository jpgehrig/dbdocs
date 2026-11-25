## Part I  Conceptual and Usage Information

Part I provides conceptual and usage information about RDF Semantic Graph.

This part contains the following chapters:

- [RDF Knowledge Graph Overview](rdf-semantic-graph-overview.md)
  Oracle Spatial and Graph support for semantic technologies consists mainly of Resource Description Framework (RDF) and a subset of the Web Ontology Language (OWL). These capabilities are referred to as the RDF Knowledge Graph feature of Oracle Spatial and Graph.
- [Quick Start for Using Semantic Data](quick-start-using-rdf-data.md)
  This section provides the steps to help you get started on working with semantic data in an Oracle Database.
- [OWL Concepts](owl-concepts.md)
  You should understand key concepts related to the support for a subset of the Web Ontology Language (OWL).
- [Simple Knowledge Organization System (SKOS) Support](simple-knowledge-organizaiton-system-skos.md)
  You can perform inferencing based on a core subset of the Simple Knowledge Organization System (SKOS) data model, which is especially useful for representing thesauri, classification schemes, taxonomies, and other types of controlled vocabulary.
- [Semantic Indexing for Documents](semantic-indexing-documents.md)
  Information extractors locate and extract meaningful information from unstructured documents. The ability to search for documents based on this extracted information is a significant improvement over the keyword-based searches supported by the full-text search engines.
- [Fine-Grained Access Control for RDF Data](fine-grained-access-control-rdf.md)
  The default control of access to the Oracle Database semantic data store is at the model level: the owner of a model can grant select, delete, and insert privileges on the model to other users by granting appropriate privileges on the view named RDFM\_\<model_name\>. However, for applications with stringent security requirements, you can enforce a fine-grained access control mechanism by using the Oracle Label Security option of Oracle Database.
- [RDF Semantic Graph Support for Apache Jena](rdf-support-for-apache-jena.md)
  RDF Semantic Graph support for Apache Jena (also referred to here as support for Apache Jena) provides a Java-based interface to Oracle Spatial and Graph RDF Semantic Graph by implementing the well-known Jena Graph, Model, and DatasetGraph APIs.
- [RDF Semantic Graph Support for Eclipse RDF4J](rdf-graph-support-eclipse-rdf4j.md)
  Oracle RDF Graph Adapter for Eclipse RDF4J utilizes the popular Eclipse RDF4J framework to provide Java developers support to use the RDF semantic graph feature of Oracle Database.
- [User-Defined Inferencing and Querying](user-defined-inferencing.md)
  RDF Semantic Graph extension architectures enable the addition of user-defined capabilities.
- [RDF Views: Relational Data as RDF](rdf-views.md)
  You can create and use RDF views over relational data in RDF Semantic Graph.
- [RDF Integration with Property Graph Data Stored in Oracle Database](rdf-integration-property-graph-data.md)
  The property graph data model is supported in Oracle Spatial and Graph. Oracle Spatial and Graph provides built-in support for RDF views of property graph data stored in Oracle Database.
