---

copyright:
  years: 2020, 2025
lastupdated: "2025-08-26"

keywords: direct link, direct link connect

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Ordering {{site.data.keyword.dl_full_notm}} Connect
{: #how-to-order-ibm-cloud-dl-connect}
{: help}
{: support}

To order {{site.data.keyword.dl_short}} Connect, you must determine the location that connects to {{site.data.keyword.cloud}}, complete the required {{site.data.keyword.dl_short}} configuration information, then click **Create** to submit your order.
{: shortdesc}

## Planning considerations
{: #before-you-begin-connect}

Make sure to review the following information before you order Direct Link Connect:

* Before you begin, contact your service provider to determine the location to IBM Cloud by verifying your provider's capabilities to reach IBM Cloud over partner interconnects (also known as network-to-network interfaces, or NNIs).
* {{site.data.keyword.cloud_notm}} highly recommends that a second, diverse direct link be established to prevent outages, whether unplanned, or planned due to maintenance. For more information, see [Models for diversity and redundancy](/docs/dl?topic=dl-models-for-diversity-and-redundancy-in-direct-link).
* All subnets of the VPC or classic network are connected to the direct link. When you create VPCs, make sure to create the VPCs with nonoverlapping prefixes and unique subnets.
   * To avoid IP address conflicts for classic connections to a direct link, don't use IP address ranges in the `10.0.0.0/14`, `10.200.0.0/14`, `10.198.0.0/15`, and `10.254.0.0/16` blocks for on-premises networks. On-prem routes that overlap are dropped.
   * For VPC connections to a direct link, you "can" use restricted Classic IP ranges in the `10.0.0.0/14`, `10.200.0.0/14`, `10.198.0.0/15`, and `10.254.0.0/16` blocks.
   * For direct links connected to transit gateways, these IP ranges are always filtered to protect classic networks that might potentially be connected to transit gateways.
* A Generic Routing Encapsulation (GRE)/IPsec tunneling requirement between your Edge router and a customer virtual router in {{site.data.keyword.cloud_notm}} requires a nonconflicting subnet when you order. Default addresses for Direct Link are nonroutable and do not support tunneling.
* VPC permits the use of RFC-1918 and IANA-registered IPv4 address space, privately within your VPC, with some exceptions in the IANA Special-Purpose ranges, and select ranges that are assigned to {{site.data.keyword.cloud_notm}} services. When you use IANA-registered ranges within your enterprise, and within VPCs with {{site.data.keyword.cloud_notm}} Direct Link, custom routes must be installed in each zone. For more information, see [Routing considerations for IANA-registered IP assignments](/docs/vpc?topic=vpc-interconnectivity#routing-considerations-iana).
* If you plan to connect a direct link to a transit gateway, keep in mind that a single direct link instance accepts a maximum of 120 on-premises address prefixes when connected to a transit gateway. Consider aggregating prefixes to keep within this limit. (A direct link can accept a maximum of 200 prefixes when not connected to a transit gateway.)
* For known limitations and restrictions, see [Known limitations](/docs/dl?topic=dl-known-limitations).

## Partner-specific instructions
{: #instructions-partner}

* [AT&T NetBond for Cloud](/docs/dl?topic=dl-netbond)
* [AT&T NetBond Essentials using Equinix Fabric](/docs/dl?topic=dl-att-netbond-essentials)
* [Cologix](/docs/dl?topic=dl-cologix-instructions)
* [Console Connect](/docs/dl?topic=dl-console-connect-ordering)
* [DE-CIX](/docs/dl?topic=dl-de-cix)
* [Digital Realty](/docs/dl?topic=dl-digital-realty)
* [Equinix](/docs/dl?topic=dl-equinix)
* [Megaport](/docs/dl?topic=dl-megaport)
* [Verizon SCI](/docs/dl?topic=dl-verizon-sci)
* [Verizon SCI using Equinix Fabric](/docs/dl?topic=dl-verizon-sci-equinix)

## Ordering instructions
{: #instructions-connect}

To order Direct Link Connect, follow these steps:

1. Log in to your [IBM Cloud account](/login){: external}.
1. Click Menu ![Menu icon](images/menu_icon.png) on the upper left of the page, then click **Infrastructure** > **Network** > **Direct Link**.
1. Click **Order Direct Link**, then click the **Direct Link Connect** tile to open the provisioning page.

   Alternatively, you can click **Direct Link** on the left navigation pane to view the Direct Link page, which lists existing Direct Link instances. Then, click **Order Direct Link** > **Direct Link Connect**.
   {: tip}

1. In the Before you begin section, click **Open checklist** to review the ordering process (also described in [Completing the connection](/docs/dl?topic=dl-how-to-order-ibm-cloud-dl-connect#complete-connection-connect)).
1. In the Resource section, complete the following information:
   * Type a name for your {{site.data.keyword.dl_short}} connection.
   * Choose a resource group to create the {{site.data.keyword.dl_short}} connection. Resource groups help manage and contain resources associated with an account. Select **default** if you don't have any other groups that are defined in the menu list. For more information about resource groups, see [Best practices for organizing resources in a resource group](/docs/account?topic=account-account_setup).
1. In the Gateway section, select a geography, followed by a market, type, site, and routing option. Then, select a provider, connection speed, and port.

   Available speeds are based on your provider's location. {{site.data.keyword.dl_short}} Connect supports the following speeds: 50 Mbps, 100 Mbps, 200 Mbps, 500 Mbps, 1 Gbps, 2 Gbps, 5 Gbps, and 10 Gbps.
   {: note}

   The routing option that you select determines the reachability of the resources in the selected location. If you select the Global routing option along with your location selections, the Region menu list displays all the regions that are globally available in the specific account. After you select a region, you can select any VPC from the Available connections menu. If you select Local routing, then only the region that corresponds to the selected location is available to select. When selected, the VPCs available in the local region for your account are shown.

1. In the Billing section, select **Metered** or **Unmetered**. Metered pricing is paying only for what you use, unmetered is unlimited access for a predicable, monthly fee. Keep in mind that pricing is determined by the routing option and speed that you choose.

   Unmetered billing is only available for specific speeds. {: #dl-connect-bgp}
   {: important}

1. In the BGP section, complete the following information:

   * Select the IBM cross-connect router for the {{site.data.keyword.dl_short}} connection. The number of direct links that are associated with your account for each router is shown next to the router name.
   * Select a BGP peering subnet for the {{site.data.keyword.dl_short}} connection. You have two choices for BGP subnets:
      * Select **Manual-select IP** to specify two of your own IP addresses (in CIDR format) from the ranges `10.254.0.0/16`, `172.16.0.0/12`, `192.168.0.0/16`, `169.254.0.0/16`, or `Public` (a public IP address that you own). Manual-select is useful when trying to avoid conflicts with an existing subnet that is in use.
      * Select **Auto-select IP** for IBM to assign an IP address from IP range `169.254.0.0/16`.

      Make sure that any self-provided BGP addresses do not conflict with blocks that are used by IBM, or by resources external to your {{site.data.keyword.dl_short}} deployment. Also, if you plan to use GRE or IPsec tunneling with your direct link, you must select a BGP IP other than `169.254.0.0/16`.
      {: important}

   * For BGP ASN, use either the default value of `64999` or select an ASN from the specified allowed ranges.
   
      Allowed ASN ranges are:
      * For a 2-byte range, enter a value between `1-64495` or the default `64999`. 
      * For a 4-byte range, enter a value between `4201000000-4294967294`.

      Excluded ASNs: 4-byte `4201065000` – `4201065999`

1. In the Additional BGP settings section, you can activate one or more of these optional settings. Make sure to enable the switch for each section before you configure the settings.

   * **Verify data integrity with Message Digest 5 (MD5)** - Add an extra layer of security between two BGP peers by verifying each transmitted message sent through the BGP session. When MD5 authentication is activated, BGP authenticates every segment that is sent over the TCP session from its peer and verifies the source of each routing update.

      **Important**:

      * Configure the same BGP MD5 authentication key on both your Edge router and the IBM cross-connect router (XCR). The shared authentication key on the IBM device must be stored in your HPCS or Key Protect instance and shared with the Direct Link service. For more information, see [Setting up BGP Message Digest 5 (MD5) authentication keys](/docs/dl?topic=dl-dl-md5).
      * You can achieve hitless key refresh if the keys are updated on both your Edge router and on the IBM cross-connect router (XCR) within 90 seconds. As a pre-condition, you must configure the BGP hold time on your router to a minimum of 90 seconds. All Direct Link routers have a 90-second configuration by default. Either side can initiate the key refresh, but both sides must refresh within the configured BGP hold time to avoid traffic disruption.
      * If a BGP peering session was established and you enable BGP MD5 authentication (or change the authentication key to a different value), BGP sessions are reestablished, which causes BGP session downtime and network disruption until the BGP peer device is configured with the same change.

      Complete the following information:
      * For the keystore, select either **Hyper Protect Crypto Services** or **Key Protect**.
      * Select an authentication keystore instance.
      * Select an authentication key.

   * **Detect network failures with bidirectional Forwarding Detection (BFD)** - Activate BFD to quickly detect faults in a network between two routers or switches that are connected by a link. BFD provides a single, standardized method for detecting link failures at any protocol layer, over any media. For more information, see [Setting up bidirectional forwarding detection](/docs/dl?topic=dl-dl-bfd).

      Activating and deactivating BFD after the BGP session is established causes BGP session downtime and network disruption until the BGP peer device is configured for the same change.
      {: important}

      Complete the following information:
      * Interval – The interval is the minimum time (in milliseconds) expected to occur between when the local routing device sends BFD hello packets and the reply from its neighbor. This value can range from 300 to 255,000 milliseconds.
      * Multiplier – The multiplier is the number of times that a hello packet is missed before BFD declares the neighbor down. This value can range from 1 to 255. The default multiplier value is 3.

   * **Prioritize direct links with AS prepends** - Adjust route preference by lengthening AS paths with multiples of the BGP Autonomous System Number (ASN). When the prefix is matched, the longer AS path becomes a lower priority for the BGP router. For more information, see [Prepending an AS path to influence route priority](/docs/dl?topic=dl-prepend-as-paths).

   * **Filter your import routes** - Select a default filter to either permit or deny all routes unmatched by active route filters. By default, all import routes are permitted. Next, click **Configure filters** to start creating import route filters. To prioritize filters, drag and drop the icon next to the Order number in the table. Click **Save** to save your configuration. For more information, see [Filtering routes](/docs/dl?topic=dl-filter-routes).

   * **Filter your export routes** - Select a default filter to either permit or deny all routes unmatched by active route filters. By default, all export routes are permitted. Next, click **Configure filters** to start creating export route filters. To prioritize filters, drag and drop the icon next to the Order number in the table. Click **Save** to save your configuration. For more information, see [Filtering routes](/docs/dl?topic=dl-filter-routes).

1. In the Connections section, select the type of network connection that you want to bind to the {{site.data.keyword.dl_short}} gateway. You can select a connection type when you create a direct link, or after your direct link is provisioned.

   Select from the following connection types:

   * Select **Direct resources** (default) to create a direct, private connection between your on-premises network and IBM Cloud deployment. Optionally, choose a connection and enter a connection name. To add multiple network connections to the {{site.data.keyword.dl_short}} gateway, click **Add connection +**. You can create one of the following connections:

      * **Classic infrastructure** networks allow you to connect to {{site.data.keyword.cloud_notm}} classic resources. Only one classic infrastructure connection is allowed per {{site.data.keyword.dl_short}} gateway.
      * **VPC** networks allow you to connect to your account’s VPC resources.

      You cannot request a connection to a network in another account when you create a gateway. However, you can request a connection to a network in another account after a gateway is provisioned. You can also create classic infrastructure and VPC connections after a gateway is created. To learn more, see [Adding virtual connections to a {{site.data.keyword.dl_short}} gateway](/docs/dl?topic=dl-add-virtual-connection).
      {: tip}

   * Select **Transit Gateway** to bind your direct link to transit gateways. You can bind your direct link to one or more local gateways, or one global gateway.

      If you select **Transit Gateway** as the type of network connection, you must also initiate a Direct Link connection through the [{{site.data.keyword.cloud_notm}} Transit Gateway console](/interconnectivity/transit){: external} from the same {{site.data.keyword.cloud_notm}} account. For instructions, see [Adding a connection](/docs/transit-gateway?topic=transit-gateway-adding-connections){: external}.
      {: important}

1. An order summary shows pricing estimates for your review. Read and agree to the [{{site.data.keyword.dl_short}} prerequisites](/docs/dl?topic=dl-ibm-cloud-dl-prerequisites) and review Cloud Services [Terms](https://www.ibm.com/products?types[0]=software){: external}. Then, click **Create** to complete your order.

   If you want to add GB egress data to your estimate, click **Add to estimate** to calculate the cost. You can also click the **About** tab for links to {{site.data.keyword.dl_short}} pricing tables and other helpful resources.
   {: tip}

After you create your {{site.data.keyword.dl_short}} order, the {{site.data.keyword.dl_short}} dashboard indicates **Create in progress** order status.

If you refresh the page after a few minutes, it shows **Provisioned** status.

## Completing the connection
{: #complete-connection-connect}

To complete your connection, follow these steps:

1. Contact your network provider and negotiate connectivity to your on-premises or colocation.
1. Create a request on the provider portal to order a virtual circuit. Reference the case ID of the {{site.data.keyword.dl_short}} Connect request as your Request ID or Authorization ID.
1. Configure the BGP parameters on your Edge router for BGP session establishment. After this action completes, the BGP status indicates `Established`.

## Related link
{: #related-links-connect}

[Direct Link Connect service providers and locations](/docs/dl?topic=dl-locations#connect-locations)
