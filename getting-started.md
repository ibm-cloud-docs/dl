---

copyright:
  years: 2020
lastupdated: "2020-06-04"

keywords: hybrid, workloads, deployments, multi-cloud, data transfer, descriptions, diverse, redundant

subcollection: dl

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:preview: .preview}
{:beta: .beta}
{:important: .important}
{:deprecated: .deprecated}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:term: .term}  
{:generic: data-hd-programlang="generic"}
{:download: .download}  

# Getting started with {{site.data.keyword.dl_full_notm}} (2.0)
{: #get-started-with-ibm-cloud-dl}

Use {{site.data.keyword.dl_full}} to seamlessly connect your on-premises resources to your cloud resources. The speed and reliability of {{site.data.keyword.dl_short}} extends your organization’s data center network and offers more consistent, higher-throughput connectivity, keeping traffic within the IBM Cloud network.
{: shortdesc}

Highlights include:

* Metered billing, which lowers the barrier of entry to {{site.data.keyword.cloud_notm}}
* Support for connections to multiple {{site.data.keyword.cloud_notm}} accounts from a single direct link
* Support for multiple VPCs (without classic access) from a single direct link within the same account
* Bring Your Own IP (BYOIP) address to create native connectivity between your on-premises environment and {{site.data.keyword.cloud_notm}}

Features coming soon:

* Support for Virtual Private Endpoints (VPEs) from customer on-premises from a single customer account
* Support for a {{site.data.keyword.dl_short}} connection to venues, such as blockchain, SAP on Power, and more
* Support for a {{site.data.keyword.dl_short}} connection to Public services

The following {{site.data.keyword.dl_short}} (2.0) offerings are available:

## {{site.data.keyword.dl_short}} Dedicated
{: #get-started-with-direct-link-dedicated}

Terminate a single-tenant, fiber-based, cross-connect into your own IBM Cloud Private network connection. This offering is also used by colocation facilities that are next to IBM Cloud PoPs and data centers.

To get started using {{site.data.keyword.dl_full_notm}} Dedicated, follow these [instructions](/docs/dl?topic=dl-how-to-order-ibm-cloud-dl-dedicated) for ordering the service.

## {{site.data.keyword.dl_short}} Connect
{: #get-started-with-direct-link-connect}

Use a service provider to quickly establish and deliver connectivity to IBM Cloud locations. These Connect providers are already connected to the IBM Cloud network that uses multi-tenant, high capacity links (also known as network-to-network interfaces, or NNI).  

To get started using {{site.data.keyword.dl_full_notm}} Connect, follow these [instructions](/docs/dl?topic=dl-how-to-order-ibm-cloud-dl-connect) for ordering the service.

23 September 2020: Direct Link Connect is a limited availability offering. If you participated in the beta release, you must migrate to a standard paid plan to continue using instances that you created during the beta. Any instances that continue to use the beta plan for this service beyond the 30 days notice of general availability are subject to deletion. For more information, see [Migrating Direct Link Connect gateways](/docs/dl?topic=dl-migration).
{: preview}

## Learn more
{: #learn-more}

* IBM Cloud highly recommends that you establish a second, diverse direct link to prevent outages, whether unplanned, or planned due to maintenance. For more information, see [Models for diversity and redundancy in Direct Link (2.0)](/docs/dl?topic=dl-models-for-diversity-and-redundancy-in-direct-link).

* If you require a diverse, redundant, or multi-cloud deployment for Direct Link Connect, see [Alternatives for your Direct Link Connect (2.0) deployment](/docs/dl?topic=dl-alternatives-for-your-ibm-cloud-direct-link-deployment).

* For more information about {{site.data.keyword.dl_short}} (2.0) offerings, see our [FAQs](/docs/dl?topic=dl-faqs).
