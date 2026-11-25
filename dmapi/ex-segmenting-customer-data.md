The examples in this section use an Expectation Maximization clustering model to segment the customer data based on common characteristics.

Example 27-6 Compute Customer Segments

This query computes natural groupings of customers and returns the number of customers in each group.

    SELECT CLUSTER_ID(em_sh_clus_sample USING *) AS clus, COUNT(*) AS cnt
      FROM mining_data_apply_v
    GROUP BY CLUSTER_ID(em_sh_clus_sample USING *)
    ORDER BY cnt DESC;

          CLUS        CNT
    ---------- ----------
             9        311
             3        294
             7        215
            12        201
            17        123
            16        114
            14         86
            19         64
            15         56
            18         36

Example 27-7 Find the Customers Who Are Most Likely To Be in the Largest Segment

The query in Example 27-6 shows that segment 9 has the most members. The following query lists the five customers who are most likely to be in segment 9.

    SELECT cust_id
    FROM (SELECT cust_id, RANK() over (ORDER BY prob DESC, cust_id) rnk_clus2
      FROM (SELECT cust_id,
              ROUND(CLUSTER_PROBABILITY(em_sh_clus_sample, 9 USING *),3) prob
              FROM mining_data_apply_v))
    WHERE rnk_clus2 <= 5
    ORDER BY rnk_clus2;

       CUST_ID
    ----------
        100002
        100012
        100016
        100019
        100021

Example 27-8 Find Key Characteristics of the Most Representative Customer in the Largest Cluster

The query in Example 27-7 lists customer 100002 first in the list of likely customers for segment 9. The following query returns the five characteristics that are most significant in determining the assignment of customer 100002 to segments with probability \> 20% (only segment 9 for this customer).

    SELECT S.cluster_id, probability prob,
           CLUSTER_DETAILS(em_sh_clus_sample, S.cluster_id, 5 using T.*) det
     FROM
      (SELECT v.*, CLUSTER_SET(em_sh_clus_sample, NULL, 0.2 USING *) pset
        FROM mining_data_apply_v v
        WHERE cust_id = 100002) T,
     TABLE(T.pset) S
     ORDER BY 2 desc;

    CLUSTER_ID    PROB DET
    ---------- ------- --------------------------------------------------------------------------------
             9  1.0000 <Details algorithm="Expectation Maximization" cluster="9">
                       <Attribute name="YRS_RESIDENCE" actualValue="4" weight="1" rank="1"/>
                       <Attribute name="EDUCATION" actualValue="Bach." weight="0" rank="2"/>
                       <Attribute name="AFFINITY_CARD" actualValue="0" weight="0" rank="3"/>
                       <Attribute name="BOOKKEEPING_APPLICATION" actualValue="1" weight="0" rank="4"/>
                       <Attribute name="Y_BOX_GAMES" actualValue="0" weight="0" rank="5"/>
                       </Details>
