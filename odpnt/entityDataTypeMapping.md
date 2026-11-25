This section describes the default number mapping behavior and how to customize it for your application. You can configure a custom mapping in the .NET configuration file to override the default mapping for each Oracle `NUMBER(p,0)`, which represents integer values.

Oracle `NUMBER` data types that represent integers do not have a matching .NET integer data type with exactly the same range of acceptable values. ODP.NET uses a default mapping that ensures any .NET integer type values can be stored within the Oracle database without requiring custom data type mapping. However, it is possible that Oracle `NUMBER(p,0)` column data can be larger than what a .NET data type can hold when retrieving values from the database.

For example, in Entity Framework 6, Oracle `NUMBER(3,0)` has a default mapping to .NET Byte. Oracle `NUMBER(3,0)` can store a value up to `999`, while a .NET `BYTE` can store up to the value of `255`. If you expect the Oracle data to exceed `255`, modify the mapping to a larger numeric data type, such as a .NET `Int16`. Setting up this custom mapping allows you to consume the data in .NET without encountering an error. When such a custom mapping is used, be cautious not to insert a .NET `Int16` value beyond what an Oracle `NUMBER(3,0)` column can hold. Trying to insert `Int16.MaxValue` (i.e. `32,767`) into a `NUMBER(3,0)` column will cause an Oracle Database error.

### Entity Framework 5 and Earlier Mapping and Customization

Example 4-1 shows an ODP.NET, Unmanaged Driver sample `app.config` file that uses custom mapping to map the `Number(1,0)` Oracle data type to the `bool` EDM type. For example, `Number(1,0)`, which is mapped to `Int16` by default, can be custom mapped to the .NET `Bool` or .NET `Byte` type. This example maps `Number(3,0)` to byte, and sets the maximum precisions for the `Int16`, `Int32`, and `Int64` data types to `4`, `9`, and `18` respectively.

Example 4-2 shows the same changes as Example 4-1, but using the traditional ODP.NET, Unmanaged Driver `app.config` format.

Example 4-3 shows a ODP.NET, Managed Driver sample `app.config` file.

Example 4-1, Example 4-2, and Example 4-3 customizes the mappings as follows:

| Oracle Type                      | Default EDM Type | Custom EDM Type |
|:---------------------------------|:-----------------|:----------------|
| `Number(1,0)`                    | `Int16`          | `bool`          |
| `Number(2,0)` to `Number(3,0)`   | `Int16`          | `byte`          |
| `Number(4,0)`                    | `Int16`          | `Int16`         |
| `Number(5,0)`                    | `Int16`          | `Int32`         |
| `Number(6,0)` to `Number(9,0)`   | `Int32`          | `Int32`         |
| `Number(10,0)`                   | `Int32`          | `Int64`         |
| `Number(11,0)` to `Number(18,0)` | `Int64`          | `Int64`         |
| `Number(19,0)`                   | `Int64`          | `Decimal`       |

Custom mapping configures the maximum precision of the Oracle `Number` type that would map to the .NET/EDM type. So, for example, the preceding custom application configuration file configures ODP.NET to map `Number(10,0)` through `Number(18,0)` to `Int64`, as opposed to the default range of `Number(11,0) `through `Number(19,0)` for `Int64`.

**Note:**

- Custom mapping does not require you to map all the .NET/EDM types. For example, if custom mapping is required just for `Int16`, then having a single entry for `Int16` is sufficient. Default mapping gets used for the other types.

- When using Model First, a `Byte` attribute is mapped to `Number(3,0)` by default. However, when a model is generated for a `Number(3,0)` column, it gets mapped to `Int16` by default unless custom mapping for `Byte` is specified.

You must make sure that your mappings allow the data to fit within the range of the .NET/EDM type and the `Number(p, s) `type. If you select a .NET/EDM type with a range too small for the Oracle `Number` data, then errors will occur during data retrieval. Also, if you select a .NET/EDM type, and the corresponding data is too big for the Oracle `Number` column, then INSERTs and UPDATEs to the Oracle database will error out.

Example 4-1 First Sample ODP.NET, Unmanaged Driver Application Configuration File to Custom Map the Number (p,0) Data Type

    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <oracle.unmanageddataaccess.client>
        <version number="*">
           <edmMappings>
               <edmMapping dataType="number">
                   <add name="bool" precision="1"/>
                   <add name="byte" precision="3" />
                   <add name="int16" precision="4" />
                   <add name="int32" precision="9" />
                   <add name="int64" precision="18" />
              </edmMapping>
           </edmMappings>
         </version>
      </oracle.unmanageddataaccess.client>
    </configuration>

Example 4-2 Second Sample ODP.NET, Unmanaged Driver Application Configuration File to Custom Map the Number (p,0) Data Type

    <?xml version="1.0" encoding="utf-8"?>
    <configuration>
      <connectionStrings>
      </connectionStrings>
      <oracle.dataaccess.client>
        <settings>
          <add name="bool" value="edmmapping number(1,0)" />
          <add name="byte" value="edmmapping number(3,0)" />
          <add name="int16" value="edmmapping number(4,0)" />
          <add name="int32" value="edmmapping number(9,0)" />
          <add name="int64" value="edmmapping number(18,0)" />
        </settings>
      </oracle.dataaccess.client>
    </configuration>

Example 4-3 Sample ODP.NET, Managed Driver Application Configuration File to Custom Map the Number Data Type

    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <oracle.manageddataaccess.client>
        <version number="*">
           <edmMappings>
               <edmMapping dataType="number">
                   <add name="bool" precision="1"/>
                   <add name="byte" precision="3" />
                   <add name="int16" precision="4" />
                   <add name="int32" precision="9" />
                   <add name="int64" precision="18" />
              </edmMapping>
           </edmMappings>
         </version>
      </oracle.manageddataaccess.client>
    </configuration>

### Entity Framework 6 Mapping and Customization

ODP.NET 12.1.0.2 introduces a new .NET configuration setting format for both managed and unmanaged ODP.NET. This new setting format applies only for use with Entity Framework 6 and Entity Data Model mappings, including Code First, Database First, and Model First use cases. Developers can continue using the existing ODP.NET format for non-Entity Framework 6 applications.

This new format unifies how ODP.NET, Managed and Unmanaged Drivers sets their configuration values and supports auto-completion.

The following is an example of an `edmMappings` section for ODP.NET, Managed Driver:

    <oracle.manageddataaccess.client>
      <version number="*">
        <edmMappings>
          <edmNumberMapping>
            <add NETType="bool" MinPrecision="1" MaxPrecision="1" DBType="Number" />
            <add NETType="byte" MinPrecision="2" MaxPrecision="3" DBType="Number" />
            <add NETType="int16" MinPrecision="4" MaxPrecision="5" DBType="Number" />
            <add NETType="int32" MinPrecision="6" MaxPrecision="10" DBType="Number" />
            <add NETType="int64" MinPrecision="11" MaxPrecision="19" DBType="Number" />
          </edmNumberMapping>
        </edmMappings>
      </version>
    </oracle.manageddataaccess.client>

Where:

- `DBType` is the Oracle Database data type

- `NETType` is the .NET data type that the Oracle data type maps to

- `MinPrecision` is the minimum range the Oracle data type will map to the .NET type

- `MaxPrecision` is the maximum range the Oracle data type will map to the .NET type

The following is an example of an `edmmappings` section for ODP.NET, Unmanaged Driver. It is exactly same format as the managed driver with the exception of the opening and closing tags.

    <oracle.unmanageddataaccess.client>
      <version number="*">
        <edmMappings>
          <edmNumberMapping>
            <add NETType="bool" MinPrecision="1" MaxPrecision="1" DBType="Number" />
            <add NETType="byte" MinPrecision="2" MaxPrecision="3" DBType="Number" />
            <add NETType="int16" MinPrecision="4" MaxPrecision="5" DBType="Number" />
            <add NETType="int32" MinPrecision="6" MaxPrecision="10" DBType="Number" />
            <add NETType="int64" MinPrecision="11" MaxPrecision="19" DBType="Number" />
          </edmNumberMapping>
        </edmMappings>
      </version>
    </oracle.unmanageddataaccess.client>

#### New Default Mappings

For Entity Framework 6, ODP.NET 12.1.0.2 introduces new default mappings that apply to Code First, Database First, and Model First scenarios. These changes were necessary to support Code First interoperability.

- .NET `Booleans` map to Oracle `Number(1,0)` and vice-versa by default

- .NET `Bytes` map to Oracle `Number(2,0) `and` Number(3,0)` and vice-versa by default

This default behavior can be changed by providing an alternative data type mapping by configuring the section of the .NET config file.

### Data Type Mapping and Customization Process

To enable custom mapping, add the mapping information to the .NET config file prior to EDM creation.

If the EDM was created already before providing the mapping information, then you can modify the mappings either through the Visual Studio tools or manually. Using Visual Studio, go to the EDM Model Browser page. Right-click on the table(s) requiring new data type mapping and select Table Mapping from the pop-up menu. The Mapping Details window will appear usually at the bottom of your screen. Update Column Mappings as desired.

If you need to add or delete mappings, find the Type values in the CSDL mapping section of your project's existing EDMX file. Add or delete those Type values to the .NET data types you want the application to use. In the example below, the property name types for `BOOLCOL` and `BYTECOL` are added to the CSDL and mapped to Boolean and Byte, respectively.

Example Mapping Before CSDL Customization:

    <Property Name="INT16COL" Type="Int16" Nullable="false" />

Example Mapping After CSDL Customization:

    <Property Name="BOOLCOL" Type="Boolean" Nullable="false" />
    <Property Name="BYTECOL" Type="Byte" Nullable="false" />
    <Property Name="INT16COL" Type="Int16" Nullable="false" />

You can employ combinations of these customization possibilities depending on your planned mapping changes. If many tables and many columns require mapping changes, it is most efficient to delete the EDMX file and regenerate the data model. If a few tables and many columns require changes, then delete the affected tables, save the EDMX file, and select Update Model from Database... to include those tables again. If only a single table and one or two columns require changes, then modify the EDMX either manually or by using the Mapping Details window.

**Note:**

When using the EDM wizard to create a complex type from a function import, any custom EDM type mappings specified will not be applied automatically. The EDM wizard uses the default type mappings. Developers must then manually edit the resulting complex type. Developers begin this process after the complex type is generated. Any type declaration (field, property, constructor parameter, etc.) in the complex object which has an undesired type mapping, such as Decimal rather than Boolean, should be manually edited to the desired type.

### StoreGeneratedPattern Enumeration

The following sections describe the Identity attribute and the Virtual column.

#### Identity Attribute

Oracle Database 12c (12.1) and later versions support table or view Identity attribute columns. Oracle has three Identity attribute types. When the EDM wizard generates a data model from an Oracle Identity attribute-containing table or view, ODP.NET will set the value of `StoreGeneratedPattern` to `Identity` in the `.edmx` file for any of three Oracle Identity types. The Identity attribute-associated column will use the server-generated value during `INSERT`: hence, application developers no longer need to create a sequence nor trigger. If the .NET application attempts to set the Identity attribute itself, this value will be ignored.

For Oracle Database 11g Release 2 (11.2) and earlier versions that do not support Identity columns, application developers can manually set `StoreGeneratedPattern` to `Identity` in columns through the entity model designer Properties after model generation, then create an `INSERT` trigger. Depending on the data type, a sequence may not be necessary if a server function, such as `sys_guid()`, can generate the value for the column.

#### Virtual Column

Oracle Database 11g (11.1) and later versions can store expressions directly in base tables as Virtual columns, also known as Generated columns. Virtual columns cannot be inserted into or updated. ODP.NET will not automatically set `StoreGeneratedPattern` to `Computed` in the EF model for Virtual columns. To avoid errors, application developers need to add or change the value of `StoreGeneratedPattern` to `Computed` for Virtual columns after the model generation. Once done, Virtual columns are excluded from `INSERT`s and `UPDATE`s upon calling `SaveChanges()`.

### Resolving Compilation Errors When Using Custom Mapping

If the custom mapping in a .NET configuration file has changed, then regenerate the data model to solve compilation errors introduced by the changes.

Under certain scenarios, custom mapping may cause compilation errors when a project that uses custom mapping is loaded by Visual Studio. One specific scenario is when Visual Studio opens a project with an existing custom mapping that now generates errors when those errors did not exist before. You may use the following workaround for such scenarios:

1.  Open Visual Studio Help, About Microsoft Visual Studio. Click OK to exit the dialog box.

    Alternatively, open the to-be-used connection in Server Explorer.

2.  Compile the project again to eliminate the compilation errors.

### Mapping Boolean and Guid Parameters in Custom INSERT, UPDATE, and DELETE Stored Procedures

When using your custom `INSERT, UPDATE,` or `DELETE` stored procedure in Stored Procedure Mapping, the following error might occur:

`Error 2042: Parameter Mapping specified is not valid.`

This can happen if a `Number` parameter has been mapped to a `Boolean` attribute, or if a `RAW` parameter has been mapped to a `Guid` attribute.

The solution is to manually add `Precision="1"` for the `Number` parameter, and `MaxLength="16"` for the RAW parameter of your stored procedure in the SSDL.
