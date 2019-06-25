---

copyright:
  years: 2018
lastupdated: "2018-11-12"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Viewing usage and call logs
{: #logging}

You can view the usage history, call logs, and SMS logs for your voice agents from the {{site.data.keyword.Bluemix_notm}} dashboard.
{: shortdesc}

## About logging

Logging is automatically enabled for {{site.data.keyword.iva_full}}. You can view your voice agent call logs in the _Usage_ dashboard.

The _Usage_ dashboard shows you quick stats about your service use and remaining resources available in your plan. This information includes the maximum number of concurrent connections that are encountered in the current month and the maximum number of concurrent connections available in your plan. In the _Call minutes_ box, you can see the number of free minutes included in the plan and the number of used minutes. The _Call logs_ section follows your _Quick stats_. The _SMS logs_ section shows similar SMS usage stats on your agents. 

You can filter _Call logs_ and _Call minutes_ by date, and by either voice agent names or numbers to reduce the number of displayed calls and isolate specific call logs. You can filter _SMS logs_ by date, and by either agent names or numbers. In addition, you can filter _Call logs_ to display only failed calls.

To learn more about creating and editing voice agents, see [Managing voice agents](/docs/services/voice-agent?topic=voice-agent-managing).

##  Viewing call logs

1. From your {{site.data.keyword.iva_short}} dashboard, navigate to the _Usage_ dashboard to view the _Quick stats_ and _Call logs_. Each row in the _Call logs_ table corresponds to one call.

      For each call, you can see the name and phone number of your voice agent, the start and stop times, and the call duration. You might also see a warning symbol next to the voice agent name, which indicates that the call failed.

1.  You can filter the list of calls by viewing calls on a specific date and by filtering calls by voice agent name or number. You can also choose to display only failed calls.

1. To access the call failure logs for an individual call, click the dots in the **Actions** column for that call to expand the menu. Then, choose **Failure logs**. This option appears only for failed calls.

1. You can examine the detailed list of message logs in the new view by using the following methods:
  * Search the failure logs
  * Filter messages based on the log type, either **Error** or **Warn**
  * Download your data set
  * Sort the failure logs by ascending or descending timestamp

1. To view any failure log message in detail, click the arrow at the beginning of the row you are interested in to expand the view. You can view more detailed information about log messages in [Voice Gateway system messages](https://www.ibm.com/support/knowledgecenter/SS4U29/messages.html){:new_window}.

1. Click the back arrow at the beginning of the page to return to the _Usage_ dashboard.

##  Viewing SMS logs

1. From your {{site.data.keyword.iva_short}} dashboard, go to the _Usage_ dashboard to view the _Quick stats_, and click _SMS logs_. Each row in the _SMS logs_ table corresponds to an agent and number.

      For agent, you can see phone number of your voice agent, and the Inbound Messages, Outbound Messages, and Billable Messages. You might also see a warning symbol next to the voice agent name, which indicates that SMS messages failed.

1.  You can filter the list of agent by viewing messages on a specific date and by filtering the messages by voice agent name or number. 

1. To access the SMS logs for an individual agent, click the dots in the **Actions** column for that call to expand the menu. Then, choose **SMS logs**. 

1. Click the back arrow at the beginning of the page to return to the _Usage_ dashboard.

## Related links
Read through more detailed information about logging in [Troubleshooting](https://www.ibm.com/support/knowledgecenter/SS4U29/troubleshooting.html){:new_window}, from the IBM Voice Gateway documentation.
