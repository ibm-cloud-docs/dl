---

copyright:
  years: 2020, 2025
lastupdated: "2025-12-31"

keywords: direct link, direct link dedicated, macsec

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Ordering {{site.data.keyword.dl_full_notm}} Dedicated
{: #how-to-order-ibm-cloud-dl-dedicated}
{: help}
{: support}

To order {{site.data.keyword.dl_short}} Dedicated, you must determine the location that connects to IBM Cloud, complete the required {{site.data.keyword.dl_short}} configuration information, then click **Create** to submit your order.
{: shortdesc}

## Planning considerations
{: #before-you-begin-dedicated}

Make sure that you review the following information before you order Direct Link Dedicated:

* Before you begin, contact your service provider to determine the location to IBM Cloud by verifying your colocation or service provider's capabilities to reach the Meet Me Room and cross-connect into IBM Cloud.
* All subnets of the VPC or classic network are connected to the direct link. When you create VPCs, make sure to create the VPCs with nonoverlapping prefixes and unique subnets.
   * To avoid IP address conflicts for classic connections to a direct link, don't use IP address ranges in the `10.0.0.0/14`, `10.200.0.0/14`, `10.198.0.0/15`, and `10.254.0.0/16` blocks for on-prem networks. On-prem routes that overlap are dropped.
   * For VPC connections to a direct link, you "can" use restricted Classic IP ranges in the `10.0.0.0/14`, `10.200.0.0/14`, `10.198.0.0/15`, and `10.254.0.0/16` blocks.
   * For direct links connected to transit gateways, these IP ranges are always filtered to protect classic networks that might potentially be connected to transit gateways.
* A Generic Routing Encapsulation (GRE)/IPsec tunneling requirement between your Edge router and a virtual router in {{site.data.keyword.cloud_notm}} requires a nonconflicting subnet when ordering. The default addresses for Direct Link are nonroutable and do not support tunneling.
* {{site.data.keyword.cloud_notm}} VPC permits the use of RFC-1918 and IANA-registered IPv4 address space, privately within your VPC. It also permits this use, with some exceptions, in the IANA Special-Purpose ranges, and select ranges that are assigned to {{site.data.keyword.cloud_notm}} services. When you use IANA-registered ranges within your enterprise, and within VPCs with {{site.data.keyword.cloud_notm}} Direct Link, custom routes must be installed in each zone. For more information, see [Routing considerations for IANA-registered IP assignments](/docs/vpc?topic=vpc-interconnectivity#routing-considerations-iana).
* If you plan to connect your direct link to a transit gateway, keep in mind that a single direct link instance accepts a maximum of 120 on-premises address prefixes when connected to a transit gateway. Consider aggregating prefixes to keep within this limit.

   A direct link can accept a maximum of 200 prefixes when not connected to a transit gateway.
   {: note}

* Be sure to consult and familiarize yourself with the [Known issues and limitations](/docs/dl?topic=dl-known-limitations).
* For Direct Link Dedicated with MACsec feature only:

   * Currently, the Direct Link Dedicated with MACsec feature is offered in select locations, with growing support.
   * Ensure that you [secure your data in Direct Link](/docs/dl?topic=dl-mng-data&interface=cli).
   * Review [Guidelines and restrictions for Direct Link Dedicated with MACsec](/docs/dl?topic=dl-limitations-macsec).

## Ordering instructions
{: #instructions-dedicated}

To order {{site.data.keyword.dl_full}} Dedicated, follow these steps.
{: shortdesc}

1. In the [{{site.data.keyword.cloud_notm}} console](/login){: external}, click the **Navigation menu** icon ![menu icon](../icons/icon_hamburger.svg), then select **Infrastructure > Network > Direct link**.
1. Click **Order Direct Link**, then click the **Direct Link Dedicated** tile to open the provisioning page.
1. In the Before you begin section, click **Expand checklist** to review the ordering process (also described in [Completing the connection](/docs/dl?topic=dl-complete-connection-dedicated)).
1. In the Resource section, complete the following information:

   * Type a name for your {{site.data.keyword.dl_short}} Dedicated connection.
   * Choose a resource group to create the {{site.data.keyword.dl_short}} connection. Resource groups help manage and contain resources that are associated with an account. Select **Default** if you don't have other groups that are defined in the menu list. For more information about resource groups, see [Best practices for organizing resources in a resource group](/docs/account?topic=account-account_setup).
   * Type your customer and carrier names.

1. Optionally, you can enable enhanced traffic security in the MACsec section. To do so, toggle the **Secure Direct Link with MACsec** switch and follow these steps:

   Before establishing a direct link with the MACsec feature, make sure that all [prerequisites](/docs/dl?topic=dl-macsec-prerequisites) are met. Additionally, make sure to review MACsec [guidelines and restrictions](/docs/dl?topic=dl-limitations-macsec).
   {: important}

   1. Type the replay protection window size in packets. The default value is `512`. The secured interface does not accept any reordered packet that is outside the specified window size.
   1. Choose the level of enforcement required for securing the network traffic:

      * **Must secure** - Enforces mandatory encryption for all network traffic, helping ensure strict confidentiality, integrity, and authenticity.
      * **Should secure** - Recommends encryption for network traffic, but it is not mandatory and can allow exceptions or fallback options.

   1. For the Security Association Key (SAK) rekey mode, define how you want your keys refreshed or changed during communication between devices:

      * **Timer** - The SAK is rekeyed after the specified time interval. This ensures that keys are periodically changed at regular time intervals, regardless of the number of packets transmitted.
      * **Packet number rollover** - The SAK is rekeyed based on the used packet numbers. This option triggers rekeying based on the number of packets sent, ensuring a new key is used after a high proportion of used packet numbers with the current SAK (the exact threshold determined at the system's discretion).

   1. Configure a primary CAK.
      1. Type a CAK name.
      1. Choose a  HPCS instance for the primary connectivity association key (CAK) key.
      1. Choose a key from HPCS containing the CAK secret.
   1. Optionally, configure a fallback CAK.
      1. Type a CAK name.  
      1. Choose a fallback key instance.
      1. Choose a key from HPCS containing the CAK secret.
   
      If you do not have a fallback key, you can set one up after you provision your direct link.
      {: note}

   1. Ensure that the switch is **Activated** for MACsec if you want to immediately try to establish a MACsec session when you provision your direct link.

         You can also activate and deactivate MACsec after creating your direct link.
         {: note}
      
1. In the Gateway section, complete the following information:

   1. Select a geography, followed by a market, type, site, and routing option.

      Local and global routing options are supported. When you select a routing option, the location details with reachable sites display.

      The routing option that you select determines the reachability of the resources in the selected location. If you select the **Global** routing option along with your location selections, the **Region** menu list displays all the regions that are globally available in the specific account. After you select a region, you can select any VPC from the **Available connections** menu. If you select **Local** routing, then only the region that corresponds to the selected location is available to select. When selected, the VPCs available in the local region for your account are shown.
      {: note}

   1. Choose a connection speed. The speeds that are supported for the {{site.data.keyword.dl_short}} Dedicated offering are 1 Gbps, 2 Gbps, 5 Gbps, and 10 Gbps.

      Speeds greater than 1 Gbps require 10 Gbps service from the client's carrier and equipment. If you intend to upgrade the speed for this gateway, select 2 Gbps to start with; otherwise, you cannot upgrade to a higher speed on this gateway.
      {: tip}

   1. Choose the cross-connect router available at the selected location for this direct link. You can't modify this router after provisioning. Some routers can be disabled based on their support for the MACsec feature and the decisions made regarding its use. 

   1. Choose the support level of MACsec that you want for this direct link. The available capabilities depend on the ports available on the selected cross-connect router. The options are:

      * **Require MACsec** - Enforce the use of MACsec, which cannot be disabled after provisioning.

         **Require MACsec** allows you to edit MACsec configuration, but you can’t remove this feature. 
         {: note}

      * **Enable/disable MACsec** - Optionally, enable or disable MACsec either during or after the provisioning of this direct link. After MACsec is enabled, you can activate or deactivate this feature.          

      * **No MACsec** - Exclude this direct link from using MACsec. MACsec can't be enabled during or after provisioning. 

         **Warning: You can’t use or enable MACsec on this direct link, nor can you select a router that supports only MACsec.**

1. In the Billing section, select **Metered** or **Unmetered**. Metered pricing means paying only for what you use. Unmetered is unlimited access, for a predicable, monthly fee. {: #dl-dedicated-bgp}
1. In the BGP section, complete the following information:
   * Select the IBM cross-connect router for the {{site.data.keyword.dl_short}} connection. The number of direct links that are associated with your account for each router is shown next to the router name.
   * Select a BGP peering subnet for the {{site.data.keyword.dl_short}} connection. You have two choices for BGP subnets:
      * Select **Manual-select IP** to specify two of your own IP addresses (in CIDR format) from the ranges `10.254.0.0/16`, `172.16.0.0/12`, `192.168.0.0/16`, `169.254.0.0/16`, or `Public` (a public IP address that you own).

         Manual-select is useful when you are trying to avoid conflicts with an existing subnet that is in use.
         {: tip}
        
      * Select **Auto-select IP** to have IBM assign an IP address from IP range `169.254.0.0/16`.

      Make sure that any self-provided BGP addresses do not conflict with blocks that are used by IBM, or by resources external to your {{site.data.keyword.dl_short}} deployment. Also, if you plan to use GRE or IPsec tunneling with your direct link, you must select a BGP IP other than `169.254.0.0/16`.
      {: important}

   * For BGP ASN, use either the default value of `64999` or select an ASN from the specified allowed ranges.  

      The router supports public and private ASNs, including both 2-byte and 4-byte values (`1` to `4`,`294,967,294`), except for the following excluded ASNs: `0`, `13884`, `36351`, `64512`, `64513`, `65100`, `65201`–`65234`, `65402`–`65433`, `65500`, `65516`, `65519`, `65521`, `65531`, and `4201065000`–`4201065999`. 

1. In the Additional gateway settings section, you can activate one or more of these optional settings:

   * **Configure Virtual Local Area Network (VLAN) tagging** - Specify the VLAN that is configured on your router to establish connectivity to IBM on the VLAN of your choice. For more information, see [Activating, deactivating, and updating VLAN tagging](/docs/dl?topic=dl-activate-vlan-tagging).

      Activating, deactivating, or updating a VLAN after the BGP session is established causes BGP session downtime and network disruption until the BGP peer device is configured for the same change.
      {: important}

      Enter a VLAN ID and a value in the range from `2` to `3967`.

      The VLAN must comply with the IEEE 802.1Q (Dot 1Q) standard.
      {: note}

   * **Verify data integrity with Message Digest 5 (MD5)** - Add an extra layer of security between two BGP peers by verifying each transmitted message sent through the BGP session. When MD5 authentication is activated, BGP authenticates every segment that is sent over the TCP session from its peer and verifies the source of each routing update.

      **Important**:

      * Configure the same BGP MD5 authentication key on both your Edge router and the IBM cross-connect router (XCR). The shared authentication key on the IBM device must be stored in your HPCS or Key Protect instance and shared with the Direct Link service. For more information, see [Setting up BGP Message Digest 5 (MD5) authentication keys](/docs/dl?topic=dl-dl-md5).
      * You can achieve hitless key refresh if the keys are updated on both your Edge router and on the IBM cross-connect router (XCR) within 90 seconds. As a precondition, you must configure the BGP hold time on your router to a minimum of 90 seconds. All Direct Link routers have a 90-second configuration by default. Either side can initiate the key refresh, but both sides must refresh within the configured BGP hold time to avoid traffic disruption.
      * If a BGP peering session was established and you enable BGP MD5 authentication (or change the authentication key to a different value), BGP sessions are reestablished. This action causes BGP session downtime and network disruption until the BGP peer device is configured with the same change.

      Complete the following information:
      * For the keystore, select either **Hyper Protect Crypto Services** or **Key Protect**.
      * Select an authentication keystore instance.
      * Select an authentication key.

   * **Detect network failures with Bidirectional Forwarding Detection (BFD)** - Activate BFD to quickly detect faults in a network between two routers or switches that are connected by a link. BFD provides a single, standardized method for detecting link failures at any protocol layer, over any media. For more information, see [Setting up bidirectional forwarding detection](/docs/dl?topic=dl-dl-bfd).

      Activating and deactivating BFD after the BGP session is established causes BGP session downtime and network disruption until the BGP peer device is configured for the same change.
      {: important}

      Complete the following information:
      * Interval – The interval is the minimum time (in milliseconds) expected to occur between when the local routing device sends BFD hello packets and the reply from its neighbor. This value can range from 300 to 255,000 milliseconds.
      * Multiplier – The multiplier is the number of times that a hello packet is missed before BFD declares the neighbor down. This value can range from 1 to 255. The default multiplier value is 3.

   * **Prioritize direct links with AS prepends** - Adjust the route preference by lengthening AS paths with multiples of the BGP Autonomous System Number (ASN). When the prefix is matched, the longer AS path becomes a lower priority for the BGP router. For more information, see [Prepending an AS path to influence route priority](/docs/dl?topic=dl-prepend-as-paths).

   * **Filter your import routes** - Select a default filter to either permit or deny all routes unmatched by active route filters. By default, all import routes are permitted. Next, click **Configure filters** to start creating import route filters. To prioritize filters, drag the icon next to the Order number in the table. Click **Save** to save your configuration. For more information, see [Filtering routes](/docs/dl?topic=dl-filter-routes).

   * **Filter your export routes** - Select a default filter to either permit or deny all routes unmatched by active route filters. By default, all export routes are permitted. Next, click **Configure filters** to start creating export route filters. To prioritize filters, drag the icon next to the Order number in the table. Click **Save** to save your configuration. For more information, see [Filtering routes](/docs/dl?topic=dl-filter-routes).

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

1. An order summary shows pricing estimates for your review. Read and agree to the [**{{site.data.keyword.dl_short}} prerequisites**](/docs/dl?topic=dl-ibm-cloud-dl-prerequisites) and review the Cloud Services [**Terms**](https://www.ibm.com/support/customer/csol/terms/?id=i126-8695){: external}. Then, click **Create** to complete your order.

   If you want to add GB egress data to your estimate, click **Add to estimate** to calculate the cost. You can also click the **About** tab for links to {{site.data.keyword.dl_short}} pricing tables and other helpful resources.
   {: tip}

## Next step
{: #dedicated-next-step}

After you submit your Direct Link Dedicated order, the Direct Link table indicates an LOA creation in progress connection status. Click the name of the connection to open its details page. Then, view the Actions section to see whether you have any pending actions.
To view the completion process, see [Completing the connection](/docs/dl?topic=dl-complete-connection-dedicated).

## Related link
{: #related-links-dedicated}

[Direct Link Dedicated locations](/docs/dl?topic=dl-locations#dedicated-locations)
