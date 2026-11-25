## 6.257 TRUSTED_SERVERS

`TRUSTED_SERVERS` displays whether a server is trusted or untrusted.

| Column  | Datatype        | NULL | Description                                                                                                                                           |
|:--------|:----------------|:-----|:------------------------------------------------------------------------------------------------------------------------------------------------------|
| `TRUST` | `VARCHAR2(9)`   |      | Trustedness of the server listed. Values can be `TRUSTED` or `UNTRUSTED` servers which are not listed in the `NAME` column have opposite trustedness. |
| `NAME`  | `VARCHAR2(128)` |      | Server name. Can be a specific server name or ALL for all servers.                                                                                    |

Table 6-1 shows examples of the values returned depending on the status of the servers.

Table 6-1 TRUSTED_SERVERS Values

| Condition (If . . . )                    | TRUSTED column | NAME column |
|:-----------------------------------------|:---------------|:------------|
| ... all servers are trusted              | `Trusted`      | `ALL`       |
| ... no servers are trusted               | `Untrusted`    | `ALL`       |
| ... all servers except DB1 are trusted   | `Untrusted`    | `DB1`       |
| ... all servers except DB1 are untrusted | `Trusted`      | `DB1`       |

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_DISTRIBUTED_TRUST_ADMIN.md)

- [Oracle Database Enterprise User Security Administrator's Guide](../dbimi/introducing-enterprise-user-security.md)
