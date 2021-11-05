---

copyright:
  years: 2020, 2021
lastupdated: "2021-03-02"

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

# Verizon SCI using Equinix Fabric ordering considerations
{: #verizon-sci}

Follow these steps to create a Direct Link connection with Verizon SCI and Equinix Fabric.

1. Obtain an IP subnet and local ASN (typically, the Verizon Public ASN `1684`) for the BGP from the Verizon SCI service.

   This block is usually a `/31` or `/30` IP block.
   {: note}

1. Order an {{site.data.keyword.cloud}} Direct Link (2.0) Connect gateway through the [{{site.data.keyword.cloud_notm}} console](https://cloud.ibm.com){: external}. For instructions, see [Ordering IBM Cloud Direct Link Connect](/docs/dl?topic=dl-how-to-order-ibm-cloud-dl-connect).

   During the ordering process (Step 7), you can specify your own IP address. Make sure to specify the Verizon SCI-supplied IP addresses instead of your actual client Edge IP addresses.

   To specify your own IP address, follow these steps:

      * Choose **Manual-select IP**.
      * For Range, select **Public**.
      * For Your CIDR, enter the specific IP address from the Verizon-supplied subnet (for example, `10.254.0.26/30`).
      * For your IBM CIDR, enter the specific IP address from the remaining addresses in the Verizon-supplied subnet (for example, `10.254.0.25/30`).
      * For BGP ASN, enter the supplied local ASN (typically, the Verizon Public ASN `1684`) supplied by Verizon.

      ![Direct Link Connect ordering](/images/public-range.png "Manual-select IP Public Range"){: caption="Manual-select IP Public Range" caption-side="bottom"}

   Write down and retain the connection name and the service key generated from the order.
   {: important}

1. Send the connection name that you created and the generated service key to the Verizon SCI team. If you are granted permission by Verizon to order Direct Link Connect through the Equinix Fabric portal, complete your order using the Equinix Cloud Exchange (ECX) Fabric portal.

## Completing your order using the Equinix Fabric portal
{: #completing-equinix-fabric-portal-order}

1. Log in to the Equinix Fabric portal.
   * Navigate to [https://ecxfabric.equinix.com](https://ecxfabric.equinix.com).
   * Enter your username and password.
   * Click **Sign In**.
1. In the Frequent Connections section, click the **IBM Cloud** tile.
1. In the **IBM Cloud Direct Link 2** profile, click **Create Connection**.

   ![Equinix ordering](/images/equinix-ibm-cloud-2.png "Equinix ordering"){: caption="Equinix ordering" caption-side="bottom"}

1. In the Origin section, click **Port**.

   ![Select a Port, Location, and Destination](/images/equinix-port.png "Select a Port, Location, and Destination"){: caption="Select a Port, Location, and Destination" caption-side="bottom"}

1. Select a **Location**, followed by a **Destination**. Then, click **Next**.
1. On the Connection Details page, enter the connection information. For the IBM Cloud Account ID, enter the service key (for example, `aaaa-bbbb-cccc`) that was generated when you provisioned your direct link. This key can be found on the Direct Link details page.

   ![Connection Details](/images/equinix-connection-details.png "Connection Details"){: caption="Connection Details" caption-side="bottom"}

1. Select a **Connection Speed**, then click **Next**.
1. Review and click **Submit Your Order**.

The IBM Special Network Services (SNS) team receives your request and is able approve the connection in the buyer-side portal. You can view your newly created virtual connection for Direct Link by going to **Connections**. The connection will be in a pending, provisioning state (**Pending Provider VLAN**).

Accept the connection request by navigating to the IBM Cloud Direct Link page and clicking **Accept** from the Actions menu. The Direct Link Gateway BGP Status shows as **Established** in the IBM Cloud Console, and **Provisioned** in the Equinix Fabric portal.

The timeline for approval is within 24-48 hours. If the 48-hour Service Level Agreement (SLA) is not acceptable, you can create an [IBM Support case](https://cloud.ibm.com/unifiedsupport/cases/form) and request that it be routed to the SNS team.

Optionally, you can enable BGP MD5 authentication to provide additional security for the BGP session. For more information, see [Accepting provider-created connections](/docs/dl?topic=dl-accepting-the-provider-created-connection).
{: note}
