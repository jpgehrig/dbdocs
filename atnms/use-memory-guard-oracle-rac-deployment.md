Memory Guard autonomously detects and monitors Oracle Real Application Clusters (Oracle RAC) or Oracle RAC One Node databases when they are open.

Memory Guard sends alert notifications when Memory Guard detects memory stress on a database node. You can find Memory Guard alerts in audit logs at `$ORACLE_BASE/crsdata/``node name``/qos/logs/dbwlm/auditing`.

Example 11-2 Memory Guard Alert Notifications

The following example shows a Memory Guard log file when the services were stopped due to memory stress.

    <MESSAGE>
    <HEADER>
    <TSTZ_ORIGINATING>2016-07-28T16:11:03.701Z</TSTZ_ORIGINATING>
    <COMPONENT_ID>wlm</COMPONENT_ID>
    <MSG_TYPE TYPE="NOTIFICATION"></MSG_TYPE>
    <MSG_LEVEL>1</MSG_LEVEL>
    <HOST_ID>hostABC</HOST_ID>
    <HOST_NWADDR>11.111.1.111</HOST_NWADDR>
    <MODULE_ID>gomlogger</MODULE_ID>
    <THREAD_ID>26</THREAD_ID>
    <USER_ID>userABC</USER_ID>
    <SUPPL_ATTRS>
    <ATTR NAME="DBWLM_OPERATION_USER_ID">userABC</ATTR>
    <ATTR NAME="DBWLM_THREAD_NAME">MPA Task Thread 1469722257648</ATTR>
    </SUPPL_ATTRS>
    </HEADER>
    <PAYLOAD>
    <MSG_TEXT>Server Pool Generic has violation risk level RED.</MSG_TEXT>
    </PAYLOAD>
    </MESSAGE>
    <MESSAGE>
    <HEADER>
    <TSTZ_ORIGINATING>2016-07-28T16:11:03.701Z</TSTZ_ORIGINATING>
    <COMPONENT_ID>wlm</COMPONENT_ID>
    <MSG_TYPE TYPE="NOTIFICATION"></MSG_TYPE>
    <MSG_LEVEL>1</MSG_LEVEL>
    <HOST_ID>hostABC</HOST_ID>
    <HOST_NWADDR>11.111.1.111</HOST_NWADDR>
    <MODULE_ID>gomlogger</MODULE_ID>
    <THREAD_ID>26</THREAD_ID>
    <USER_ID>userABC</USER_ID>
    <SUPPL_ATTRS>
    <ATTR NAME="DBWLM_OPERATION_USER_ID">userABC</ATTR>
    <ATTR NAME="DBWLM_THREAD_NAME">MPA Task Thread 1469722257648</ATTR>
    </SUPPL_ATTRS>
    </HEADER>
    <PAYLOAD>
    MSG_TEXT>Server userABC-hostABC-0 has violation risk level RED. New connection requests will no longer be accepted.</MSG_TEXT>
    </PAYLOAD>
    </MESSAGE>

The following example shows a Memory Guard log file when the services were restarted after relieving the memory stress.

    <MESSAGE>
    <HEADER>
    <TSTZ_ORIGINATING>2016-07-28T16:11:07.674Z</TSTZ_ORIGINATING>
    <COMPONENT_ID>wlm</COMPONENT_ID>
    <MSG_TYPE TYPE="NOTIFICATION"></MSG_TYPE>
    <MSG_LEVEL>1</MSG_LEVEL>
    <HOST_ID>hostABC</HOST_ID>
    <HOST_NWADDR>11.111.1.111</HOST_NWADDR>
    <MODULE_ID>gomlogger</MODULE_ID>
    <THREAD_ID>26</THREAD_ID>
    <USER_ID>userABC</USER_ID>
    <SUPPL_ATTRS>
    <ATTR NAME="DBWLM_OPERATION_USER_ID">userABC</ATTR>
    <ATTR NAME="DBWLM_THREAD_NAME">MPA Task Thread 1469722257648</ATTR>
    </SUPPL_ATTRS>
    </HEADER>
    <PAYLOAD>
    <MSG_TEXT>Memory pressure in Server Pool Generic has returned to normal.</MSG_TEXT>
    </PAYLOAD>
    </MESSAGE>
    <MESSAGE>
    <HEADER>
    <TSTZ_ORIGINATING>2016-07-28T16:11:07.674Z</TSTZ_ORIGINATING>
    <COMPONENT_ID>wlm</COMPONENT_ID>
    <MSG_TYPE TYPE="NOTIFICATION"></MSG_TYPE>
    <MSG_LEVEL>1</MSG_LEVEL>
    <HOST_ID>hostABC</HOST_ID>
    <HOST_NWADDR>11.111.1.111</HOST_NWADDR>
    <MODULE_ID>gomlogger</MODULE_ID>
    <THREAD_ID>26</THREAD_ID>
    <USER_ID>userABC</USER_ID>
    <SUPPL_ATTRS>
    <ATTR NAME="DBWLM_OPERATION_USER_ID">userABC</ATTR>
    <ATTR NAME="DBWLM_THREAD_NAME">MPA Task Thread 1469722257648</ATTR>
    </SUPPL_ATTRS>
    </HEADER>
    <PAYLOAD>
    <MSG_TEXT>Memory pressure in server userABC-hostABC-0 has returned to normal. New connection requests are now accepted.</MSG_TEXT>
    </PAYLOAD>
    </MESSAGE>
    <MESSAGE>

**Parent topic:** [Resolving Memory Stress](purpose-memory-guard.md)
