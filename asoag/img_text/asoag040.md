# Description of the illustration asoag040.png

Figure asoag040.png illustrates how TDE column encryption works. Its components are as follows:

- External to the datbase is the software or hardware keystore. Within this software or hardware keystore, there is the TDE master encryption key.

- Within the database, in the data dictionary, are the TDE table keys. There are also tables that store encrypted data. This illustration shows a table that has encrypted credit card numbers.

The software or hardware keystore connects to the database and performs the encryption and decryption through the TDE table keys in the data dictionary, which in turn apply the encryption and decryption to the protected table, in this case, credit card numbers.
