---

copyright:
  years: 2018, 2020
lastupdated: "2020-07-16"

keywords: 

subcollection: dl

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
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

# Alternatives for your Direct Link Connect (2.0) deployment
{: #alternatives-for-your-ibm-cloud-direct-link-deployment}

Describes alternatives that you can choose for your Direct Link Connect deployments.
{:shortdesc}

The default deployments of Direct Link Connect do not include redundant configuration, although they can be deployed diversely on discrete routers.

Many customers choose to create redundant deployments by setting up an additional Direct Link connection. The following diagrams illustrate some schematic representations of alternative Direct Link deployments

IBM Cloud Direct Link also makes it easy to establish diverse Connect deployments, as shown in Figure 1.

![Diverse Connect](/images/connect_alt_2.png "Diverse Connect"){: caption="Figure 1. A diverse IBM Cloud Direct Link Connect deployment to enable redundancy via Customer BGP schema" caption-side="bottom"}

## Using Connect along with other clouds
{: #using-exchange-and-connect-in-conjunction-with-other-clouds}

Some customers want to use Direct Link Connect along with other cloud providers, such as AWS, Azure, or Google Cloud. The following schematic shows an overview of how to establish this type of connection with a Telco (service provider).

![Other Clouds Connect](/images/connect_alt_3.png "Other Clouds Connect"){: caption="Figure 2. Using Direct Link Connect in conjunction with other clouds" caption-side="bottom"}
