<table class="oac_no_warn" data-border="0" data-cellpadding="1" data-cellspacing="0" data-summary="Layout table... probably." width="100%">
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Overview </td>
<td style="text-align: right;" data-valign="top"><em><strong>Oracle® OLAP Java API Reference<br />
19c</strong><br />
E96404-01</em></td>
</tr>
</tbody>
</table>

------------------------------------------------------------------------

**Examples for MdmMetadataProvider**

This file contains the following examples of exporting and importing Oracle OLAP metadata objects by using the `exportFullXML`, `exportIncrementalXML`, and `importXML` methods of an `MdmMetadataProvider`.

- Example 1 exports objects by using the `exportFullXML` and `exportIncrementalXML` methods.
- Example 2 exports and imports objects and uses the `bindVariables` and `bindValues` parameters.

Example 1 gets a persistent `MdmCube`, gets the `AWCubeOrganization` for the cube, and changes the measure storage option. The example then exports the full XML for the object, the full XML that has changed for the object in the transaction, and the incremental XML, which is just the line of XML that records the changed option for the object. In the code, `mp` is the `MdmMetadataProvider` and `mdmDBSchema` is an `MdmDatabaseSchema`.

**Example 1 Exporting XML**

      private void exportingXMLExample()
      {
        MdmCube mdmUnitsCube = (MdmCube)
                                mdmDBSchema.getTopLevelObject("UNITS_CUBE_AWJ");
        AWCubeOrganization awCubeOrg = (AWCubeOrganization)
                                        mdmUnitsCube.getOrganization();
        // Change an option in the current Transaction.
        awCubeOrg.setMeasureStorage(awCubeOrg.INDEPENDENT_MEASURE_STORAGE);
        ArrayList objects = new ArrayList();
        objects.add(mdmUnitsCube);
        try
        {
          println("Export the full definition of the cube.");
          println(mp.exportFullXML(objects, null, false));
          println("\nExport the full definition of the changed object only.");
          // A null Transaction specfies the persistent state of the object,
          // which in this case is the state before the change to the option.
          println(mp.exportFullXML((Transaction)null, null, false));
          println("\nExport the incremental change only.");
          println(mp.exportIncrementalXML(null, null, false));
        }
        catch (Exception ex)
        {
          println("Cannot export the XML.");
          ex.printStackTrace();
        }
        // Commit the current Transation, which moves the change to persistent
        // storage.
        getContext().commit();
      }

The preceding code displays the following output. Most of the lines of the full XML are not shown.

    Export the full definition of the cube.

    <Metadata
      Version="1.0">
      <Cube
        ETViewname="UNITS_CUBE_AWJ_VIEW"
        name="UNITS_CUBE_AWJ"
        ConsistentSolve="SOLVE
    (
      SUM OVER ALL
    )">
    ...
       <Organization>
         <AWCubeOrganization
           MVOption="NONE"
           SparseType="COMPRESSED"
           MeasureStorage="INDEPENDENT"
    ...
         </AWCubeOrganization>
       </Organization>
    ...
      </Cube>
    </Metadata>

    Export the full definition of the changed option only.

    <Metadata
      Version="1.0">
      <Cube
        name="UNITS_CUBE_AWJ">
        <Organization>
          <AWCubeOrganization
            MVOption="NONE"
            SparseType="COMPRESSED"
            MeasureStorage="INDEPENDENT"
     ...
          </AWCubeOrganization>
        </Organization>
      </Cube>
    </Metadata>

    Export the incremental change only.

    <Metadata
      Version="1.0">
      <Cube
        name="UNITS_CUBE_AWJ">
        <Organization>
          <AWCubeOrganization
            MeasureStorage="INDEPENDENT">
          </AWCubeOrganization>
        </Organization>
      </Cube>
    </Metadata>

**Example 2 Exporting and Importing XML With Bind Variables**

This example gets the GLOBAL_AWJ analytic workspace, the UNITS_CUBE_AWJ cube, and the CHANNEL_AWJ dimension. It creates an `ArrayList` for the objects to export. It creates `HashMap` objects for the `bindVariables` and `bindValues` parameters and puts keys and values in those hash maps.

It exports the objects to XML using the `exportFullXML(List objects, Map renameMap, boolean includeOwnerString, Map bindVariables)` method. The example displays the XML string. It then imports the XML using the `importXML(String inXML, MdmDatabaseSchema destinationSchema, boolean modifyIfExists, Map<String, String> bindValues)` method. It iterates through the imported objects and displays the name of the `MdmPrimaryDimension` objects and the owning `AW` object. Finally, the example exports and displays the XML for the imported objects.

      private void bindVariablesExample()
      {
        AW aw = mdmDBSchema.findOrCreateAW("GLOBAL_AWJ");
        AW newAW = mdmDBSchema.findOrCreateAW(aw.getName() + "_NEW");

        MdmCube mdmUnitsCube = mdmDBSchema.findOrCreateCube("UNITS_CUBE_AWJ");

        MdmStandardDimension mdmChanDim =
                     mdmDBSchema.findOrCreateStandardDimension("CHANNEL_AWJ");

        ArrayList objs = new ArrayList(1);
        HashMap bindVariables = new HashMap();
        HashMap bindValues = new HashMap();

        String bindVar = "B1";
        bindVariables.put(aw, bindVar);
        bindValues.put(bindVar, newAW.getName());

        bindVar = "B2";
        bindVariables.put(mdmUnitsCube, bindVar);
        bindValues.put(bindVar, mdmUnitsCube.getName() + "_NEW");

        bindVar = "B3";
        bindVariables.put(mdmChanDim, bindVar);
        bindValues.put(bindVar, mdmChanDim.getName() + "_NEW");

        objs.add(mdmUnitsCube);
        objs.add(mdmChanDim);

        String xml = null;
        try
        {
          println("Exporting the XML.");
          xml = mp.exportFullXML(objs, null, false, bindVariables);
          println("The XML is:" + xml);
        }
        catch (Exception ex)
        {
          println("Cannot export XML.");
          ex.printStackTrace();
        }

        List modObjs = null;
        ArrayList newObjs = new ArrayList();

        try
        {
          println("Importing the XML.");
          modObjs = mp.importXML(xml, mdmDBSchema, false, bindValues);
        }
        catch (Exception ex)
        {
          println("Cannot import the XML.");
          ex.printStackTrace();
        }

        for (Iterator iter = modObjs.iterator(); iter.hasNext();)
        {
          BaseMetadataObject obj = (BaseMetadataObject) iter.next();

          AW currAW = null;

          if (obj instanceof MdmCube)
          {
            println("\nThe name of the imported cube is " +
                ((MdmCube)obj).getName());
            CubeOrganization cubeOrg = ((MdmCube)obj).getOrganization();
            currAW = ((AWCubeOrganization)cubeOrg).getAW();
            println("The cube is deployed to the analytic workspace "+
                     currAW.getName());
          }
          else if (obj instanceof MdmPrimaryDimension)
          {
            println("\nThe name of the imported dimension is " +
                    ((MdmPrimaryDimension)obj).getName());
            PrimaryDimensionOrganization dimOrg =
              ((MdmPrimaryDimension)obj).getOrganization();
            currAW = ((AWPrimaryDimensionOrganization)dimOrg).getAW();
            println("The dimension is deployed to the analytic workspace "+
                     currAW.getName());
          }

          newObjs.add(obj);
        }

        try
        {
          println("\nExporting the new objects to XML:");
          println("The XML is:" + mp.exportFullXML(newObjs, null, false));
        }
        catch(Exception ex)
        {
          println("Cannot export the XML");
          ex.printStackTrace();
        }

      }

The preceding code displays the following output. Most of the lines of the full XML are not shown.

    Exporting the XML.
    The XML is:
    <!DOCTYPE Metadata [
      <!ENTITY % BIND_VALUES PUBLIC "OLAP BIND VALUES" "OLAP METADATA">
      %BIND_VALUES;
      ]>
    <Metadata
      Version="1.0">
      <Cube
        ETViewname="UNITS_CUBE_AWJ_VIEW"
        name="O_B2_"
    ...
      >
    ...
        <CubeMap
          name="MAP1"
    ...
        >
    ...
          <CubeDimensionalityMap
            name="CHANNEL_AWJ"
            Expression="UNITS_FACT.CHANNEL_ID">
    ...
            <Dimensionality
              name="CHANNEL_AWJ"/>
            <MappedDimension
              name="O_B3__CHANNEL_PRIMARY_CHANNEL"/>
          </CubeDimensionalityMap>
        </CubeMap>
        <Organization>
          <AWCubeOrganization
    ....
            <AW
              name="O_B1_"/>
          </AWCubeOrganization>
        </Organization>
    ...
        <Dimensionality
          name="CHANNEL_AWJ"
          ETKeyColumnname="CHANNEL_AWJ">
          <Dimension
            name="O_B3_"/>
        </Dimensionality>
      </Cube>

      <StandardDimension
        name="O_B3_"
    ...
        <Organization>
          <AWPrimaryDimensionOrganization
    ...
          >
    ...
            <AW
              name="O_B1_"/>
          </AWPrimaryDimensionOrganization>
        </Organization>
    ...
      </StandardDimension>
    </Metadata>

    The name of the imported cube is UNITS_CUBE_AWJ_NEW
    The cube is deployed to the analytic workspace GLOBAL_AWJ_NEW

    The name of the imported dimension is CHANNEL_AWJ_NEW
    The dimension is deployed to the analytic workspace GLOBAL_AWJ_NEW

    Exporting the new objects to XML:
    The XML is:
    <Metadata
      Version="1.0">
      <Cube
        ETViewname="UNITS_CUBE_AWJ_VIEW"
        name="UNITS_CUBE_AWJ_NEW"
    ...
      >
    ...
        <CubeMap
          name="MAP1"
    ...
        >
    ...
          <CubeDimensionalityMap
            name="CHANNEL_AWJ"
            Expression="UNITS_FACT.CHANNEL_ID">
            <Dimensionality
              name="CHANNEL_AWJ"/>
            <MappedDimension
              name="CHANNEL_AWJ_NEW_CHANNEL_PRIMARY_CHANNEL"/>
          </CubeDimensionalityMap>
        </CubeMap>
    ...
        <Organization>
          <AWCubeOrganization
    ...
            <AW
              name="GLOBAL_AWJ_NEW"/>
          </AWCubeOrganization>
        </Organization>
    ...
        <Dimensionality
          name="CHANNEL_AWJ"
          ETKeyColumnname="CHANNEL_AWJ">
          <Dimension
            name="CHANNEL_AWJ_NEW"/>
        </Dimensionality>
      </Cube>

      <StandardDimension
        name="CHANNEL_AWJ_NEW"
        ETViewname="CHANNEL_AWJ_VIEW"
    ...
        <Organization>
          <AWPrimaryDimensionOrganization
    ...
          >
    ...
            <AW
              name="GLOBAL_AWJ_NEW"/>
          </AWPrimaryDimensionOrganization>
        </Organization>
    ...
      </StandardDimension>
    </Metadata>

------------------------------------------------------------------------

Copyright © 2002, 2018, Oracle. All rights reserved.
