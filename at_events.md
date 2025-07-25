---

copyright:
  years: 2020, 2025
lastupdated: "2025-06-17"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Activity tracking events for {{site.data.keyword.dl_full_notm}}
{: #at_events}

{{site.data.keyword.cloud_notm}} services, such as {{site.data.keyword.dl_full_notm}}, generate activity tracking events.
{: shortdesc}

Activity tracking events report on activities that change the state of a service in {{site.data.keyword.cloud_notm}}. You can use the events to investigate abnormal activity and critical actions and to comply with regulatory audit requirements.

You can use {{site.data.keyword.atracker_full_notm}}, a platform service, to route auditing events in your account to destinations of your choice by configuring targets and routes that define where activity tracking events are sent. For more information, see [About {{site.data.keyword.atracker_full_notm}}](/docs/atracker?topic=atracker-about).

You can use {{site.data.keyword.logs_full_notm}} to visualize and alert on events that are generated in your account and routed by {{site.data.keyword.atracker_full_notm}} to an {{site.data.keyword.logs_full_notm}} instance.

Activity tracker events are captured for all locations, even if recorded in `eu-de`. Because Direct Link is a global control plan, if you perform an action to a resource in `us-south`, it's handled by that control plane and logged in the `us-south` location (by default).
{: remember}

## Locations where activity tracking events are generated
{: #at-locations}

{{site.data.keyword.dl_short}} is a global service, and can generate activity tracking events in all regions.

By default, Direct Link activity tracking events are stored in the Frankfurt (eu-de) location. If you prefer not to store these events in this region, you can set up your AT log routing rules to route to an AT instance in a different location.

## Viewing activity tracking events for {{site.data.keyword.dl_full_notm}}
{: #at-viewing}

You can use {{site.data.keyword.logs_full_notm}} to visualize and alert on events that are generated in your account and routed by {{site.data.keyword.atracker_full_notm}} to an {{site.data.keyword.logs_full_notm}} instance.

### Launching {{site.data.keyword.logs_full_notm}} from the Observability page
{: #log-launch-standalone}

For information on launching the {{site.data.keyword.logs_full_notm}} UI, see [Launching the UI in the {{site.data.keyword.logs_full_notm}} documentation.](/docs/cloud-logs?topic=cloud-logs-instance-launch)

## List of management events
{: #at_actions}

The following table lists actions that generate management events.

| Action             | Description      |
|--------------------|------------------|
| `directlink.dedicated.gateway.create` | A Dedicated gateway was created. |
| `directlink.dedicated.gateway.delete` | A Dedicated gateway was deleted. |
| `directlink.dedicated.gateway.update` | A Dedicated gateway was updated. |
| `directlink.dedicated.completion-notice.create` | A Dedicated completion notice was created. |
| `directlink.dedicated.completion-notice.read` | A Dedicated completion notice was retrieved. |
| `directlink.gateway.route-report.create` | A route report was created. |
| `directlink.gateway.route-report.delete` | A route report was deleted. |
| `directlink.dedicated.virtual-connection.create` | A Dedicated virtual connection was created. |
| `directlink.dedicated.virtual-connection.delete` | A Dedicated virtual connection was deleted. |
| `directlink.dedicated.virtual-connection.update` | A Dedicated virtual connection was updated. |
| `directlink.connect.gateway.create` | A Connect gateway was retrieved. |
| `directlink.connect.gateway.delete` | A Connect gateway was deleted. |
| `directlink.connect.gateway.update` | A Connect gateway was updated. |
| `directlink.connect.gateway.action` | A Connect gateway action was applied. |
| `directlink.gateway.route-report.create` | A route report was created. |
| `directlink.gateway.route-report.delete` | A route report was deleted. |
| `directlink.connect.virtual-connection.create` | A Connect virtual connection was created. |
| `directlink.connect.virtual-connection.delete` | A Connect virtual connection was deleted. |
| `directlink.connect.virtual-connection.update` | A Connect virtual connection was updated. |
{: caption="Actions that generate management events" caption-side="bottom"}

## List of data events
{: #at_actions_data}

| Action                           | Description                        |
|----------------------------------|------------------------------------|
| `directlink.dedicated.gateway.read` | A Dedicated gateway was retrieved. |
| `directlink.gateway.list` | Dedicated and Connect gateways were listed. |
| `directlink.gateway.route-report.read` | A route report was retrieved. |
| `directlink.gateway.route-report.list` | A route report was listed. |
| `directlink.dedicated.virtual-connection.read` | A Dedicated virtual connection was retrieved. |
| `directlink.dedicated.virtual-connection.list` | A Dedicated gateway's virtual connections were listed. |
| `directlink.connect.gateway.read` | A Connect gateway was retrieved. |
| `directlink.gateway.list`  | Dedicated and Connect gateways were listed. |
| `directlink.gateway.route-report.read` | A route report was retrieved. |
| `directlink.gateway.route-report.list` | A route reports were listed. |
| `directlink.connect.virtual-connection.list` | A Connect virtual connections were listed. |
| `directlink.connect.virtual-connection.read` | A Connect virtual connection was retrieved. |
{: caption="Actions that generate data events" caption-side="bottom"}

## Analyzing {{site.data.keyword.dl_full_notm}} activity tracking events
{: #at_events_iam_analyze}

Refer to the following information when analyzing events:

- Use the search bar to search for `action:directlink.connect.virtual-connection` to get the list of events related to Direct Link Connect, or `action:directlink.dedicated.virtual-connection`  to get events that are related to Direct Link Dedicated.
- The target field identifies the direct link that is associated with an event. When the gateway exists in a different account or there is no gateway that is associated with the request, the target is set as `crn:v1:bluemix:public:directlink:global:a/<your account ID>:::`.  Events that do not correspond to a gateway don't have resource group information. For more information about cross-account gateway connections, see [Adding a cross-account (VPC only) connection](/docs/dl?topic=dl-cross-account-virtual-connection-vpc).
- Events that report update actions do not include information about the delta of the change.
- The event's initiator field contains information about who initiated each request. In authorized cross-account scenarios, `IBM` is identified as the initiator.
- The name of the service in {{site.data.keyword.cloud_notm}} is `directlink.connect`; therefore, all AT events have an action formatted as `<svcname>.<object>.<action>`, where `svcname` can be `directlink.connect` or `directlink.dedicated`.
