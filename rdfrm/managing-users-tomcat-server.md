## 14.2.2 Managing Users and Roles in Tomcat Server

For Apache Tomcat, edit the Tomcat users file `conf/tomcat-users.xml` to include the RDF user roles. For example:

    <tomcat-users xmlns="http://tomcat.apache.org/xml" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" version="1.0" xsi:schemaLocation="http://tomcat.apache.org/xml tomcat-users.xsd">

        <role rolename="rdf-admin-user"/>

        <role rolename="rdf-read-user"/>

        <role rolename="rdf-readwrite-user"/>

        <user password="adminpassword" roles="manager-script,admin,rdf-admin-user" username="admin"/>

        <user password="rdfuserpassword" roles="rdf-readwrite-user" username="rdfuser"/>

        <user password="notrdfuserpassword" roles="rdf-read-user" username="notrdfuser"/>

    </tomcat-users>

**Parent topic:** [Managing User Roles for RDF Graph Query UI](managing-user-roles-rdf-graph-query-ui.md)
