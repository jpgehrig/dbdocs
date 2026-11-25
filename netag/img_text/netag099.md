# Description of the illustration netag099.eps

This illustration depicts the various layers of stack communication used in a client/server application connection. On the client side, from the top down, the stack includes the following layers:

- Client Application (uses OCI)

- Presentation - TTC

- Oracle Net Foundation Layer

- Oracle Protocol Support

- Network Protocol (TCP/IP, TCP/IP with TLS, SDP, and Named Pipes

On the server side, from the top down, the stack includes the following layers:

- RDBMS (uses OPI)

- Presentation - TTC

- Oracle Net Foundation Layer

- Oracle Protocol Support

- Transport Protocol (TCP/IP, TCP/IP with TLS, SDP, and Named Pipes.

The Oracle Net Foundation Layer and Oracle Protocol Support make up Oracle Net. On the client side, Oracle Net Foundation Layer is associated with naming methods. On both the client and server sides, Oracle Net Foundation Layer is associated with security services.
