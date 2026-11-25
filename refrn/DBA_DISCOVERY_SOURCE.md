## 4.266 DBA_DISCOVERY_SOURCE

`DBA_DISCOVERY_SOURCE` describes sensitive data discovery import information.

| Column        | Datatype        | NULL | Description                                                                                                                |
|:--------------|:----------------|:-----|:---------------------------------------------------------------------------------------------------------------------------|
| `SOURCE_NAME` | `VARCHAR2(128)` |      | The name of the discovery source. In the case of Application Data Model (ADM), this is the ADM instance name.              |
| `SOURCE_TYPE` | `VARCHAR2(6)`   |      | The type of the source:<br>• `ADM`: import from ADM<br>• `CUSTOM`: custom import<br>• `DB`: discovered within the database |
| `CTIME`       | `TIMESTAMP(6)`  |      | The last time sensitive data was imported from this source                                                                 |

**See Also:**

[Oracle Database Security Guide](../dbseg/using-transparent-sensitive-data-protection.md) for more information about transparent sensitive data protection
