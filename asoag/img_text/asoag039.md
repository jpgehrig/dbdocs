# Description of the illustration asoag039.png

Figure asoag039.png illustrates how TDE tablespace encryption works. Its components are as follows:

- External to the datbase is the software or hardware keystore. Within this software or hardware keystore, there is the TDE master encryption key.

- Within the database are two tablespaces. The software or hardware keystore controls the encryption for each one. Each tablespace has its own tablespace encryption key, which in turn encrypts the data files within the tablespace.
