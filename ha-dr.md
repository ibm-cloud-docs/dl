---

copyright:
  years: 2025
lastupdated: "2025-06-17"

keywords: HA for direct link, DR for direct link, direct link recovery time objective, direct link recovery point objective

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Understanding high availability and disaster recovery for {{site.data.keyword.dl_full_notm}}
{: #ha-dr-dl}

[High availability](#x2284708){: term} (HA) is the ability for a service to remain operational and accessible in the presence of unexpected failures. [Disaster recovery](#x2113280){: term} (DR) is the process of recovering the service instance to a working state.
{: shortdesc}

{{site.data.keyword.cloud}} strongly recommends setting up a secondary, diverse direct link to avoid outages, whether unplanned or scheduled for maintenance. Effective disaster recovery, especially for issues impacting an entire location, requires careful planning and preparation.
{: attention}

IBM Cloud Direct Link is a highly available service designed to meet the [Service Level Objectives (SLO)](/docs/resiliency?topic=resiliency-slo). It is composed of zonal and regional configurations to fit a variety of needs. To better understand the underlying infrastructure, including definitions of data centers, zones, and Points of Presence (PoPs), see [IBM Cloud region and data center locations for resource deployment](/docs/overview?topic=overview-locations). For information about available regions and data center locations for Direct Link, see the Gateway section on the [Direct Link Connect](/interconnectivity/direct-link/connect/provision) or [Direct Link Dedicated](/interconnectivity/direct-link/dedicated/provision) provisioning pages.

To learn more about the IBM Cloud approach to high availability and disaster recovery, including platform-wide standards and best practices, see [How IBM Cloud ensures high availability and disaster recovery](/docs/resiliency?topic=resiliency-ha-redundancy#zero-downtime). You can also find information about high availability in the IBM Cloud [Service Level Agreement](https://www.ibm.com/support/customer/csol/terms/?id=i126-9268&lc=en){: external} (SLA). 

## High availability architecture
{: #ha-architecture}

Achieving a high availability (HA) architecture with IBM Cloud Direct Link requires more than just adding a second connection—it means eliminating all single points of failure, including those related to your connectivity providers. Provisioning a second Direct Link from a different location or network path is a good start, but true resilience depends on more than physical separation.

This is where the concepts of redundancy and diversity become important. Redundancy means having backup systems or connections in place so that if one fails, another can take over. Diversity goes a step further—it ensures that those backups are independent, ideally using different providers, infrastructure, or physical paths. Without diversity, redundant systems may still share a single point of failure.

For example, relying on a single provider for both Direct Link connections still introduces risk. To ensure full path redundancy, you should establish additional connections through diverse providers. This helps maintain connectivity to IBM Cloud even during provider-specific outages.

To further strengthen availability, IBM recommends deploying Direct Link Connect or Dedicated connections across multiple IBM Cloud zones. While IBM provides the infrastructure and tools to support resilient designs, it’s up to you to build and maintain architectures that meet their specific availability requirements. This includes distributing workloads across regions, implementing diverse connections, and regularly testing disaster recovery and failover procedures.

You are responsible for understanding how your Direct Link connection is configured, customized, and used. You are also responsible for re-creating an instance of the service in a new location and restoring your data. For information on how to design diversity to achieve HA with Direct Link, see [Models for diversity and redundancy in Direct Link](/docs/dl?topic=dl-models-for-diversity-and-redundancy-in-direct-link).
{: important}

### High availability features
{: #high-availability-features}
  
{{site.data.keyword.dl_full_notm}} supports the following high availability features:

| Feature| Description | Consideration |
| -------------- | -------------- | -------------- |
| IBM Cloud Transit Gateway | Attach multiple direct links to a transit gateway for centralized, scalable, and redundant network routing across VPCs and on-prem.	Centralizes routing, reduces complexity in large-scale deployments. | To avoid a single point of failure, deploy redundant transit gateways in separate zones or regions and attach direct links to each. Watch for configuration limits, such as attachment quotas and route propagation. |
| Border Gateway Protocol (BGP) support| Use BGP to dynamically reroute traffic in the event of a direct link failure, allowing fast recovery and automated path selection. | Must configure BGP session monitoring and route preference tuning to avoid asymmetric routing or failover delays. |
{: caption="High availability features for {{site.data.keyword.dl_full_notm}}" caption-side="bottom"}

As a customer, you can create and support the following other high availability features:

| Feature| Description | Consideration |
| -------------- | -------------- | -------------- |
| Multiple devices on-premises | Set up multiple redundant devices (for example, routers and switches) on-premises to ensure high availability in the network path to your direct link. | Plan for physical space, power, and cabling redundancy. Test failover scenarios regularly to ensure device-level HA works as expected. |
| Connection of on-premises devices to different PoPs and data centers | Connect devices (for example, routers and firewalls) to different Points of Presence (PoPs) or data centers to avoid single points of failure. | Evaluate network latency and bandwidth across PoPs and data centers. Ensure diverse physical paths and coordinate with providers to avoid shared risk groups. |
| AS prepending, BGP |  Configure AS prepending and BGP routing to manage traffic flow between active and passive connections.| Define clear routing policies for inbound and outbound traffic. Monitor BGP advertisements for correctness and adjust AS path strategies as needed.|
| Bidirectional Forwarding Detection (BFD)  | Enable BFD to quickly detect link failures and ensure rapid failover, improving availability.| Verify that all network elements support BFD. Monitor BFD session health and tune detection intervals carefully to balance sensitivity and false positives. |
{: caption="Customer HA features for {{site.data.keyword.dl_full_notm}}" caption-side="bottom"}
 
## Disaster recovery architecture
{: #disaster-recovery-intro}

IBM Cloud Direct Link plays a critical role in building resilient, high-availability architectures. For disaster recovery planning, Direct Link offers a range of features that are designed to support reliable, low-latency connectivity during disruptions.

Organizations can choose from multiple port speed options (50 Mbps to 10 Gbps) based on their data replication needs. While redundancy is not built-in, you can configure it by provisioning dual links across diverse cross-connect routers (XCRs) and implementing proper BGP failover strategies. Direct Link supports both local and global routing, enabling workload distribution across regions for improved resilience. Integration with multi-zone regions (MZRs) and support for configuration backup and recovery provide further protection against localized failures.

The following table outlines these features and key considerations.
 
### Disaster recovery features
{: #dr-features}

{{site.data.keyword.dl_full_notm}} supports the following disaster recovery features:
 
| Feature | Description | Consideration |
| -------------- | -------------- | -------------- |
| Local and Global routing | Direct Link includes both local and global routing, providing seamless connectivity to data centers within the same market (local routing) and across different geographic markets (global routing). | Global routing is necessary for inter-region workload sharing and disaster recovery across multiple regions. |
| Backup and recovery of configurations | IBM Cloud provides tools to back up Direct Link configurations, allowing you to restore services if there is a disaster. | Regular backups and testing of recovery procedures are recommended to ensure quick restoration during outages. |
| Multi-zone Region (MZR) support | Direct Link integrates with IBM Cloud's MZRs, enhancing availability and resilience by distributing workloads across multiple zones. | Proper deployment across multiple zones is necessary to achieve high availability and minimize the impact of zone-specific failures. |
{: caption="Disaster Recovery features for {{site.data.keyword.dl_full_notm}}" caption-side="bottom"}
 
As a customer, you can create and support the following other disaster recovery options:

| Feature | Description | Consideration |
| -------------- | -------------- | -------------- |
| Backup/restore scripts and backup data | Create and maintain their own backup and restore scripts, as well as securely store configuration and network state data, to expedite recovery during outages. | Ensure that backups are encrypted, versioned, and stored in geographically diverse locations. Automate backup schedules and periodically validate restore procedures. |
| Diverse Direct Link connections	| Establish diverse Direct Link connections across different regions or zones to ensure continuous connectivity during regional outages. | Implementing diverse connections requires careful planning of network architecture and BGP configurations to ensure seamless failover.|
| Data protection	| IBM provides robust solutions for data backup, retention, and recovery, which are critical for maintaining business continuity and supporting disaster recovery efforts. | Regularly test backup and restore processes to ensure data integrity and availability. |
{: caption="Customer disaster recovery features for {{site.data.keyword.dl_full_notm}}" caption-side="bottom"}

### Planning for disaster recovery
{: #disaster-recovery-planning}

It’s critical to regularly practice your disaster recovery steps to ensure that you are well-prepared for unexpected disruptions. As you build your disaster recovery plan, consider the following failure scenarios and resolutions for IBM Cloud Direct Link.

There can be multiple ways to recover from certain failures, so be sure to assess each scenario based on your specific architecture and requirements. Here are common failure scenarios, along with potential recovery actions:

| Failure | Resolution |
| -------------- | -------------- |
| PoP failure | Ensure that there are two or more connections that don't connect to the same PoP. |
| Data center (zone) failure | Ensure that there are two or more direct links across different zones to ensure failover. IBM Cloud Direct Link can reroute traffic automatically, but customer-side configuration improves resilience. |
| Region failure | Anticipate this by having connections in a restored region. If this is cost prohibitive, have VPN capabilities and associated scripts in place to replace direct link connections. |
| Hardware failure (single point)	|  The IBM Cloud Direct Link architecture is designed to handle single point hardware failures by providing diverse network connections. Failover occurs seamlessly, with no customer configuration needed. |  
| Network connection packet loss | Use monitoring tools to identify the root cause. Check for traffic spikes that exceed provisioned bandwidth, which can trigger policing and packet drops. Inspect ports, cabling, and network hardware for faults. If the issue persists or cannot be isolated, escalate to IBM Support for further investigation. |
| Two direct links are provisioned using different providers to the same PoP, but both are connected to the same hardware device, creating a single point of failure. | Ensure port diversity by checking port assignment details in the IBM Cloud console when ordering direct links. For nonintegrated providers (ordered separately in both the provider portal and IBM Cloud console), verify the port that is used by an existing link and select a different one. For API-integrated providers (where orders are initiated in the provider's portal and reflected in the IBM Cloud console), consult our [provider-specific instructions](/docs/dl?topic=dl-netbond). For dedicated direct links, check for existing cross-connects in the same PoP.|
{: caption="Disaster recovery scenarios for {{site.data.keyword.dl_full_notm}}" caption-side="bottom"} 

## Your responsibilities for HA and DR
{: #ha-dr-responsibilities}

For background information about responsibility ownership for using Direct Link between {{site.data.keyword.IBM_notm}} and you, the customer, see [Understanding your responsibilities when using IBM Cloud Direct Link](/docs/dl?topic=dl-dl-responsibilities). It is your responsibility to continuously test your plan for HA and DR.

Interruptions in network connectivity and short periods of unavailability of a service might occur. It is your responsibility to make sure that application source code includes [client availability retry logic](/docs/resiliency?topic=resiliency-high-availability-design#client-retry-logic-for-ha) to maintain high availability of the application.   
{: note}  

## Recovery time objective (RTO) 
{: #rto-features}  

Direct Link provides mechanisms to protect your data and restore service functions. Business continuity plans are in place to achieve targeted [recovery time objective](#x3167918){: term} (RTO) for the service. The following table outlines the targets for Direct Link.

| Feature | RTO |
| -------------- | -------------- |
| Redundancy configuration | Within minutes (usually < than 5 minutes)  |
| Routing | Automatic failover within minutes (typically < 2 minutes)   |
| Backup and recovery |Based on data size: ~10 minutes + 1 minute per 10 GB of data restored  |
| Multi-zone region | ~10 minutes + 1 minute per 10 GB if data restoration is needed | 
| Backup/restore scripts and backup data | 30 minutes – several hours, depending on automation and data volume |
| Diverse Direct Link connections | < 5 minutes (typically 1–2 minutes) if BGP and routing failover are properly configured and regularly tested  |
| Data protection, assuming IBM-provided tools | 10 minutes + 1 minute per 10 GB of data restored (same as IBM standard backup recovery) |
{: caption="RTO objectives for IBM Cloud Direct Link" caption-side="bottom"}

## Change management
{: #change-management}

Change management includes tasks such as upgrades, configuration changes, and deletion.

Grant users and processes the Identity and Access Management (IAM) roles and actions with the least privilege that is required for their work. For more information, see [How can I prevent accidental deletion of services?](/docs/resiliency?topic=resiliency-dr-faq#prevent-accidental-deletion).
{: tip} 

Best practices for managing change also include:
 
* Plan and document changes by maintaining a change log for any modifications that are made to your Direct Link configuration. 
* Create a backup of critical configurations before performing upgrade or major changes.
* Schedule upgrade or high-impact changes during low-traffic windows and notify impacted teams.
* Monitor your Direct Link connection health and metrics to ensure that everything is performing as expected. 

## How IBM supports disaster recovery planning
{: #ibm-disaster-recovery-planning}

IBM designs its infrastructure with resiliency in mind, especially for services like IBM Cloud Direct Link, which is critical for connecting on-premises networks to IBM Cloud. In the event of a failure:

* Incident response teams quickly identify and isolate the failure.
* Traffic rerouting is performed when possible using IBM’s backbone and provider networks.
* Service status communication is maintained through the IBM Cloud Status page to keep you informed.

When it comes to zone and regional failures, IBM takes the following recovery actions:

### How IBM recovers from zone failures
{: #ibm-zone-failure}

A zone failure refers to the failure of one data center or availability zone within a region. IBM mitigates the impact in these ways:

* Direct Link operates across multiple physical network paths. Diverse links and paths ensure that a failure in one zone doesn’t take down the entire connection.
* IBM constantly monitors the health of Direct Link endpoints. If a zone becomes unavailable, traffic can be rerouted to healthy zones where applicable.

If IBM can’t restore the service instance, you must restore the service as described in [Disaster recovery architecture](/docs/dl?topic=dl-ha-dr-dl#disaster-recovery-intro).    

### How IBM recovers from regional failures
{: #ibm-regional-failure}

In the rare event of a regional failure:

* IBM encourages you to architect workloads across multiple regions. Direct Link connections can be provisioned to different IBM Cloud regions, helping reduce the impact of a regional outage.
* IBM’s global backbone and partnerships with major telecom network providers offer alternative routes for traffic if a region becomes unavailable.
* IBM supports your disaster recovery plans by enabling provisioning of Direct Link in multiple regions. It is recommended that you configure diverse links in secondary regions that can be activated as needed.

If {{site.data.keyword.IBM_notm}} can’t restore the service instance, you must restore the service as described in the [Disaster recovery architecture](#disaster-recovery-intro).

## How IBM maintains services
{: #ibm-service-maintenance}

All upgrades follow {{site.data.keyword.IBM_notm}} service best practices, including recovery plans and rollback processes. Regular maintenance might cause short interruptions, mitigated by [client availability retry logic](/docs/resiliency?topic=resiliency-high-availability-design#client-retry-logic-for-ha). Changes are rolled out sequentially, region by region, and zone by zone within a region. {{site.data.keyword.IBM_notm}} reverts updates at the first sign of a defect. 

IBM provides advance notice for all planned maintenance activities. If a change is expected to affect your workloads, IBM communicates this through official notifications. To stay updated on maintenance, service announcements, and other updates, see the [Monitoring notifications and status](/docs/account?topic=account-viewing-cloud-status) page.
