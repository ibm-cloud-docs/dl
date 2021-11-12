---

copyright:
  years: 2018, 2020
lastupdated: "2020-07-07"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Models for diversity and redundancy in {{site.data.keyword.dl_short}}
{: #models-for-diversity-and-redundancy-in-direct-link}

{{site.data.keyword.dl_full}} is not a redundant service at the cross-connect router (XCR); customers have the responsibility for creating redundancy through their border gateway protocol (BGP) schemas. This document presents possible configurations which can help you find a model for creating the most successful {{site.data.keyword.dl_short}} deployment to meet your needs. The configurations are arranged in increasing levels of complexity and also according to the {{site.data.keyword.dl_short}} offering.
{: shortdesc}

Key:

* BCR - Back-end customer router
* XCR - Cross-connect router
* NE - Network Edge

## Simple configurations that achieve diversity
{: #section-1-diversity-models}

The configurations that are shown in this group assume that all of the assets are located in the same PoP and in the same global market.

![Connect with diversity in the same PoP](/images/connect-diversity-same-pop.png "Connect with diversity in the same PoP"){: caption="Figure 1: {{site.data.keyword.dl_short}} Connect with diversity in the same PoP (non-AZ)" caption-side="bottom"}

![Dedicated with diversity in the same PoP](/images/dedicated-diversity-same-pop.png "Dedicated with diversity in the same PoP"){: caption="Figure 2: {{site.data.keyword.dl_short}} Dedicated with diversity in same PoP (non-AZ)" caption-side="bottom"}

## Diversity that includes AZs and global routing options
{: #section-2-diversity-models}

The configurations that are shown in this group offer options for connecting across local availability zones and markets.

### Diversity in a local availability zone (AZ)
{: #section-2-part-a}

![Connect with diversity in the local AZ](/images/connect-diversity-local-az.png "Connect with diversity in the local AZ"){: caption="Figure 3: {{site.data.keyword.dl_short}} Connect with diversity in a local AZ (WDC, DAL, FRA, LON)" caption-side="bottom"}

![Dedicated with diversity in the local AZ](/images/dedicated-diversity-local-az.png "Dedicated with diversity in the local AZ"){: caption="Figure 4: {{site.data.keyword.dl_short}} Dedicated with diversity in a local AZ (WDC, DAL, FRA, LON)" caption-side="bottom"}

### Diversity in different local markets, with global routing
{: #section-2-part-b}

![Connect with diversity and global routing](/images/connect-diversity-global.png "Connect with diversity and global routing"){: caption="Figure 5: {{site.data.keyword.dl_short}} Connect with diversity and global routing" caption-side="bottom"}

![Dedicated with diversity and global routing](/images/dedicated-diversity-global.png "Dedicated with diversity and global routing"){: caption="Figure 6: {{site.data.keyword.dl_short}} Dedicated with diversity and global routing" caption-side="bottom"}

## About ECMP
{: #more-about-ecmp}

Equal-cost multipath (ECMP) is a feature of BGP. Some customers ask to use ECMP as a way to achieve redundancy. However, ECMP alone is not sufficient.

**This section explains why IBM Cloud does NOT recommend the use of ECMP. ECMP balancing with IBM Cloud only extends to the cross-connect routers (XCRs). Past the XCRs, the ECMP-based traffic presents itself as the same IP address to the IBM Cloud network, and the IBM Cloud network routing defaults to the shortest path found. This means that only one of the {{site.data.keyword.dl_short}}s in the ECMP configuration is usable at a given time. All requests for ECMP require Network exception approval by IBM Cloud Offering Management.**

ECMP isn’t designed for creating redundant connections but for balancing the load over two links. With ECMP on {{site.data.keyword.cloud_notm}}, both connections must terminate to the same IBM Cloud XCR, which makes it a single point of failure. In other words, ECMP can be provisioned as two sessions only on the same {{site.data.keyword.cloud_notm}} XCR.

![ECMP Dedicated model](/images/ecmp-without-diversity.png "ECMP Dedicated model"){: caption="Figure 7: ECMP provisioning" caption-side="bottom"}

## Achieving diversity and redundancy
{: #how-to-achieve-diversity-and-redundancy}

If you are looking for High Availability (HA), or full redundancy, set up two links into different XCRs in the same data center (for example DAL03). Then, fail over as needed using BGP configurations.

![ECMP Dual XCR Model](/images/ecmp-with-diversity.png "ECMP Dual XCR Model"){: caption="Figure 8: ECMP with Dual XCRs" caption-side="bottom"}
