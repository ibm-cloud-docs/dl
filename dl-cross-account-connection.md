---

copyright:
  years: 2020, 2021
lastupdated: "2021-02-01"

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

# Adding a cross-account (VPC only) connection
{: #cross-account-virtual-connection-vpc}

You can request virtual connections to networks in other {{site.data.keyword.cloud_notm}} accounts for {{site.data.keyword.dl_short}} gateways that indicate the **Provisioned** status.

Only one pending request is allowed per gateway. To create more requests, you can cancel the pending virtual connection request or wait for it to be accepted. Connection requests expire if not accepted within 72 hours.
{:note}

Follow these steps to connect networks owned by different accounts:

1. Click the {{site.data.keyword.dl_short}} name in the table to show its details, then click **Add connection** in the Virtual connections section.
2. On the Add connection page select **Request connection to a network in another account**.
3. Type the VPC CRN of the cross-account network.

   **Tip**: To get the CRN of a VPC, click Menu ![Menu icon](/images/menu_icon.png) > **Resource List** from the {{site.data.keyword.cloud_notm}} console. Expand **VPC infrastructure** to list your VPCs. Then, click the row of the VPC, copy the CRN to the clipboard, and paste it in the {{site.data.keyword.dl_short}} window.  For example:

   ![Get CRN of a VPC](/images/crn.png)

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
