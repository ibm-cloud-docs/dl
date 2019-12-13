---

copyright:
  years: 2016, 2019
lastupdated: "2019-11-19"

keywords: IBM, activity tracker, LogDNA, event, security, Direct Link

subcollection: dl

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:important: .important}
{:note: .note}

# Activity Tracker events for IBM Cloud Direct Link Dedicated
{: #at_events}

As a security officer, auditor, or manager, you can use the Activity Tracker service to track how users and applications interact with the Direct Link service in {{site.data.keyword.cloud}}.
{: shortdesc}

{{site.data.keyword.at_full_notm}} records user-initiated activities that change the state of a service in {{site.data.keyword.cloud_notm}}. You can use this service to investigate abnormal activity and critical actions and to comply with regulatory audit requirements. In addition, you can be alerted about actions as they happen. The events that are collected comply with the Cloud Auditing Data Federation (CADF) standard. For more information, see the [getting started tutorial for {{site.data.keyword.at_full_notm}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).

## Actions and event messaging for Direct Link API calls on Activity Tracker
{: #at_actions}
 
### List of gateway events for Direct Link Dedicated
{: #at_actions}

The following table lists the actions that generate an event for the Direct Link Dedicated offering.



| Action                      | Description |
|-----------------------------|---------|
| `directlink.dedicated.gateway.create`   | An event is generated when an initiator creates a Direct Link Dedicated gateway. |
| `directlink.dedicated.gateway.delete`     | An event is generated when an initiator deletes a Direct Link Dedicated gateway. |
| `directlink.dedicated.gateway.update`   | An event is generated when an initiator updates a Direct Link Dedicated gateway. |
| `directlink.dedicated.virtual_connection.create`   | An event is generated when an initiator creates a Direct Link Dedicated virtual connection. |
| `directlink.dedicated.virtual_connection.delete`     | An event is generated when an initiator deletes a Direct Link Dedicated virtual connection. |
| `directlink.dedicated.virtual_connection.update`  | An event is generated when an initiator updates a Direct Link Dedicated virtual connection. |
| `directlink.dedicated.completion_notice.create`    | An event is generated when an initiator creates a Direct link Dedicated completion notice. |
{: caption="Table 1. Manage Direct Link Dedicated gateway actions" caption-side="top"}

** Things that coincide with GA **

[Plan to add a new Network Foundations category for DL 2.0](https://test.cloud.ibm.com/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-cloud_services)

[Does DL 2.0 support all locations on this page?  If so, need a statement saying what we support & any if there are any limitations](https://test.cloud.ibm.com/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-cloud_services_locations)
