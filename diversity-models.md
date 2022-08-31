---

copyright:
  years: 2018, 2022
lastupdated: "2022-08-31"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Models for diversity in {{site.data.keyword.dl_short}}
{: #models-for-diversity-and-redundancy-in-direct-link}

Customers have the responsibility for creating diversity through their border gateway protocol (BGP) schemas; {{site.data.keyword.dl_full}} is not a redundant service at the cross-connect router (XCR). This document presents possible configurations which can help you find a model for creating the most successful {{site.data.keyword.dl_short}} deployment to meet your needs. The configurations are arranged in increasing levels of complexity and also according to the {{site.data.keyword.dl_short}} offering.
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

![Connect with diversity in the local AZ](/images/connect-diversity-local-az.png "Connect with diversity in the local AZ"){: caption="Figure 3: {{site.data.keyword.dl_short}} Connect with diversity in a local AZ" caption-side="bottom"}

![Dedicated with diversity in the local AZ](/images/dedicated-diversity-local-az.png "Dedicated with diversity in the local AZ"){: caption="Figure 4: {{site.data.keyword.dl_short}} Dedicated with diversity in a local AZ" caption-side="bottom"}

### Diversity in different local markets, with global routing
{: #section-2-part-b}

![Connect with diversity and global routing](/images/connect-diversity-global.png "Connect with diversity and global routing"){: caption="Figure 5: {{site.data.keyword.dl_short}} Connect with diversity and global routing" caption-side="bottom"}

![Dedicated with diversity and global routing](/images/dedicated-diversity-global.png "Dedicated with diversity and global routing"){: caption="Figure 6: {{site.data.keyword.dl_short}} Dedicated with diversity and global routing" caption-side="bottom"}

## Achieving redundancy
{: #how-to-achieve-diversity-and-redundancy}

If you are looking for High Availability (HA), or full redundancy, set up two links into different XCRs in the same data center (for example DAL03). Then, fail over as needed using BGP configurations.

![ECMP Dual XCR Model](/images/ecmp-with-diversity.png "ECMP Dual XCR Model"){: caption="Figure 7: ECMP with Dual XCRs" caption-side="bottom"}
