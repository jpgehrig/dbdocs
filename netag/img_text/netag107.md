# Description of the illustration netag107.eps

This illustration shows a client/server application connection using Oracle Net. The client shows a communication stack. From the top down, the stack is constructed with the following layers:

- Application

- Oracle Net

The database server also shows a communication stack. From the top down, the stack is constructed with the following layers.

- RDBMS

- Oracle Net

The TCP/IP network protocol resides between the client and the database server.

During the connection, the client application communicates with the Oracle Net layer. In turn, Oracle Net communicates with the TCP/IP protocol, which passes the connection to the Oracle Net layer on the database server.
