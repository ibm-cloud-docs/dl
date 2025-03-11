---

copyright:
  years: 2025
lastupdated: "2025-03-11"

keywords: direct link, direct link dedicated

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Completing the connection
{: #complete-connection}

After you submit your {{site.data.keyword.dl_short}} Dedicated order, the {{site.data.keyword.dl_short}} table indicates an **LOA creation in progress** connection status. Click the name of the connection to open its details page. Then, view the **Actions** section to see if you have any pending actions.

Here's how the process works:

1. IBM Cloud uploads a Letter of Authorization (LOA) containing a Connecting Facility Assignment (CFA) within 24 hours. In turn, the connection status changes to **Waiting LOA review**. Currently, you can click the corresponding buttons to preview and accept the LOA.
1. After you accept the LOA and download it, the connection status changes to **Waiting completion notice upload**. Now take the LOA document to your carrier and get the completion notice ([Example](/docs/dl?topic=dl-completion-notice-example)). To do so, you can:

   * Supply the LOA/CFA to your colocation provider and have them order a cross-connect and any required inter-campus connectivity.
   * Supply the LOA/CFA to your service provider and have them order a third-party cross-connect, as well as the circuit between your on-premises and the appropriate Meet Me Room.

   IBM Cloud will not order a cross-connect on a customer's behalf.
   {: note}

1. After you receive the completion notice from your carrier, upload it. The completion notice must be in PDF format with the name **completion_notice.pdf** for the automation to process it properly. The specific connection shows an option in the {{site.data.keyword.cloud_notm}} console to upload the completion notice. Notice that the connection status changes to **Completion notice review in progress**.

1. The IBM Cloud team reviews the completion notice and accepts it. The IBM Cloud team then places an order for the fiber to be installed between the patch panel/port mentioned in the LOA and the device port. This process can take 1-4 business days, depending on how quickly the site provider finishes the request. This completes the physical-layer portion of the direct link and the connection status changes to **Provisioned.**

1. Configure the BGP parameters on your Edge router for BGP session establishment. After this completes, the **BGP status** indicates **Established** and **Link status** indicates **Up**. It can take up to 30 minutes for the link status to update.

If you decide to cancel your direct link, remember to disconnect the cross-connect router with the site provider; otherwise, you will continue to be charged for the cross-connect.
{: important}
