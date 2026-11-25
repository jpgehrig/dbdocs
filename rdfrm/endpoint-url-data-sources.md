## 13.1.2 Endpoint URL Data Sources

External RDF data sources are defined using an endpoint URL. In general, each RDF store has a generic URL that accepts SPARQL queries and SPARQL updates. Depending on the RDF store service, it may also provide some capabilities request to retrieve available datasets.

Table 13-1 External Data source Parameters

| Parameters  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|:------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| name        | A generic name of the data source.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| type        | The type of the data source. For external data sources, the type must be ‘ENDPOINT’.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| description | A generic description of the data source.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| properties  | Specific mapping parameters with values for data source properties:<br>• base URL: the base URL to issue SPARQL queries to RDF store. This is the default URL.<br>• query URL (optional): the URL to execute SPARQL queries. If defined, it will overwrite the base URL value.<br>• update URL (optional): the URL to execute SPARQL updates. If defined, it will overwrite the base URL value.<br>• capabilities (optional): Some RDF stores (like Apache Jena Fuseki) may provide a capabilities URL that returns the datasets available in service. A JSON response is expected in this case.<br>• get URL: the get capabilities URL.<br>• datasets parameter: defines the JSON parameter that contains the RDF datasets information.<br>• dataset parameter name: defines the JSON parameter that contains the RDF dataset name. |

The following example shows the JSON representation of a Dbpedia external data source :

    {
      "name": "dbpedia",
      "type": "ENDPOINT",
      "description": "Dbpedia RDF data - Dbpedia.org",
      "properties": {
          "baseUrl": "http://dbpedia.org/sparql",
          "provider": "Dbpedia"
       }
    }

The following example shows the JSON representation of a Apache Jena Fuseki external data source. The `${DATASET}` is a parameter that is replaced at run time with the Fuseki dataset name:

    {
        "name": "Fuseki",
        "type": "ENDPOINT",
        "description": "Jena Fuseki server",
        "properties": {
          "queryUrl": "http://localhost:8080/fuseki/${DATASET}/query",
          "baseUrl": "http://localhost:8080/fuseki",
          "capabilities": {
            "getUrl": "http://localhost:8080/fuseki/$/server",
            "datasetsParam": "datasets",
            "datasetNameParam": "ds.name"
          },
          "provider": "Apache",
          "updateUrl": "http://localhost:8080/fuseki/${DATASET}/update"
        }
    }

**Parent topic:** [Data Sources](data-sources.md)
