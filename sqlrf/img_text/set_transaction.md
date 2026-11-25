# Description of the illustration set_transaction.eps

    SET TRANSACTION
       { { READ { ONLY | WRITE }
         | ISOLATION LEVEL
           { SERIALIZABLE | READ COMMITTED }
         | USE ROLLBACK SEGMENT rollback_segment
         } [ NAME string ]
       | NAME string
       } ;
