Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ReplayStatistics.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](ReplayableConnection.StatisticsReportType.md)
- Next Class

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.jdbc.replay

## Interface ReplayStatistics

-

  ------------------------------------------------------------------------



      public interface ReplayStatistics

  Various runtime statistics about Application Continuity (AC), such as how many JDBC calls are affected by outages, how many replay attempts are made, how many replay succeed, etc. This interface provides query-only operations on all available AC statistics.
  The statistics can be collected on a single connection, or across multiple connections. The specific case is determined at the time of the call that produces the ReplayStatistics object. The `getReplayStatistics` method on `ReplayableConnection` is the API to obtain a `ReplayStatistics` object. There is an auxiliary method on `OracleDataSource` as well.

  See Also:
  [`OracleDataSource`](OracleDataSource.md), [`ReplayableConnection`](ReplayableConnection.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                            |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------|
    | `int`             | `getCurrentRequestSize``()`<br>Obtains the size of the current request, in terms of the number of JDBC calls.                     |
    | `long`            | `getFailedReplayCount``()`<br>Obtains the number of replays that failed.                                                          |
    | `long`            | `getReplayDisablingCount``()`<br>Obtains the number of times that replay is disabled.                                             |
    | `int[]`           | `getRequestSizeHistogram``()`<br>Obtains a histogram of request sizes, in terms of the number of JDBC calls in each request.      |
    | `long`            | `getSuccessfulReplayCount``()`<br>Obtains the number of replays that succeeded.                                                   |
    | `long`            | `getTotalCalls``()`<br>Obtains the total number of JDBC calls executed so far.                                                    |
    | `long`            | `getTotalCallsAffectedByOutages``()`<br>Obtains the number of JDBC calls affected by outages.                                     |
    | `long`            | `getTotalCallsAffectedByOutagesDuringReplay``()`<br>Obtains the number of JDBC calls affected by outages in the middle of replay. |
    | `long`            | `getTotalCallsTriggeringReplay``()`<br>Obtains the number of JDBC calls that triggered replay.                                    |
    | `long`            | `getTotalCompletedRequests``()`<br>Obtains the total number of completed requests so far.                                         |
    | `long`            | `getTotalProtectedCalls``()`<br>Obtains the total number of JDBC calls executed so far that are protected by AC.                  |
    | `long`            | `getTotalReplayAttempts``()`<br>Obtains the number of replay attempts.                                                            |
    | `long`            | `getTotalRequests``()`<br>Obtains the total number of successfully submitted requests so far.                                     |

<!-- -->

- - ### Method Detail

    - #### getTotalRequests

          long getTotalRequests()

      Obtains the total number of successfully submitted requests so far.
      Returns:
      The number of successfully submitted requests.

    <!-- -->

    - #### getTotalCompletedRequests

          long getTotalCompletedRequests()

      Obtains the total number of completed requests so far.
      Returns:
      The number of completed requests.

    <!-- -->

    - #### getTotalCalls

          long getTotalCalls()

      Obtains the total number of JDBC calls executed so far.
      Returns:
      The number of JDBC calls.

    <!-- -->

    - #### getTotalProtectedCalls

          long getTotalProtectedCalls()

      Obtains the total number of JDBC calls executed so far that are protected by AC.
      Returns:
      The number of JDBC calls protected by AC.

    <!-- -->

    - #### getTotalCallsAffectedByOutages

          long getTotalCallsAffectedByOutages()

      Obtains the number of JDBC calls affected by outages. This includes both local calls and calls that involve roundtrip(s) to the database server.
      Returns:
      The number of JDBC calls affected by outages.

    <!-- -->

    - #### getTotalCallsTriggeringReplay

          long getTotalCallsTriggeringReplay()

      Obtains the number of JDBC calls that triggered replay. Not all the calls affected by an outage trigger replay, because replay can be disabled for some requests.
      Returns:
      The number of JDBC calls that triggered replay.

    <!-- -->

    - #### getTotalCallsAffectedByOutagesDuringReplay

          long getTotalCallsAffectedByOutagesDuringReplay()

      Obtains the number of JDBC calls affected by outages in the middle of replay. Outages may be cascaded and strike a call multiple times when replay is ongoing. AC automatically reattempts replay when this happens, unless it reaches the maximum retry limit.
      Returns:
      The number of JDBC calls affected by outages during replay.

    <!-- -->

    - #### getSuccessfulReplayCount

          long getSuccessfulReplayCount()

      Obtains the number of replays that succeeded. Successful replays mask the outages from applications.
      Returns:
      The number of successful replays.

    <!-- -->

    - #### getFailedReplayCount

          long getFailedReplayCount()

      Obtains the number of replays that failed. When replay fails, it rethrows the original SQLRecoverableException to the application, with the reason for the failure chained to that original exception. Application can call `getNextException` to retrieve the reason.
      Returns:
      The number of successful replays.

    <!-- -->

    - #### getReplayDisablingCount

          long getReplayDisablingCount()

      Obtains the number of times that replay is disabled. When replay is disabled in the middle of a request, the remaining calls in that request are no longer protected by AC. In case an outage strikes one of those remaining calls, no replay will be attempted, and application simply gets an SQLRecoverableException.
      Returns:
      The number of times that replay is disabled.

    <!-- -->

    - #### getTotalReplayAttempts

          long getTotalReplayAttempts()

      Obtains the number of replay attempts. AC automatically reattempts when replay fails, so this number may exceed the number of JDBC calls that triggered replay.
      Returns:
      The number of replay attempts.

    <!-- -->

    - #### getCurrentRequestSize

          int getCurrentRequestSize()

      Obtains the size of the current request, in terms of the number of JDBC calls.
      Returns:
      The size of the current request. 0 if called outside any open request.

    <!-- -->

    - #### getRequestSizeHistogram

          int[] getRequestSizeHistogram()

      Obtains a histogram of request sizes, in terms of the number of JDBC calls in each request. The histogram is returned as an integer array. The element at index-i represents the number of request sizes between `2^i` and `2^(i+1)-1`, where i ranges from 0 to array length - 1.
      Returns:
      The histogram array.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ReplayStatistics.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](ReplayableConnection.StatisticsReportType.md)
- Next Class

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2008, 2022, Oracle and/or its affiliates.
