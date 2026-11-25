## 2.173 ALL_ENCRYPTED_COLUMNS

`ALL_ENCRYPTED_COLUMNS` displays encryption algorithm information for the encrypted columns in the tables accessible to the current user.

### Related Views

- `DBA_ENCRYPTED_COLUMNS` displays encryption algorithm information for all encrypted columns in the database.

- `USER_ENCRYPTED_COLUMNS` displays encryption algorithm information for the encrypted columns in the tables owned by the current user. This view does not display the `OWNER` column.

| Column           | Datatype        | NULL       | Description                                                                                                                                                                       |
|:-----------------|:----------------|:-----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`          | `VARCHAR2(128)` | `NOT NULL` | Owner of the table                                                                                                                                                                |
| `TABLE_NAME`     | `VARCHAR2(128)` | `NOT NULL` | Name of the table                                                                                                                                                                 |
| `COLUMN_NAME`    | `VARCHAR2(128)` | `NOT NULL` | Name of the column                                                                                                                                                                |
| `ENCRYPTION_ALG` | `VARCHAR2(29)`  |            | Encryption algorithm used to protect secrecy of data in this column:<br>• `3 Key Triple DES 168 bits key`<br>• `AES 128 bits key`<br>• `AES 192 bits key`<br>• `AES 256 bits key` |
| `SALT`           | `VARCHAR2(3)`   |            | Indicates whether the column is encrypted with SALT (`YES`) or not (`NO`)                                                                                                         |
| `INTEGRITY_ALG`  | `VARCHAR2(12)`  |            | Integrity algorithm used for the column:<br>• `SHA-1`<br>• `NOMAC`                                                                                                                |

**See Also:**

- "[DBA_ENCRYPTED_COLUMNS](DBA_ENCRYPTED_COLUMNS.md)"

- "[USER_ENCRYPTED_COLUMNS](USER_ENCRYPTED_COLUMNS.md)"
