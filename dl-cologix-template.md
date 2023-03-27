---

copyright:
  years: 2023
lastupdated: "2023-03-22"

keywords: direct link, cologix

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Cologix ordering considerations
{: #cologix-instructions}

Follow these steps to order Direct Link Connect from Cologix:

1. Log in to the [Cologix portal](https://my.cologix.com) and navigate to the Manage Ports & Connections page.  Then, choose the port to add a Direct Link connection.

   ![Choose port for Direct Link connection](/images/cologix1.png "Choose port for Direct Link connection"){: caption="Choose port for Direct Link connection" caption-side="bottom"} 
1. To add a new connection, select **Cloud Connection**.

   ![Add new connection](/images/cologix2.png "Cologix 1"){: caption="Cologix 2" caption-side="bottom"}
1. Select **{{site.data.keyword.cloud_notm}}**. 
1. When prompted, select to either add a **Single Connection** or **Redundant Connections**. Your initial source XC is already chosen. Select a redundant port (if applicable), then click **Next**.

   ![Add single or redundant connections](/images/cologix5.png "Add single or redundant connections"){: caption="Add single or redundant connections" caption-side="bottom"} 
1. Enter your IBM gateway virtual cross-connect (VXC) details. The following parameters are required: 

   - IBM Customer Account ID
   - Name
   - VLAN Identifier (VID)
   - Direct Connect Port Location
   - Connection Speed 
   - VLAN Tagging
   
   The ASN and CIDR values are optional and will be automatically populated if left blank.
   {: note}
   
   Validate your order, then click **Submit**.

   ![Enter XVC details](/images/cologix6.png "Enter XVC details]"){: caption="Enter XVC details" caption-side="bottom"} 
1. After provisioning the new gateways, check the `Request Sent` status to verify that the connections are ready for acceptance on the [{{site.data.keyword.cloud_notm}} console](/login){: external}. This status is also used on edits and deletions. Additions, changes, and deletions can be accepted or rejected and the VXC will return to the appropriate state.

   ![Check Request Sent status](/images/cologix7.png "Check Request Sent status"){: caption="Check Request Sent status" caption-side="bottom"}  
1. Log in to the {{site.data.keyword.cloud_notm}} console. The new gateways are ready for acceptance.
   
   ![Gateways ready for acceptance](/images/cologix8.png "Gateways ready for acceptance"){: caption="Gateways ready for acceptance" caption-side="bottom"} 
1. After your request is accepted in the {{site.data.keyword.cloud_notm}} console, the VXCs move to an `Active` status and can be edited and deleted from the Details page.

   ![Direct Link Details page](/images/cologix9.png "Direct Link Details page"){: caption="Direct Link Details page" caption-side="bottom"}   
1. From the Details page, you can click **Edit** for any editable values, including: 

   - EVC/Connection Name
   - Speed
   - VLAN
   - Notes
   - BGP ASN Number
 
   ![Edit fields](/images/cologix10.png "Edit fields"){: caption="Edit fields" caption-side="bottom"}   
1. The gateway returns to a `Pending` state until the edits are accepted or rejected in the {{site.data.keyword.cloud_notm}} console. 

   ![Pending until edits are accepted or rejected](/images/cologix11.png "Pending until edits are accepted or rejected"){: caption="Pending until edits are accepted or rejected" caption-side="bottom"}   
1. Similarly, you must also confirm deletions in the {{site.data.keyword.cloud_notm}} console. 

   ![Confirm deletions in the {{site.data.keyword.cloud_notm}} console](/images/cologix12.png "Confirm deletions in the {{site.data.keyword.cloud_notm}} console"){: caption="Confirm deletions in the {{site.data.keyword.cloud_notm}} console" caption-side="bottom"}   
   After accepted, your edits are `Active` while the deletion is pending confirmation on the {{site.data.keyword.cloud_notm}} console.
   
   ![Active while deletion is pending confirmation](/images/cologix13.png "Active while deletion is pending confirmation"){: caption="Active while deletion is pending confirmation" caption-side="bottom"}   
