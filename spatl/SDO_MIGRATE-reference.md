## 28  SDO_MIGRATE Package (Upgrading)

The MDSYS.SDO_MIGRATE package contains a single subprogram, SDO_MIGRATE.TO_CURRENT.

The SDO_MIGRATE.TO_CURRENT subprogram described in this chapter has both procedure and function interfaces. As a procedure, it lets you upgrade spatial geometry tables from previous releases of Spatial and Graph; and as a function, it lets you upgrade a single SDO_GEOMETRY object.

This subprogram has very limited uses, as explained in the Usage Notes for its documentation.

- SDO_MIGRATE.TO_CURRENT

**Parent topic:** [Reference Information](spatial-reference-information.md)

### 28.1 SDO_MIGRATE.TO_CURRENT

#### Format (Any Object-Relational Model Implementation to Current)

    SDO_MIGRATE.TO_CURRENT(
         tabname         IN VARCHAR2      
         [, column_name  IN VARCHAR2]);

or

    SDO_MIGRATE.TO_CURRENT(
         tabname       IN VARCHAR2,
         column_name   IN VARCHAR2
         [, commit_int IN NUMBER]);

#### Format (Single Object-Relational Model Geometry to Current)

    SDO_MIGRATE.TO_CURRENT(
         geom  IN SDO_GEOMETRY,
         dim   IN SDO_DIM_ARRAY
         
    ) RETURN SDO_GEOMETRY;

#### Format (Any Relational Model Implementation to Current)

    SDO_MIGRATE.TO_CURRENT(
         layer       IN VARCHAR2,
         newtabname  IN VARCHAR2,
         gidcolumn   IN VARCHAR2,
         geocolname  IN VARCHAR2,
         layer_gtype IN VARCHAR2,
         updateflag  IN VARCHAR2);

#### Description

Upgrades data from the obsolete Spatial relational model (release 8.1.5 or earlier) to the current release, or upgrades one or more object-relational model (release 8.1.6 or later) geometries that need to be upgraded (as explained in the Usage Notes). As a procedure, TO_CURRENT upgrades an entire layer (all geometries in a column); as a function, TO_CURRENT upgrades a single geometry object, which must be of type SDO_GEOMETRY.

For upgrading a layer, the procedure format depends on whether you are upgrading from the Spatial relational model (release 8.1.5 or earlier) or object-relational model (release 8.1.6 or later). See the Usage Notes for the model that applies to you.

**Note:**

This procedure applies to two-dimensional geometries only. It is not supported for three-dimensional geometries.

#### Parameters

tabname
Table with geometry objects.

column_name
Column in `tabname` that contains geometry objects. If `column_name` is not specified or is specified as null, the column containing geometry objects is upgraded.

commit_int
Number of geometries to upgrade before Spatial and Graph performs an internal commit operation. If `commit_int` is not specified, no internal commit operations are performed during the upgrade.

If you specify a `commit_int` value, you can use a smaller rollback segment than would otherwise be needed.

geom
Single geometry object to be upgraded to the current release.

dim
Dimensional information array for the geometry object to be upgraded. The SDO_DIM_ARRAY type is explained in [DIMINFO](spatial-datatypes-metadata.md).

layer
Name of the layer to be upgraded.

newtabname
Name of the new table to which you are upgrading the data.

gidcolumn
Name of the column in which to store the GID from the old table.

geocolname
Name of the column in the new table where the geometry objects will be inserted.

layer_gtype
One of the following values: POINT or NOTPOINT (default).

If the layer you are upgrading is composed solely of point data, set this parameter to POINT for optimal performance; otherwise, set this parameter to NOTPOINT. If you set the value to POINT and the layer contains any nonpoint geometries, the upgrade might produce invalid data.

updateflag
One of the following values: UPDATE or INSERT (default).

If you are upgrading the layer into an existing populated attribute table, set this parameter to UPDATE; otherwise, set this parameter to INSERT.

#### Usage Notes for Object-Relational Model Layer and Single Geometry Upgrade

This subprogram is not needed for normal upgrades of Oracle Spatial and Graph. It is sometimes needed if spatial data is loaded using a third-party loader and if the resulting geometries have the wrong orientation or invalid ETYPE or GTYPE values. For information about using this subprogram as part of the recommended procedure for loading and validating spatial data, see [Recommendations for Loading and Validating Spatial Data](loading-spatial-data.md).

This subprogram upgrades the specified geometry or all geometry objects in the specified layer so that their SDO_GTYPE and SDO_ETYPE values are in the format of the current release:

- SDO_GTYPE values of 4 digits are created, using the format (DLTT) shown in [SDO_GTYPE](spatial-datatypes-metadata.md).

- SDO_ETYPE values are as discussed in [SDO_ELEM_INFO](spatial-datatypes-metadata.md).

Geometries are ordered so that exterior rings are followed by their interior rings, and coordinates are saved in the correct rotation (counterclockwise for exterior rings, and clockwise for interior rings).

#### Usage Notes for Relational Model Upgrade

If you are you upgrading from the Spatial relational model (release 8.1.5 or earlier), consider the following when using this procedure:

- The new table must be created before you call this procedure.

- If the data to be upgraded is geodetic, the tolerance value (SDO_TOLERANCE column value in the \<layername\>\_SDODIM table or view) must be expressed in decimal degrees (for example, 0.00000005).

- The procedure converts geometries from the relational model to the object-relational model.

- A commit operation is performed by this procedure.

- If any of the upgrade steps fails, nothing is upgraded for the layer.

- `layer` is the underlying layer name, without the \_SDOGEOM suffix.

- The old SDO_GID is stored in `gidcolumn`.

- SDO_GTYPE values of 4 digits are created, using the format (DLTT) shown in [SDO_GTYPE](spatial-datatypes-metadata.md).

- SDO_ETYPE values are created, using the values discussed in [SDO_ELEM_INFO](spatial-datatypes-metadata.md).

- The procedure orders geometries so that exterior rings are followed by their interior rings, and it saves coordinates in the correct rotation (counterclockwise for exterior rings, and clockwise for interior rings).

#### Examples

The following example changes the definitions of geometry objects in the ROADS table from the format of a release later than 8.1.5 to the format of the current release.

    EXECUTE SDO_MIGRATE.TO_CURRENT('ROADS');

**Parent topic:** SDO_MIGRATE Package (Upgrading)
