The Recommendations for SQL ID:fudq5z56q642p page is shown.

The Return button is on the right side of the page.

Below the title is the following sentence: Only one recommendation should be implemented.

The SQL Text section contains the following text: SELECT sum(quantity_sold) FROM sales s, products p WHERE s.prod_id = p.prod_id and s.amount_sold \> 20000 and p.prod name =. The text is a link.

The Select Recommendation section includes the Original Explain Plan (Annotated) button. Underneath it is the Implement button.

The section has a table that has the following columns: Select, Type, Findings, Recommendations, Rationale, Benefit (%), New Explain Plan, Compare Explain Plans. The values in the Select columns are options. The values in the New Explain Plan and Compare Explain Plans are View icons (spectacles). The rows of the table have the following values:

Row 1: (selected), SQL Profile, A potentially better execution plan was found for this statement, No SQL profile currently exists for this recommendation. Consider accepting the recommended SQL profile, The SQL profile was not automatically created because auto-creation was disabled. Set task parameter ACCEPT_SQL_PROFILES to TRUE to enable auto-creation, 96.01, (spectacles icon), (spectacles icon).

Row 2: (deselected), Index, The execution plan of this statement can be improved by creating one or more indices, Consider running the Access Advisor to improve the physical schema design or creating the recommended index. SH_PRODUCTS("PROD_NAME") SH.SALES("AMOUNT_SOLD"), Creating the recommended indices significantly improves the execution plan of this statement. However, it might be preferable to run "Access Advisor" using a representative SQL workload as opposed to a single statement. This will allow to get comprehensive index recommendations which takes into account index maintenance overhead and additional space consumption., 62.12, (spectacles icon), (spectacles icon).

End of description.
