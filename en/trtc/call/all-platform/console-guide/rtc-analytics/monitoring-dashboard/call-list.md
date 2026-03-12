# Call List

Tencent RTC offers a monitoring dashboard for developers to monitor call quality. You can view call details and learn about the call status of users in the monitoring dashboard.

## Viewing Call List

Log in to the [Tencent RTC Console > Monitoring Dashboard](https://console.trtc.io/monitor) to view the call details of all rooms under the logged-in account.

The call list in the monitoring dashboard, displays 10 call records on one page by default, sorted in reverse order by the start time of the call, i.e. the first one is the most recently created call record. Each record includes 6 fields: Room ID, Start Time - End Time, Call Status, Room Duration, Joined Users, Operation.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/7ada9daba61e11eeae9a525400c26da5.png)

The information displayed in the call list includes:

| Item | Description |
| --- | --- |
| Room ID | The room ID of the call |
| Start Time - End Time | The start and end time of the call |
| Call Status | Includes two states: Not completed and Ended. |
| Room Duration | The time between the entry of the first user and exit of the last user. If a call is in progress, the time from the entry of the first user to when the query takes place is displayed. |
| Joined Users | The total number of users who have entered the room |
| Operation | Click [Call Details](https://www.tencentcloud.com/document/product/647/39070) to go to the details page and view the details of the call. |

## Searching for Calls

In the monitoring dashboard, you can filter the call list using a number of search methods.

- To view the information of call rooms of a particular application, click **Select application**, select the application from the drop-down list, and click **Search**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/53d1378c9a3c11ee8964525400321be2.png)

- To view the information of calls during a specific time period, select **Today**, **Yesterday**, **Last 6 hours**, or enter a time range, and click **Search**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/5d07ad069a3c11ee8964525400321be2.png)

- To view the information of a particular call, select a time range, enter a room ID (`roomid`) or user ID (`userid`), and click **Search**.

![](https://cloudcache.intl.tencent-cloud.com/cms/backend-cms/63dc11d39a3c11ee8964525400321be2.png)

## More Operations

If you want to view the call details of a particular room, see [Call Details](https://www.tencentcloud.com/document/product/647/39070).


---
*Source: [https://trtc.io/document/39069](https://trtc.io/document/39069)*
