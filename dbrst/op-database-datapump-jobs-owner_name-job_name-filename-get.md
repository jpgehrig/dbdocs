Returns the log or export file for the given data pump job. A client requires SQL Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- filename: string
  Name of the file associated with the Data Pump job.
- job_name: string
  Name of the Data Pump job.
- owner_name: string
  Owner of the Data Pump job.

Back to Top

### Response

Supported Media Types

- text/plain
- application/vnd.tcpdump.pcap

#### 200 Response

The requested file for the Data Pump job. Log files are text/plain. Export file are application/vnd.tcpdump.pcap.

Body ()

Root Schema : schema

Type: `string`

Back to Top
