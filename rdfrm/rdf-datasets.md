## 13.2 RDF Datasets

Each RDF data source contains metadata information that describe the avaliable RDF objects.

The following describes the metadata information defined by each provider.

- Oracle RDF data sources: The RDF metadata includes information about the following RDF objects: private networks, models (real, virtual, view), rulebases, entailments, network indexes and datatypes.

- External RDF providers: For Apache Jena Fuseki, the metadata includes dataset names. Other external providers may not have a metadata concept, in which case the base URL points to generic (default) metadata.

RDF datasets point to one or more RDF objects available in the RDF data source. A dataset definition is used in SPARQL query requests. Each provider has its own set of properties to describe the RDF dataset.

The following are a few examples of a JSON representation of a dataset.

Oracle RDF dataset definition:

    [
       {
         "networkOwner": "RDFUSER",
         "networkName": "MYNET",
         "models": ["M1"]
       }
    ]

Apache RDF Jena Fuseki dataset definition:

    [
       {
         "name": "dataset1"
       }
    ]

For RDF stores that do not have a specific dataset, a simple JSON {} or a 'Default' name as shown for Apache Jena Fuseki in the above example can be used.

**Parent topic:** [RDF Graph Server and Query UI Concepts](rdf-graph-server-and-query-ui-concepts.md)
