## 5  Recovery Catalog Views

This chapter contains descriptions of recovery catalog views. You can only access these views if you have created a recovery catalog (see [`CREATE CATALOG`](CREATE-CATALOG.md)). For a summary of the recovery catalog views, refer to "[Summary of RMAN Recovery Catalog Views](summary-of-rman-recovery-catalog-views.md)".

**Note:**

These views are not normalized, but are optimized for RMAN and Enterprise Manager usage. Hence, most catalog views have redundant values that result from joining of several underlying tables.

The views intended for use by Enterprise Manager are generally less useful for direct querying than the other views.
