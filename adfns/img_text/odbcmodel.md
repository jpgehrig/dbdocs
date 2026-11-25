# Description of the illustration odbcmodel.gif

This graphic shows an ODBC application accessing three separate databases. An ODBC application makes a call to the Driver Manager through the ODBC API. The Driver Manager can be either the Microsoft Driver Manager or the unixODBC Driver Manager. Still using the ODBC API, the Driver Manager makes a call to the ODBC Driver. The ODBC Driver accesses the database over a network communications link using the database API.
