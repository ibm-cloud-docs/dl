---

copyright:
  years: 2020, 2021
lastupdated: "2021-02-01"

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

Make sure that no IP address conflicts between on-premises subnets and subnets on IBM Cloud for both VPC and classic infrastructure connections.
{: important}

To add a connection to a provisioned gateway, follow these steps:

1. In the table row of the gateway where you want to add a connection, click **Add connection** from the Actions ![Actions menu](images/overflow.png) menu. Alternatively, you can click **Add connection +** on the gateway's details page.
 
   You can create a connection to the logged-in account, or request a connection to a network within another account.

2. Choose the type of network connection and enter a name for the connection.
3. For VPC connections, select the region and the VPC network to attach to the gateway. For connections to VPC networks in another {{site.data.keyword.cloud_notm}} account, enter the Cloud Resource Name (CRN) of the target VPC.
4. Click **Add** to attach the virtual connection to the gateway.

After the virtual connection is added to the gateway, the VPC name is shown under the virtual connections section on the gateway's details page.

You can add only one classic infrastructure virtual connection to a provisioned {{site.data.keyword.dl_short}} connection. However, you can add multiple VPC virtual connections.  
{: note}
