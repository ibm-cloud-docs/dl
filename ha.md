---

copyright:
  years: 2024
lastupdated: "2024-11-12"

keywords:

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Understanding high availability for Direct Link
{: #ha}

[High availability](#x2284708){: term} (HA) is a core discipline in an IT infrastructure to keep your apps up and running, even after a partial or full site failure. The main purpose of high availability is to eliminate potential points of failures in an IT infrastructure.
{: shortdesc}

IBM Cloud highly recommends setting up a secondary, diverse direct link to avoid outages, whether unplanned or scheduled for maintenance. Effective disaster recovery, especially for issues impacting an entire location, requires careful planning and preparation. 

You are responsible for understanding your connection configuration, customization, and usage of the service. You are also responsible for being ready to re-create an instance of the service in a new location and restore your data there.  For information on how to design Diversity to achieve HA with Direct Link, see [Models for diversity and redundancy in Direct Link](/docs/dl?topic=dl-models-for-diversity-and-redundancy-in-direct-link).
{: important}

See [How IBM Cloud ensures high availability and disaster recovery](/docs/overview?topic=overview-zero-downtime#zero-downtime) to learn more about the high availability and disaster recovery standards in {{site.data.keyword.cloud_notm}}. You can also find information about [Service Level Agreements](/docs/overview?topic=overview-slas#slas).

### High availability within the service
{: #high-availability}

{{site.data.keyword.cloud_notm}} service supports high availability with no single point of failure. The service achieves high availability automatically and transparently by means of the Multi-Zone Region ([MZR](/docs/overview?topic=overview-locations#table-mzr)) feature provided by {{site.data.keyword.cloud_notm}}.

### High availability for customer {{site.data.keyword.dl_short}} connections
{: #high-availability-customer}

Your {{site.data.keyword.dl_short}} connections are location-specific. It is up to you to set up any High Availability or Disaster Recovery plans that are required. For information on how to design Diversity to achieve HA with Direct Link, see [Models for diversity and redundancy in Direct Link](/docs/dl?topic=dl-models-for-diversity-and-redundancy-in-direct-link).

## Responsibilities
{: #ha-responsibilities}

To find out more about responsibility ownership for using Direct Link between {{site.data.keyword.IBM_notm}} and the customer, see [Understanding your responsibilities when using Direct Link](/docs/dl?topic=dl-dl-responsibilities).

## What level of availability do I need?
{: #ha-level}

You can achieve high availability on different levels in your IT infrastructure and within different components of your cluster. The level of availability that is right for you depends on several factors, such as your business requirements, the service level agreements (SLAs) that you have with your customers, and the resources that you want to expend.

## What level of availability does {{site.data.keyword.cloud_notm}} offer?
{: #ha-service}

The level of availability that you set up for your cluster impacts your coverage under the {{site.data.keyword.cloud_notm}} high availability service level agreement terms.

Service level objectives (SLOs) describe the design points that the {{site.data.keyword.cloud_notm}} services are engineered to meet. Direct Link is designed to achieve the following availability target.

| Availability target | Target value   |
|---|---|
|  Availability % | 99.999%  |
{: caption="SLO for Direct Link" caption-side="bottom"}

The SLO is not a warranty and {{site.data.keyword.IBM_notm}} will not issue credits for failure to meet an objective. Refer to the SLAs for commitments and credits that are issued for failure to meet any committed SLAs. For a summary of all SLOs, see [{{site.data.keyword.cloud_notm}} service level objectives](/docs/overview?topic=overview-slo).

## Locations
{: #ha-locations}

For more information about service availability within regions and data centers, see [Service and infrastructure availability by location](/docs/overview?topic=overview-services_region).
