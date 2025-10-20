---

copyright:
  years: 2025
lastupdated: "2025-10-20"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# CenturyLink Dynamic Connections ordering considerations
{: #clink}

Follow these steps to request activation and provisioning from CenturyLink Dynamic Connections:

1. Order the CenturyLink Dynamic Connections connect on the CenturyLink portal.

   CenturyLink Dynamic Connections requires two Direct Link Connect orders, one for the Primary connection and one for the Secondary. To proceed with placing this order, select the appropriate port for either the Primary or Secondary connection.
 
   CenturyLink is responsible for making sure that this VLAN is not in use with any CenturyLink Dynamic Connections connections within IBM.
   {: note}

1. Using your IBM Cloud account, order an {{site.data.keyword.cloud}} Direct Link Connect gateway by using the [{{site.data.keyword.cloud_notm}} console](/login){: external}. For instructions, see [Ordering IBM Cloud Direct Link Connect](/docs/dl?topic=dl-how-to-order-ibm-cloud-dl-connect).

   * When defining the IP range to be used for BGP, select **Manual-select IP**.
   * Choose the IP range that you want to use with this gateway.

      Ensure that the IP range you select matches the range specified in the CenturyLink portal. Additionally, verify that you are using the correct Primary or Secondary subnet corresponding to the port that you have chosen.
      {: note}

   * In the BGP ASN field, specify the ASN provided by CenturyLink.

1. Open an IBM Support case. For details, see [Create a case](/unifiedsupport/cases/add) in the IBM Support Center.

   * Select the **Direct Link Connect** tile.
   * In the IBM Support case, add the following information:

      * **Subject**: ATTN: SNS - DL Connect CenturyLink Activation & Provisioning
      * **Description**:
         * Route this case directly to the Special Network Services (SNS) queue for Direct Link Connect implementation with CenturyLink.
         * Include the CenturyLink connection service key that was assigned by CenturyLink (as provided in Step 1).
         * Include the direct link name or service key from the Direct Link page. For example, `0xx43ex3-b8f0-4d52-8b84-x91af2x02yy3`.

The SNS team receives the IBM Support case and initiates a series of steps to bring routers and the IBM portal database into synchronization.

After completion, the IBM Support case is annoted and closed. The timeframe for this activity is five business days from receipt of the case in the SNS queue.
