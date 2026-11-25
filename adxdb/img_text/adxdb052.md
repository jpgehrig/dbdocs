This illustration shows the following components needed to send XML messages over HTTP:

- An AQ client program that sends XML messages, conforming to iDAP format, to the AQ Servlet. This can be any HTTP client, such as a Web browser.

- The Web server or ServletRunner which hosts the AQ servlet that can interpret the incoming XML messages. For example, Apache/Jserv or Tomcat.

- Oracle Server/Database. Oracle Streams AQ servlet connects to Oracle Database to perform operations on the queues.
