---

copyright:
  years: 2022
lastupdated: "2022-09-21"

keywords: direct link cli change log

subcollection: dl

content-type: release-note

---

{{site.data.keyword.attribute-definition-list}}

# Direct Link CLI change log
{: #direct-link-cli-change-log}

Learn about the latest changes, improvements, and updates for the IBM Cloud Direct Link CLI plug-in (`ibmcloud dl`). Changes to existing CLI versions are designed to be compatible with existing client applications.
{: shortdesc}

To learn about general updates and improvements to Direct Link offerings, see [Release notes for Direct Link](/docs/dl?topic=dl-direct-link-release-notes).
{: note}

## 21 September 2022
{: #dl-sep1222}
{: release-note}

BGP AS prepend support
:    Support AS prepend information as part of the `--file` option.

   * [Create a Connect gateway](/docs/dl?topic=dl-cli-plugin-dl-cli#create-connect-gateway) - `connect-gateway-create`, `conn-gwc`   
   * [Create a Dedicated gateway](/docs/dl?topic=dl-cli-plugin-dl-cli#create-dedicated-gateway) - `dedicated-gateway-create`, `ded-gwc` 
   * [Approve a gateway change request](/docs/dl?topic=dl-cli-plugin-dl-cli#gateway-change-approve-cmd) - `gateway-change-approve`, `gwca`    

Route report support
:    New commands:

   * [View details of a route report](/docs/dl?topic=dl-cli-plugin-dl-cli#route-report-view) - `route-report`, `rr` 
   * [Create a route report](/docs/dl?topic=dl-cli-plugin-dl-cli#route-report-create-view) - `route-report-create`, `rrc`      
   * [Delete a route report](/docs/dl?topic=dl-cli-plugin-dl-cli#route-report-delete-view) - `route-report-delete`, `rrd`  
   * [List all route reports](/docs/dl?topic=dl-cli-plugin-dl-cli#route-report-list-view) - `route-reports`, `rrs`

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

Direct Link connection support for transit gateways
:    Added the **--connection** flag to [dedicated-gateway-create](/docs/dl?topic=dl-cli-plugin-dl-cli#create-dedicated-gateway) and [connect-gateway-create](/docs/dl?topic=dl-cli-plugin-dl-cli#create-connect-gateway) commands.

## 24 June 2021
{: #dl-jun2421}
{: release-note}

BGP Message Digest 5 authentication support
:    Added the **--file** option to create a Direct Link gateway with MD5 authentication key. See the [template](/apidocs/direct_link#create-gateway) to provide the MD5 authentication key.
