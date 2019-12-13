---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-02"

keywords: diversity, redundancy, schematics, deployment, configuration, global routing, ECMP, Dual XCRs, model

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

# Leveraging ECMP for redundant connections
{: #more-about-ecmp} 

Equal-cost multipath (ECMP) is a feature of border gateway protocol (BGP). Some customers asked us about using ECMP as a way to achieve redundancy. However, ECMP alone is not sufficient. This section explains why.

ECMP isn’t designed for creating redundant connections but for balancing the load over two links. With ECMP on {{site.data.keyword.cloud_notm}}, both connections must terminate to the same IBM Cloud cross-connect router (XCR), which makes it a single point of failure. (In other words, ECMP can be provisioned as two sessions only on the same {{site.data.keyword.cloud_notm}} XCR).

![ECMP Dedicated model](/images/ecmp-without-diversity.png "ECMP Dedicated model"){: caption="Figure 1: ECMP provisioning" caption-side="top"}


![ECMP Dual XCR Model](/images/ecmp-with-diversity.png "ECMP Dual XCR Model"){: caption="Figure 2: ECMP with Dual XCRs" caption-side="top"}
