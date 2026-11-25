## 14.3.3.1 Data Sources JSON Configuration File

The JSON file for data sources stores the general attributes of a data source, including specific properties associated with data source.

The following example shows a data source JSON file with two data sources: one an Oracle container data source defined on the application server, and the other an external data source.

    {
      "datasources" : [
       {
        "name" : "rdfuser193c",
        "type" : "DATABASE",
        "description" : "19.3 Oracle database",
        "properties" : {
          "jndiName" : "jdbc/RDFUSER193c"
        }
       },
       {
         "name" : "dbpedia",
         "type" : "ENDPOINT",
         "description" : "Dbpedia RDF data - Dbpedia.org",
          "properties" : {
             "baseUrl" : "http://dbpedia.org/sparql",
             "provider" : "Dbpedia"
           }
        }
      ]
    }

**Parent topic:** [Configuration Files for RDF Server and Client](configuration-files-rdf-server-and-client.md)
