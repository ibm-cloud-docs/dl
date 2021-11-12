---

copyright:
  years: 2020
lastupdated: "2020-07-02"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# High availability and disaster recovery for {{site.data.keyword.dl_short}}
{: #ha-dr}

The {{site.data.keyword.dl_full}} global service is highly available within any {{site.data.keyword.cloud_notm}} location. However, recovering from disasters that affect an entire location requires planning and preparation.
{: shortdesc}

You are responsible for understanding your connection configuration, customization, and usage of the service. You are also responsible for being ready to re-create an instance of the service in a new location and restore your data there.  For information on how to design Diversity to achieve HA with Direct Link, see [Models for diversity and redundancy in Direct Link](/docs/dl?topic=dl-models-for-diversity-and-redundancy-in-direct-link).

## High availability within the service
{: #high-availability}

{{site.data.keyword.cloud_notm}} service supports high availability with no single point of failure. The service achieves high availability automatically and transparently by means of the Multi-Zone Region ([MZR](/docs/overview?topic=overview-locations#mzr-table)) feature provided by {{site.data.keyword.cloud_notm}}.

## High availability for customer {{site.data.keyword.dl_short}} connections
{: #high-availability-customer}

Your {{site.data.keyword.dl_short}} connections are location specific. It is up to you to set up any High Availability or Disaster Recovery plans that are required. For information on how to design Diversity to achieve HA with Direct Link, see [Models for diversity and redundancy in Direct Link](/docs/dl?topic=dl-models-for-diversity-and-redundancy-in-direct-link).

## Disaster recovery
{: #disaster-recovery}

In the event of a catastrophic failure impacting an entire region, and the {{site.data.keyword.dl_short}} physical link between on-premises and {{site.data.keyword.cloud_notm}} was in that region, you would experience an outage. If you require a highly available connection to {{site.data.keyword.cloud_notm}}, it is imperative that you have a redundant connection in a second region. If you decide to rely on a single connection, it is recommended that you back up all configuration elements in case you would ever have to recreate your {{site.data.keyword.dl_short}} gateway and virtual connections. For information on how to design Diversity to achieve HA with Direct Link, see [Models for diversity and redundancy in Direct Link](/docs/dl?topic=dl-models-for-diversity-and-redundancy-in-direct-link).

### Backing up {{site.data.keyword.dl_short}} gateways for disaster recovery
{: #disaster-recovery-dl}

You must be prepared to recreate your {{site.data.keyword.dl_short}} gateways and connections. This section helps you ensure that you have all the data needed.

{{site.data.keyword.dl_short}} backups are cross-regionally durable. Backups are stored across multiple regions, and are restorable to other regions.
{: note}

Preserve a list of all your direct links and their connections. To do so, perform the following procedure:

The following steps use the IBM Cloud CLI, but you can also use the {{site.data.keyword.cloud_notm}} console or API.
{: tip}

1. Use the `ibmcloud dl gateways` command to list details about all your direct links. Save this output.
2. For each gateway, use the `ibmcloud dl virtual-connections GATEWAY_ID` command to list information about its connections. Save this output.

For more information, see the [{{site.data.keyword.dl_short}} CLI reference](/docs/dl?topic=dl-cli-plugin-dl-cli). 

Saving the information returned from these commands helps you recover from a failure quickly. In the event of a failure, use the saved information and run the `ibmcloud dl gateway-create` and `ibmcloud dl virtual-connection-create` commands to recreate your direct links and their connections.
