# Description of the illustration admin556.eps

This illustration shows a materialized view database and a master database. The materialized views in the `hr` schema use a private database link to connect to the tables in the `hr` schema at the master database. The database link is shown connecting to the master database in the following way:

    CONNECT TO hr
      IDENTIFIED BY ...

The materialized views in the `oe` schema use a private database link to connect to the tables in the `oe` schema at the master database. The database link is shown connecting to the master database in the following way:

    CONNECT TO oe
      IDENTIFIED BY ...
