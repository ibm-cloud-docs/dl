---

copyright:
  years: 2020, 2022
lastupdated: "2022-03-23"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Equinix ordering considerations
{: #equinix}

You must use the Equinix Cloud Exchange (ECX) Fabric portal to create a connection for your Equinix service provider. Then, using your IBM Cloud account, return to the Direct Link page in the [IBM Cloud console](https://cloud.ibm.com/interconnectivity/direct-link){: external} to review, accept, and finalize the creation of your direct link.

For Exchange on Classic instructions, see [Steps to order Direct Link Exchange on Classic for Equinix](/docs/direct-link?topic=direct-link-how-to-order-ibm-cloud-direct-link-exchange#provisioning-ibm-cloud-direct-link-exchange-for-equinix).
{: note}

1. Log in to the ECX Fabric portal.
   * Navigate to [https://ecxfabric.equinix.com](https://ecxfabric.equinix.com).
   * Enter your username and password.
   * Click **Sign In**.   
1. In the Frequent Connections section, click the **IBM Cloud** tile.
1. In the **IBM Cloud Direct Link 2** profile, click **Create Connection**.

   ![Equinix ordering](/images/equinix-ibm-cloud-2.png "Equinix ordering"){: caption="Equinix ordering" caption-side="bottom"}
1. In the Origin section, click **Port**.

   ![Select a Port, Location, and Destination](/images/equinix-port.png "Select a Port, Location, and Destination"){: caption="Select a Port, Location, and Destination" caption-side="bottom"}       

1. Select a **Location**, followed by a **Destination**. Then, click **Next**.
1. On the Connection Details page, enter the connection information.

   Your IBM Cloud Account ID is located in the Account section on the [Account settings](https://cloud.ibm.com/account/settings){: external} page.
   {: note}

   ![Connection Details](/images/equinix-connection-details.png "Connection Details"){: caption="Connection Details" caption-side="bottom"}     

1. Select a **Connection Speed**, then click **Next**.   
1. Review and click **Submit Your Order**.
1. Return to the [Direct Link page](https://cloud.ibm.com/interconnectivity/direct-link){: external} in the IBM Cloud console using your IBM Cloud account. Notice that the connection status for your direct link connection states **Create Approval Pending**.
1. Click the Direct Link name in the table to view its Details page. Then, go to the **Actions** section and click **Review** to finalize provisioning of the direct link.

   ![Select to Review this request to finalize direct link provisioning](/images/equinix-review.png "Select to Review this request to finalize direct link provisioning"){: caption="Select to Review this request to finalize direct link provisioning" caption-side="bottom"}

1. In the Review configuration side panel, review your settings, then click **Accept**.

   ![Select Accept to finalize creation of your direct link](/images/equinix-accept.png "Select Accept to finalize creation of your direct link"){: caption="Select Accept to finalize creation of your direct link" caption-side="bottom"}   

1. After your direct link settings are accepted successfully, select a resource group, routing option, and billing type. Optionally, you can [enable MD5 authentication](/docs/dl?topic=dl-enable-disable-md5) to provide additional security for the BGP session, or [update your network connection type](/docs/dl?topic=dl-virtual-connection-types).

   Review your order summary, agree to the [Direct Link Connect prerequisites](/docs/dl?topic=dl-ibm-cloud-dl-prerequisites), and then click **Create** to complete this order.

   ![Complete your direct link settings, then click Create.](/images/equinix-create.png "Complete your direct link settings, then click Create."){: caption="Complete your direct link settings, then click Create" caption-side="bottom"}   

Your direct link is created:

![Completion of your direct link.](/images/equinix-created.png "Completion of your direct link."){: caption="Completion of your direct link" caption-side="bottom"}   
