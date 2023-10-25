---

copyright:
  years: 2023
lastupdated: "2023-10-25"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Digital Realty ordering considerations
{: #digital-realty}

Follow these steps to order Direct Link Connect from Digital Realty:

1. Log in to the Digital Realty [ServiceFabric portal](https://servicefabric.digital.realty.com){: external} using your credentials.
1. On the ServiceFabric dashboard, click **Create Link** in the **OTHER RESOURCES** section.
1. In the Create Link side panel, complete the following information:

   * **Name** - Enter a unique name for the link to IBM Cloud.
   * **Description** - Enter an optional description of the service.
   * **Port** - Select the port to create the IBM Cloud Direct Link.
   * **A-Side** - Set an optional VLAN tag to the link. Alternatively, you can select the *Automatic VLAN Assignment** and a VLAN will be selected automatically.
   * **Attachment Type** - Select IBM Cloud as provider.
   * **Account ID** - Enter your IBM Cloud account ID.

      To find the ID, navigate to the [IBM Cloud console](/login){: external} and select **Manage > Account > Account settings**.
      {: note}

   * **Cloud Port Attachment** - Select the IBM Cloud on-ramp location where you want to connect.
   * **Customer ASN** - Enter the AS (Autonomous System) Number of your router.
   * **Customer IP Address** - Enter the IP address of your router.
   * **IBM IP Address** - Enter the IP Address of the IBM Cloud router.
   * **Speed** - Select the link speed to IBM Cloud.

   ![Create Link side panel properties](/images/servicefabric1.jpg "Create Link side panel properties"){: caption="Create Link side panel properties" caption-side="bottom"}

   On the ServiceFabric dashboard, the Active Services window shows the new service status as **Creating**.

1. Log in to your [IBM Cloud account](/login){: external}. Click Menu ![Menu icon](/images/menu_icon.png) on the upper left of the page, then click **Interconnectivity**.
1. Scroll to locate the Connect tile, then click **Order {{site.data.keyword.dl_short}} Connect**.
1. In the Direct Link table, click the new service name, then select **Review** in the Actions section.

   ![Review creation request from your service provider](/images/servicefabric2.jpg "Review creation request from your service provider"){: caption="Review creation request from your service provider" caption-side="bottom"}

1. Select a resource group, routing type, and router configurations for the direct link, then click **Next**.

   ![Complete direct link configuration](/images/servicefabric3.jpg "Complete direct link configuration"){: caption="Finalize direct link configuration" caption-side="bottom"}

1. Finalize the direct link configuration process, then click **Create**.

   ![Finalize direct link configuration](/images/servicefabric4.jpg "Finalize direct link configuration"){: caption="Finalize direct link configuration" caption-side="bottom"}

1. Navigate back to the ServiceFabric portal. The service appears as **Active**.
