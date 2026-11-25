# Description of the illustration db_pooling.eps

This image shows multiple clients from two different hosts with persistent connections to the connection broker. One client is shown directly connected to a pool of dedicated server processes that connect to the system global area of the database, implying that the client is doing database work. When the work is done, The connection broker hands back the connection to the pool of dedicated server processes.
