---

copyright:
  years: 2024
lastupdated: "2024-02-20"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Verizon SCI using Equinix Fabric ordering considerations
{: #verizon-sci-equinix}

Follow these steps to create a Direct Link connection with Verizon SCI and Equinix Fabric.

1. Obtain the following values from the Verizon SCI connection details.

   * Verizon VLAN ID
   * Primary Verizon NNI ID
   * Secondary Verizon NNI ID
   * Primary Verizon IPv4 Address
   * Primary IBM IPv4 Address
   * Secondary Verizon IPv4 Address
   * Secondary IBM IPv4 Address
   * Verizon BGP AS Number

1. Order an {{site.data.keyword.cloud}} Direct Link Connect gateway through the [{{site.data.keyword.cloud_notm}} console](/login){: external}. For instructions, see [Ordering IBM Cloud Direct Link Connect](/docs/dl?topic=dl-how-to-order-ibm-cloud-dl-connect).

   During the ordering process, you can specify your own IP address. Make sure to specify the Verizon SCI-supplied IP addresses instead of your actual client Edge IP addresses.

   To specify your own IP address, follow these steps:

      * Choose **Manual-select IP**.
      * For Range, select **Public**.
      * For Your CIDR, enter the specific IP address from the Verizon-supplied subnet (for example, `10.254.0.26/30`).
      * For your IBM CIDR, enter the specific IP address from the remaining addresses in the Verizon-supplied subnet (for example, `10.254.0.25/30`).
      * For BGP ASN, enter the supplied local ASN (typically, the Verizon Public ASN `1684`) supplied by Verizon.

      ![Direct Link Connect ordering](/images/public-range.png "Manual-select IP Public Range"){: caption="Manual-select IP Public Range" caption-side="bottom"}

   Write down and retain the connection name and the service key generated from the order.
   {: important}

   1. Open an IBM Support case. For details, see [Create a case](/unifiedsupport/cases/add) in the IBM Support Center.

      * Select the **Direct Link Connect** tile.
      * In the IBM Support case, add the following information:
         * **Subject:** DL Connect manual implementation Verizon SCI
         * **Description:**
            * Route this case directly to the Special Network Services (SNS) queue for Direct Link Connect implementation with Verizon SCI.
            * Include the Verizon SCI connection service details (as provided in Step 1):
               * Verizon VLAN ID
               * Primary Verizon NNI ID
               * Secondary Verizon NNI ID
               * Primary Verizon IPv4 Address
               * Primary IBM IPv4 Address
               * Secondary Verizon IPv4 Address
               * Secondary IBM IPv4 Address
               * Verizon BGP AS Number

            * Include the direct link name or service key from the Direct Link page. For example, `0xx43ex3-b8f0-4d52-8b84-x91af2x02yy3`.

The SNS team receives the IBM Support case and initiates a series of steps to bring routers and the IBM portal database into synchronization.

After completion, the IBM Support case is annotated and closed. The timeframe for this activity is five business days from receipt of the case in the SNS queue.
