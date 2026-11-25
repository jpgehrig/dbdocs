## 6.181 DICTIONARY_CREDENTIALS_ENCRYPT

`DICTIONARY_CREDENTIALS_ENCRYPT` indicates whether encryption of dictionary credentials is enforced or not. You can encrypt sensitive credential information, such as passwords that are stored in the data dictionary.

| Column        | Datatype      | NULL | Description                                                                                                                                                                                                          |
|:--------------|:--------------|:-----|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ENFORCEMENT` | `VARCHAR2(8)` |      | Enforcement status for encryption of dictionary credentials. Possible values:<br>• `ENABLED`: Encryption of dictionary credentials is enforced<br>• `DISABLED`: Encryption of dictionary credentials is not enforced |

**See Also:**

[Oracle Database Security Guide](../dbseg/encrypt-sensitive-data.md) for information about encrypting sensitive credential information in the data dictionary
