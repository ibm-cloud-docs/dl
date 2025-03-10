---

copyright:
  years: 2024, 2025
lastupdated: "2025-03-10"
keywords: service metrics

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Monitoring Direct Link
{: #monitoring}

[IBM Cloud Monitoring](https://www.ibm.com/products/cloud-monitoring){: external} is a cloud-native and container-intelligent management system that you can include as part of your IBM Cloud architecture. Use it to gain operational visibility into the performance and health of your applications, services, and platforms. It offers administrators, DevOps teams, and developers full-stack telemetry with advanced features to monitor and troubleshoot, define alerts, and design custom dashboards.
{: shortdesc}

Service metrics enable gathering usage and status metrics. Metrics datasets are available on a metrics-enabled instance in the same region. You can visualize and analyze metrics from the respective metrics-enabled instance.

## Platform metrics overview
{: #platform-metrics-pm}

You can configure only one instance of the {{site.data.keyword.mon_full}} service per region to collect service metrics. Service metrics are enabled by default in all instances and cannot be disabled.

- Provision an instance of the {{site.data.keyword.mon_full_notm}} service. After you provision the Monitoring instance, the *Observability* page opens. To continue working with {{site.data.keyword.cloud_notm}}, go back to the {{site.data.keyword.cloud_notm}} console.
- To configure the Monitoring instance, you must turn on the *service metrics* configuration setting.
- If a Monitoring instance in a region is already enabled to collect service metrics, metrics from enabled-monitoring services are collected automatically and available for monitoring through this instance. For more information about enabled-monitoring services, see [IBM Cloud Monitoring](https://www.ibm.com/products/cloud-monitoring){: external}.

To monitor service metrics, check that the Monitoring instance is provisioned in the same region where the {{site.data.keyword.cloud_notm}} instance is provisioned.
{: important}

## Metrics available for Direct Link
{: #metrics_dictionary-pm}

Each metric is composed of the following metadata types:

* Metric name - The name for the collected metric.
* Metric type - Determines whether the metric value is a counter metric or a gauge metric. Each of these metrics is of type `gauge`, which represents a single numerical value that can arbitrarily fluctuate over time.
* Value type - A unit of measurement for a specific metric. Examples include bytes or counts. A value type of `none` means that the metric value represents individual occurrences of that metric type.
* Segment - How you want {{site.data.keyword.mon_full_notm}} to divide and display the monitoring metrics.

### Direct Link Connect - Bytes per second data for egress traffic
{: #ibm_cloud_direct_link_connect_bytes_per_second_egress}

Bytes per second data for all the egress data flow on a gateway.

The metric contains the following metadata:

| Metadata | Description |
|----------|-------------|
| Metric name | `ibm_directlink_connect_gateway_egress_bytes_per_second` |
| Metric type | `gauge` |
| Value type | `bytes per second` |
| Segment by | `ibm_ctype`, `ibm_scope`,`ibm_location`,`ibm_service_name`, `ibm_resource_name`, `ibm_resource`, `ibm_resource_type`|
{: caption="IBM Cloud Direct Link Connect egress bytes per second metrics" caption-side="bottom"}

### Direct Link Connect - Bytes Per Second data for ingress Traffic
{: #ibm_cloud_direct_link_connect_bytes_per_second_ingress}

Bytes per second data for all the ingress data flow on a gateway.

The metric contains the following metadata:

| Metadata | Description |
|----------|-------------|
| Metric name | `ibm_directlink_connect_gateway_ingress_bytes_per_second` |
| Metric type | `gauge` |
| Value type | `bytes per second` |
| Segment by | `ibm_ctype`, `ibm_scope`,`ibm_location`,`ibm_service_name`, `ibm_resource_name`, `ibm_resource`, `ibm_resource_type`|
{: caption="IBM Cloud Direct Link Connect ingress bytes per second metrics" caption-side="bottom"}

### Direct Link Dedicated - Bytes per second data for egress traffic
{: #ibm_cloud_direct_link_dedicated_bytes_per_second_egress}

Bytes per second data for all the egress data flow on a gateway.

The metric contains the following metadata:

| Metadata | Description |
|----------|-------------|
| Metric name | `ibm_directlink_dedicated_gateway_egress_bytes_per_second` |
| Metric type | `gauge` |
| Value type | `bytes per second`|
| Segment by |`ibm_ctype`, `ibm_scope`,`ibm_location`,`ibm_service_name`, `ibm_resource_name`, `ibm_resource`, `ibm_resource_type`|
{: caption="IBM Cloud Direct Link Dedicated egress bytes per second metrics" caption-side="bottom"}

### Direct Link Dedicated - Bytes per second data for ingress traffic
{: #ibm_cloud_direct_link_dedicated_bytes_per_second_ingress}

Bytes per second data for all the ingress data flow on a gateway.

The metric contains the following metadata:

| Metadata | Description |
|----------|-------------|
| Metric name | `ibm_directlink_dedicated_gateway_ingress_bytes_per_second` |
| Metric type | `gauge` |
| Value type | `bytes per second`|
| Segment by |`ibm_ctype`, `ibm_scope`,`ibm_location`,`ibm_service_name`, `ibm_resource_name`, `ibm_resource`, `ibm_resource_type`|
{: caption="IBM Cloud Direct Link Dedicated ingress bytes per second metrics" caption-side="bottom"}

### Direct Link Dedicated - Packets per second data for egress traffic
{: #ibm_cloud_direct_link_dedicated_packets_per_second_egress}

Packets per second data for all the egress data flow on a gateway.

The metric contains the following metadata:

| Metadata | Description |
|----------|-------------|
| Metric name | `ibm_directlink_dedicated_gateway_egress_packet_per_second` |
| Metric type | `gauge` |
| Value type | `packets per second`|
| Segment by |`ibm_ctype`, `ibm_scope`,`ibm_location`,`ibm_service_name`, `ibm_resource_name`, `ibm_resource`, `ibm_resource_type`|
{: caption="IBM Cloud Direct Link Dedicated egress packets per second metrics" caption-side="bottom"}

### Direct Link Dedicated - Packets per second data for ingress traffic
{: #ibm_cloud_direct_link_dedicated_packets_per_second_ingress}

Packets per second data for all the ingress data flow on a gateway.

The metric contains the following metadata:

| Metadata | Description |
|----------|-------------|
| Metric name | `ibm_directlink_dedicated_gateway_ingress_packet_per_second` |
| Metric type | `gauge` |
| Value type | `packets per second`|
| Segment by |`ibm_ctype`, `ibm_scope`,`ibm_location`,`ibm_service_name`, `ibm_resource_name`, `ibm_resource`, `ibm_resource_type`|
{: caption="IBM Cloud Direct Link Dedicated ingress packets per second metrics" caption-side="bottom"}

### Direct Link Dedicated - Packets dropped per second data for ingress traffic
{: #ibm_cloud_direct_link_dedicated_packets_dropped_per_second_ingress}

Packets dropped per second data for all the ingress data flow on a gateway.

The metric contains the following metadata:

| Metadata | Description |
|----------|-------------|
| Metric name | `ibm_directlink_dedicated_gateway_ingress_packet_dropped_per_second` |
| Metric type | `gauge` |
| Value type | `packets per second`|
| Segment by |`ibm_ctype`, `ibm_scope`,`ibm_location`,`ibm_service_name`, `ibm_resource_name`, `ibm_resource`, `ibm_resource_type`|
{: caption="IBM Cloud Direct Link Dedicated ingress packets dropped per second metrics" caption-side="bottom"}

### Direct Link Dedicated - Error count data
{: #ibm_cloud_direct_link_dedicated_error_count}

Error count data for all the data flow on a gateway.

The metric contains the following metadata:

| Metadata | Description |
|----------|-------------|
| Metric name | `ibm_directlink_dedicated_gateway_error_count_per_second` |
| Metric type | `count` |
| Value type | `none`|
| Segment by |`ibm_ctype`, `ibm_scope`,`ibm_location`,`ibm_service_name`, `ibm_resource_name`, `ibm_resource`, `ibm_resource_type`|
{: caption="IBM Cloud Direct Link Dedicated error count metrics" caption-side="bottom"}

The Segment by labels correspond to the following definitions:

* **ibm_ctype** - Type of cloud gateway: `public`
* **ibm_scope** - The account that is associated with a given gateway
* **ibm_location** - Gateway location
* **ibm_service_name** - `directlink`
* **ibm_resource_name** - Gateway name
* **ibm_resource** - Gateway resource ID
* **ibm_resource_type** - Type of resource: `connect` or `dedicated`

### Launching {{site.data.keyword.mon_full_notm}} web UI from the Observability page
{: #view_metrics}

Complete the following steps to launch the {{site.data.keyword.mon_full_notm}} web UI from the *Observability* page:

1. [Launch the {{site.data.keyword.mon_full_notm}} web UI](/docs/monitoring?topic=monitoring-launch).
1. Click **DASHBOARDS**.
1. In the **Default Dashboards** section, expand **{{site.data.keyword.IBM_notm}}**.
1. Choose the Direct Link Overview Dashboard from the list.

   You can also reach your deployment's {{site.data.keyword.mon_full_notm}} dashboard from {{site.data.keyword.mon_full_notm}} in the sidebar, under {{site.data.keyword.IBM_notm}}.

   Next, change the scope or make a copy of the *Default* dashboard to monitor a Direct Link gateway.

For more options to customize your dashboard, follow the steps in [Creating custom dashboards in the Web UI](/docs/monitoring?topic=monitoring-dashboards#dashboards_create).
