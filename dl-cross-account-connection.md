---

copyright:
  years: 2020, 2024
lastupdated: "2024-06-20"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Adding a cross-account (VPC only) connection
{: #cross-account-virtual-connection-vpc}

You can request virtual connections to networks in other {{site.data.keyword.cloud_notm}} accounts for {{site.data.keyword.dl_short}} gateways that indicate the **Provisioned** status.

Only one pending request is allowed per gateway. To create more requests, you can cancel the pending virtual connection request or wait for it to be accepted. Connection requests expire if not accepted within 72 hours.
{: note}

Follow these steps to connect networks owned by different accounts:

1. Click the {{site.data.keyword.dl_short}} name in the table to show its details, then click **Add connection** in the Virtual connections section.
1. On the Add connection page select **Request connection to a network in another account**.
1. Type the VPC CRN of the cross-account network.

   To get the CRN of a VPC, click Menu ![Menu icon](images/menu_icon.png) > **Resource List** from the {{site.data.keyword.cloud_notm}} console. Expand **VPC infrastructure** to list your VPCs. Then, click the row of the VPC, copy the CRN to the clipboard, and paste it in the {{site.data.keyword.dl_short}} window.
   {: note}

1. Type the name of the network connection, then click **Add**. The network connection shows in the gateway account with the **Pending approval** status.
1. The network (VPC) owner's account shows the gateway in **View only** mode. From the network (VPC) owner's account, go to the {{site.data.keyword.dl_short}} dashboard and click the gateway name in the table.
1. In the Virtual Connections section, see **Action required** to view the incoming request. Click **Accept** to accept the network connection request. Then, click **Accept** to confirm.
1. When you change back to the original account, the status of the virtual connection changes to **Ready**, indicating that the network request was accepted.

The gateway account owner (or the network account owner) can delete the virtual connection. If the network owner deletes the virtual connection, the gateway owner sees the connection status as **Detached**. The gateway owner can delete the detached virtual connection from the gateway.
{: note}
