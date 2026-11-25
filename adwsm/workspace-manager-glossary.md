### active version

See current version.

**Parent topic:** Glossary

### child workspace

A workspace created from its parent workspace.

See also parent workspace and workspace hierarchy.

**Parent topic:** Glossary

### conflicts

Differences in data values resulting from changes to rows in the child and parent workspace. Conflicts are detected at merge time and presented to the user in conflict views.

See also merging (a workspace).

**Parent topic:** Glossary

### context

Information about the workspace that determines what data the session can see in the workspace. The context can be retrieved using the [GetSessionInfo](DBMS_WM-reference.md) procedure

**Parent topic:** Glossary

### current version

The version in which the changes are currently being made.

**Parent topic:** Glossary

### exclusive locking

A Workspace Manager lock mode that prevents any other user from changing a locked row.

See also locks.

**Parent topic:** Glossary

### explicit savepoint

A savepoint that is explicitly created. It can later be used to perform partial rollbacks in workspaces.

See also savepoint, implicit savepoint, and removable savepoint.

**Parent topic:** Glossary

### freezing (a workspace)

Causing the condition in which no changes can be made to data in version-enabled rows in a workspace, and access to the workspace is restricted.

**Parent topic:** Glossary

### implicit savepoint

A savepoint that is created automatically whenever a new workspace is created.

See also savepoint, explicit savepoint, and removable savepoint.

**Parent topic:** Glossary

### LATEST

The name of the logical savepoint that refers to the latest version in the workspace.

See also savepoint.

**Parent topic:** Glossary

### LIVE

The name of the topmost workspace in the workspace hierarchy.

See also workspace hierarchy.

**Parent topic:** Glossary

### locks

Version locks provided by Workspace Manager, separate from locks provided by conventional Oracle database transactions. These locks are primarily intended to eliminate row conflicts between a parent workspace and a child workspace. Locking is enabled at a session level and is a session property independent of the workspace in which the session is. When locking is enabled for a session, it locks rows in all workspaces in which it participates.

**Parent topic:** Glossary

### merging (a workspace)

Applying changes made in a workspace to its parent workspace.

**Parent topic:** Glossary

### nonwriter site

A master site in a multimaster group in a Workspace Manager replication environment that is not the writer site. A nonwriter site cannot perform any write operations, but can perform all read operations, such as [CreateSavepoint](DBMS_WM-reference.md) or SELECT queries on version-enabled tables.

See also writer site.

**Parent topic:** Glossary

### parent workspace

A workspace from which another workspace (a child workspace) was created.

See also child workspace and workspace hierarchy.

**Parent topic:** Glossary

### privileges

A set of privileges for Workspace Manager that are separate from standard Oracle database privileges. Workspace-level privileges (with names in the form xxx\_WORKSPACE) that allow the user to affect a specified workspace. System-level privileges (with names in the form xxx\_ANY_WORKSPACE) that allow the user to affect any workspace.

**Parent topic:** Glossary

### removable savepoint

A workspace that can be deleted by the [CompressWorkspace](DBMS_WM-reference.md), [CompressWorkspaceTree](DBMS_WM-reference.md), and [DeleteSavepoint](DBMS_WM-reference.md) procedures. A savepoint is removable if it is an explicit savepoint or if it is an implicit savepoint that does not have any child dependencies.

See also savepoint, explicit savepoint, and implicit savepoint.

**Parent topic:** Glossary

### rolling back (a workspace)

Deleting either all changes made in the workspace or all changes made after a savepoint (that is, an explicit savepoint).

**Parent topic:** Glossary

### savepoint

A point in the workspace to which operations can be rolled back. It is analogous to a firewall, in that by creating a savepoint you can prevent any damage to the "other side" of the wall (that is, operations performed in the workspace before the savepoint was created).

See also explicit savepoint, implicit savepoint, and removable savepoint.

**Parent topic:** Glossary

### session context

See context.

**Parent topic:** Glossary

### shared locking

A Workspace Manager lock mode that allows only users in the workspace in which the row was locked to modify the row.

See also locks.

**Parent topic:** Glossary

### unfreezing (a workspace)

Reversing the effect of a freeze operation.

See also freezing (a workspace).

**Parent topic:** Glossary

### valid time

The time during which a record is valid, or the ability to specify the time for which a record is valid. Also called effective dating.

**Parent topic:** Glossary

### valid time filter

A time that is applied to queries against version-enabled tables that have valid time support. When a valid time filter is set for the current session, only rows that are valid for the specified time are returned.

**Parent topic:** Glossary

### version-enabled table

A table in the database in which all rows in the table can now support multiple versions of data. The versioning infrastructure is not visible to the database users. After a table has been version-enabled, users automatically see the correct version of the record in which they are interested.

**Parent topic:** Glossary

### workspace

A virtual environment that one or more users can share to make changes to the data in the database. Workspace management involves managing one or more workspaces that can be shared by many users.

**Parent topic:** Glossary

### workspace hierarchy

The hierarchy of workspaces in the database. For example, a workspace can be a parent to one or more workspaces. By default, when a workspace is created, it is created from the topmost, or `LIVE`, database workspace.

**Parent topic:** Glossary

### workspace management

The ability of the database to hold different versions of the same record (that is, row) in one or more workspaces.

**Parent topic:** Glossary

### writer site

The master definition site in a Workspace Manager replication environment. Only the writer site can perform workspace operations and DML and DDL operations on version-enabled tables. All other sites in the multimaster group are nonwriter sites.

See also nonwriter site.

**Parent topic:** Glossary
