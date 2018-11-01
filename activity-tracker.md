---

copyright:
  years: 2018
lastupdated: "2018-10-30"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Activity tracker events
{: #activity-tracker}

Use the {{site.data.keyword.cloudaccesstrailfull}} service to track how users and applications interact with the {{site.data.keyword.iva_full}} service in {{site.data.keyword.Bluemix}}. {: shortdesc}

The {{site.data.keyword.cloudaccesstrailfull_notm}} service records user-initiated activities that change the state of a service in {{site.data.keyword.Bluemix_notm}}. For more information, see the [{{site.data.keyword.cloudaccesstrailshort}}](../cloud-activity-tracker/index.html#getting-started-with-cla).

## List of events
{: #event-List}

The following table lists the actions that generate an event.

|Action| description |
| --- | ---- |
| `create agent: POST /config/submitconfig` | Create a new voice agent |
| `update agent: POST /config/submitconfig` | Update a voice agent |
| `Update concurrency: POST /config/updatemax` | Update the maximum call concurrency |
| `delete agent: POST /config/submitconfig` | Delete a voice agent |
{: caption="Table 1. Actions that generate events" caption-side="top"}

## Where to view activity events
{: #view-event}

{{site.data.keyword.cloudaccesstrailshort}} events are available in the {{site.data.keyword.cloudaccesstrailshort}} account domain that is available in the {{site.data.keyword.Bluemix_notm}} region where the events are generated.

## Filtering events
{: #filter_events}

### Filtering by voice agent ID
{: #filter_id}

You can filter the list of activity events for a specific voice agent by its instance ID.

1. Go to the **Manage** page in the {{site.data.keyword.cloudaccesstrailshort}}.
2. Enter `target.name_str` in the **Search Field** and your voice agent instance ID in the **Search** field as a string. Check that the voice agent instance ID is percent encoded and that you use a wildcard search, _*_ .

For example, to search for your voice agent instance ID, `serviceInstanceId=crn%3A...`.

  * **Search Field**: `target.name_str`
  * **Search**: `"*crn%3A...*"`

### Filtering by action event
{: #filter_action}

You can also filter the list of activity events for specific action events

1. Go to the **Manage** page in the {{site.data.keyword.cloudaccesstrailshort}}, and enter the following configuration value for each of the fields.

  * **View logs**: `Space logs`
  * **Search Field**: `action_str`
  * **Search**: `"action string"`

## Creating advanced filters
{: #advanced_filters}

You can also make advanced filters by using `AND` or `OR` to combine search terms in the **Search** field.

For example, filter by a specific voice agent instance id and a specific action.

* **View logs**: `Space logs`
* **Search Field**: `target.name_str`
* **Search**: `"*crn%3A...*" AND action_str:"action string"`

**Remember**: Check that the voice agent instance id is percent encoded and that you use a wildcard search, _*_ .
