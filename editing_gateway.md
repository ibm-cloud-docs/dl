---

copyright:
  years: 2021
lastupdated: "2021-11-03"

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
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Updating a {{site.data.keyword.dl_short}}
{: #update-dl-gateway}
{: help}
{: support}

You can update a {{site.data.keyword.dl_short}} gateway either before or after the gateway moves to the **Provisioned** state. However, a gateway is restricted from editing during **In review**, **Configuring**, and some in-progress states.
{: shortdesc}

To edit a {{site.data.keyword.dl_short}} gateway, follow these steps:

1. Click the Direct Link name in the table to show its details.

   Alternatively, you can click the **Actions** icon at the end of the table row of a provisioned direct link to **Edit gateway**, **Edit BGP**, **Add connection**, or **Delete**.
   {: tip}

   ![Edit direct link gateway](/images/dl-edit.png){: caption="Edit direct link gateway" caption-side="bottom"}

1. Click **Edit** link in the upper right of the Details or BGP section. A page with the current configuration shows. For example, you can update the BGP Autonomous System Number (ASN), or enable a BGP feature.  

   ![Edit BGP content](/images/dl-bgp-edit.png){: caption="Edit BGP content" caption-side="bottom"}

   **Important**: Keep in mind that the following tasks result in downtime where traffic is interrupted:

   * Activating and deactivating MD5 authentication, or rotating MD5 key authentication after a BGP session is established
   * Activating and deactivating Bidirectional Forwarding Detection (BFD) after establishing a BGP session
   * Modifying BGP ASN and BGP peer IP addresses after initial configuration

1. Update the content as needed.

   If you modify the speed or routing option, the pricing changes. Any updated charges take effect during the next billing cycle.  
   {: note}

1. Read and agree to the [{{site.data.keyword.dl_short}} prerequisites](/docs/dl?topic=dl-ibm-cloud-dl-prerequisites).
1. Click **Submit** for your changes to take effect.

Configuration updates start automatically after you click **Submit**. Notice that the gateway changes to **Configuring** state in the Direct Link table, followed by **Provisioned** when the update is completed.
