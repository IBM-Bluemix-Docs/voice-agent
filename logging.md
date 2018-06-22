---

copyright:
  years: 2018
lastupdated: "2018-06-13"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Viewing usage and call logs
{: #logging}

You can view the usage history and call logs for your voice agents from the {{site.data.keyword.Bluemix_notm}} dashboard.
{: shortdesc}

## About logging

Logging is automatically enabled for {{site.data.keyword.iva_full}}. You can view your voice agent call logs in the _Usage_ dashboard.

The _Usage_ dashboard shows you quick stats about your service use for the current month and remaining resources available in your plan. This information includes the maximum number of concurrent connections that are encountered in the current month and the maximum number of concurrent connections available in your plan. You can also see the number of free minutes included in the plan and the number of used minutes. The _Call logs_ section follows your _Quick stats_.

In the _Call logs_ section, you can filter call logs by date and voice agent name to reduce the number of displayed calls and isolate specific call logs.

To learn more about creating and editing voice agents, see [Managing voice agents](managing.html).

##  Viewing call logs

1. From your {{site.data.keyword.iva_short}} dashboard, navigate to the _Usage_ dashboard to view the _Quick stats_ and _Call logs_. Each row in the _Call logs_ table corresponds to one call.

      For each call, you can see the name and phone number of your voice agent, the start and stop times, and the call duration. You might also see a warning symbol next to the voice agent name, which indicates that the call failed.

1.  You can filter the list of calls by viewing calls on a specific date or filtering calls by voice agent name.

1. To access the call failure logs for an individual call, click the **Logs** icon in the **Failure Logs** column for that call.

1. You can examine the detailed list of message logs in the new view by using the following methods:
  * Search the failure logs
  * Filter messages based on the log type, either **Error** or **Warn**
  * Download your data set
  * Sort the failure logs by ascending or descending timestamp

1. To view any failure log message in detail, click the arrow at the beginning of the row you are interested in to expand the view. You can view more detailed information about log messages in [Voice Gateway system messages](https://www.ibm.com/support/knowledgecenter/SS4U29/messages.html){:new_window}.

1. Click the back arrow at the beginning of the page to return to the _Usage_ dashboard.

## Related links
Read through more detailed information about logging in [Troubleshooting](https://www.ibm.com/support/knowledgecenter/SS4U29/troubleshooting.html){:new_window}, from the IBM Voice Gateway documentation.
