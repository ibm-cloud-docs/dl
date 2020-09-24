---

copyright:
  years: 2020
lastupdated: "2020-05-26"

keywords: direct link, configure, connection

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

# Adding virtual connections to a {{site.data.keyword.dl_short}} gateway
{: #add-virtual-connection}
{: help}
{: support}

You can add a virtual connection when you create a {{site.data.keyword.dl_short}} gateway, or after the gateway is provisioned.
{: shortdesc}

Make sure that there are no IP address conflicts between on-premises subnets and subnets on IBM Cloud for both VPC and classic infrastructure connections.
{: important}

To add a connection to a provisioned gateway, follow these steps:

1. Highlight the row of the gateway in the {{site.data.keyword.dl_short}} table, then click **Add connection** from the Overflow ![Overflow menu](images/overflow.png) menu. Alternatively, you can click **Add connection +** on the gateway's details page.

   You can create a connection to the logged-in account, or request a connection to a network within another account.

2. Select a network connection, then choose your region from the menu list.
3. Select the VPC network to attach to the gateway and enter a name for the connection. For connections to VPC networks in another {{site.data.keyword.cloud_notm}} account, enter the Cloud Resource Name (CRN) of the target VPC.
4. Click **Add** to attach the virtual connection to the gateway.

After the virtual connection is added to the gateway, the VPC name is shown under the virtual connections section on the gateway's details page.

You can add only one classic infrastructure virtual connection to a provisioned {{site.data.keyword.dl_short}} connection. However, you can add multiple VPC virtual connections.  
{: note}

## Cross-account (VPC only) network connectivity with {{site.data.keyword.dl_short}}
{: #cross-account-virtual-connection}

You can request virtual connections to networks in other {{site.data.keyword.cloud_notm}} accounts for {{site.data.keyword.dl_short}} gateways that indicate the **Provisioned** status.

Only one pending request is allowed per gateway. To create more requests, you can cancel the pending virtual connection request or wait for it to be accepted. Connection requests expire if not accepted within 72 hours.
{:tip}

Follow these steps to connect networks owned by different accounts:

1. Click the {{site.data.keyword.dl_short}} name in the table to show its details, then click **Add connection** in the Virtual connections section.
2. On the Add connection page select **Request connection to a network in another account**.   
3. Type the VPC CRN of the cross-account network.

   To get the CRN of a VPC, click Menu ![Menu icon](/images/menu_icon.png) > **Resource list** from the {{site.data.keyword.cloud_notm}} console. Expand **VPC Infrastructure** to list your VPCs. Select a VPC and click the **Status** entry to view its details. Copy the CRN and paste it in the {{site.data.keyword.dl_short}} window.
   {: tip}

4.  Type the name of the network connection, then click **Add**.

   ![Request connection to a network in another account](/images/dl-add-conn.png)

   The network connection shows in the gateway account with the **Pending approval** status.  

5. The network (VPC) owner's account shows the gateway in **View only** mode. From the network (VPC) owner's account, go to the {{site.data.keyword.dl_short}} dashboard and click the gateway name in the table.

6. In the Virtual Connections section, see **Action required** to view the incoming request. Click **Accept** to accept the network connection request.   

   ![Accept connection request from the network owner's account](/images/dl-vc2.png)

   Confirm by clicking **Accept**.

   ![Are you sure? confirmation](/images/dl-vc3.png)

   The status of the network connection indicates **Attaching**.

7. When you change back to the original account, the status of the virtual connection changes to **Ready**, indicating that the network request was accepted.

   ![Virtual connection changes to Ready](/images/dl-vc5.png)

The gateway account owner (or the network account owner) can delete the virtual connection. If the network owner deletes the virtual connection, the gateway owner sees the connection status as **Detached**. The gateway owner can delete the detached virtual connection from the gateway.
{:note}
