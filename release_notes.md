---

copyright:
  years: 2022, 2023
lastupdated: "2023-07-06"

keywords: direct link release notes

subcollection: dl

content-type: release-note

---

{{site.data.keyword.attribute-definition-list}}

# Release notes for Direct Link
{: #direct-link-release-notes}

Check back regularly to see what's new with {{site.data.keyword.cloud}} Direct Link.
{: shortdesc}

## 06 July 2023
{: #dl-july0623}
{: release-note}

Route report enhancements
:   Added advertised routes to verify route filters and AS prepends applied to the Direct Link gateway.

:   Added “AS path” information to on-prem routes to verify AS prepends.

    For more information, see [Generating a direct link route report](/docs/dl?topic=dl-generate-route-reports&interface=ui).
    {: note}

Support for Madrid multi-zone region (MZR)

## 20 March 2023
{: #dl-march2023}
{: release-note}

BGP route filtering support
:   Configure route filters to control the inbound routes learned by your direct link and outbound routes advertised by your direct link. BGP route filtering can help reduce resource usage, influence network traffic, and add security. For more information, see [About route filtering](/docs/dl?topic=dl-filter-routes).

## 21 September 2022
{: #dl-september2122}
{: release-note}

Generate a route report for a specific direct link
:   Request a route report to verify expected routes and figure out which routes are associated with attached virtual connections. This assists in diagnosing and troubleshooting routing and connectivity issues. For more information, see [Generating a direct link route report](/docs/dl?topic=dl-generate-route-reports&interface=ui).

BGP AS prepending support
:   Prepend one or more autonomous system numbers (ASNs) at the beginning of an AS path. Prepending an AS path makes a shorter AS path look longer and therefore less preferable to BGP. For more information, see [Using AS prepends to influence route preference](/docs/dl?topic=dl-dl-about#use-case-1).

## 01 April 2022
{: #dl-apr0122}
{: release-note}

Reduced unmetered plan pricing for Direct Link Connect
:   IBM is pleased to announce _a significant reduction in unmetered pricing_ for IBM Cloud Direct Link Connect and Direct Link Dedicated. Note that Direct Link also offers a metered pricing plan, allowing you to switch between metered and unmetered pricing plans to suit your bandwidth usage needs.

## 27 January 2022
{: #dl-jan2722}
{: release-note}

VLAN mapping
:    A Provider can now specify their own VLAN value at the time of gateway creation, or update it later using the [Direct Link Provider API](/apidocs/direct_link_provider_api). Previously, the VLAN was selected for you.

## 24 September 2021
{: #dl-sep2422}
{: release-note}

Bidirectional Forwarding Detection (BFD)
:    Activate BFD to quickly detect faults in a network between two routers or switches that are connected by a link. BFD provides a single, standardized method for detecting link failures at any protocol layer, over any media.

More flexibility in configuring BGP values
:    Instead of being able to specify BGP values (ASN and IP addresses) only during initial configuration, you'll now be able to modify BGP values after direct link provisioning.

## 30 August 2021
{: #dl-aug3021}
{: release-note}

Direct Link connection support for transit gateways
:    Direct Link now supports Transit Gateway connections. A Direct Link connection allows an on-premises network to connect to other networks (for instance, VPC and classic infrastructure) that are connected to the same transit gateway.

:    The beta release for this feature has ended. If you participated in this beta, you can continue to use the gateways that you created during the beta period.

## 24 June 2021
{: #dl-jun2421}
{: release-note}

BGP Message Digest 5 authentication support
:    Border Gateway Protocol (BGP) authentication enables routers to share information only if they can verify that they are talking to a trusted source, based on a key. TCP MD5 authentication adds an extra layer of security between BGP peers by verifying each transmitted message sent through a BGP session. You can store your keys in either Key Protect or Hyper Protect Crypto Services (HPCS).
