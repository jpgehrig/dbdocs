Use the `oclumon dumpnodeview local` command to view log information from the system monitor service in the form of a node view.

### Usage Notes

**Note:**

The `oclumon dumpnodeview local` command has no dependency on GIMR or MGMTDB and can return Cluster Health Monitor data irrespective of GIMR being configured.

### Syntax

    dumpnodeview local [[([(-system | -protocols | -v)] |
         [(-cpu | -process | -procagg | -device | -nic | -filesystem | -nfs)
         [-detail] [-all] [-sort <metric_name>] [-filter <string>] [-head <rows_count>] [-i <seconds>]])
         [([-s <start_time>  -e <end_time>] | -last <duration>)]] |
         [-inputDataDir <absolute_path> -logDir <absolute_path>]
         [-h]]

### Parameters

Table B-10 oclumon dumpnodeview local Command Parameters

| Parameter     | Description                                                                                                                       |
|:--------------|:----------------------------------------------------------------------------------------------------------------------------------|
| `local`       | Cluster Health Monitor local dump. Dumps metrics from node local Cluster Health Monitor repository.                               |
| `-system`     | Dumps system metrics. For example:<br>`oclumon dumpnodeview local -system`<br>.                                                   |
| `-cpu`        | Dumps CPU metrics. For example:<br>`oclumon dumpnodeview local -cpu`<br>.                                                         |
| `-process`    | Dumps process metrics. For example:<br>`oclumon dumpnodeview local -process`<br>.                                                 |
| `-procagg`    | Dumps process aggregate metrics. For example:<br>`oclumon dumpnodeview local -procagg`<br>.                                       |
| `-device`     | Dumps disk metrics. For example:<br>`oclumon dumpnodeview local -device`<br>.                                                     |
| `-nic`        | Dumps network interface metrics. For example:<br>`oclumon dumpnodeview local -nic`<br>.                                           |
| `-filesystem` | Dumps filesystem metrics. For example:<br>`oclumon dumpnodeview local -filesystem`<br>.                                           |
| `-nfs`        | Dumps NFS metrics. For example:<br>`oclumon dumpnodeview local -nfs`<br>.                                                         |
| `-protocols`  | Dumps network protocol metrics, cumulative values from system start. For example:<br>`oclumon dumpnodeview local -protocols`<br>. |
| `-v`          | Displays verbose node view output. For example:<br>`oclumon dumpnodeview local -v`<br>.                                           |
| `-h, --help`  | Displays the command-line help and exits.                                                                                         |

Table B-11 oclumon dumpnodeview local Command Flags

| Flag                           | Description                                                                                                                                                                                                                                                                                                                                                                                              |
|:-------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-detail`                      | Use this option to dump detailed metrics. Applicable to the `-process` and `-nic` options.<br>For example:<br>`oclumon dumpnodeview local -process -detail`<br>.                                                                                                                                                                                                                                         |
| `-all`                         | Use this option to dump the node views of all entries. Applicable to the `-process` option.<br>For example:<br>`oclumon dumpnodeview local -process -all`<br>.                                                                                                                                                                                                                                           |
| `-head ``rows_count`           | Use this option to dump the node view of the specified number of metrics rows in the result. Applicable to the `-process` option. Default is set to 5.<br>For example:<br>`oclumon dumpnodeview local -process -head 7`<br>.                                                                                                                                                                             |
| `-sort ``metric_name`          | Use this option to sort based on the specified metric name, supported with the `-process`, `-device`, `-nic`, `-cpu`, `-procagg`, `-filesystem`, `-nfs` options.<br>For example:<br>`oclumon dumpnodeview local -device -sort "ioR"`<br>.                                                                                                                                                                |
| `-i ``seconds`                 | Display data separated by the specified interval in seconds. Must be a multiple of 5. Applicable to continuous mode query.<br>For example:<br>`oclumon dumpnodeview local -device -i 5`                                                                                                                                                                                                                  |
| `-filter ``string`             | Use this option to search for a filter string in the Name column of the respective metric.<br>For example, `-process -filter "ora"` will display the process metrics, which contain "`ora`" substring in their name.<br>Supported with the `-process`, `-device`, `-nic`, `-cpu`, `-procagg`, `-filesystem`, `-nfs` options.<br>For example:<br>`oclumon dumpnodeview local -process -filter "ora"`<br>. |
| `-show_all_sample_with_filter` | All samples where filter doesn't matches will also show in the output . Can be used only with -filter option.<br>For example:<br>`oclumon dumpnodeview local -filter filter_criteria -show_all_sample_with_filter`                                                                                                                                                                                       |

Table B-12 oclumon dumpnodeview local Command Log File Directories

| Directory                           | Description                                                                                                                                                                                      |
|:------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-inputDataDir ``absolute_dir_path` | Specifies absolute path of the directory that contains JSON logs files.<br>For example:<br>`oclumon dumpnodeview local -cpu -inputDataDir absolute_path`                                         |
| `-logDir ``absolute_log_dir_path`   | Specifies absolute path of the directory, which will contain the script run logs.<br>For example:<br>`oclumon dumpnodeview local -cpu -inputDataDir absolute_path -logDir absolute_log_dir_path` |

Table B-13 oclumon dumpnodeview local Command Historical Query Options

| Flag                                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:-------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-s ``start_time`<br>`-e ``end_time` | Use the `-s` option to specify a time stamp from which to start a range of queries and use the `-e` option to specify a time stamp to end the range of queries.<br>Specify time in the `YYYY-MM-DD HH24:MM:SS` format surrounded by double quotation marks (`""`).<br>Specify these two options together to obtain a range.<br>For example:<br>`oclumon dumpnodeview local -cpu -s "2019-07-10 03:40:25" -e "2019-07-10 03:45:25"` |
| `-last ``duration`                   | Use this option to specify a time, given in `HH24:MM:SS` format surrounded by double quotation marks (""), to retrieve the last metrics.<br>Specifying "`00:45:00`" will dump metrics for the last 45 minutes.<br>For example:<br>`oclumon dumpnodeview local -nic -last "00:45:00"`<br>.                                                                                                                                          |

**Parent topic:** [OCLUMON Command Reference](oclumon-command-reference.md)
