## A GeoRaster Metadata XML Schema

This appendix provides the XML schema definition that is used for GeoRaster metadata.

The following is the definition of the GeoRaster metadata XML schema. (You can also see this definition by querying the SDO_GEOR_XMLSCHEMA_TABLE table, which is described in [GeoRaster XML Schema](georaster-datatypes.md).)

    <?xml version="1.0" encoding="UTF-8"?>
    <!-- Oracle GeoRaster Metadata Schema -->
    <xsd:schema targetNamespace="http://xmlns.oracle.com/spatial/georaster" xmlns="http://xmlns.oracle.com/spatial/georaster" xmlns:xsd="http://www.w3.org/2001/XMLSchema" elementFormDefault="qualified" version="0.0">
    <xsd:annotation>
      <xsd:documentation>====================================================
      This is the XML Schema defining the metadata of Oracle GeoRaster object type
      It consists of two parts: data type definitions and its element content
         Part 1: Data Types
         Part 1.1: Data Types for Object Info
         Part 1.2: Data Types for Raster Info
         Part 1.3: Data Types for Spatial-Temporal-Band Reference Systems
         Part 1.3.1: Data Types for Raster Spatial Reference Systems
         Part 1.3.2: Data Types for Raster Temporal Reference Systems
         Part 1.3.3: Data Types for Raster Band Reference Systems
         Part 1.4: Data Types for Layer Metadata
         Part 2: GeoRaster Metadata Elements or Content Structure
         =============================================================
        </xsd:documentation>
      </xsd:annotation>
    <xsd:annotation>
      <xsd:documentation> ===============================================
      Part 1:      Data Types
      ================================================
      </xsd:documentation>
      </xsd:annotation>
    <xsd:annotation>
      <xsd:documentation> ==============================
      Part 1.1: Data Types for Object Info
       =============================
       </xsd:documentation>
    </xsd:annotation>
    <xsd:complexType name="objectDescriptionType">
      <xsd:sequence>
          <xsd:element name="rasterType" type="xsd:integer"/>
          <xsd:element name="ID" type="xsd:string" minOccurs="0"/>
          <xsd:element name="description" type="xsd:string" minOccurs="0" maxOccurs="unbounded"/>
          <xsd:element name="majorVersion" type="xsd:string" minOccurs="0"/>
          <xsd:element name="minorVersion" type="xsd:string" minOccurs="0"/>
          <xsd:element name="isBlank" type="xsd:boolean" default="false"/>
          <xsd:element name="blankCellValue" type="xsd:double" minOccurs="0"/>
          <xsd:element name="defaultRed" type="xsd:positiveInteger" minOccurs="0"/>
          <xsd:element name="defaultGreen" type="xsd:positiveInteger" minOccurs="0"/>

          <xsd:element name="defaultBlue" type="xsd:positiveInteger" minOccurs="0"/>

          <xsd:element name="defaultAlpha" type="xsd:positiveInteger" minOccurs="0"/>

          <xsd:element name="defaultPyramidLevel" type="xsd:integer" minOccurs="0"/>
          <xsd:any minOccurs="0" maxOccurs="unbounded"/>
        </xsd:sequence>
      </xsd:complexType>
      <xsd:annotation>
        <xsd:documentation> ==============================
        Part 1.2: Data Types for Raster Info
        ==============================
        </xsd:documentation>
      </xsd:annotation>
      <xsd:simpleType name="cellRepresentationType">
        <xsd:restriction base="xsd:string">
          <xsd:enumeration value="POINT"/>
          <xsd:enumeration value="SEGMENT"/>
          <xsd:enumeration value="TRIANGLE"/>
          <xsd:enumeration value="SQUARE"/>
          <xsd:enumeration value="RECTANGLE"/>
          <xsd:enumeration value="CUBE"/>
          <xsd:enumeration value="TETRAHEDRON"/>
          <xsd:enumeration value="HEXAHEDRON"/>
          <xsd:enumeration value="UNDEFINED"/>
        </xsd:restriction>
      </xsd:simpleType>
      <xsd:simpleType name="cellDepthType">
        <xsd:restriction base="xsd:string">
          <xsd:enumeration value="1BIT"/>
          <xsd:enumeration value="2BIT"/>
          <xsd:enumeration value="4BIT"/>
          <xsd:enumeration value="8BIT_U"/>
          <xsd:enumeration value="8BIT_S"/>
          <xsd:enumeration value="16BIT_U"/>
          <xsd:enumeration value="16BIT_S"/>
          <xsd:enumeration value="32BIT_U"/>
          <xsd:enumeration value="32BIT_S"/>
          <xsd:enumeration value="32BIT_REAL"/>
          <xsd:enumeration value="64BIT_REAL"/>
          <xsd:enumeration value="64BIT_COMPLEX"/>
          <xsd:enumeration value="128BIT_COMPLEX"/>
        </xsd:restriction>
      </xsd:simpleType>
      <xsd:simpleType name="supportedDimensionNumber">
        <xsd:restriction base="xsd:integer">
          <xsd:minInclusive value="2"/>
          <xsd:maxInclusive value="3"/>
        </xsd:restriction>
      </xsd:simpleType>
      <xsd:simpleType name="cellDimensionType">
        <xsd:annotation>
          <xsd:documentation>
          The "Band" dimension can be treated as any other semantic dimension
          or any "Layer" if not remote sensing imagery or photographs
          </xsd:documentation>
        </xsd:annotation>
        <xsd:restriction base="xsd:string">
          <xsd:enumeration value="ROW"/>
          <xsd:enumeration value="COLUMN"/>
          <xsd:enumeration value="VERTICAL"/>
          <xsd:enumeration value="BAND"/>
          <xsd:enumeration value="TEMPORAL"/>
        </xsd:restriction>
      </xsd:simpleType>
      <xsd:complexType name="cellDimensionSizeType">
        <xsd:sequence>
          <xsd:element name="size" type="xsd:positiveInteger" default="1"/>
        </xsd:sequence>
        <xsd:attribute name="type" type="cellDimensionType" use="required"/>
      </xsd:complexType>
      <xsd:complexType name="cellCoordinateType">
        <xsd:sequence>
          <xsd:element name="row" type="xsd:integer" default="0"/>
          <xsd:element name="column" type="xsd:integer" default="0"/>
          <xsd:element name="vertical" type="xsd:integer" minOccurs="0"/>
          <xsd:element name="band" type="xsd:integer" minOccurs="0"/>
          <xsd:element name="temporal" type="xsd:integer" minOccurs="0"/>
          <xsd:any minOccurs="0" maxOccurs="unbounded"/>
        </xsd:sequence>
      </xsd:complexType>
      <xsd:simpleType name="compressionType">
        <xsd:restriction base="xsd:string">
          <xsd:enumeration value="NONE"/>
          <xsd:enumeration value="JPEG-F"/>
          <xsd:enumeration value="DEFLATE"/>
          <xsd:enumeration value="LT-MG2"/>
          <xsd:enumeration value="LT-MG3"/>
          <xsd:enumeration value="LT-JP2"/>
        </xsd:restriction>
      </xsd:simpleType>
      <xsd:simpleType name="compressionQuality">
        <xsd:restriction base="xsd:integer">
          <xsd:minInclusive value="0"/>
          <xsd:maxInclusive value="100"/>
        </xsd:restriction>
      </xsd:simpleType>
      <xsd:complexType name="compressionDescriptionType">
        <xsd:sequence>
          <xsd:element name="type" type="compressionType" default="NONE"/>
          <xsd:element name="quality" type="compressionQuality" minOccurs="0"/>
          <xsd:any minOccurs="0" maxOccurs="unbounded"/>
        </xsd:sequence>
      </xsd:complexType>
      <xsd:simpleType name="blockingType">
        <xsd:restriction base="xsd:string">
          <xsd:enumeration value="NONE"/>
          <xsd:enumeration value="REGULAR"/>
        </xsd:restriction>
      </xsd:simpleType>
      <xsd:complexType name="blockingDescriptionType">
        <xsd:sequence>
          <xsd:element name="type" type="blockingType" default="NONE"/>
          <xsd:element name="totalRowBlocks" type="xsd:positiveInteger" default="1"/>
          <xsd:element name="totalColumnBlocks" type="xsd:positiveInteger" default="1"/>
          <xsd:element name="totalBandBlocks" type="xsd:positiveInteger" default="1" minOccurs="0"/>
          <xsd:element name="rowBlockSize" type="xsd:positiveInteger"/>
          <xsd:element name="columnBlockSize" type="xsd:positiveInteger"/>
          <xsd:element name="bandBlockSize" type="xsd:positiveInteger" minOccurs="0"/>
          <xsd:any minOccurs="0" maxOccurs="unbounded"/>
        </xsd:sequence>
      </xsd:complexType>
      <xsd:simpleType name="cellInterleavingType">
        <xsd:restriction base="xsd:string">
          <xsd:enumeration value="BSQ"/>
          <xsd:enumeration value="BIL"/>
          <xsd:enumeration value="BIP"/>
        </xsd:restriction>
      </xsd:simpleType>
      <xsd:simpleType name="pyramidType">
        <xsd:restriction base="xsd:string">
          <xsd:enumeration value="NONE"/>
          <xsd:enumeration value="DECREASE"/>
          <xsd:enumeration value="INCREASE"/>
          <xsd:enumeration value="BIDIRECTION"/>
        </xsd:restriction>
      </xsd:simpleType>
      <xsd:simpleType name="resamplingType">
        <xsd:restriction base="xsd:string">
          <xsd:enumeration value="NN"/>
          <xsd:enumeration value="BILINEAR"/>
          <xsd:enumeration value="CUBIC"/>
          <xsd:enumeration value="AVERAGE4"/>
          <xsd:enumeration value="AVERAGE16"/>
          <xsd:enumeration value="BIQUADRATIC"/>
          <xsd:enumeration value="OTHER"/>
        </xsd:restriction>
      </xsd:simpleType>
      <xsd:complexType name="pyramidDescriptionType">
        <xsd:sequence>
          <xsd:element name="type" type="pyramidType" default="NONE"/>
          <xsd:element name="resampling" type="resamplingType" default="NN" minOccurs="0"/>
          <xsd:element name="maxLevel" type="xsd:nonNegativeInteger" default="0" minOccurs="0"/>
          <xsd:any minOccurs="0" maxOccurs="unbounded"/>
        </xsd:sequence>
      </xsd:complexType>
      <xsd:complexType name="rasterDescriptionType">
        <xsd:sequence>
          <xsd:element name="cellRepresentation" type="cellRepresentationType" default="UNDEFINED"/>
          <xsd:element name="cellDepth" type="cellDepthType" default="8BIT_U"/>
          <xsd:element name="NODATA" type="xsd:double" minOccurs="0"/>
          <xsd:element name="totalDimensions" type="supportedDimensionNumber" default="2"/>
          <xsd:element name="dimensionSize" type="cellDimensionSizeType" maxOccurs="5"/>
          <xsd:element name="ULTCoordinate" type="cellCoordinateType"/>
          <xsd:element name="blocking" type="blockingDescriptionType"/>
          <xsd:element name="interleaving" type="cellInterleavingType" default="BSQ"/>
          <xsd:element name="pyramid" type="pyramidDescriptionType"/>
          <xsd:element name="compression" type="compressionDescriptionType"/>
          <xsd:any minOccurs="0" maxOccurs="unbounded"/>
        </xsd:sequence>
      </xsd:complexType>
      <xsd:annotation>
        <xsd:documentation>===========================================================
        Part 1.3.1: Data Types for GeoRaster Spatial Reference System

        Spatial extent (footprint) is recorded as an attribute of GeoRaster object.
        ts type is SDO_GEOMETRY. So it is not included in the metadata
        The cell space coordinates are named as (row, column, vertical)
        The model space coordinates are named as (x, y, z)
        Spatial unit information is stored in the WKT of the specified SRID
        ============================================================
        </xsd:documentation>
      </xsd:annotation>
      <xsd:simpleType name="modelDimensionType">
        <xsd:annotation>
          <xsd:documentation>
          The following "S" means "Spectral" for remote sensing imagery. Any of X, Y,
          and Z can be horizontal or vertical or any other spatial direction
          (depending on user interpretation in "modelDimensionDescription").
          </xsd:documentation>
        </xsd:annotation>
        <xsd:restriction base="xsd:string">
          <xsd:enumeration value="X"/>
          <xsd:enumeration value="Y"/>
          <xsd:enumeration value="Z"/>
          <xsd:enumeration value="T"/>
          <xsd:enumeration value="S"/>
        </xsd:restriction>
      </xsd:simpleType>
      <xsd:complexType name="resolutionType">
        <xsd:sequence>
          <xsd:element name="resolution" type="xsd:double" default="1"/>
        </xsd:sequence>
        <xsd:attribute name="dimensionType" type="modelDimensionType" use="required"/>
      </xsd:complexType>
      <xsd:simpleType name="doubleNumberListType">
        <xsd:list itemType="xsd:double"/>
      </xsd:simpleType>
      <xsd:complexType name="polynomialType">
        <xsd:sequence>
          <xsd:element name="polynomialCoefficients" type="doubleNumberListType"/>
        </xsd:sequence>
        <xsd:attribute name="pType" type="xsd:nonNegativeInteger" use="optional" default="1"/>
        <xsd:attribute name="nVars" type="xsd:nonNegativeInteger" use="required"/>
        <xsd:attribute name="order" type="xsd:nonNegativeInteger" use="required"/>
        <xsd:attribute name="nCoefficients" type="xsd:nonNegativeInteger" use="required"/>
        <xsd:anyAttribute/>
      </xsd:complexType>
      <xsd:complexType name="rationalPolynomialType">
        <xsd:annotation>
          <xsd:documentation>
          row    =   pPolynomial(x, y, z) / qPolynomial(x, y, z)
          column =   rPolynomial(x, y, z) / sPolynomial(x, y, z)
          </xsd:documentation>
        </xsd:annotation>
        <xsd:sequence>
          <xsd:element name="pPolynomial" type="polynomialType"/>
          <xsd:element name="qPolynomial" type="polynomialType"/>
          <xsd:element name="rPolynomial" type="polynomialType"/>
          <xsd:element name="sPolynomial" type="polynomialType"/>
          <xsd:any minOccurs="0" maxOccurs="unbounded"/>
        </xsd:sequence>
        <xsd:attribute name="rowOff" type="xsd:double" use="required"/>
        <xsd:attribute name="columnOff" type="xsd:double" use="required"/>
        <xsd:attribute name="xOff" type="xsd:double" use="required"/>
        <xsd:attribute name="yOff" type="xsd:double" use="required"/>
        <xsd:attribute name="zOff" type="xsd:double" use="required"/>
        <xsd:attribute name="rowScale" type="xsd:double" use="required"/>
        <xsd:attribute name="columnScale" type="xsd:double" use="required"/>
        <xsd:attribute name="xScale" type="xsd:double" use="required"/>
        <xsd:attribute name="yScale" type="xsd:double" use="required"/>
        <xsd:attribute name="zScale" type="xsd:double" use="required"/>
        <xsd:attribute name="rowRMS" type="xsd:double" use="optional"/>
        <xsd:attribute name="columnRMS" type="xsd:double" use="optional"/>
        <xsd:attribute name="totalRMS" type="xsd:double" use="optional"/>
        <xsd:attribute name="xRMS" type="xsd:double" use="optional"/>
        <xsd:attribute name="yRMS" type="xsd:double" use="optional"/>
        <xsd:attribute name="zRMS" type="xsd:double" use="optional"/>
        <xsd:attribute name="modelTotalRMS" type="xsd:double" use="optional"/>
        <xsd:anyAttribute/>
      </xsd:complexType>
      <xsd:annotation>
        <xsd:documentation>
        The following types and definitions are for GCP support. It stores
        GCP collection for the GeoRaster object. It also optionally specify
        the Functional Fitting method for generating FFM using the GCP collection.
        cellDimension can 2 or 3 (only 2 is supported in current release).
        modelDimension can be 2, 3, -2, -3. cellCoordinate must be (row, column)
        in current release.
        modelCoordinate must be (X, Y) or (X, Y, Z) in current release.
        </xsd:documentation>
      </xsd:annotation>
      <xsd:simpleType name="gcpPointType">
        <xsd:restriction base="xsd:string">
          <xsd:enumeration value="ControlPoint"/>
          <xsd:enumeration value="CheckPoint"/>
        </xsd:restriction>
      </xsd:simpleType>
      <xsd:simpleType name="gcpPointStatusType">
        <xsd:restriction base="xsd:string">
          <xsd:enumeration value="Measured"/>
          <xsd:enumeration value="Removed"/>
          <xsd:enumeration value="Estimated"/>
          <xsd:enumeration value="Validated"/>
          <xsd:enumeration value="Invalid"/>
        </xsd:restriction>
      </xsd:simpleType>
      <xsd:complexType name="GCPType">
        <xsd:attribute name="ID" type="xsd:string" use="optional"/>
        <xsd:attribute name="description" type="xsd:string" use="optional"/>
         <xsd:attribute name="type" type="gcpPointType" use="required"/>
        <xsd:attribute name="cellDimension" type="xsd:nonNegativeInteger" use="required"/>
        <xsd:attribute name="row" type="xsd:double" default="0" />
        <xsd:attribute name="column" type="xsd:double" default="0" />
        <xsd:attribute name="vertical" type="xsd:integer" use="optional"/>
        <xsd:attribute name="modelDimension" type="xsd:nonNegativeInteger" use="required"/>
        <xsd:attribute name="X" type="xsd:double" default="0"/>
        <xsd:attribute name="Y" type="xsd:double" default="0"/>
        <xsd:attribute name="Z" type="xsd:double" use="optional"/>
        <xsd:attribute name="xRMS" type="xsd:double" use="optional"/>
        <xsd:attribute name="yRMS" type="xsd:double" use="optional"/>
        <xsd:attribute name="zRMS" type="xsd:double" use="optional"/>
        <xsd:attribute name="status" type="gcpPointStatusType" use="optional"/>
        <xsd:anyAttribute/>
      </xsd:complexType>
      <xsd:simpleType name="FFMethodType">
                <xsd:restriction base="xsd:string">
                    <xsd:enumeration value="Affine"/>
                    <xsd:enumeration value="QuadraticPolynomial"/>
                    <xsd:enumeration value="CubicPolynomial"/>
                    <xsd:enumeration value="DLT"/>
                    <xsd:enumeration value="QuadraticRational"/>
                    <xsd:enumeration value="RPC"/>
               </xsd:restriction>
            </xsd:simpleType>
      <xsd:complexType name="GCPGeoreferenceType">
        <xsd:sequence>
          <xsd:element name="gcp" type="GCPType" minOccurs="0" maxOccurs="unbounded"/>
        </xsd:sequence>
        <xsd:attribute name="FFMethod" type="FFMethodType" use="optional"/>
      </xsd:complexType>
      <xsd:simpleType name="rasterSpatialReferenceModelType">
        <xsd:restriction base="xsd:string">
          <xsd:enumeration value="RigorousModel"/>
          <xsd:enumeration value="StoredFunction"/>
          <xsd:enumeration value="FunctionalFitting"/>
        </xsd:restriction>
      </xsd:simpleType>
      <xsd:complexType name="rasterSpatialReferenceSystemType">
        <xsd:sequence>
          <xsd:element name="isReferenced" type="xsd:boolean" default="false"/>
          <xsd:element name="isRectified" type="xsd:boolean" minOccurs="0"/>
          <xsd:element name="isOrthoRectified" type="xsd:boolean" minOccurs="0"/>
          <xsd:element name="description" type="xsd:string" minOccurs="0"/>
          <xsd:element name="SRID" type="xsd:nonNegativeInteger" default="0"/>
          <xsd:element name="verticalSRID" type="xsd:integer" minOccurs="0"/>
          <xsd:element name="modelDimensionDescription" type="xsd:string" minOccurs="0"/>
          <xsd:element name="spatialResolution" type="resolutionType" minOccurs="0" maxOccurs="3"/>
          <xsd:element name="spatialTolerance" type="xsd:double" minOccurs="0"/>
          <xsd:element name="modelCoordinateLocation" minOccurs="0">
            <xsd:simpleType>
              <xsd:restriction base="xsd:string">
                <xsd:enumeration value="CENTER"/>
                <xsd:enumeration value="UPPERLEFT"/>
              </xsd:restriction>
            </xsd:simpleType>
          </xsd:element>
          <xsd:element name="modelType" type="rasterSpatialReferenceModelType"
             minOccurs="0" maxOccurs="3"/>
          <xsd:element name="polynomialModel" type="rationalPolynomialType"
             minOccurs="0"/>
          <xsd:choice minOccurs="0">
             <xsd:element name="gcpGeoreferenceModel" type="GCPGeoreferenceType"/>
               <xsd:element name="gcpTableName" type="xsd:string" minOccurs="0"/>
          </xsd:choice>
          <xsd:any minOccurs="0" maxOccurs="unbounded"/>
        </xsd:sequence>
      </xsd:complexType>
      <xsd:annotation>
        <xsd:documentation> =================================================
        Part 1.3.2: Data Types for GeoRaster Temporal Reference System

        The TRS will be modeled by formulas in the future.
        =================================================
        </xsd:documentation>
      </xsd:annotation>
      <xsd:complexType name="rasterTemporalReferenceSystemType">
        <xsd:sequence>
          <xsd:element name="isReferenced" type="xsd:boolean" default="false"/>
          <xsd:element name="description" type="xsd:string" minOccurs="0"/>
          <xsd:element name="beginDateTime" type="xsd:dateTime" minOccurs="0"/>
          <xsd:element name="endDateTime" type="xsd:dateTime" minOccurs="0"/>
          <xsd:element name="temporalResolutionDescription" type="xsd:string" minOccurs="0"/>
          <xsd:any minOccurs="0" maxOccurs="unbounded"/>
        </xsd:sequence>
      </xsd:complexType>
      <xsd:annotation>
        <xsd:documentation> ==================================================
        Part 1.3.3: Data Types for GeoRaster Band Reference System

        For multispectral remote sensing images, each band is optionally
        described in the layerDescriptionType.
        The BRS is modeled by formulas for hyperspectral imagery
        based on number of spectral segments, min and max wavelength
        and number of bands for each segment.
        Detailed radiometric info will be added in the future.
        =====================================================
        </xsd:documentation>
      </xsd:annotation>
      <xsd:simpleType name="wavelengthUnit">
        <xsd:restriction base="xsd:string">
          <xsd:enumeration value="METER"/>
          <xsd:enumeration value="MILLIMETER"/>
          <xsd:enumeration value="MICROMETER"/>
          <xsd:enumeration value="NANOMETER"/>
        </xsd:restriction>
      </xsd:simpleType>
      <xsd:complexType name="extentType">
        <xsd:sequence>
          <xsd:element name="min" type="xsd:double"/>
          <xsd:element name="max" type="xsd:double"/>
        </xsd:sequence>
      </xsd:complexType>
      <xsd:complexType name="segmentationDataType">
        <xsd:sequence>
          <xsd:element name="totalSegNumber" type="xsd:positiveInteger" default="1"/>
          <xsd:element name="firstSegNumber" type="xsd:integer" default="1"/>
          <xsd:element name="extent" type="extentType"/>
        </xsd:sequence>
      </xsd:complexType>
      <xsd:complexType name="bandReferenceType">
        <xsd:sequence>
          <xsd:element name="bands" type="segmentationDataType" minOccurs="0" maxOccurs="unbounded"/>
          <xsd:any minOccurs="0" maxOccurs="unbounded"/>
        </xsd:sequence>
      </xsd:complexType>
      <xsd:complexType name="rasterBandReferenceSystemType">
        <xsd:sequence>
          <xsd:element name="isReferenced" type="xsd:boolean" default="false"/>
          <xsd:element name="description" type="xsd:string" minOccurs="0"/>
          <xsd:element name="radiometricResolutionDescription" type="xsd:string" minOccurs="0"/>
          <xsd:element name="spectralUnit" type="wavelengthUnit" default="MICROMETER"/>
          <xsd:element name="spectralTolerance" type="xsd:double" minOccurs="0"/>
          <xsd:element name="spectralResolutionDescription" type="xsd:string" minOccurs="0"/>
          <xsd:element name="minSpectralResolution" type="resolutionType" minOccurs="0"/>
          <xsd:element name="spectralExtent" type="extentType"/>
          <xsd:element name="bandReference" type="bandReferenceType" minOccurs="0"/>
          <xsd:any minOccurs="0" maxOccurs="unbounded"/>
        </xsd:sequence>
      </xsd:complexType>
      <xsd:annotation>
        <xsd:documentation> ====================================================
        Part 1.4: Data Types for Layer Metadata

        For each sub-layer the layerNumber is a positive integer, i.e., layers are
        logically numbered from 1 to n if the size of the specified layerDimension is
        n. The layerDimensionOrdinate of each sublayer must be in the range of the
        dimension and must be in the order of band ordinates.
        For objectLayer, the layerNumber should be 0 but its layerDimensionOrdinate
        is not used.
        =======================================================
        </xsd:documentation>
      </xsd:annotation>
            <xsd:complexType name="NODATAType">
              <xsd:sequence>
                <xsd:element name="value" type="xsd:double" minOccurs="0" maxOccurs="unbounded"/>
                <xsd:element name="range" type="extentType" minOccurs="0" maxOccurs="unbounded"/>
                <xsd:element name="mask" type="xsd:boolean" minOccurs="0"/>
                <xsd:any minOccurs="0" maxOccurs="unbounded"/>
              </xsd:sequence>
            </xsd:complexType>
      <xsd:complexType name="scalingFunctionType">
        <xsd:annotation>
          <xsd:documentation>
                             value = (a0 + a1 * cellValue)  /  (b0 + b1 * cellValue)
                      </xsd:documentation>
        </xsd:annotation>
        <xsd:sequence>
          <xsd:element name="a0" type="xsd:double" default="1"/>
          <xsd:element name="a1" type="xsd:double" default="0"/>
          <xsd:element name="b0" type="xsd:double" default="1"/>
          <xsd:element name="b1" type="xsd:double" default="0"/>
          <xsd:any minOccurs="0" maxOccurs="unbounded"/>
        </xsd:sequence>
      </xsd:complexType>
      <xsd:simpleType name="binType">
        <xsd:annotation>
          <xsd:documentation>
          LINEAR bin function:
          binNumber = numbins * (cellValue - min) / (max - min) + firstBinNumber
          if (binNumber less than 0) binNumber =  firstBinNumber
          if (binNumber greater than or equal to numbins) binNumber = numbins + firstBinNumber - 1
          LOGARITHM bin function:
          binNumber = numbins * (ln (1.0 + ((cellValue - min)/(max - min)))/ ln (2.0)) + firstBinNumber
          if (binNumber less than 0) binNumber =  firstBinNumber
          if (binNumber greater than or equal to numbins) binNumber = numbins + firstBinNumber - 1
          EXPLICIT bin function means explicit (or direct) value (or value range)
          for each bin and it will be stored in a table
          </xsd:documentation>
        </xsd:annotation>
        <xsd:restriction base="xsd:string">
          <xsd:enumeration value="LINEAR"/>
          <xsd:enumeration value="LOGARITHM"/>
          <xsd:enumeration value="EXPLICIT"/>
        </xsd:restriction>
      </xsd:simpleType>
      <xsd:complexType name="binFunctionType">
        <xsd:annotation>
          <xsd:documentation>
          The MAX and MIN in statistic dataset will be used if they are not provided
          here. binTableName is used by EXPLICIT type only.
          </xsd:documentation>
        </xsd:annotation>
        <xsd:sequence>
          <xsd:choice>
            <xsd:element name="binFunctionData" type="segmentationDataType"/>
            <xsd:element name="binTableName" type="xsd:string"/>
            <xsd:any minOccurs="0" maxOccurs="unbounded"/>
          </xsd:choice>
        </xsd:sequence>
        <xsd:attribute name="type" type="binType" use="required"/>
      </xsd:complexType>
      <xsd:complexType name="rectangularWindowType">
        <xsd:sequence>
          <xsd:element name="origin" type="cellCoordinateType"/>
          <xsd:element name="rowHeight" type="xsd:positiveInteger"/>
          <xsd:element name="columnWidth" type="xsd:positiveInteger"/>
          <xsd:any minOccurs="0" maxOccurs="unbounded"/>
        </xsd:sequence>
      </xsd:complexType>
      <xsd:complexType name="cellCountType">
        <xsd:attribute name="value" type="xsd:double" use="required"/>
        <xsd:attribute name="count" type="xsd:nonNegativeInteger" use="required"/>
        <xsd:anyAttribute/>
      </xsd:complexType>
      <xsd:complexType name="rasterCountType">
        <xsd:sequence>
          <xsd:element name="cell" type="cellCountType" maxOccurs="unbounded"/>
        </xsd:sequence>
      </xsd:complexType>
      <xsd:complexType name="histogramType">
        <xsd:sequence>
          <xsd:choice>
            <xsd:element name="counts" type="rasterCountType"/>
            <xsd:element name="tableName" type="xsd:string"/>
          </xsd:choice>
        </xsd:sequence>
      </xsd:complexType>
      <xsd:complexType name="statisticDatasetType">
        <xsd:sequence>
          <xsd:element name="samplingFactor" type="xsd:positiveInteger" default="1"/>
          <xsd:element name="samplingWindow" type="rectangularWindowType" minOccurs="0"/>
          <xsd:element name="MIN" type="xsd:double"/>
          <xsd:element name="MAX" type="xsd:double"/>
          <xsd:element name="MEAN" type="xsd:double"/>
          <xsd:element name="MEDIAN" type="xsd:double"/>
          <xsd:element name="MODEVALUE" type="xsd:double"/>
          <xsd:element name="STD" type="xsd:double"/>
          <xsd:element name="histogram" type="histogramType" minOccurs="0"/>
          <xsd:any minOccurs="0" maxOccurs="unbounded"/>
        </xsd:sequence>
      </xsd:complexType>
      <xsd:complexType name="cellGrayType">
        <xsd:attribute name="value" type="xsd:double" use="required"/>
        <xsd:attribute name="gray" type="xsd:integer" use="required"/>
        <xsd:anyAttribute/>
      </xsd:complexType>
      <xsd:complexType name="rasterGrayType">
        <xsd:sequence>
          <xsd:element name="cell" type="cellGrayType" maxOccurs="unbounded"/>
        </xsd:sequence>
      </xsd:complexType>
      <xsd:complexType name="grayScaleType">
        <xsd:sequence>
          <xsd:choice>
            <xsd:element name="grays" type="rasterGrayType"/>
            <xsd:element name="tableName" type="xsd:string"/>
          </xsd:choice>
        </xsd:sequence>
      </xsd:complexType>
      <xsd:complexType name="cellPseudoColorType">
        <xsd:attribute name="value" type="xsd:double" use="required"/>
        <xsd:attribute name="red" type="xsd:integer" use="required"/>
        <xsd:attribute name="green" type="xsd:integer" use="required"/>
        <xsd:attribute name="blue" type="xsd:integer" use="required"/>
        <xsd:attribute name="alpha" type="xsd:double" use="optional"/>
        <xsd:anyAttribute/>
      </xsd:complexType>
      <xsd:complexType name="rasterPseudoColorType">
        <xsd:sequence>
          <xsd:element name="cell" type="cellPseudoColorType" maxOccurs="unbounded"/>
        </xsd:sequence>
      </xsd:complexType>
      <xsd:complexType name="colorMapType">
        <xsd:sequence>
          <xsd:choice>
            <xsd:element name="colors" type="rasterPseudoColorType"/>
            <xsd:element name="tableName" type="xsd:string"/>
          </xsd:choice>
        </xsd:sequence>
      </xsd:complexType>
      <xsd:complexType name="layerType">
        <xsd:sequence>
          <xsd:element name="layerNumber" type="xsd:nonNegativeInteger"/>
          <xsd:element name="layerDimensionOrdinate" type="xsd:integer"/>
          <xsd:element name="layerID" type="xsd:string"/>
          <xsd:element name="description" type="xsd:string" minOccurs="0" maxOccurs="unbounded"/>
                            <xsd:element name="bitmapMask" type="xsd:boolean" minOccurs="0" default="false"/>
                            <xsd:element name="NODATA" type="NODATAType" minOccurs="0"/>
          <xsd:element name="scalingFunction" type="scalingFunctionType" minOccurs="0"/>
          <xsd:element name="binFunction" type="binFunctionType" minOccurs="0"/>
          <xsd:element name="statisticDataset" type="statisticDatasetType" minOccurs="0"/>
          <xsd:element name="grayScale" type="grayScaleType" minOccurs="0"/>
          <xsd:element name="colorMap" type="colorMapType" minOccurs="0"/>
          <xsd:element name="vatTableName" type="xsd:string" minOccurs="0"/>
          <xsd:any minOccurs="0" maxOccurs="unbounded"/>
        </xsd:sequence>
      </xsd:complexType>
      <xsd:complexType name="layerDescriptionType">
        <xsd:sequence>
          <xsd:element name="layerDimension" type="cellDimensionType" default="BAND"/>
          <xsd:element name="objectLayer" type="layerType" minOccurs="0"/>
          <xsd:element name="subLayer" type="layerType" minOccurs="0" maxOccurs="unbounded"/>
          <xsd:any minOccurs="0" maxOccurs="unbounded"/>
        </xsd:sequence>
      </xsd:complexType>
      <xsd:annotation>
        <xsd:documentation> =======================================================
        Part 2: Metadata Elements / Content Structure of Oracle GeoRaster Object
        ==========================================================
        </xsd:documentation>
      </xsd:annotation>
      <xsd:element name="georasterMetadata">
        <xsd:complexType>
          <xsd:sequence>
            <xsd:element name="objectInfo" type="objectDescriptionType"/>
            <xsd:element name="rasterInfo" type="rasterDescriptionType"/>
            <xsd:element name="spatialReferenceInfo" type="rasterSpatialReferenceSystemType" minOccurs="0"/>
            <xsd:element name="temporalReferenceInfo" type="rasterTemporalReferenceSystemType" minOccurs="0"/>
            <xsd:element name="bandReferenceInfo" type="rasterBandReferenceSystemType" minOccurs="0"/>
            <xsd:element name="layerInfo" type="layerDescriptionType" maxOccurs="unbounded"/>
            <xsd:element name="sourceInfo" type="xsd:string" minOccurs="0" maxOccurs="unbounded"/>
            <xsd:any minOccurs="0" maxOccurs="unbounded"/>
          </xsd:sequence>
        </xsd:complexType>
      </xsd:element>
    </xsd:schema>
