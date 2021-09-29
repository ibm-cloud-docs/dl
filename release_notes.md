---
copyright:
  years: 2021
lastupdated: "2021-08-30"

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
{:beta: .beta}
{:tip: .tip}
{:term: .term}
{:generic: data-hd-programlang="generic"}
{:download: .download}

# Release notes
{: #release-notes}

Check back regularly to see what's new with {{site.data.keyword.cloud}} Direct Link.
{: shortdesc}

## 24 September 2021
{: #september-2021}

**Bidirectional Forwarding Detection (BFD)** - Activate BFD to quickly detect faults in a network between two routers or switches that are connected by a link. BFD provides a single, standardized method for detecting link failures at any protocol layer, over any media.

**More flexibility in configuring BGP values** - Instead of being able to specify BGP values (ASN and IP addresses) only during initial configuration, you'll now be able to modify BGP values after direct link provisioning.

## 30 August 2021
{: #august-2021}

**Direct Link (2.0) connection support for transit gateways** - Direct Link now supports Transit Gateway connections. A Direct Link connection allows an on-premises network to connect to other networks (for instance, VPC and classic infrastructure) that are connected to the same transit gateway.

   The beta release for this feature has ended. If you participated in this beta, you can continue to use the gateways that you created during the beta period.
   {: note}

## 24 June 2021
{: #june-2021}

**BGP Message Digest 5 authentication support** - Border Gateway Protocol (BGP) authentication enables routers to share information only if they can verify that they are talking to a trusted source, based on a key. TCP MD5 authentication adds an extra layer of security between BGP peers by verifying each transmitted message sent through a BGP session. You can store your keys in either Key Protect or Hyper Protect Crypto Services (HPCS).
