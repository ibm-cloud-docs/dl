---

copyright:
  years: 2020
lastupdated: "2020-02-19"

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

# Adding virtual connections to a Direct Link gateway
{: #add-virtual-connection}

You can add a virtual connection when you create a Direct Link gateway by using the **Network connections** option. You can also add a virtual connection to the gateway after the gateway is provisioned.
{: shortdesc}

To add a connection to a provisioned gateway, follow these steps:

1. Highlight the row of the gateway in the Direct Link table, then click **Add connection** from the **Overflow** ![Overflow menu](images/overflow.png) menu. Alternatively, you can click **Actions > Add connection** on the gateway's details page.

You can create a new connection to the logged-in account, or request a connection to a network within another account.

2. Select a network connection and then select your region from the menu list.
3. Select the VPC network to attach to the gateway and enter a name for the connection. For connections to VPC networks in another {{site.data.keyword.cloud_notm}} account, enter the Cloud Resource Name (CRN) of the target VPC.
4. Click **Add** to attach the virtual connection to the gateway.

After the virtual connection is added to the gateway, the VPC name displays under the virtual connections section on the gateway's details page.

You can add only one classic infrastructure virtual connection to a provisioned Direct Link connection. However, you can add multiple VPC virtual connections.  
{: note}

## Cross-account network connectivity with Direct Link
{: #cross-account-virtual-connection}

You can request virtual connections to networks in other {{site.data.keyword.cloud_notm}} accounts only for Direct Link gateways that are already **Provisioned**.

Only one pending request is allowed per gateway. To create more requests, you can cancel the pending virtual connection request, or wait for it to be accepted. Connection requests expire if not accepted within 72 hours.
{:note}

Follow these steps to connect networks owned by different accounts:

1. Click the Direct Link name in the table to show its details, then click **Add connection** in the "Virtual connections" section.
2. On the "Add connection" page, select to **Request connection to a network within another account**.
3. Type the VPC CRN of the cross-account network. Then, enter the name of the network connection and click **Add**.

   To get the CRN of a VPC, click **Menu** ![Menu icon](../icons/icon_hamburger.svg) > **Resource list** from the {{site.data.keyword.cloud_notm}} console. Expand **VPC Infrastructure** to list your VPCs. Select a VPC and then click the **Status** entry to view its details. Copy the CRN and paste it in the Direct Link window.
   {: tip}

   The network connection displays in the gateway account with **Pending approval** status.   
3. The network owner's account displays the gateway in **view only** mode. Click the gateway name and **Accept** the network connection request from the network owner's account.
4. After the network request is accepted, the status of the virtual connection changes to **Ready**.

The gateway account owner, or the network account owner, can delete the virtual connection. If the network owner deletes the virtual connection, the gateway owner sees the connection status as **Detached**. The gateway owner can delete the detached virtual connection from the gateway.
{:note}
