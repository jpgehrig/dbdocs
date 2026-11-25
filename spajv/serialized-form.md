Skip navigation links

- [Overview](overview-summary.md)
- Package
- Class
- [Tree](overview-tree.md)
- [Deprecated](deprecated-list.md)
- [Index](index-all.md)
- [Help](help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)

# Serialized Form

- ## Package oracle.spatial.geometry

  - ### Class [oracle.spatial.geometry.AbstractRTree.PairDebug](oracle/spatial/geometry/AbstractRTree.PairDebug.md) extends [Pair](oracle/spatial/geometry/Pair.md)\<[P](oracle/spatial/geometry/AbstractRTree.PairDebug.md),[Q](oracle/spatial/geometry/AbstractRTree.PairDebug.md)\> implements Serializable

    - ### Serialized Fields

      - #### pComment

            java.lang.String pComment

      - #### qComment

            java.lang.String qComment

  - ### Class [oracle.spatial.geometry.Chain.CenterPoint](oracle/spatial/geometry/Chain.CenterPoint.md) extends [JPoint2DD](oracle/spatial/geometry/JPoint2DD.md) implements Serializable

    serialVersionUID:
    1996381016013365072L

    - ### Serialized Fields

      - #### radius

            double radius

      - #### CUW

            boolean CUW

  - ### Class [oracle.spatial.geometry.CoordSysInfo](oracle/spatial/geometry/CoordSysInfo.md) extends java.lang.Object implements Serializable

    - ### Serialization Methods

      - #### readResolve

            protected java.lang.Object readResolve()
                                            throws java.io.ObjectStreamException

        Throws:
        `java.io.ObjectStreamException`

    - ### Serialized Fields

      - #### srid

            int srid

      - #### isGeodetic

            boolean isGeodetic

      - #### smax

            double smax

      - #### iflat

            double iflat

  - ### Class [oracle.spatial.geometry.DataException](oracle/spatial/geometry/DataException.md) extends java.lang.Exception implements Serializable

    - ### Serialized Fields

      - #### description

            java.lang.String description

      - #### detail

            java.lang.Throwable detail

  - ### Class [oracle.spatial.geometry.FastJGeometry](oracle/spatial/geometry/FastJGeometry.md) extends [JGeometry](oracle/spatial/geometry/JGeometry.md) implements Serializable

    - ### Serialized Fields

      - #### opStatus

            java.util.EnumMap<K extends java.lang.Enum<K>,V> opStatus

        The PPStatus of each preprocessable operation

      - #### tol

            double tol

      - #### opsSet

            java.util.EnumSet<E extends java.lang.Enum<E>> opsSet

      - #### ppInfo

            oracle.spatial.geometry.PointPolygon ppInfo

        Preprocessing information for point-in-polygon queries (null if preprocessing hasn't been done)

  - ### Class [oracle.spatial.geometry.J3D_Geometry](oracle/spatial/geometry/J3D_Geometry.md) extends [JGeometry](oracle/spatial/geometry/JGeometry.md) implements Serializable

    - ### Serialized Fields

      - #### solids1

            java.util.ArrayList<E> solids1

      - #### solids2

            java.util.ArrayList<E> solids2

      - #### solidHoles1

            java.util.ArrayList<E> solidHoles1

      - #### solidHoles2

            java.util.ArrayList<E> solidHoles2

      - #### surfs1

            java.util.ArrayList<E> surfs1

      - #### surfs2

            java.util.ArrayList<E> surfs2

      - #### surfHoles1

            java.util.ArrayList<E> surfHoles1

      - #### surfHoles2

            java.util.ArrayList<E> surfHoles2

      - #### belongingGeometry

            java.util.ArrayList<E> belongingGeometry

  - ### Class [oracle.spatial.geometry.JGeometry](oracle/spatial/geometry/JGeometry.md) extends java.lang.Object implements Serializable

    - ### Serialization Methods

      - #### readObject

            private void readObject(java.io.ObjectInputStream in)
                             throws java.io.IOException,
                                    java.lang.ClassNotFoundException

        required method for serialization support.
        Throws:
        `java.io.IOException`

        `java.lang.ClassNotFoundException`

      - #### writeObject

            private void writeObject(java.io.ObjectOutputStream out)
                              throws java.io.IOException

        required method for serialization support.
        Throws:
        `java.io.IOException`

    - ### Serialized Fields

      - #### gtype

            int gtype

      - #### linfo

            int linfo

      - #### srid

            int srid

      - #### sridCSI

            CoordSysInfo sridCSI

      - #### x

            double x

      - #### y

            double y

      - #### z

            double z

      - #### elemInfo

            int[] elemInfo

      - #### ordinates

            double[] ordinates

      - #### mbr

            double[] mbr

      - #### mer

            Mer mer

      - #### dim

            int dim

      - #### lttpH

            oracle.spatial.geometry.JGeometry.LT_transform lttpH

      - #### gtransH

            oracle.spatial.geometry.JGeometry.Gc_trans gtransH

  - ### Class [oracle.spatial.geometry.JPoint2DD](oracle/spatial/geometry/JPoint2DD.md) extends java.lang.Object implements Serializable

    serialVersionUID:
    -7599734575655966334L

    - ### Serialized Fields

      - #### x

            double x

      - #### y

            double y

  - ### Class [oracle.spatial.geometry.Mer](oracle/spatial/geometry/Mer.md) extends java.lang.Object implements Serializable

    - ### Serialized Fields

      - #### mer

            double[] mer

  - ### Class [oracle.spatial.geometry.Pair](oracle/spatial/geometry/Pair.md) extends java.lang.Object implements Serializable

    - ### Serialized Fields

      - #### p

            java.lang.Object p

      - #### q

            java.lang.Object q

  - ### Class [oracle.spatial.geometry.RStarTree](oracle/spatial/geometry/RStarTree.md) extends [AbstractRTree](oracle/spatial/geometry/AbstractRTree.md)\<[T](oracle/spatial/geometry/RStarTree.md) extends [RNode](oracle/spatial/geometry/RNode.md)\> implements Serializable

    - ### Serialized Fields

      - #### dim

            int dim

      - #### minFill

            int minFill

      - #### maxFill

            int maxFill

      - #### size

            int size

      - #### root

            oracle.spatial.geometry.RStarTree.RStarInternal<T extends RNode> root

      - #### rootReinserts

            long rootReinserts

      - #### rootSplits

            long rootSplits

      - #### nodesReinserted

            long nodesReinserted

      - #### nodesReinsertedSame

            long nodesReinsertedSame

      - #### nodesSplit

            long nodesSplit

      - #### nodesOverflowed

            long nodesOverflowed

      - #### assessSplitsCalls

            long assessSplitsCalls

- ## Package oracle.spatial.georaster

  - ### Class [oracle.spatial.georaster.GeoRasterException](oracle/spatial/georaster/GeoRasterException.md) extends java.lang.Exception implements Serializable

    - ### Serialized Fields

      - #### m_message

            java.lang.String m_message

- ## Package oracle.spatial.network

  - ### Class [oracle.spatial.network.GeometryMetadata](oracle/spatial/network/GeometryMetadata.md) extends java.lang.Object implements Serializable

    - ### Serialization Methods

      - #### readObject

            private void readObject(java.io.ObjectInputStream in)
                             throws java.lang.ClassNotFoundException,
                                    java.io.IOException

        Throws:
        `java.lang.ClassNotFoundException`

        `java.io.IOException`

      - #### writeObject

            private void writeObject(java.io.ObjectOutputStream out)
                              throws java.io.IOException

        Throws:
        `java.io.IOException`

    - ### Serialized Fields

      - #### p_owner

            java.lang.String p_owner

      - #### p_tableName

            java.lang.String p_tableName

      - #### p_columnName

            java.lang.String p_columnName

      - #### p_srid

            int p_srid

      - #### p_noOfDims

            int p_noOfDims

  - ### Class [oracle.spatial.network.NetworkDataException](oracle/spatial/network/NetworkDataException.md) extends java.lang.Exception implements Serializable

  - ### Class [oracle.spatial.network.SystemConstraint](oracle/spatial/network/SystemConstraint.md) extends java.lang.Object implements Serializable

    - ### Serialized Fields

      - #### p_network

            Network p_network

      - #### p_mustAvoidNodes

            java.util.Vector<E> p_mustAvoidNodes

      - #### p_mustAvoidLinks

            java.util.Vector<E> p_mustAvoidLinks

      - #### p_maxCost

            double p_maxCost

      - #### p_maxDistance

            double p_maxDistance

      - #### p_maxMBR

            MBR p_maxMBR

      - #### p_maxDepth

            int p_maxDepth

      - #### p_maxDuration

            double p_maxDuration

- ## Package oracle.spatial.network.lod

  - ### Class [oracle.spatial.network.lod.CategorizedUserDataImpl](oracle/spatial/network/lod/CategorizedUserDataImpl.md) extends java.lang.Object implements Serializable

    serialVersionUID:
    0L

    - ### Serialized Fields

      - #### userDataArray

            UserData[] userDataArray

  - ### Class [oracle.spatial.network.lod.LinkNotFoundException](oracle/spatial/network/lod/LinkNotFoundException.md) extends [LODNetworkException](oracle/spatial/network/lod/LODNetworkException.md) implements Serializable

  - ### Class [oracle.spatial.network.lod.LODNetworkException](oracle/spatial/network/lod/LODNetworkException.md) extends java.lang.Exception implements Serializable

    - ### Serialized Fields

      - #### errorCode

            int errorCode

  - ### Class [oracle.spatial.network.lod.MethodNotSupportedException](oracle/spatial/network/lod/MethodNotSupportedException.md) extends [LODNetworkException](oracle/spatial/network/lod/LODNetworkException.md) implements Serializable

  - ### Class [oracle.spatial.network.lod.NodeNotFoundException](oracle/spatial/network/lod/NodeNotFoundException.md) extends [LODNetworkException](oracle/spatial/network/lod/LODNetworkException.md) implements Serializable

  - ### Class [oracle.spatial.network.lod.UserDataImpl](oracle/spatial/network/lod/UserDataImpl.md) extends java.lang.Object implements Serializable

    serialVersionUID:
    -568596639057102910L

    - ### Serialized Fields

      - #### userDataArray

            java.lang.Object[] userDataArray

- ## Package oracle.spatial.network.lod.config

  - ### Class [oracle.spatial.network.lod.config.LODConfigException](oracle/spatial/network/lod/config/LODConfigException.md) extends [LODNetworkException](oracle/spatial/network/lod/LODNetworkException.md) implements Serializable

- ## Package oracle.spatial.network.nfe.expression

  - ### Class [oracle.spatial.network.nfe.expression.InvalidExpressionException](oracle/spatial/network/nfe/expression/InvalidExpressionException.md) extends java.lang.Exception implements Serializable

    serialVersionUID:
    1L

- ## Package oracle.spatial.network.nfe.io

  - ### Class [oracle.spatial.network.nfe.io.InvalidDBConnectionException](oracle/spatial/network/nfe/io/InvalidDBConnectionException.md) extends java.sql.SQLException implements Serializable

  - ### Class [oracle.spatial.network.nfe.io.NFEIOException](oracle/spatial/network/nfe/io/NFEIOException.md) extends java.lang.Exception implements Serializable

    - ### Serialized Fields

      - #### errorCode

            int errorCode

      - #### errorMsg

            java.lang.String errorMsg

- ## Package oracle.spatial.network.nfe.model.edit.undo

  - ### Class [oracle.spatial.network.nfe.model.edit.undo.FeatureElementPropertyChangedUndoableEdit](oracle/spatial/network/nfe/model/edit/undo/FeatureElementPropertyChangedUndoableEdit.md) extends [NFEAtomicUndoableEdit](oracle/spatial/network/nfe/model/edit/undo/NFEAtomicUndoableEdit.md) implements Serializable

    serialVersionUID:
    1L

    - ### Serialized Fields

      - #### previousValue

            java.lang.Object previousValue

      - #### newValue

            java.lang.Object newValue

      - #### featureElement

            NFEFeatureElement featureElement

      - #### propertyName

            java.lang.String propertyName

  - ### Class [oracle.spatial.network.nfe.model.edit.undo.FeatureElementsAddedUndoableEdit](oracle/spatial/network/nfe/model/edit/undo/FeatureElementsAddedUndoableEdit.md) extends [NFEAtomicUndoableEdit](oracle/spatial/network/nfe/model/edit/undo/NFEAtomicUndoableEdit.md) implements Serializable

    serialVersionUID:
    1L

    - ### Serialized Fields

      - #### featureElementsList

            java.util.Collection<E> featureElementsList

  - ### Class [oracle.spatial.network.nfe.model.edit.undo.FeatureElementsRemovedUndoableEdit](oracle/spatial/network/nfe/model/edit/undo/FeatureElementsRemovedUndoableEdit.md) extends [NFEAtomicUndoableEdit](oracle/spatial/network/nfe/model/edit/undo/NFEAtomicUndoableEdit.md) implements Serializable

    serialVersionUID:
    1L

    - ### Serialized Fields

      - #### featureElementsList

            java.util.Collection<E> featureElementsList

  - ### Class [oracle.spatial.network.nfe.model.edit.undo.FeaturePropertyChangedUndoableEdit](oracle/spatial/network/nfe/model/edit/undo/FeaturePropertyChangedUndoableEdit.md) extends [NFEAtomicUndoableEdit](oracle/spatial/network/nfe/model/edit/undo/NFEAtomicUndoableEdit.md) implements Serializable

    serialVersionUID:
    1L

    - ### Serialized Fields

      - #### previousValue

            java.lang.Object previousValue

      - #### newValue

            java.lang.Object newValue

      - #### feature

            NFEFeature feature

      - #### propertyName

            java.lang.String propertyName

  - ### Class [oracle.spatial.network.nfe.model.edit.undo.FeaturesAddedUndoableEdit](oracle/spatial/network/nfe/model/edit/undo/FeaturesAddedUndoableEdit.md) extends [NFEAtomicUndoableEdit](oracle/spatial/network/nfe/model/edit/undo/NFEAtomicUndoableEdit.md) implements Serializable

    serialVersionUID:
    1L

    - ### Serialized Fields

      - #### featuresList

            java.util.Collection<E> featuresList

  - ### Class [oracle.spatial.network.nfe.model.edit.undo.FeaturesRemovedUndoableEdit](oracle/spatial/network/nfe/model/edit/undo/FeaturesRemovedUndoableEdit.md) extends [NFEAtomicUndoableEdit](oracle/spatial/network/nfe/model/edit/undo/NFEAtomicUndoableEdit.md) implements Serializable

    serialVersionUID:
    1L

    - ### Serialized Fields

      - #### featuresList

            java.util.Collection<E> featuresList

  - ### Class [oracle.spatial.network.nfe.model.edit.undo.NetworkElementPropertyChangedUndoableEdit](oracle/spatial/network/nfe/model/edit/undo/NetworkElementPropertyChangedUndoableEdit.md) extends [NFEAtomicUndoableEdit](oracle/spatial/network/nfe/model/edit/undo/NFEAtomicUndoableEdit.md) implements Serializable

    serialVersionUID:
    1L

    - ### Serialized Fields

      - #### previousValue

            java.lang.Object previousValue

      - #### newValue

            java.lang.Object newValue

      - #### netElem

            NFENetworkElement netElem

      - #### propertyName

            java.lang.String propertyName

  - ### Class [oracle.spatial.network.nfe.model.edit.undo.NetworkElementsAddedUndoableEdit](oracle/spatial/network/nfe/model/edit/undo/NetworkElementsAddedUndoableEdit.md) extends [NFEAtomicUndoableEdit](oracle/spatial/network/nfe/model/edit/undo/NFEAtomicUndoableEdit.md) implements Serializable

    serialVersionUID:
    1L

    - ### Serialized Fields

      - #### netElems

            java.util.Collection<E> netElems

  - ### Class [oracle.spatial.network.nfe.model.edit.undo.NetworkElementsRemovedUndoableEdit](oracle/spatial/network/nfe/model/edit/undo/NetworkElementsRemovedUndoableEdit.md) extends [NFEAtomicUndoableEdit](oracle/spatial/network/nfe/model/edit/undo/NFEAtomicUndoableEdit.md) implements Serializable

    serialVersionUID:
    1L

    - ### Serialized Fields

      - #### netElems

            java.util.Collection<E> netElems

  - ### Class [oracle.spatial.network.nfe.model.edit.undo.NFEAtomicUndoableEdit](oracle/spatial/network/nfe/model/edit/undo/NFEAtomicUndoableEdit.md) extends javax.swing.undo.AbstractUndoableEdit implements Serializable

    serialVersionUID:
    1L

    - ### Serialized Fields

      - #### model

            NFEModel model

      - #### timeStamp

            long timeStamp

  - ### Class [oracle.spatial.network.nfe.model.edit.undo.NFEBlockUndoableEdit](oracle/spatial/network/nfe/model/edit/undo/NFEBlockUndoableEdit.md) extends javax.swing.undo.AbstractUndoableEdit implements Serializable

    serialVersionUID:
    1L

    - ### Serialized Fields

      - #### model

            NFEModel model

      - #### presentationName

            java.lang.String presentationName

      - #### threadId

            long threadId

      - #### uEdits

            java.util.List<E> uEdits

      - #### closeTime

            long closeTime

      - #### open

            boolean open

  - ### Class [oracle.spatial.network.nfe.model.edit.undo.RuleInstanceAddedUndoableEdit](oracle/spatial/network/nfe/model/edit/undo/RuleInstanceAddedUndoableEdit.md) extends [NFEAtomicUndoableEdit](oracle/spatial/network/nfe/model/edit/undo/NFEAtomicUndoableEdit.md) implements Serializable

    serialVersionUID:
    3815973576786856957L

    - ### Serialized Fields

      - #### ruleInstance

            NFERuleInstance ruleInstance

  - ### Class [oracle.spatial.network.nfe.model.edit.undo.RuleInstanceRelationAddedUndoableEdit](oracle/spatial/network/nfe/model/edit/undo/RuleInstanceRelationAddedUndoableEdit.md) extends [NFEAtomicUndoableEdit](oracle/spatial/network/nfe/model/edit/undo/NFEAtomicUndoableEdit.md) implements Serializable

    serialVersionUID:
    7188529939332698300L

    - ### Serialized Fields

      - #### ruleInstanceRel

            NFERuleInstanceRelation ruleInstanceRel

  - ### Class [oracle.spatial.network.nfe.model.edit.undo.RuleInstanceRelationRemovedUndoableEdit](oracle/spatial/network/nfe/model/edit/undo/RuleInstanceRelationRemovedUndoableEdit.md) extends [NFEAtomicUndoableEdit](oracle/spatial/network/nfe/model/edit/undo/NFEAtomicUndoableEdit.md) implements Serializable

    serialVersionUID:
    -953596146347239254L

    - ### Serialized Fields

      - #### ruleInstanceRel

            NFERuleInstanceRelation ruleInstanceRel

  - ### Class [oracle.spatial.network.nfe.model.edit.undo.RuleInstanceRemovedUndoableEdit](oracle/spatial/network/nfe/model/edit/undo/RuleInstanceRemovedUndoableEdit.md) extends [NFEAtomicUndoableEdit](oracle/spatial/network/nfe/model/edit/undo/NFEAtomicUndoableEdit.md) implements Serializable

    serialVersionUID:
    1075174444506434643L

    - ### Serialized Fields

      - #### ruleInstance

            NFERuleInstance ruleInstance

- ## Package oracle.spatial.network.nfe.model.event

  - ### Class [oracle.spatial.network.nfe.model.event.NFEEventDispatchException](oracle/spatial/network/nfe/model/event/NFEEventDispatchException.md) extends java.lang.Exception implements Serializable

    serialVersionUID:
    3430557187240545541L

    - ### Serialized Fields

      - #### failedDispatches

            java.lang.Object[] failedDispatches

  - ### Class [oracle.spatial.network.nfe.model.event.NFEModelEvent](oracle/spatial/network/nfe/model/event/NFEModelEvent.md) extends java.util.EventObject implements Serializable

    serialVersionUID:
    460503768944528635L

    - ### Serialized Fields

      - #### threadId

            long threadId

      - #### timestamp

            long timestamp

  - ### Class [oracle.spatial.network.nfe.model.event.NFEModelObjectEvent](oracle/spatial/network/nfe/model/event/NFEModelObjectEvent.md) extends [NFEModelEvent](oracle/spatial/network/nfe/model/event/NFEModelEvent.md) implements Serializable

    serialVersionUID:
    1246707907289056013L

    - ### Serialized Fields

      - #### modelObject

            java.lang.Object modelObject

  - ### Class [oracle.spatial.network.nfe.model.event.NFEModelObjectPropertyChangedEvent](oracle/spatial/network/nfe/model/event/NFEModelObjectPropertyChangedEvent.md) extends [NFEModelObjectEvent](oracle/spatial/network/nfe/model/event/NFEModelObjectEvent.md) implements Serializable

    serialVersionUID:
    1L

    - ### Serialized Fields

      - #### propertyName

            java.lang.String propertyName

      - #### previousValue

            java.lang.Object previousValue

  - ### Class [oracle.spatial.network.nfe.model.event.NFEModelObjectsEvent](oracle/spatial/network/nfe/model/event/NFEModelObjectsEvent.md) extends [NFEModelEvent](oracle/spatial/network/nfe/model/event/NFEModelEvent.md) implements Serializable

    serialVersionUID:
    1L

    - ### Serialized Fields

      - #### modelObjects

            java.util.Collection<E> modelObjects

      - #### modelObjectsClass

            java.lang.Class<T> modelObjectsClass

- ## Package oracle.spatial.network.nfe.model.spatial.interaction

  - ### Class [oracle.spatial.network.nfe.model.spatial.interaction.LineIntersectionList](oracle/spatial/network/nfe/model/spatial/interaction/LineIntersectionList.md) extends java.util.LinkedList\<[Intersection](oracle/spatial/network/nfe/model/spatial/interaction/Intersection.md)\<[E](oracle/spatial/network/nfe/model/spatial/interaction/LineIntersectionList.md)\>\> implements Serializable

    - ### Serialized Fields

      - #### element

            java.lang.Object element

      - #### line

            JGeometry line

      - #### tolerance

            double tolerance

      - #### distanceMap

            java.util.Map<K,V> distanceMap

      - #### addComparator

            java.util.Comparator<T> addComparator

      - #### searchComparator

            java.util.Comparator<T> searchComparator

- ## Package oracle.spatial.network.nfe.vis.maps.core

  - ### Class [oracle.spatial.network.nfe.vis.maps.core.LayerManagerEvent](oracle/spatial/network/nfe/vis/maps/core/LayerManagerEvent.md) extends javax.swing.event.ChangeEvent implements Serializable

    - ### Serialized Fields

      - #### type

            int type

      - #### layer

            Layer layer

      - #### oldPosition

            java.lang.Integer oldPosition

      - #### newPosition

            java.lang.Integer newPosition

      - #### tags

            java.util.TreeSet<E> tags

  - ### Class [oracle.spatial.network.nfe.vis.maps.core.MapCanvas](oracle/spatial/network/nfe/vis/maps/core/MapCanvas.md) extends javax.swing.JPanel implements Serializable

    - ### Serialized Fields

      - #### paintTime

            long paintTime

      - #### loop

            CoreLoop loop

      - #### eventManager

            EventManager eventManager

      - #### layerManager

            LayerManager layerManager

      - #### undoManager

            MapUndoManager undoManager

      - #### mapRegion

            MapRegion mapRegion

      - #### popUpMenu

            javax.swing.JPopupMenu popUpMenu

      - #### progressBar

            javax.swing.JProgressBar progressBar

      - #### progressRecord

            java.util.Hashtable<K,V> progressRecord

      - #### myCursor

            java.awt.Cursor myCursor

      - #### listenerList

            javax.swing.event.EventListenerList listenerList

  - ### Class [oracle.spatial.network.nfe.vis.maps.core.MapRegionEvent](oracle/spatial/network/nfe/vis/maps/core/MapRegionEvent.md) extends javax.swing.event.ChangeEvent implements Serializable

    - ### Serialized Fields

      - #### oldXFM

            java.awt.geom.AffineTransform oldXFM

      - #### newXFM

            java.awt.geom.AffineTransform newXFM

      - #### oldDataWindow

            java.awt.geom.Rectangle2D oldDataWindow

      - #### newDataWindow

            java.awt.geom.Rectangle2D newDataWindow

  - ### Class [oracle.spatial.network.nfe.vis.maps.core.MapUndoManager](oracle/spatial/network/nfe/vis/maps/core/MapUndoManager.md) extends javax.swing.undo.UndoManager implements Serializable

    - ### Serialized Fields

      - #### openBlocks

            int openBlocks

      - #### listenerList

            javax.swing.event.EventListenerList listenerList

      - #### undoORredoPerformed

            boolean undoORredoPerformed

  - ### Class [oracle.spatial.network.nfe.vis.maps.core.SelectionEvent](oracle/spatial/network/nfe/vis/maps/core/SelectionEvent.md) extends javax.swing.event.ChangeEvent implements Serializable

    - ### Serialized Fields

      - #### type

            int type

      - #### param

            java.lang.Object param

- ## Package oracle.spatial.network.nfe.vis.maps.index

  - ### Class [oracle.spatial.network.nfe.vis.maps.index.RTreeIndex](oracle/spatial/network/nfe/vis/maps/index/RTreeIndex.md) extends [AbstractSpatialIndex](oracle/spatial/network/nfe/vis/maps/index/AbstractSpatialIndex.md) implements Serializable

    serialVersionUID:
    65468421L

    - ### Serialized Fields

      - #### tree

            RTree tree

- ## Package oracle.spatial.topo

  - ### Class [oracle.spatial.topo.Edge](oracle/spatial/topo/Edge.md) extends java.lang.Object implements Serializable

    - ### Serialized Fields

      - #### id

            int id

      - #### originNode

            int originNode

      - #### endNode

            int endNode

      - #### boundedFaceL

            int boundedFaceL

      - #### boundedFaceR

            int boundedFaceR

      - #### nextEdgeL

            int nextEdgeL

      - #### prevEdgeL

            int prevEdgeL

      - #### nextEdgeR

            int nextEdgeR

      - #### prevEdgeR

            int prevEdgeR

      - #### traceCount

            int traceCount

      - #### coords

            Point2DD[] coords

  - ### Class [oracle.spatial.topo.Face](oracle/spatial/topo/Face.md) extends java.lang.Object implements Serializable

    - ### Serialized Fields

      - #### id

            int id

      - #### boundaryEdge

            int boundaryEdge

      - #### islandEdges

            int[] islandEdges

      - #### islandNodes

            int[] islandNodes

      - #### mbr

            Point2DD[] mbr

  - ### Class [oracle.spatial.topo.InvalidTopoOperationException](oracle/spatial/topo/InvalidTopoOperationException.md) extends java.lang.Exception implements Serializable

  - ### Class [oracle.spatial.topo.Node](oracle/spatial/topo/Node.md) extends java.lang.Object implements Serializable

    - ### Serialized Fields

      - #### id

            int id

      - #### startEdge

            int startEdge

      - #### containFace

            int containFace

      - #### coord

            Point2DD coord

  - ### Class [oracle.spatial.topo.Point2DD](oracle/spatial/topo/Point2DD.md) extends java.lang.Object implements Serializable

    - ### Serialized Fields

      - #### x

            double x

      - #### y

            double y

  - ### Class [oracle.spatial.topo.TopoDataException](oracle/spatial/topo/TopoDataException.md) extends java.lang.Exception implements Serializable

  - ### Class [oracle.spatial.topo.TopoEntityNotFoundException](oracle/spatial/topo/TopoEntityNotFoundException.md) extends java.lang.Exception implements Serializable

  - ### Class [oracle.spatial.topo.TopoFrame](oracle/spatial/topo/TopoFrame.md) extends java.awt.Frame implements Serializable

    - ### Serialized Fields

      - #### t

            TopoMap t

  - ### Class [oracle.spatial.topo.TopoValidationException](oracle/spatial/topo/TopoValidationException.md) extends java.lang.Exception implements Serializable

- ## Package oracle.spatial.util

  - ### Class [oracle.spatial.util.GeoHash](oracle/spatial/util/GeoHash.md) extends java.lang.Object implements Serializable

    serialVersionUID:
    -7226377382696157205L

    - ### Serialized Fields

      - #### bitsValue

            long bitsValue

      - #### numberOfBits

            short numberOfBits

      - #### point

            JPoint2DD point

      - #### mer

            double[] mer

      - #### ghString

            java.lang.String ghString

      - #### value

            long value

  - ### Class [oracle.spatial.util.GeometryExceptionWithContext](oracle/spatial/util/GeometryExceptionWithContext.md) extends java.lang.Exception implements Serializable

    - ### Serialized Fields

      - #### m_oracleErrorMessage

            java.lang.String m_oracleErrorMessage

      - #### m_specifics

            java.lang.String m_specifics

      - #### m_context

            java.lang.String m_context

  - ### Class [oracle.spatial.util.RTree](oracle/spatial/util/RTree.md) extends java.lang.Object implements Serializable

    - ### Serialized Fields

      - #### nDimensions

            int nDimensions

      - #### nodeSize

            int nodeSize

      - #### minFill

            int minFill

      - #### nodeCount

            int nodeCount

      - #### leafCount

            int leafCount

      - #### entryCount

            int entryCount

      - #### levels

            int levels

      - #### mbh

            oracle.spatial.util.RTree.Span[] mbh

      - #### root

            oracle.spatial.util.RTree.TreeNode root

      - #### my_tolerance

            double my_tolerance

  - ### Class [oracle.spatial.util.RTree.RTreePlot](oracle/spatial/util/RTree.RTreePlot.md) extends java.awt.Frame implements Serializable

Skip navigation links

- [Overview](overview-summary.md)
- Package
- Class
- [Tree](overview-tree.md)
- [Deprecated](deprecated-list.md)
- [Index](index-all.md)
- [Help](help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
