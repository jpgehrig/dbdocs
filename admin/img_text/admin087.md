# Description of the illustration admin087.eps

This is a text description of max_util_limit_ex.gif. It illustrates the multilevel schema created by the example in the following text.

The resource plan APPS_PLAN is the top level plan. At the next lower level are the following: consumer group APP1_GROUP, subplan APP2_SUBPLAN, and consumer group APP3_GROUP. The UTILIZATION_LIMIT attribute is set to 40% for both APP1_GROUP and APP2_SUBPLAN.

At the next lower level, the subplan APP2_SUBPLAN further contains resource allocations for the consumer group APP2_OLTP_GROUP and the subplan APP2_REPORTS_SUBPLAN.The UTILIZATION_LIMIT attribute for APP2_OLTP_GROUP is set to 90%.

At the next lower level, the APP2_REPORTS_SUBPLAN contains the consumer groups APP2_ADHOC_GROUP and APP2_REPORT_GROUP. The UTILIZATION_LIMIT attribute for both these groups is set to 50%.
