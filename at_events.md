---

copyright:
  years: 2020, 2021
lastupdated: "2021-02-01"

keywords:

subcollection: dl

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:important: .important}
{:note: .note}

# Auditing events for {{site.data.keyword.dl_full_notm}}
{: #at_events}

As a security officer, auditor, or manager, you can use the Activity Tracker service to track how users and applications interact with the {{site.data.keyword.dl_short}} service in {{site.data.keyword.cloud}}.
{: shortdesc}

{{site.data.keyword.at_full_notm}} records user-initiated activities that change the state of a service in {{site.data.keyword.cloud_notm}}. You can use this service to investigate abnormal activity and critical actions and to comply with regulatory audit requirements. In addition, you can be alerted about actions as they happen. The events that are collected comply with the Cloud Auditing Data Federation (CADF) standard. For more information, see the [getting started tutorial for {{site.data.keyword.at_full_notm}}](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-getting-started).

## Events for {{site.data.keyword.dl_short}} Dedicated
{: #at_actions_dedicated}

### List of management events
{: #at_management_events_dedicated}

| Action                      | Description |
|-----------------------------|---------|
| `directlink.dedicated.gateway.create` | Dedicated gateway was created. |
| `directlink.dedicated.gateway.delete` | Dedicated gateway was deleted. |
| `directlink.dedicated.gateway.update` | Dedicated gateway was updated. |
{: class="simple-tab-table"}
{: caption="Table 1. List of {{site.data.keyword.dl_short}} Dedicated gateway events" caption-side="left"}
{: #simpletabtable1}
{: tab-title="Dedicated Gateway Events"}
{: tab-group="connect-simple-1"} 

| Action                      | Description |
|-----------------------------|---------|
| `directlink.dedicated.virtual-connection.create` | Dedicated virtual connection was created. |
| `directlink.dedicated.virtual-connection.delete` | Dedicated virtual connection was deleted. |
| `directlink.dedicated.virtual-connection.update` | Dedicated virtual connection was updated. |
| `directlink.dedicated.completion-notice.create` | Dedicated completion notice was created. |
{: caption="Table 2. List of {{site.data.keyword.dl_short}} Dedicated virtual connection events" caption-side="left"}
{: #simpletabtable2}
{: tab-title="Dedicated Virtual Connection Events"}
{: tab-group="connect-simple-1"}
{: class="simple-tab-table"}

### List of data events
{: #at_data_events_dedicated}

| Action                      | Description |
|-----------------------------|---------|
| `directlink.dedicated.gateway.read` | Dedicated gateway was retrieved. |
| `directlink.gateway.list` | Dedicated and Connect gateways were listed. |
{: class="simple-tab-table"}
{: caption="Table 3. List of {{site.data.keyword.dl_short}} Dedicated data events" caption-side="left"}
{: #simpletabtable1}
{: tab-title="Dedicated Gateway Events"}
{: tab-group="connect-simple-2"}  

| Action                      | Description |
|-----------------------------|---------|
| `directlink.dedicated.virtual-connection.read` | Dedicated virtual connection was retrieved. |
| `directlink.dedicated.completion-notice.read` | Dedicated completion notice was retrieved. |
{: class="simple-tab-table"}
{: caption="Table 4. List of {{site.data.keyword.dl_short}} Dedicated Data Events" caption-side="left"}
{: #simpletabtable2}
{: tab-title="Dedicated Virtual Connection Events"}
{: tab-group="connect-simple-2"}  

## Events for {{site.data.keyword.dl_short}} Connect
{: #at_actions_connect}

### List of management events
{: #at_management_events_connect}

| Action                      | Description |
|-----------------------------|---------|
| `directlink.connect.gateway.create` | Connect gateway was retrieved. |
| `directlink.connect.gateway.delete` | Connect gateway was deleted. |
| `directlink.connect.gateway.update` | Connect gateway was updated. |
| `directlink.connect.gateway.action` | Connect gateway action was applied. |
{: class="simple-tab-table"}
{: caption="Table 5. List of {{site.data.keyword.dl_short}} Connect Gateway Events" caption-side="left"}
{: #simpletabtable1}
{: tab-title="Connect Gateway Events"}
{: tab-group="connect-simple-3"} 

| Action                      | Description |
|-----------------------------|---------|
| `directlink.connect.virtual-connection.create` | Connect virtual connection was created. |
| `directlink.connect.virtual-connection.delete` | Connect virtual connection was deleted. |
| `directlink.connect.virtual-connection.update` | Connect virtual connection was updated. |
{: class="simple-tab-table"}
{: caption="Table 6. List of {{site.data.keyword.dl_short}} Connect Virtual Connection Events" caption-side="left"}
{: #simpletabtable2}
{: tab-title="Connect Virtual Connection Events"}
{: tab-group="connect-simple-3"} 
 

### List of data events
{: #at_data_events_connect}

| Action                      | Description |
|-----------------------------|---------|
| `directlink.connect.gateway.read` | Connect gateway was retrieved. |
| `directlink.gateway.list`  | Dedicated and Connect gateways were listed. |
{: class="simple-tab-table"}
{: caption="Table 7. List of {{site.data.keyword.dl_short}} Connect Gateway Events" caption-side="left"}
{: #simpletabtable1}
{: tab-title="Connect Gateway Events"}
{: tab-group="connect-simple-4"} 

| Action                      | Description |
|-----------------------------|---------|
| `directlink.connect.virtual-connection.list` | Connect virtual connections were listed. |
| `directlink.connect.virtual-connection.read` | Connect virtual connection was retrieved. |
{: class="simple-tab-table"}
{: caption="Table 8. List of {{site.data.keyword.dl_short}} Connect Virtual Connection Events" caption-side="left"}
{: #simpletabtable2}
{: tab-title="Connect Virtual Connection Events"}
{: tab-group="connect-simple-4"} 

## Viewing events
{: #at_ui}

Events are available in the **Frankfurt (eu-de)** region.

To view these events, you must [provision an instance](/docs/services/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-provision#provision) of the {{site.data.keyword.at_full_notm}} service in the **Frankfurt (eu-de)** region. Then, you must [open the {{site.data.keyword.at_full_notm}} UI](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-launch).

## Analyzing events
{: #at_events_iam_analyze}

Refer to the following information when analyzing events:

- Use the search bar to search for `action:directlink.connect.virtual-connection` to get the list of events related to Direct Link Connect, or `action:directlink.dedicated.virtual-connection`  to get events that are related to Direct Link Dedicated.
- The target field identifies the Direct Link gateway assocated with an event. When the gateway exists in a different account or there is no gateway associated with the request, the target is set as `crn:v1:bluemix:public:directlink:global:a/<your account ID>:::`.  Events that don't correspond to a gateway will not have resource group information. For more information about cross-account gateway connections, see [Cross-account (VPC only) network connectivity with Direct Link](/docs/dl?topic=dl-add-virtual-connection#cross-account-virtual-connection). 
- Events that report update actions do not include information about the delta of the change.
- The event's initiator field contains information about who initiated each request. In authorized cross-account scenarios `IBM` is identified as the initiator. 
- The name of the service in {{site.data.keyword.cloud_notm}} is `directlink.connect`; therefore, all AT events have an action formatted as `<svcname>.<object>.<action>`, where `svcname` can be `directlink.connect` or `directlink.dedicated`.
