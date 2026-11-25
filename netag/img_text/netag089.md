# Description of the illustration netag089.eps

This illustration shows where the listener fits into a client/server application connection.

The client shows a communication stack. From the top down, the stack is constructed with the following layers:

- Application

- Oracle Net foundation layer

- Oracle protocol support

The illustration shows the listener receiving the client connection on the database server. The database server shows a communication stack that includes three layers. From the top down, the stack is constructed with the following layers:

- RDBMS

- Oracle Net foundation layer

- Oracle protocol support

The TCP/IP network protocol resides between the client and the database server.

During a connection, the client application communicates with the Oracle Net layer. In turn, Oracle Net communicates with the TCP/IP protocol, which passes the connection to the Oracle Net layer on the database server.
