---

copyright:
  years: 2020, 2024
lastupdated: "2024-06-19"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# DE-CIX ordering considerations
{: #de-cix}

Follow these steps to order Direct Link Connect from DE-CIX:

1. Navigate to the [Login - DE-CIX portal](https://portal.de-cix.net/login){: external} and enter your Username and Password, then click **Login**.
1. Click **Add Service**, then select **Add DirectCLOUD Service**.
1. On the Choose your Provider page, select **IBM Cloud** and click **Next**.

   ![Choose your Provider page](/images/decix-choose-provider.png "Choose your Provider page"){: caption="Choose your Provider page" caption-side="bottom"}

1. Enter your IBM Account number, then click **Next**.

   ![Provider Credentials page](/images/decix-credentials.png "Provider Credentials page"){: caption="Provider Credentials page" caption-side="bottom"}

1. Complete required values, then click **Next**.

   * **Cloud On-Ramp Location**: IBM Cloud on-ramp location where you want to get connected
   * **Metro Area of your Access**: Location of your DE-CIX access port
   * **External reference**: _Optional_
   * **Purchase order**: _Optional_
   * **Subscriber CIDR**: IP Address of your router
   * **Provider CIDR**: IP Address of the IBM Cloud router
   * **ASN**: AS number of your router
   * **Bandwidth**: Bandwidth of the connection that you want

   ![Service Details page](/images/decix-service-details.png "Service Details page"){: caption="Service Details page" caption-side="bottom"}

1. Review your connection details, then click **Order**.

   ![Complete Your Order page](/images/decix-complete-order.png "Complete Your Order page"){: caption="Complete your order" caption-side="bottom"}

1. Wait until the service gets created, then click **Next**.

   ![Provisioning page](/images/decix-provisioning.png "Provisioning page"){: caption="Provisioning page" caption-side="bottom"}

1. Select a VLAN ID for the service, then click **Next**.

   If you have any questions regarding the options on this page, contact the DE-CIX support team.
   {: note}

   ![Configure VLANs page](/images/decix-configure-vlans.png "Configure VLANs page"){: caption="Configure VLANs page" caption-side="bottom"}

1. Click **Accept IBM connection** to be forwarded to the IBM Cloud console.

   ![Accept IBM connection](/images/decix-accept-connection.png "Accept IBM connection"){: caption="Accept IBM connection" caption-side="bottom"}

1. Click **Review** to finalize the provisioning process.

   ![Details page](/images/decix-review.png "Details page"){: caption="Details page"}

1. Review your settings and click **Accept**.

   ![Review configuration](/images/decix-review-configuration.png "Review configuration"){: caption="Review configuration" caption-side="bottom"}

1. After your direct link settings are accepted successfully, select a resource group, routing option, and billing type. Optionally, you can enable MD5 authentication to provide additional security for the BGP session, or update your network connection type.

1. Review your order summary, agree to the Direct Link Connect prerequisites, and then click **Create** to complete this order.

   ![Finalize creation](/images/decix-finalize-creation.png "Finalize creation"){: caption="Finalize creation" caption-side="bottom"}

   Your direct link is created:

   ![Direct Link created](/images/decix-direct-link.png "Direct Link created"){: caption="Direct Link created" caption-side="bottom"}

   If you switch back to the DE-CIX portal, you should see the following page after some time. The status on this page shows you that your direct link was created successfully.

   ![Cloud order completed](/images/decix-order-completed.png "Cloud order completed"){: caption="Cloud order completed" caption-side="bottom"}
