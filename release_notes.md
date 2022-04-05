---

copyright:
  years: 2022
lastupdated: "2022-04-01"

keywords: direct link release notes

subcollection: dl

content-type: release-note

---

{{site.data.keyword.attribute-definition-list}}

# Release notes
{: #direct-link-release-notes}

Check back regularly to see what's new with {{site.data.keyword.cloud}} Direct Link.
{: shortdesc}


## 01 April 2022
{: #dl-apr0122}

Reduced unmetered plan pricing for Direct Link Connect
:    IBM is pleased to announce a price reduction for IBM Cloud Direct Link Connect — _now offering the lowest unmetered pricing of our leading competitors_. For more information, see [Pricing for IBM Cloud Direct Link](/docs/dl?topic=dl-pricing-for-ibm-cloud-dl).

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

Direct Link (2.0) connection support for transit gateways
:    Direct Link now supports Transit Gateway connections. A Direct Link connection allows an on-premises network to connect to other networks (for instance, VPC and classic infrastructure) that are connected to the same transit gateway.

:    The beta release for this feature has ended. If you participated in this beta, you can continue to use the gateways that you created during the beta period.

## 24 June 2021
{: #dl-jun2421}
{: release-note}

BGP Message Digest 5 authentication support
:    Border Gateway Protocol (BGP) authentication enables routers to share information only if they can verify that they are talking to a trusted source, based on a key. TCP MD5 authentication adds an extra layer of security between BGP peers by verifying each transmitted message sent through a BGP session. You can store your keys in either Key Protect or Hyper Protect Crypto Services (HPCS).
