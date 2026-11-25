# Description of the illustration create_user

    CREATE USER [ IF NOT EXISTS ] user
       { {
           IDENTIFIED

            {
               BY password [ [HTTP] DIGEST { ENABLE | DISABLE } ]
                   [ AND FACTOR auth_method AS external_name ]
               | EXTERNALLY [ AS 'certificate_DN'  |  AS 'kerberos_principal_name' ]
               | GLOBALLY [ AS '{ directory_DN | { AZURE_USER | AZURE_ROLE }=value
                                           | {IAM_GROUP_NAME | IAM_PRINCIPAL_NAME}=value  }']
               }
            }
              | NO AUTHENTICATION
       }
       [ DEFAULT COLLATION collation_name ]
       [ DEFAULT TABLESPACE tablespace
       | [ LOCAL ] TEMPORARY TABLESPACE { tablespace | tablespace_group_name }
       | { QUOTA { size_clause | UNLIMITED } ON tablespace }...
       | PROFILE profile
       | PASSWORD EXPIRE
       | ACCOUNT { LOCK | UNLOCK }
         [ DEFAULT TABLESPACE tablespace
         | TEMPORARY TABLESPACE
              { tablespace | tablespace_group_name }
         | { QUOTA { size_clause | UNLIMITED } ON tablespace }...
         | PROFILE profile
         | PASSWORD EXPIRE
         | ACCOUNT { LOCK | UNLOCK }
         | ENABLE EDITIONS
         | CONTAINER = { CURRENT | ALL }
         ]...
      ] ;
