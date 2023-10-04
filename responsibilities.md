---

copyright:
  years: 2020, 2023
lastupdated: "2023-10-04"

keywords: direct link responsibilities

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Understanding your responsibilities when using {{site.data.keyword.dl_full_notm}}
{: #dl-responsibilities}

Learn about the management responsibilities and terms and conditions that you have when you use {{site.data.keyword.dl_full_notm}}. For a high-level view of the service types in {{site.data.keyword.Bluemix}} and the breakdown of responsibilities between the customer and {{site.data.keyword.IBM_notm}} for each type, see [Shared responsibilities for {{site.data.keyword.cloud_notm}} offerings](/docs/overview?topic=overview-shared-responsibilities).
{: shortdesc}

Review the following sections for the specific responsibilities for you and for {{site.data.keyword.IBM_notm}} when you use {{site.data.keyword.dl_full_notm}}. For the overall terms of use, see [{{site.data.keyword.Bluemix}} Terms and Notices](/docs/overview/terms-of-use?topic=overview-terms).

## Incident and operations management
{: #incident-and-ops}

Incident and operations management includes tasks, such as monitoring, event management, high availability, problem determination, recovery, and full state backup and recovery.

| Task | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|----------|-----------------------|--------|
| High Availability | {{site.data.keyword.IBM_notm}} is responsible for deploying a fully managed, highly available, secure, IBM-owned infrastructure.  | The Customer is responsible for ordering two diverse direct links, and create a Border Gateway Protocol (BGP) schema that allows for failover between the two links. |
| Management | {{site.data.keyword.IBM_notm}} provisions and manages the {{site.data.keyword.dl_short}} gateway. | The Customer is responsible for:  \n Following instructions in the {{site.data.keyword.dl_full_notm}} user documentation to make any necessary configurations, such as BGP.  \n Setting up routing, adding virtual connections to resources, and adjusting networking configurations to meet the needs of their workloads.  \n Making sure that any self-provided BGP addresses do not conflict with blocks that are used by IBM, or by resources external to your deployment.  \n Ensuring that there are no IP address conflicts between on-premises subnets, and subnets on IBM Cloud for both VPC and classic infrastructure connections. |
| Fulfillment| {{site.data.keyword.IBM_notm}} fulfills requests for {{site.data.keyword.dl_short}} connections and additional capacity based on use. | The Customer is responsible for monitoring service notifications for communications regarding maintenance operations. The Customer is also responsible for uploading the Completion notice from their service provider when Cross Connect is completed by the chosen service provider. |
| Partnership | {{site.data.keyword.IBM_notm}} provides partner relationships with physical locations for {{site.data.keyword.dl_short}} interconnects. | The Customer is responsible for ordering connectivity services from appropriate partner.|
| Performance | A Customer can achieve 99.99% effectively with two or more direct links that are properly configured for failover by using BGP, but IBM cannot control that. | The Customer is responsible for opening tickets in the event of an outage to track performance. |
| IP addressing | {{site.data.keyword.IBM_notm}} assigns the subnets to VPCs specified by the Customer. | The Customer is responsible for ensuring no IP  overlap on their on-premises subnet. |
{: caption="Table 1. Responsibilities for incident and operations" caption-side="bottom"}

## Change management
{: #change-management}

Change management includes tasks, such as deployment, configuration, upgrades, patching, configuration changes, and deletion.

| Task | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|----------|-----------------------|--------|
| Major version upgrades| {{site.data.keyword.IBM_notm}} is responsible for providing availability and tooling for major version updates. | The Customer is responsible for migrating to a supported version before end-of-support for an old version. |
| API version changes| {{site.data.keyword.IBM_notm}} is responsible for versioning the REST APIs.  | The Customer is responsible for integrating with the desired version of REST APIs. |
| Scaling | {{site.data.keyword.IBM_notm}} is responsible for scaling infrastructure as requested and to meet the capacity that you selected. | The Customer is responsible for ordering the appropriate Direct Link port speed in the IBM Cloud console. |
| Updates, fixes, and new features | {{site.data.keyword.IBM_notm}} is responsible for providing regular updates, bug fixes, and new features, following a continuous delivery model in a way that is transparent to you. Notifications are posted for changes that impact you.  | The Customer is responsible for reading system-generated notifications and taking appropriate action.
{: caption="Table 2. Responsibilities for change management" caption-side="bottom"}

## Traffic management
{: #traffic-management}

Traffic management includes tasks, such as bandwidth monitoring, packet inspection, forwarding detection, and traffic routing.

| Task | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|----------|-----------------------|--------|
| Equal-cost multipath (ECMP)| N/A | {{site.data.keyword.IBM_notm}} does not offer equal-cost multi-pathing, outbound from the direct link router to the customer router. The Customer is responsible for configuring ECMP on their equipment to load-balancer traffic into IBM Cloud.|
| API version changes| {{site.data.keyword.IBM_notm}} is responsible for versioning the REST APIs.  | The Customer is responsible for integrating with the desired version of REST APIs. |
| Scaling | {{site.data.keyword.IBM_notm}} is responsible for scaling infrastructure as requested and to meet the capacity that you selected. | The Customer is responsible for ordering the appropriate Direct Link port speed in the IBM Cloud console. |
| Updates, fixes, and new features | {{site.data.keyword.IBM_notm}} is responsible for providing regular updates, bug fixes, and new features, following a continuous delivery model in a way that is transparent to you. Notifications are posted for changes that impact you.  | The Customer is responsible for reading system-generated notifications and taking appropriate action.
{: caption="Table 3. Responsibilities for traffic management" caption-side="bottom"}

## Identity and access management
{: #iam-responsibilities}

Identity and access management includes tasks, such as authentication, authorization, access control policies, and approving, granting, and revoking access.

| Task | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|----------|-----------------------|--------|
| Identity and access | {{site.data.keyword.IBM_notm}} provides the function to restrict access to resources through the IBM Cloud console and REST APIs.  | The Customer is responsible for managing access to resources through IBM Cloud Identity and Access Management (IAM). |
{: caption="Table 4. Responsibilities for identity and access management" caption-side="bottom"}

## Security and regulation compliance
{: #security-compliance}

Security and regulation compliance includes tasks, such as security controls implementation and compliance certification.

| Task |  {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|---------------------------|------|-----|
| Encryption | {{site.data.keyword.IBM_notm}} does not provide encryption capabilities.| The Customer is responsible for encryption of data on disk, in motion, and in backups. The Customer is also responsible for choosing and managing appropriate additional security features. If the Customer uses Key Protect (Bring Your Own Key), or another form of encryption, the Customer is responsible for managing the service authorization and keys. |
| Security | {{site.data.keyword.IBM_notm}} is responsible for ensuring the security of data on disk and data in motion within its infrastructure. | The Customer is responsible for restricting user access to the appropriate resources and resource groups. |
{: caption="Table 5. Responsibilities for security and regulation compliance" caption-side="bottom"}

## Disaster recovery
{: #disaster-recovery-responsibilities}

Disaster recovery includes tasks, such as providing dependencies on disaster recovery sites, provision disaster recovery environments, data and configuration backup, replicating data and configuration to the disaster recovery environment, and failover on disaster events.

| Task | {{site.data.keyword.IBM_notm}} Responsibilities |  Your Responsibilities |
|----------|-----------------------|-------|
| Diversity | {{site.data.keyword.IBM_notm}} provides diverse network options for consumption. | The Customer must ensure diversity of {{site.data.keyword.dl_short}} is deployed. |
| Redundancy | {{site.data.keyword.IBM_notm}} provides diverse network options for consumption. Direct Link is not a redundant service. | The Customer is responsible for establishing redundancy, as needed, via BGP schema. The Customer must also understand that {{site.data.keyword.dl_short}} is *not* a redundant service. While IBM Cloud supplies Diverse Router (XCR) options, failover must be built into the BGP scheme a customer deploys between multiple {{site.data.keyword.dl_short}}s. |
| Host service in multiple regions | {{site.data.keyword.IBM_notm}} is responsible for hosting this service in multiple regions. | The Customer is responsible for designing and deploying their workload in a way that achieves the wanted availability and Disaster Recovery capabilities by using provided tools. For example, deploy in different zones of a region, use at least two load balancers that are located in different zones, and either use DNS records to point to the load balancers, or ensure that your application can handle a list of IP addresses that it can connect to. |
| Backup user configuration data | {{site.data.keyword.IBM_notm}} is not responsible for backup of user configuration data. | The Customer is responsible for backup of configuration data, as needed. |
| Backup and recovery of workload | {{site.data.keyword.IBM_notm}} is not responsible for backup or recovery of user configuration data. |  The Customer is responsible for backup and recovery of their workloads, as needed. |
{: caption="Table 6. Responsibilities for disaster recovery" caption-side="bottom"}
