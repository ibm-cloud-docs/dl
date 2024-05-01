---

copyright:
  years: 2020, 2024
lastupdated: "2024-05-01"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Adding virtual connections to a direct link
{: #add-virtual-connection}
{: help}
{: support}

You can add a virtual connection when you create a direct link, or after the gateway is provisioned.
{: shortdesc}

**Important:**

* Make sure that there are no IP address conflicts between on-premises subnets and subnets on IBM Cloud for both VPC and classic infrastructure connections.
* If you selected Transit Gateway as your network connection type, you cannot add another connection to your direct link. Keep in mind that classic routes are not blocked. For more information, see [Preparing for Direct LinK Gateway changes to advertised service network routes](/docs/dl?topic=dl-notification-dl-tgw).
{: important}

To add a connection to a provisioned gateway, follow these steps:

1. In the table row of the gateway where you want to add a connection, click **Add connection** from the Actions ![Actions menu](images/overflow.png) menu. Alternatively, you can click the Direct Link name in the table and click **Add connection** in the Virtual connections section on the gateway's details page.

   You can create a connection to the logged-in account, or request a connection to a network within another account.
   {: note}

1. Choose the type of network connection and enter a name for the connection. Choices are **Classic infrastructure** and **VPC**.
1. For VPC connections, select the region and the VPC network to attach to the gateway. For connections to VPC networks in another {{site.data.keyword.cloud_notm}} account, enter the Cloud Resource Name (CRN) of the target VPC.
1. Click **Add** to attach the virtual connection to the gateway.

After the virtual connection is added to the gateway, the VPC name is shown under the virtual connections section on the gateway's details page.

You can add only one classic infrastructure virtual connection to a provisioned {{site.data.keyword.dl_short}} connection. However, you can add multiple VPC virtual connections.
{: note}
