## 13.1.1 Oracle Data Sources

Oracle data sources are defined using JDBC connections. Three types of Oracle JDBC data sources can be defined:

- A JDBC URL data source with standard Oracle JDCB parameters, which include SID or service name, host, port, and user credentials.
- A container JDBC data source that can be defined inside the application Server (WebLogic, Tomcat, or others).
- An Oracle wallet data source that contains the files needed to make the database connection.

The parameters that define an Oracle database data source include:

- name: A generic name of the data source.
- type: The data source type. For databases, it must be ‘DATABASE’.
- description (optional): A generic description of the data source.
- properties: Specific mapping parameters with values for data source properties:
  - For a JDBC URL:
    - Database SID or service name
    - Host machine
    - Database listening port
    - User name and password credentials

  - For a container data source:
    - JNDI name - Java naming and directory interface (JNDI) name

  - For a wallet data source:

    - A string describing the wallet service
    - User name and password credentials (required if the user credentials are not stored in the wallet)
    - Optional proxy details

    For a cloud wallet it is usually an alias name stored in the tnsnames.ora file, but for a simple wallet it contains the host, port, and service name information.

The following example shows the JSON representation of a JDBC URL data source.

    {
        "name" : "rdfuser_jdbc_sid",
        "type" : "DATABASE",
        "description" : "",
        "properties" : {
        "host" : "127.0.0.1"
        "sid" : "orcl193"
        "port" : "1524",
        "user" : "rdfuser",
            "password" : "<password>"
        }
    }

The following example shows the JSON representation of a container data source:

    {
       "name": "rdfuser_ds_ct",
       "type": "DATABASE",
       "description": "Database Container connection",
       "properties": {
           "jndiName": "jdbc/RDFUSER193c"
       }
    }

The following example shows the JSON representation of a wallet data source where the credentials are stored in the wallet:

    {
       "name": "rdfuser_ds_wallet",
       "type": "DATABASE",
       "description": "Database wallet connection",
       "properties": {
           "walletService": "db202002041627_medium"
       }
    }

**Parent topic:** [Data Sources](data-sources.md)
