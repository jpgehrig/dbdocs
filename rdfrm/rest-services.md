## 13.3 REST Services

An RDF REST API allows communication between client and backend RDF data stores.

The REST services can be divided into the following groups:

- Server generic services: allows access to available data sources, and configuration settings for general, proxy, and logging parameters.

- Oracle RDF services: allows CRUD operations on Oracle RDF objects.

- SPARQL services: allows execution of SPARQL queries and updates on the data sources.

Assuming the deployment of RDF web application with context-root set to `orardf`, on `localhost` machine and port number `7101`, the base URL for REST requests is ` http://localhost:7101/orardf/api/v1`.

Most of the REST services are protected with Form-based authentication. Administrator users can define a public RDF data source using the RDF Graph Server and Query UI web application. The public REST endpoints will then be available to perform SPARQL queries on published datasets.

**Note:**

The examples in this section and throughout this chapter reference host machine as `localhost` and port number as `7101`. These values can vary depending on your application deployment.

The following are some RDF REST examples:

- Get the server information:

  The following is a public endpoint URL. It can be used to test if the server is up and running.

  `http://localhost:7101/orardf/api/v1/utils/version`

- Get a list of data sources:

  `http://localhost:7101/orardf/api/v1/datasources`

- Get general configuration parameters:

  `http://localhost:7101/orardf/api/v1/configurations/general`

- Get a list of RDF semantic networks for Oracle RDF:

  `http://localhost:7101/orardf/api/v1/networks?datasource=rdfuser_ds_193c`

- Get a list of all Oracle RDF models for MDSYS network:

  `http://localhost:7101/orardf/api/v1/models?datasource=rdfuser_ds_193c`

- Get a list of all Oracle RDF real models for a private semantic network (applies from 19c databases):

  `http://localhost:7101/orardf/api/v1/models?datasource=rdfuser_ds_193c&networkOwner=RDFUSER&networkName=LOCALNET&type=real`

- Post request for SPARQL query:

  `http://localhost:7101/orardf/api/v1/datasets/query?datasource=rdfuser_ds_193c&datasetDef={"metadata":[ {"networkOwner":"RDFUSER", "networkName":"LOCALNET","models":["UNIV_BENCH"]} ] }`

  Query Payload: `select ?s ?p ?o where { ?s ?p ?o} limit 10`

- Get request for SPARQL query:

  `http://localhost:7101/orardf/api/v1/datasets/query?datasource=rdfuser_ds_193c&query=select ?s ?p ?o where { ?s ?p ?o} limit 10&datasetDef={"metadata":[ {"networkOwner":"RDFUSER", "networkName":"LOCALNET","models":["UNIV_BENCH"]} ] }`

- Put request to publish an RDF model:

  `http://localhost:7101/orardf/api/v1/datasets/publish/DSETNAME?datasetDef={"metadata":[ {"networkOwner":"RDFUSER", "networkName":"LOCALNET" "models":["UNIV_BENCH"]} ]}`

  Default SPARQL Query Payload: `select ?s ?p ?o where { ?s ?p ?o} limit 10`

  This default SPARQL can be overwritten when requesting the contents of a published dataset. The `datasource` parameter in the preceding request is optional. However, if you define this parameter on the URL, it must match the current publishing data source name because this API version supports just one publishing data source. Otherwise, the published data source name is automatically used.

- Get request for a published dataset:

  The following is a public endpoint URL. It is using the default parameters (SPARQL query, output format, and others) that are stored in dataset definition. However, these default parameters can be overwritten in REST request by passing new parameter values.

  `http://localhost:7101/orardf/api/v1/datasets/query/published/DSETNAME`

A detailed list of available REST services can be found in the Swagger json file, `orardf_swagger.json`, which is packaged in the application documentation directory.

**Parent topic:** [RDF Graph Server and Query UI Concepts](rdf-graph-server-and-query-ui-concepts.md)
