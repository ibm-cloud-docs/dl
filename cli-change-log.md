---

copyright:
  years: 2022
lastupdated: "2022-09-21"

keywords: direct link cli change log

subcollection: dl

content-type: release-note

---

{{site.data.keyword.attribute-definition-list}}

# Direct Link (2.0) CLI change log
{: #direct-link-cli-change-log}

Learn about the latest changes, improvements, and updates for the IBM Cloud Direct Link CLI plug-in (`ibmcloud dl`). Changes to existing CLI versions are designed to be compatible with existing client applications.
{: shortdesc}

To learn about general updates and improvements to Direct Link offerings, see [Release notes for Direct Link](/docs/dl?topic=dl-direct-link-release-notes).
{: note}

## 24 September 2021
{: #dl-sep2422}
{: release-note}

Bidirectional Forwarding Detection (BFD)
:    Added the parameters **--bfd-interval** and **--bfd-multiplier** in [dedicated-gateway-create](/docs/dl?topic=dl-cli-plugin-dl-cli#create-dedicated-gateway), [connect-gateway-create](/docs/dl?topic=dl-cli-plugin-dl-cli#create-connect-gateway), and [gateway-update](/docs/dl?topic=dl-cli-plugin-dl-cli#update-gateway) commands.

More flexibility in configuring BGP values
:    Added the fields **--bgp-asn**, **--bgp-cer-cidr**, and **--bgp-ibm-cidr** in [gateway-update](/docs/dl?topic=dl-cli-plugin-dl-cli#update-gateway) to update BGP values (ASN and IP addresses).

## 30 August 2021
{: #dl-aug3021}
{: release-note}

Direct Link (2.0) connection support for transit gateways
:    Added the **--connection** flag to [dedicated-gateway-create](/docs/dl?topic=dl-cli-plugin-dl-cli#create-dedicated-gateway) and [connect-gateway-create](/docs/dl?topic=dl-cli-plugin-dl-cli#create-connect-gateway) commands.

## 24 June 2021
{: #dl-jun2421}
{: release-note}

BGP Message Digest 5 authentication support
:    Added the **--file** option to create a Direct Link gateway with MD5 authentication key. See the [template](/apidocs/direct_link#create-gateway) to provide the MD5 authentication key.
