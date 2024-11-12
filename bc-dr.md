---

copyright:
  years: 2024
lastupdated: "2024-11-12"

keywords:

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Understanding business continuity and disaster recovery for Direct Link
{: #bc-dr}

[Disaster recovery](#x2113280){: term} involves a set of policies, tools, and procedures for returning a system, an application, or an entire data center to full operation after a catastrophic interruption. It includes procedures for copying and storing an installed system's essential data in a secure location, and for recovering that data to restore normalcy of operation.
{: shortdesc}

In the event of a catastrophic failure that impacts an entire region, and the {{site.data.keyword.dl_short}} physical link between on-premises and {{site.data.keyword.cloud_notm}} was in that region, you would experience an outage. If you require a highly available connection to {{site.data.keyword.cloud_notm}}, it is imperative that you have a redundant connection in a second region. If you decide to rely on a single connection, it is recommended that you back up all configuration elements in case you would ever have to re-create your {{site.data.keyword.dl_short}} gateway and virtual connections. For information on how to design Diversity to achieve HA with Direct Link, see [Models for diversity and redundancy in Direct Link](/docs/dl?topic=dl-models-for-diversity-and-redundancy-in-direct-link).

## Responsibilities
{: #bc-dr-responsibilities}

To find out more about responsibility ownership for using {{site.data.keyword.cloud}} products between {{site.data.keyword.IBM_notm}} and customer see [Understanding your responsibilities when using Direct Link](/docs/dl?topic=dl-dl-responsibilities).

## Disaster recovery strategy
{: #bc-dr-strategy}

{{site.data.keyword.cloud_notm}} has [business continuity](#x3026801){: term} plans in place to provide for the recovery of services within hours if a disaster occurs. You are responsible for your data backup and associated recovery of your content.

Direct Link provides mechanisms to protect your data and restore service functions. Business continuity plans are in place to achieve targeted [recovery point objective](#x3429911){: term} (RPO) and [recovery time objective](#x3167918){: term} (RTO) for the service. The following table outlines the targets for Direct Link.

| Disaster recovery objective | Target value |
|---|---|
|  RPO | 24 hrs |
|  RTO | 24 hrs |
{: caption="Table 1. RPO and RTO for Direct Link" caption-side="bottom"}

## Locations
{: #ha-locations}

For more information about service availability within regions and data centers, see [Service and infrastructure availability by location](/docs/overview?topic=overview-services_region).

## Backing up {{site.data.keyword.dl_short}} gateways for disaster recovery
{: #disaster-recovery-dl}

Be prepared to re-create your {{site.data.keyword.dl_short}} gateways and connections. This section helps you ensure that you have all the data needed.

{{site.data.keyword.dl_short}} backups are cross-regionally durable. Backups are stored across multiple regions, and are restorable to other regions.
{: note}

Preserve a list of all your direct links and their connections. To do so, perform the following procedure:

The following steps use the IBM Cloud CLI, but you can also use the {{site.data.keyword.cloud_notm}} console or API.
{: tip}

1. Use the `ibmcloud dl gateways` command to list details about all your direct links. Save this output.
2. For each gateway, use the `ibmcloud dl virtual-connections GATEWAY_ID` command to list information about its connections. Save this output.

For more information, see the [{{site.data.keyword.dl_short}} CLI reference](/docs/dl?topic=dl-dl-cli).

Saving the information that is returned from these commands helps you recover from a failure quickly. If a failure occurs, use the saved information and run the `ibmcloud dl gateway-create` and `ibmcloud dl virtual-connection-create` commands to re-create your direct links and their connections.
