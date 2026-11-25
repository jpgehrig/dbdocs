## 14.3.3 Configuration Files for RDF Server and Client

The Graph Query UI application settings are determined by the JSON files that are included in the RDF Server and Client installation.

- `datasource.json`: File with RDF data source definitions.
- `general.json`: General configuration parameters.
- `proxy.json`: Proxy server parameters.
- `logging.json`: Logging settings.
- `seed.json`: Master seed key value generated at first deployment of the application. This is a unique value to be used for encrypting and decrypting passwords for Oracle data sources defined with credentials. This is an important file, and losing it will not allow you to encrypt or to decrypt passwords values.

On the server side, the directory `WEB-INF/workspace` is the default directory to store configuration information, logs, and temporary files. The configuration files are stored by default in `WEB-INF/workspace/config`.

**Note:**

If the RDF Graph Query application is deployed from an unexploded `.war` file, and if no JVM parameter is defined for the workspace folder location, then the default workspace location for the application is `WEB-INF/workspace`. However, any updates to the configuration, log, and temp files done by the application may be lost if the application is redeployed. Also, wallet data source files and published dataset files can be lost.

To overcome this, you must start the application server, such as Weblogic or Tomcat, with the JVM parameter `oracle.rdf.workspace.dir` set. For example: `=Doracle.rdf.workspace.dir=/rdf/server/workspace`. The workspace folder must exist on the file system. Otherwise, the workspace folder defaults to `WEB-INF/workspace`.

It is recommended to have a backup of the workspace folder, in case of redeploying the application on a different location. Copying the workspace folder contents to the location of the JVM parameter, allows to restore all configurations in new deployment.

- [Data Sources JSON Configuration File](data-sources-json-configuration-file.md)
- [General JSON configuration file](general-json-configuration-file.md)
- [Proxy JSON Configuration File](proxy-json-configuration-file.md)
- [Logging JSON Configuration File](logging-json-configuration-file.md)

**Parent topic:** [Getting Started with RDF Graph Query UI](gettting-started-rdf-graph-query-ui.md)
