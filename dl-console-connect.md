---

copyright:
  years: 2024
lastupdated: "2024-05-08"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Console Connect ordering considerations
{: #console-connect-ordering}

Follow these steps to create a Direct Link connection with Console Connect by PCCW Global.

1. From the Console Connect dashboard, go to the menu and click **Connections > Add new**.
   ![Console Connect dashboard](/images/pccw-dashboard.png "Console Connect dashboard"){: caption="Console Connect dashboard" caption-side="bottom"}

1. Make sure that the **Cloud & XaaS** tile is selected, then click the **IBM Cloud** tile.
   ![New Connection page](/images/pccw-new-connection.png "New Connection page"){: caption="New Connection page" caption-side="bottom"}

1. For the IBM Cloud Account ID, enter your 32-bit IBM account number, then click **Next: Ports**.
   ![IBM Cloud details page](/images/pccw-account-id.png "IBM Cloud details page"){: caption="IBM Cloud details page" caption-side="bottom"}

   To obtain your IBM account number, go to the [IBM Cloud console](/login){: external} and click **Manage > Account**. Then, click **Account settings** to display your IBM Cloud account ID. Copy and paste the ID into the IBM Cloud Account ID field.
   {: tip}

1. On the Ports page, select your source port and interconnect destination, then click **Next: Connection**.
   ![Ports page](/images/pccw-ports.png "Ports page"){: caption="Ports page" caption-side="bottom"}

1. On the Connection details page, enter a name for your connection, select a rate limit (Mbps), then specify your plan usage and duration. Click **Next: Review**.
   ![Connection details page](/images/pccw-connection-details.png "Connection details page"){: caption="Connection details page" caption-side="bottom"}

   The Source VLAN ID is auto-assigned.
   {: note}

1. On the Review page, review your order, then click **Next: Payment**.
   ![Review page](/images/pccw-review.png "Review page"){: caption="Review page" caption-side="bottom"}

1. Select a payment method and agree to the Terms and Conditions. Then, click **Connect** to finalize your order.
   ![Finalize order](/images/pccw-terms.png "Finalize order"){: caption="Finalize order" caption-side="bottom"}

   The console begins to provision this Layer 2 service.

1. Navigate back to the [IBM Cloud console](/login){: external} to accept the direct link and complete the provisioning. To do so, follow these steps:

   1. Select the **Navigation Menu** icon ![menu icon](../icons/icon_hamburger.svg), then click **Interconnectivity > Direct Link**.
   1. In the table, click the name of the new direct link to display its details, then click **Review**.
   1. Select a resource group and type of routing (Local or Global), then click **Next**.
   1. (Optional) Configure any AS prepends if required, then click **Next**.
   1. (Optional) Configure any route filters if required, then click **Next**.
   1. Review and agree to the configuration and cost.
   1. Select to read and agree to the Direct Link prerequisities, then click **Create**.

This might take a few minutes to complete.

* In the Console Connect dashboard, IBM Direct Link connection changes to **Accept on Cloud** and provisioning continues.
   ![Accept on Cloud](/images/pccw-accept-on-cloud.png "Accept on Cloud"){: caption="Accept on Cloud" caption-side="bottom"}

* In the IBM Cloud console, the direct link connection changes to `Provisioned` state.
   ![Provisioned](/images/pccw-provisioned.png "Provisioned"){: caption="Provisioned" caption-side="bottom"}

* In the Console Connect dashboard, the IBM Direct Link connection shows active (**Up**), but requires BGP to be configured.
   ![Connection is Up](/images/pccw-up.png "Connection is Up"){: caption="Connection is Up" caption-side="bottom"}

## Next step
{: #pccw-next-step}

Configure BGP configurations on your equipment. Optionally, you can enable MD5 authentication to secure the BGP session by allowing routing of messages only from routers using a shared authentication key. For more information, see [Enabling MD5 authentication for BGP peers](/docs/dl?topic=dl-accepting-provider-created-connection#dl-enable-md5-provider).

This completes the provisioning of your direct link.
