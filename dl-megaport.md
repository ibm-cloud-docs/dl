---

copyright:
  years: 2020, 2021
lastupdated: "2021-06-24"

keywords:

subcollection: dl

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:preview: .preview}
{:note: .note}
{:beta: .beta}
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

# Megaport ordering considerations
{: #megaport}

Follow these steps to order an {{site.data.keyword.dl_full}} Connect gateway with Megaport:

   For instructions on creating Megaport Cloud Router (MCR) connections, see [MCR Connections to IBM Cloud Direct Link 2.0](https://docs.megaport.com/cloud/mcr/ibm-2.0/).
   {: note}

1. Using your IBM Cloud account, order a {{site.data.keyword.dl_short}} (2.0) Connect gateway by using the {{site.data.keyword.cloud_notm}} console. For instructions, see [Ordering IBM Cloud Direct Link Connect](/docs/dl?topic=dl-how-to-order-ibm-cloud-dl-connect).

1. After the {{site.data.keyword.dl_short}} is created, copy the **Service key** assigned in Step 1, and enter this this information in the [Megaport Portal](https://portal.megaport.com/login){: external} to provision a Virtual Cross Connect (VXC) to the {{site.data.keyword.dl_full_notm}} Connect peering location.

   ![Provisioning a VXC to Direct Link Connect in the Megaport Portal](/images/megaport_portal.png "Provisioning a VXC to Direct Link Connect in the Megaport Portal"){: caption="Provisioning a VXC to Direct Link Connect in the Megaport Portal" caption-side="bottom"}   

1. In the [Megaport Portal](https://portal.megaport.com/login){: external}, go to the Services page and select the port that you want to use. If you haven't already created a port, see [Creating a Port](https://docs.megaport.com/connections/creating-port/){: external} in the Megaport documentation.

1. Add an {{site.data.keyword.cloud_notm}} connection to the port. If this is the first connection for the port, click the {{site.data.keyword.cloud_notm}} tile.

    Alternatively, click **+Connection > Cloud > IBM Cloud**.

   ![Add IBM Cloud connection](/images/megaport_add_connection.png "Add IBM Cloud connection")

1. Select the {{site.data.keyword.dl_full_notm}} location where the peer will be set up with {{site.data.keyword.cloud_notm}}, then click **Next**.  

   This destination should match the peer location selected in the {{site.data.keyword.cloud_notm}}.

   ![Select the IBM Cloud Direct Link location where the peer will be set up](/images/megaport_location.png "Select the IBM Direct Link location where the peer will be set up"){: caption="Select the IBM Cloud Direct Link location where the peer will be set up" caption-side="bottom"}   

1. Specify these connection details:

   * **Name your connection** – Enter the {{site.data.keyword.dl_full_notm}} service key.
   * **Invoice Reference** - Optionally, enter a reference description, such as a PO number or billing reference number.
   * **Rate Limit** – Enter the speed of your connection in Mbps. Match the port speed created in the IBM Cloud console for the {{site.data.keyword.dl_short}} service.
   * **Preferred A-End VLAN** – Optionally, specify an unused VLAN ID for this connection. This must be a unique VLAN ID on this port and can range from `2` to `4093`. If you specify a VLAN ID that is already in use, the system displays the next available VLAN number. The VLAN ID must be unique to proceed with the order. If you don’t specify a value, Megaport assigns one.

   Alternatively, you can click **Untag** to remove the VLAN tagging for this connection. The untagged option limits you to only one VXC deployed on this port.

   ![Connection Details page](/images/megaport_connection_details.png "Connection Details page"){: caption="Connection Details page" caption-side="bottom"}   

1. Click **Next**. A Summary page appears that includes the monthly cost.

   ![Summary page](/images/megaport_summary.png "Summary page"){: caption="Summary page" caption-side="bottom"}   

1. Click **Back** to make changes, or click **Add VXC**.

   After you have completed this configuration, you can configure additional VXCs, or proceed through the ordering process.

1. Review the details and click **Order**.

   ![Configured Services page](/images/megaport_configured_services.png "Configured Services page"){: caption="Configured Services page" caption-side="bottom"}   

1. Click **Order Now** to complete the ordering process.

   ![Order Services page](/images/megaport_order_services.png "Order Services page"){: caption="Order Services page" caption-side="bottom"}   

After IBM verifies and approves the inbound IBM VXC, the {{site.data.keyword.dl_full_notm}} Connect status changes to **Provisioned** and the Megaport VXC is active.

The timeline for IBM approval is from 24 to 48 hours. If the 24 to 48 hour Service Level Agreement (SLA) is not acceptable, you can create an [IBM Support case](https://cloud.ibm.com/unifiedsupport/cases/form) and request that it be routed to the IBM Special Network Service (SNS) team. Include the service key in your case.
