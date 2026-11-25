The Data Mining SQL functions operate in two modes: by applying a pre-defined model, or by executing an analytic clause. If you supply an analytic clause instead of a model name, the function builds one or more transient models and uses them to score the data.

The ability to score data dynamically without a pre-defined model extends the application of basic embedded data mining techniques into environments where models are not available. Dynamic scoring, however, has limitations. The transient models created during dynamic scoring are not available for inspection or fine tuning. Applications that require model inspection, the correlation of scoring results with the model, special algorithm settings, or multiple scoring queries that use the same model, require a predefined model.

The following example shows a dynamic scoring query. The example identifies the rows in the input data that contain unusual customer age values.

Example 32-13 Dynamic Prediction

    SELECT cust_id, age, pred_age, age-pred_age age_diff, pred_det FROM
     (SELECT cust_id, age, pred_age, pred_det,
        RANK() OVER (ORDER BY ABS(age-pred_age) DESC) rnk FROM
        (SELECT cust_id, age,
             PREDICTION(FOR age USING *) OVER () pred_age,
             PREDICTION_DETAILS(FOR age ABS USING *) OVER () pred_det
      FROM mining_data_apply_v))
    WHERE rnk <= 5;

    CUST_ID  AGE   PRED_AGE AGE_DIFF PRED_DET
    ------- ---- ---------- -------- --------------------------------------------------------------
     100910   80 40.6686505    39.33 <Details algorithm="Support Vector Machines">
                                     <Attribute name="HOME_THEATER_PACKAGE" actualValue="1"
                                      weight=".059" rank="1"/>
                                     <Attribute name="Y_BOX_GAMES" actualValue="0"
                                      weight=".059" rank="2"/>
                                     <Attribute name="AFFINITY_CARD" actualValue="0"
                                      weight=".059" rank="3"/>
                                     <Attribute name="FLAT_PANEL_MONITOR" actualValue="1"
                                      weight=".059" rank="4"/>
                                     <Attribute name="YRS_RESIDENCE" actualValue="4"
                                      weight=".059" rank="5"/>
                                      </Details>

     101285   79 42.1753571    36.82 <Details algorithm="Support Vector Machines">
                                     <Attribute name="HOME_THEATER_PACKAGE" actualValue="1"
                                      weight=".059" rank="1"/>
                                     <Attribute name="HOUSEHOLD_SIZE" actualValue="2" weight=".059"
                                      rank="2"/>
                                     <Attribute name="CUST_MARITAL_STATUS" actualValue="Mabsent"
                                      weight=".059" rank="3"/>
                                     <Attribute name="Y_BOX_GAMES" actualValue="0" weight=".059"
                                      rank="4"/>
                                     <Attribute name="OCCUPATION" actualValue="Prof." weight=".059"
                                      rank="5"/>
                                     </Details>

     100694   77 41.0396722    35.96 <Details algorithm="Support Vector Machines">
                                     <Attribute name="HOME_THEATER_PACKAGE" actualValue="1"
                                      weight=".059" rank="1"/>
                                     <Attribute name="EDUCATION" actualValue="&lt; Bach."
                                      weight=".059" rank="2"/>
                                     <Attribute name="Y_BOX_GAMES" actualValue="0" weight=".059"
                                      rank="3"/>
                                     <Attribute name="CUST_ID" actualValue="100694" weight=".059"
                                      rank="4"/>
                                     <Attribute name="COUNTRY_NAME" actualValue="United States of
                                      America" weight=".059" rank="5"/>
                                     </Details>

     100308   81 45.3252491    35.67 <Details algorithm="Support Vector Machines">
                                     <Attribute name="HOME_THEATER_PACKAGE" actualValue="1"
                                      weight=".059" rank="1"/>
                                     <Attribute name="Y_BOX_GAMES" actualValue="0" weight=".059"
                                      rank="2"/>
                                     <Attribute name="HOUSEHOLD_SIZE" actualValue="2" weight=".059"
                                      rank="3"/>
                                     <Attribute name="FLAT_PANEL_MONITOR" actualValue="1"
                                      weight=".059" rank="4"/>
                                     <Attribute name="CUST_GENDER" actualValue="F" weight=".059"
                                      rank="5"/>
                                     </Details>

     101256   90 54.3862214    35.61 <Details algorithm="Support Vector Machines">
                                     <Attribute name="YRS_RESIDENCE" actualValue="9" weight=".059"
                                      rank="1"/>
                                     <Attribute name="HOME_THEATER_PACKAGE" actualValue="1"
                                      weight=".059" rank="2"/>
                                     <Attribute name="EDUCATION" actualValue="&lt; Bach."
                                      weight=".059" rank="3"/>
                                     <Attribute name="Y_BOX_GAMES" actualValue="0" weight=".059"
                                      rank="4"/>
                                     <Attribute name="COUNTRY_NAME" actualValue="United States of
                                      America" weight=".059" rank="5"/>
                                     </Details>
