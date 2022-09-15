---

copyright:
  years: 2021, 2022
lastupdated: "2022-09-15"

keywords: direct link

subcollection: dl
---

{{site.data.keyword.attribute-definition-list}}

# Updating a direct link
{: #update-dl-gateway}
{: help}
{: support}

You can update a direct link either before or after the gateway moves to the **Provisioned** state. However, a gateway is restricted from editing during **In review**, **Configuring**, and some in-progress states.
{: shortdesc}

To edit a direct link, follow these steps:

1. Click the Direct Link name in the table to show its details. 

   Alternatively, you can click the **Actions** icon at the end of the table row of a provisioned direct link to **Edit gateway**, **Edit BGP**, **Add connection**, or **Delete**.
   {: tip}
   
   If your Direct Link connection was ordered through a third-party Connect provider (as described in [{{site.data.keyword.cloud_notm}} Getting started with IBM Cloud Direct Link (2.0](/docs/dl?topic=dl-get-started-with-ibm-cloud-dl), you might not be able to edit your BGP configuration as described here. The direct link's details page will display a note stating, "This direct link is read-only. Link-specific actions must be initiated through the provider portal." To edit your BGP configuration, contact your provider either directly, or through the provider's portal.
{: important}

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
