---

copyright:
  years: 2019
lastupdated: "2019-12-15"

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

You can add a virtual connection when you create a Direct Link gateway using the **Network connections** option. You can also add a virtual connection to the gateway either before or after the gateway is moved to **Provisioned** state.
{: shortdesc}

A gateway is restricted from adding connections during **In review** and some **In progress** states.
{:note}

To add a virtual connection, follow these steps:

1. To add a virtual connection to an existing gateway, highlight the row of the gateway in the Direct Link table, then click **Add connection** from the **Overflow** ![Overflow menu](images/overflow.png) menu. Alternatively, you can click **Actions > Add connection+** on the gateway's details page.

You can create a new connection to the logged-in account, or request a connection to a network within another account.

2. Select a network connection and then select your region from the menu list.
3. Select the VPC network to attach to the gateway and enter a name for the connection. For connections to VPC networks in another {{site.data.keyword.cloud_notm}} account, enter the CRN of the target VPC.
4. Click **Add** to attach the virtual connection to the gateway.

After adding the virtual connection to the gateway, the VPC name displays under the virtual connections section on the gateway's details page.

You can add only one classic infrastructure virtual connection to a provisioned Direct Link connection; however, you can add multiple VPC virtual connections.  
{: note}

## Cross-account network connectivity with Direct Link
{: #cross-account-virtual-connection}

You can request virtual connections to networks in other {{site.data.keyword.cloud_notm}} accounts only for Direct Link gateways that are already **Provisioned**.

Only one pending request is allowed per gateway. To create additional requests, you can cancel the pending virtual connection request, or wait for it to be accepted. Connection requests expire if not accepted within 72 hours.
{:note}

Follow these steps to connect networks owned by different accounts:

1. Click the Direct Link name in the table to show its details, then click **Add connection +** in the "Virtual connections" section.
2. On the "Add connection" page, select to **Request connection to a network within another account**.
3. Type the VPC CRN of the cross-account network. Then, enter the name of the network connection and click **Add**.

   The network connection displays in the gateway account with **Pending approval** status.   
3. The network owner's account displays the gateway in **view only** mode. Click the gateway name and **Accept** the network connection request from the network owner's account.
4. After accepting the network request, the status of the virtual connection changes to **Ready**.

The gateway account owner, or the network account owner, can delete the virtual connection. If the network owner deletes the virtual connection, the gateway owner will see the connection status as **Detached**. The gateway owner can delete the detached virtual connection from the gateway.
{:note}
