The illustration shows four server pools: Sales, ERP, HR, and Free.

- There are four servers that run an Oracle RAC database instance in the Sales server pool. The Sales server pool supports all workloads that use the Sales service.

- There is one server that runs an Oracle RAC database instance in the ERP server pool. The ERP server pool supports all workloads that use the AP and AR services.

- In the HR server pool, there are two servers that run instances of the same Oracle RAC database as the ERP server pool. The HR server pool supports all workloads that use the HR and OS services.

- The Free server pool contains a single server, managed by Oracle Clusterware. The server does not have an Oracle RAC database running on it.

Underlying all the Oracle RAC database instances, server pools, and servers, including the server in the Free server pool, is Oracle Clusterware.

End of Description.
