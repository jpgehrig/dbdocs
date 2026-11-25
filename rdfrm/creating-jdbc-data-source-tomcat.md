## 14.3.1.2.2 Creating a JDBC Data Source in Tomcat

There are different ways to create a JDBC data source in Tomcat. See [Tomcat documentaion](http://tomcat.apache.org/tomcat-3.2-doc/index.html) for more details.

The following examples denote creation of JDBC data source in Tomcat by modifying the configuration files `conf/server.xml` and `conf/content.xml`.

- Add global JNDI resources on `conf/server.xml`.

      <GlobalNamingResources>
          <Resource name="jdbc/RDFUSER19c" auth="Container" global="jdbc/RDFUSER19c"
                    type="javax.sql.DataSource" driverClassName="oracle.jdbc.driver.OracleDriver"
                    url="jdbc:oracle:thin:@host.name:db_port_number:db_sid"
                    username="rdfuser" password="rdfuserpwd" maxTotal="20" maxIdle="10"
                    maxWaitMillis="-1"/>
       </GlobalNamingResources>

- Add the resource link to global JNDI’s on `conf/context.xml`:

      <Context>
          <ResourceLink name="jdbc/RDFUSER19c"
                        global="jdbc/RDFUSER19c"
                        auth="Container"
                        type="javax.sql.DataSource" />
      </Context>

**Parent topic:** [Creating an Oracle Container Data Source](creating-oracle-container-data-source.md)
