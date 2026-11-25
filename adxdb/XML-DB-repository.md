Oracle XML DB Repository lets you version your data, implement and manage security, and use APIs to access and manipulate repository resources.

- [Access to Oracle XML DB Repository Data](accessing-XML-DB-repository-data.md)
  There are several ways to access and manipulate data in Oracle XML DB Repository, including using standard protocols such as FTP and HTTP(S)/WebDAV; Oracle XML DB resource Application Program Interfaces (APIs); and the repository views `RESOURCE_VIEW` and `PATH_VIEW`.
- [Configuration of Oracle XML DB Repository](configuration-of-XML-DB-repository.md)
  Overall configuration of Oracle XML DB Repository applies to all repository resources. It does not include configuring parameters for handling events or managing XLink and XInclude processing. You use resource configuration files to configure resources.
- [Use of XLink and XInclude with Oracle XML DB](use-of-XLink-and-XInclude-with-XML-DB.md)
  You can use XLink and XInclude with resources in Oracle XML DB Repository. But the use of XLink is deprecated.
- [Repository Access Using RESOURCE_VIEW and PATH_VIEW](repository-access-using-RESOURCE_VIEW-and-PATH_VIEW.md)
  Predefined public views `RESOURCE_VIEW` and `PATH_VIEW` provide access to Oracle XML DB repository data. You can use Oracle SQL functions `under_path` and `equals_path` to query resources based on their path names, and functions `path` and `depth` to return resource path names and depths.
- [Resource Versions](resource-versions.md)
  Oracle XML DB Repository resources can be versioned. A record is kept of all changes to a resource that is under version control.
- [PL/SQL Access to Oracle XML DB Repository](PLSQL-access-to-XML-DB-repository.md)
  PL/SQL packages `DBMS_XDB_CONFIG` and `DBMS_XDB_REPOS` together provide the Oracle XML DB resource application program interface (API) for PL/SQL. You use the former to configure Oracle XML DB and its repository. You use the latter to perform other, non-configuration operations on the repository.
- [Repository Access Control](repository-access-control.md)
  Oracle Database provides classic database security such as row-level and column-level secure access by database users. It also provides fine-grained access control for resources in Oracle XML DB Repository. You can create, set, and modify access control lists (ACLs).
- [Repository Access Using Protocols](repository-access-using-protocols.md)
  You can access Oracle XML DB Repository data using protocols FTP and HTTP(S)/WebDAV.
- [User-Defined Repository Metadata](user-defined-repository-metadata.md)
  You can create your own metadata to associate with XML data stored in Oracle XML DB Repository.
- [Oracle XML DB Repository Events](XML-DB-repository-events.md)
  You can use Oracle XML DB Repository to store and access data of any kind, in the form of repository resources. You can access repository data from any application. Sometimes your application needs to perform certain actions whenever a particular repository operation occurs. You can do this using repository events.
- [Guidelines for Oracle XML DB Applications in Java](how-to-write-XML-DB-applications-in-Java.md)
  Design guidelines are presented for writing Oracle XML DB applications in Java. This includes guidelines for writing and configuring Java servlets for Oracle XML DB.
- [Data Access Using URIs](data-access-using-URIs.md)
  You can generate and store URIs in the database and use them to retrieve the database data they target. There are three kinds of URIs you can use this way: DBUris, XDBUris, and HTTPUris.
- [Native Oracle XML DB Web Services](native-XML-DB-web-services.md)
  Your applications can access Oracle Database using native Oracle XML DB Web services.
