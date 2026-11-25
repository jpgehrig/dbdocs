This appendix contains the code for the `SingleSelectionTemplate` class. This class is used by the examples in [Using a TransactionProvider](using-transaction-provider.md), and [Creating Dynamic Queries](creating-dynamic-queries.md).

### B.1 Code for the SingleSelectionTemplate Class

The following is the `SingleSelectionTemplate.java` class.

    import java.util.ArrayList;
    import java.util.Collections;
    import java.util.Iterator;
    import java.util.List;
    import oracle.olapi.data.cursor.CursorManager;
    import oracle.olapi.data.cursor.ValueCursor;
    import oracle.olapi.data.source.DataProvider;
    import oracle.olapi.data.source.DynamicDefinition;
    import oracle.olapi.data.source.Source;
    import oracle.olapi.data.source.StringSource;
    import oracle.olapi.data.source.SourceGenerator;
    import oracle.olapi.data.source.Template;
    import oracle.olapi.metadata.mdm.MdmAttribute;
    import oracle.olapi.metadata.mdm.MdmDimensionMemberInfo;
    import oracle.olapi.metadata.mdm.MdmHierarchy;
    import oracle.olapi.metadata.mdm.MdmPrimaryDimension;
    import oracle.olapi.transaction.TransactionProvider;
    import oracle.olapi.transaction.NotCommittableException;
    import oracle.olapi.transaction.metadataStateManager.MetadataState;

    /**
     * A Template that joins Source objects for selected members of
     * dimension hierarchies to a Source for a measure.
     */
    public class SingleSelectionTemplate extends Template
    {
      // Variable to store the DynamicDefinition.
      private DynamicDefinition dynamicDef;

      /**
       * Creates a SingleSelectionTemplate.
       */
      public SingleSelectionTemplate(Source measure, DataProvider dataProvider)
      {
        super(new SingleSelectionTemplateState(measure), dataProvider);
        dynamicDef = createDynamicDefinition(
                              new SingleSelectionTemplateGenerator(dataProvider));
      }

      /**
       * Gets the Source produced by the SingleSelectionTemplateGenerator
       * from the DynamicDefinition.
       */
      public final Source getSource()
      {
        return dynamicDef.getSource();
      }

      /**
       * Gets the Source for the measure stored by the SingleSelectionTemplateState.
       */
      public Source getMeasure()
      {
        SingleSelectionTemplateState state =
          (SingleSelectionTemplateState)getCurrentState();
        return state.measure;
      }

      /**
       * Specifies the Source for the measure stored by the
       * SingleSelectionTemplateState.
       */
      public void setMeasure(Source measure)
      {
        SingleSelectionTemplateState state =
          (SingleSelectionTemplateState)getCurrentState();
        state.measure = measure;
        setCurrentState(state);
      }

      /**
       * Gets the List of MdmDimensionMemberInfo objects for the selected members
       * of the dimensions.
       */
      public List getDimMemberInfos()
      {
        SingleSelectionTemplateState state =
          (SingleSelectionTemplateState)getCurrentState();
        return Collections.unmodifiableList(state.dimMemberInfos);
      }

      /**
       * Adds an MdmDimensionMemberInfo to the List of
       * MdmDimensionMemberInfo objects.
       */
      public void addDimMemberInfo(MdmDimensionMemberInfo mdmDimMemberInfo)
      {
        SingleSelectionTemplateState state =
          (SingleSelectionTemplateState)getCurrentState();
        state.dimMemberInfos.add(mdmDimMemberInfo);
        setCurrentState(state);
      }

      /**
       * Changes the member specified for a dimension.
       */
      public void changeSelection(MdmDimensionMemberInfo mdmDimMemberInfo)
      {
        SingleSelectionTemplateState state =
          (SingleSelectionTemplateState)getCurrentState();
        int i = 0;

        Iterator dimMemberInfosItr = state.dimMemberInfos.iterator();
        while (dimMemberInfosItr.hasNext())
        {
          MdmDimensionMemberInfo mdmDimMemberInfoInList =
            (MdmDimensionMemberInfo)dimMemberInfosItr.next();
          MdmPrimaryDimension mdmPrimDim1 = mdmDimMemberInfo.getPrimaryDimension();
          MdmPrimaryDimension mdmPrimDim2 =
            mdmDimMemberInfoInList.getPrimaryDimension();
          //String value = (String)valuesItr.next();
          if (mdmPrimDim1.getName().equals(mdmPrimDim2.getName()))
          {
            state.dimMemberInfos.remove(i);
            state.dimMemberInfos.add(i, mdmDimMemberInfo);
            break;
          }
          i++;
        }

        setCurrentState(state);
      }

      /**
       * Gets the short value description of the each of the dimension members
       * specified by the list of MdmDimensionMemberInfo objects and returns
       * the descriptions in a StringBuffer.
       */
      public StringBuffer getMemberShortDescrs(DataProvider dp)
      {
        boolean firsttime = true;

        List mdmDimMemInfoList = getDimMemberInfos();

        StringBuffer shortDescrForMemberVals = new StringBuffer(" ");
        Iterator mdmDimMemInfoListItr = mdmDimMemInfoList.iterator();

        while(mdmDimMemInfoListItr.hasNext())
        {
          MdmDimensionMemberInfo mdmDimMemInfo =
            (MdmDimensionMemberInfo)mdmDimMemInfoListItr.next();
          MdmPrimaryDimension mdmPrimDim = mdmDimMemInfo.getPrimaryDimension();
          MdmAttribute mdmShortDescrAttr =
            mdmPrimDim.getShortValueDescriptionAttribute();
          Source shortDescrAttr = mdmShortDescrAttr.getSource();
          MdmHierarchy mdmHier = mdmDimMemInfo.getHierarchy();
          StringSource hierSrc = (StringSource) mdmHier.getSource();
          Source memberSel = hierSrc.selectValue(mdmDimMemInfo.getUniqueValue());
          Source shortDescrForMember = shortDescrAttr.joinHidden(memberSel);

          // Commit the current transaction.
          try
          {
            (dp.getTransactionProvider()).commitCurrentTransaction();
          }
          catch (Exception ex)
          {
            println("Could not commit the Transaction. " + ex);
          }
        }

          CursorManager cmngr = dp.createCursorManager(shortDescrForMember);
          ValueCursor valCursor = (ValueCursor)cmngr.createCursor();

          String shortDescrForMemberVal = valCursor.getCurrentString();

          if(firsttime)
          {
            shortDescrForMemberVals.append(shortDescrForMemberVal);
            firsttime = false;
          }
          else
          {
            shortDescrForMemberVals.append(", " + shortDescrForMemberVal);
          }
        }

        return shortDescrForMemberVals;
      }

      /**
       * Inner class that implements the MetadataState object for this Template.
       * Stores data that can be changed by its SingleSelectionTemplate.
       * The data is used by a SingleSelectionTemplateGenerator in producing
       * a Source for the SingleSelectionTemplate.
       */
      private static class SingleSelectionTemplateState
         implements MetadataState
      {
        public Source measure;
        public ArrayList dimMemberInfos;

        /**
         * Creates a SingleSelectionTemplateState.
         */
        public SingleSelectionTemplateState(Source measure)
        {
          this(measure, new ArrayList());
        }

        private SingleSelectionTemplateState(Source measure,
                                             ArrayList dimMemberInfos)
        {
          this.measure = measure;
          this.dimMemberInfos = dimMemberInfos;
        }

        public Object clone()
        {
          return new SingleSelectionTemplateState(measure,
                                                  (ArrayList)
                                                   dimMemberInfos.clone());
        }
      }

      /**
       * Inner class that implements the SourceGenerator object for this Template.
       * Produces a Source based on the data values of a SingleSelectionTemplate.
       */
      private static final class SingleSelectionTemplateGenerator
          implements SourceGenerator
      {
        DataProvider dp = null;

        /**
         * Creates a SingleSelectionTemplateGenerator.
         */
        public SingleSelectionTemplateGenerator(DataProvider dataProvider)
        {
          dp = dataProvider;
        }

        /**
         * Generates a Source for the SingleSelectionTemplate.
         */
        public Source generateSource(MetadataState state)
        {
          SingleSelectionTemplateState castState =
            (SingleSelectionTemplateState)state;
          Source result = castState.measure;

          Iterator dimMemberInfosItr = castState.dimMemberInfos.iterator();
          while (dimMemberInfosItr.hasNext())
          {
            MdmDimensionMemberInfo mdmDimMemInfo =
              (MdmDimensionMemberInfo)dimMemberInfosItr.next();
            MdmHierarchy mdmHier = mdmDimMemInfo.getHierarchy();
            StringSource hierSrc = (StringSource) mdmHier.getSource();
            Source memberSel = hierSrc.selectValue(mdmDimMemInfo.getUniqueValue());
            // Join the Source objects for the selected dimension members
            // to the measure.
            result = result.joinHidden(memberSel);
          }
          return result;
        }
      }
    }
