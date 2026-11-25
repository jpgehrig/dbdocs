The illustration shows on the left three sources of data collection in the Internet of Things: smart meters, sensor data, and traffic cameras. These sources send high-frequency inserts to the application server.

The application server sends deferred inserts to the Large Pool. The ingested data is batched in the database in the large pool and is not immediately written. The ingest process is very fast. Background processes later write the data to the database.
