## 37  SDO_WFS_LOCK Package (WFS)

The MDSYS.SDO_WFS_LOCK package contains subprograms for WFS support for registering and unregistering feature tables.

Registering a feature table enables the table for WFS transaction locking; unregistering a feature table disables the table for WFS transaction locking.

To use the subprograms in this chapter, you must understand the conceptual and usage information about Web Feature Services (WFS) in [Web Feature Service (WFS) Support](web-feature-service-wfs-concepts.md).

The rest of this chapter provides reference information on the subprograms, listed in alphabetical order.

- SDO_WFS_LOCK.EnableDBTxns
- SDO_WFS_LOCK.RegisterFeatureTable
- SDO_WFS_LOCK.UnRegisterFeatureTable

**Parent topic:** [Reference Information](spatial-reference-information.md)

### 37.1 SDO_WFS_LOCK.EnableDBTxns

#### Format

    SDO_WFS_LOCK.EnableDBTxns();

#### Description

Enables database transactions on WFS tables.

#### Parameters

None.

#### Usage Notes

This procedure overrides, through the end of the session, the WFS-T standard restriction against database transactions on WFS tables, so that any transaction with the current session ID can perform update and delete operations on WFS tables. Oracle Database triggers still check the WFS locks before the current transaction is allowed to modify a row; and so if a WFS transaction has a lock on a row, the triggers will not allow the operation to be performed. However, if there is no WFS lock on the current row, the triggers will allow the current transaction to modify the row.

You must call this procedure to perform certain operations when using Oracle Workspace Manager to version-enable a WFS table, as explained in [Using WFS with Oracle Workspace Manager](web-feature-service-wfs-concepts.md). However, you can also use this procedure even if you do not use Workspace Manager with WFS tables.

For information about support for Web Feature Services, see [Web Feature Service (WFS) Support](web-feature-service-wfs-concepts.md).

#### Examples

The following example enables database transactions on WFS tables for the remainder of the current session.

    BEGIN
      SDO_WFS_LOCK.enableDBTxns;
    END;
    /

**Parent topic:** SDO_WFS_LOCK Package (WFS)

### 37.2 SDO_WFS_LOCK.RegisterFeatureTable

#### Format

    SDO_WFS_LOCK.RegisterFeatureTable(
         username  IN VARCHAR2,
         tablename IN VARCHAR2);

#### Description

Registers a feature table; that is, enables the feature table for WFS transaction locking.

#### Parameters

username
Name of the database user that owns the feature table to be registered.

tablename
Name of the feature table to be registered.

#### Usage Notes

This procedure ensures that the necessary constraints for implementing WFS transaction semantics are associated with the feature table.

For information about support for Web Feature Services, see [Web Feature Service (WFS) Support](web-feature-service-wfs-concepts.md).

To unregister a table that has not been version-enabled, use the SDO_WFS_LOCK.UnRegisterFeatureTable procedure.

#### Examples

The following example registers the feature table named COLA_MARKETS_CS, which is owned by user WFS_REL_USER.

    BEGIN
      SDO_WFS_LOCK.registerFeatureTable('wfs_rel_user', 'cola_markets_cs');
    END;
    /

**Parent topic:** SDO_WFS_LOCK Package (WFS)

### 37.3 SDO_WFS_LOCK.UnRegisterFeatureTable

#### Format

    SDO_WFS_LOCK.UnRegisterFeatureTable(
         username  IN VARCHAR2,
         tablename IN VARCHAR2);

#### Description

Unregisters a feature table; that is, disables the feature table for WFS transaction locking.

#### Parameters

username
Name of the database user that owns the feature table to be unregistered.

tablename
Name of the feature table to be unregistered.

#### Usage Notes

This procedure disables, for the feature table, the constraints for implementing WFS transaction semantics.

The feature table must have been previously registered in a call to the SDO_WFS_LOCK.RegisterFeatureTable procedure.

For information about support for Web Feature Services, see [Web Feature Service (WFS) Support](web-feature-service-wfs-concepts.md).

#### Examples

The following example unregisters the feature table named COLA_MARKETS_CS, which is owned by user WFS_REL_USER.

    BEGIN
      SDO_WFS_LOCK.unRegisterFeatureTable('wfs_rel_user', 'cola_markets_cs');
    END;
    /

**Parent topic:** SDO_WFS_LOCK Package (WFS)
