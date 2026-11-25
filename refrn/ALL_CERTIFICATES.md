## 2.116 ALL_CERTIFICATES

`ALL_CERTIFICATES` displays the certificates accessible to the current user which are used for signature verification for blockchain tables.

### Related Views

- `DBA_CERTIFICATES` displays all certificates in the database which are used for signature verification for blockchain tables.

- `USER_CERTIFICATES` displays the certificates added by the current user which are used for signature verification for blockchain tables. This view does not display the `USER_NAME` column.

| Column               | Datatype         | NULL       | Description                                              |
|:---------------------|:-----------------|:-----------|:---------------------------------------------------------|
| `CERTIFICATE_ID`     | `RAW(16)`        | `NOT NULL` | ID for the certificate                                   |
| `USER_NAME`          | `VARCHAR2(128)`  | `NOT NULL` | User who added the certificate                           |
| `DISTINGUISHED_NAME` | `VARCHAR2(2000)` |            | Uniquely identifies the entity that owns the certificate |
| `CERTIFICATE`        | `BLOB`           |            | Contents of the certificate                              |

**Note:**

This view is available starting with Oracle Database 19c, Release Update 19.10.

**See Also:**

- "[DBA_CERTIFICATES](DBA_CERTIFICATES.md)"

- "[USER_CERTIFICATES](USER_CERTIFICATES.md)"
