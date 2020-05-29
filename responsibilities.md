---

copyright:
  years: 2020
lastupdated: "2020-05-14"

---

{:new_window: target="_blank_"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:download: .download}
{:preview: .preview}

# Understanding your responsibilities when using IBM Cloud Direct Link
{: #dl-responsibilities}

Learn about the management responsibilities and terms and conditions that you have when you use {{site.data.keyword.dl_full_notm}}. For a high-level view of the service types in {{site.data.keyword.Bluemix}} and the breakdown of responsibilities between the customer and {{site.data.keyword.IBM_notm}} for each type, see [Shared responsibilities for {{site.data.keyword.cloud_notm}} offerings](/docs/overview?topic=overview-shared-responsibilities).
{:shortdesc}

Review the following sections for the specific responsibilities for you and for {{site.data.keyword.IBM_notm}} when you use {{site.data.keyword.dl_full_notm}}. For the overall terms of use, see [{{site.data.keyword.Bluemix}} Terms and Notices](/docs/overview/terms-of-use?topic=overview-terms).

## IBM Cloud infrastructure
{: #ibmcloud-infrastructure}

You and IBM have unique responsibilities for infrastructure provisioning and management.

| Responsibilities |  Ownership |
|---------------------------|------|
| Deploy a fully managed, highly available, secured, IBM-owned infrastructure. | IBM |
| Provision and manage the Direct Link gateway. | IBM |
| Fulfill requests for Direct Link connections. | IBM |
| Fulfill requirements for additional capacity based on use. | IBM |
| Provide partner relationships with physical locations for Direct Link interconnects. | IBM |
| Follow the instructions in the {{site.data.keyword.dl_full_notm}} user documentation to make any necessary configurations, such as BGP, setting up local or global routing and connections to resources. | Customer |
| Understand Direct Link is *not* a redundant service; and while IBM Cloud supplies Diverse Router (XCR) options, failover must be built into the BGP scheme a customer deploys between multiple Direct Links. | Customer|
| Use the provided capabilities, and adjust networking configurations to meet the needs of your workload. | Customer |
| Order cross-connects via chosen service provider (such as Equinix and AT&T) as needed for Direct Link Dedicated. | Customer |
| Upload Completion notice from service provider when Cross Connect is completed by chosen service provider. | Customer |
| Monitor service notifications for communications regarding maintenance operations. | Customer |
| Make sure that any self-provided BGP addresses do not conflict with blocks that are used by IBM or by resources external to your deployment. | Customer |
| Make sure that there are no IP address conflicts between on-premises subnets and subnets on IBM Cloud for both VPC and Classic infrastructure connections. | Customer |
| Establish diversity and redundancy as needed. | Customer |
| Design and deploy your workload in a way that achieves the wanted availability and Disaster Recovery capabilities by using our provided tools. For example, deploy in different zones of a region, use at least two load balancers that are located in different zones, and either use DNS records to point to the load balancers, or ensure that your application can handle a list of IP addresses that it can connect to.

{: caption="Table 1. IBM Cloud infrastructure responsibilities" caption-side="top"}

## Security and regulation compliance
{: #security-rich-environment}

You and IBM have unique responsibilities for security and compliance.

| Responsibilities |  Ownership |
|---------------------------|------|
| Maintain General Data Protection Regulation (GDPR) readiness for customer compliance. | IBM |
| Enable security features. | IBM |
| Restrict user access to the appropriate resources and resource groups. | Customer |
{: caption="Table 2. Security and regulation responsibilities" caption-side="top"}

## Disaster recovery
{: #disaster-recovery-responsibilities}

You and IBM have unique responsibilities for disaster recovery.

| Responsibilities |  Ownership |
|----------|-----------------------|
| Provide diverse network options for consumption. | IBM |
| Ensure diversity of Direct Link is deployed. | Customer |
{: caption="Table 3. Disaster recovery responsibilities" caption-side="top"}
