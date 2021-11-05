---

copyright:
  years: 2020, 2021
lastupdated: "2021-11-03"

keywords:  

subcollection: dl

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:beta: .beta}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:term: .term}  
{:generic: data-hd-programlang="generic"}
{:download: .download}  
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Ordering {{site.data.keyword.dl_full_notm}} Dedicated
{: #how-to-order-ibm-cloud-dl-dedicated}
{: help}
{: support}

To order {{site.data.keyword.dl_short}} Dedicated, you must determine the location connecting to IBM Cloud, complete the required configuration information, then click **Create** to submit your order.
{: shortdesc}

## Planning considerations
{: #before-you-begin-dedicated}

Make sure that you review the following considerations before ordering Direct Link Dedicated:

* Before you begin, determine the location connection to IBM Cloud by verifying your colocation provider's or service provider's capabilities to reach the Meet Me Room and cross-connect into IBM Cloud.
* All subnets of the VPC or classic network will be connected to the direct link. When creating VPCs, make sure to create the VPCs with non-overlapping prefixes and unique subnets. To ensure successful connectivity with the classic infrastructure, do not use IP addresses for your VPCs in the `10.0.0.0/14`, `10.200.0.0/14`, `10.198.0.0/15`, and `10.254.0.0/16` blocks.
* A Generic Routing Encapsulation (GRE)/IPsec tunneling requirement between your Edge router and a virtual router in {{site.data.keyword.cloud_notm}} requires a non-conflicting subnet when ordering. Default addresses for Direct Link are non-routable and do not support tunneling.
* {{site.data.keyword.cloud_notm}} VPC permits the use of RFC-1918 and IANA-registered IPv4 address space, privately within your VPC, with some exceptions in the IANA Special-Purpose ranges, and select ranges assigned to {{site.data.keyword.cloud_notm}} services. When using IANA-registered ranges within your enterprise, and within VPCs in conjunction with {{site.data.keyword.cloud_notm}} Direct Link, custom routes must be installed in each zone. For more information, see [Routing considerations for IANA-registered IP assignments](/docs/vpc?topic=vpc-interconnectivity#routing-considerations-iana).
* If you plan to connect your direct link to a transit gateway, keep in mind that a single Direct Link gateway instance accepts a maximum of 120 on-premises address prefixes when connected to a transit gateway. Consider aggregating prefixes to keep within this limit.

## Ordering instructions
{: #instructions-dedicated}

To order {{site.data.keyword.dl_full}} Dedicated, follow these steps.
{: shortdesc}

1. Log in to your [{{site.data.keyword.cloud_notm}}](https://{DomainName}/){: external} account.
1. Click Menu ![Menu icon](images/menu_icon.png) on the upper left, then click **Interconnectivity**.
1. Scroll to locate the Dedicated tile, then click **Order {{site.data.keyword.dl_short}} Dedicated** to order.

   ![Direct Link offerings](/images/dl-dedicated-options.png){: caption="Direct Link offerings" caption-side="bottom"}    

   Alternatively, you can click **Direct Link** in the left navigation pane to view the Direct Link page, which lists existing Direct Link instances. From this page, you can click **Order Direct Link** > **Direct Link Dedicated** tile.
   {: tip}

1. In the Before you begin section, click **Open checklist** to review the ordering process (also described in [Completing the connection](/docs/dl?topic=dl-how-to-order-ibm-cloud-dl-dedicated#complete-connection)).

   ![Before you begin section](/images/dl-before-you-begin.png){: caption="Before you begin section" caption-side="bottom"}    

1. In the Resource section, complete the following information:

   * Type a name for your {{site.data.keyword.dl_short}} Dedicated connection.
   * Choose a resource group to create the {{site.data.keyword.dl_short}} connection. Resource groups help manage and contain resources associated with an account. Select **Default** if you don't have other groups defined in the drop-down list. For more information about resource groups, see [Best practices for organizing resources in a resource group](/docs/account?topic=account-account_setup).    
   * Type your customer and carrier names.

      ![Resource section](/images/dl-resource-dedicated.png){: caption="Resource section" caption-side="bottom"}  

1. In the Gateway section, complete the following:

   * Select a geography, followed by a market, type, site, and routing option.

      Local and global routing options are supported. When you select a routing option, the location details with reachable sites are displayed.  
      {: note}

   * Choose a connection speed. The speeds supported for the {{site.data.keyword.dl_short}} Dedicated offering are 1 Gbps, 2 Gbps, 5 Gbps, and 10 Gbps.

      Speeds greater than 1 Gbps require 10 Gbps service from the client's carrier and equipment. If you intend to upgrade the speed for this gateway, select 2 Gbps to start with; otherwise, you will not be able to upgrade to a higher speed on this gateway.
      {: tip}   

   * Choose an IBM cross-connect router, if available.

      ![Gateway section](/images/dl-config-dedicated.png){: caption="Gateway section" caption-side="bottom"}     

   The routing option that you select determines the reachability of the resources in the selected location. If you select the **Global** routing option along with your location selections, the **Region** menu list displays all the regions that are globally available in the specific account. After selecting a region, you can select any VPC from the **Available connections** menu. If you select **Local** routing, then only the region that corresponds to the selected location is available to select. When selected, the VPCs available in the local region for your account are shown.
   {: note}

1. In the Billing section, select **Metered** or **Unmetered**. Metered pricing is paying only for what you use. Unmetered is unlimited access, for a predicable, monthly fee. See [Pricing for {{site.data.keyword.dl_full_notm}}](/docs/dl?topic=dl-pricing-for-ibm-cloud-dl) for details.

   ![Billing section](/images/dl-billing.png){: caption="Billing section" caption-side="bottom"}    

1. In the BGP section, complete the following information: {: #dl-dedicated-bgp}

   * Select the IBM cross-connect router for the {{site.data.keyword.dl_short}} connection. The number of direct links associated with your account for each router is shown next to the router name.   
   * Select a BGP peering subnet for the {{site.data.keyword.dl_short}} connection. There are two choices for BGP subnets:
      * Select **Auto-select IP** for IBM to assign an IP address from IP range `169.254.0.0/16`.
      * Select **Manual-select IP** to specify two of your own IP addresses (in CIDR format) from the ranges `10.254.0.0/16`, `172.16.0.0/12`, `192.168.0.0/16`, `169.254.0.0/16`, or `Public` (a public IP address that you own). Manual-select is useful when trying to avoid conflicts with an existing subnet that is in use.
      
      Make sure that any self-provided BGP addresses do not conflict with blocks that are used by IBM, or by resources external to your {{site.data.keyword.dl_short}} deployment. Also, if you plan to use GRE or IPsec tunneling with your Direct Link gateway, you must select a BGP IP other than `169.254.0.0/16`.
      {: important}

   * For BGP ASN, use either the default value of `64999` or select an ASN from the specified allowed ranges.
      Allowed ASN ranges are:
      * For a 2-byte range, enter a value between `1-64495` or the default `64999`.
      * For a 2-byte or 4-byte range, enter a value between `131072-4199999999`.
      * For a 4-byte range, enter a value between `4201000000-4201064511`.

      Excluded ASNs: `64512`, `64513`, `65100`, `65201-65234`, `65402-65433`, `65500`, and `4201065000-4201065999`.

      ![BGP section](/images/bgp-dedicated.png){: caption="BGP section" caption-side="bottom"}       

1. In the Additional BGP settings section, you can activate one or more of these optional settings.

   ![BGP section](/images/bgp-opt-settings.png){: caption="BGP section" caption-side="bottom"}         

   * **BGP Message Digest 5 (MD5) Authentication** - Add an extra layer of security between two BGP peers by verifying each transmitted message sent through the BGP session. When MD5 authentication is activated, BGP authenticates every segment sent over the TCP session from its peer and verifies the source of each routing update.

      **Important**:  

      * You must configure the same BGP MD5 authentication key on both your Edge router and the IBM cross-connect router (XCR). The shared authentication key on the IBM device must be stored in your HPCS or Key Protect instance and shared with the Direct Link service. For more information, see [Setting up BGP Message Digest 5 (MD5) authentication keys](/docs/dl?topic=dl-dl-md5).
      * You can achieve hitless key refresh if the keys are updated on both your Edge router and on the IBM cross-connect router (XCR) within 90 seconds. As a pre-condition, you must configure the BGP hold time on your router to a minimum of 90 seconds. All Direct Link routers have a 90-second configuration by default. Either side can initiate the key refresh, but both sides must refresh within the configured BGP hold time to avoid traffic disruption.
      * If a BGP peering session was established and you enable BGP MD5 authentication (or change the authentication key to a different value), BGP sessions are re-established, which causes BGP session downtime and network disruption until the BGP peer device is configured with the same change.

      Complete the following information:
      * For the keystore, select either **Hyper Protect Crypto Services** or **Key Protect**.
      * Select an authentication keystore instance.
      * Select an authentication key.

   * **Bidirectional Forwarding Detection (BFD)** - Activate BFD to quickly detect faults in a network between two routers or switches that are connected by a link. BFD provides a single, standardized method for detecting link failures at any protocol layer, over any media. For more information, see [Setting up bidirectional forwarding detection](/docs/dl?topic=dl-dl-bfd).

      Activating and deactivating BFD after the BGP session is established causes BGP session downtime and network disruption until the BGP peer device is configured for the same change.
      {: important}

      Complete the following information:
      * Interval – The interval is the minimum time (in milliseconds) expected to occur between when the local routing device sends BFD hello packets and the reply from its neighbor. This value can range from 300 to 255,000 milliseconds.
      * Multiplier – The multiplier is the number of times that a hello packet is missed before BFD declares the neighbor down. This value can range from 1 to 255. The default multiplier value is 3.

1. In the Connections section, select the type of network connection that you want to bind to the {{site.data.keyword.dl_short}} gateway. You can select a connection type when you create a direct link, or after your direct link is provisioned.

   Select from the following connection types:

   * Select **Direct resources** (default) to create a direct, private connection between your on-premises network and IBM Cloud deployment. Optionally, choose a connection and enter a connection name. To add multiple network connections to the {{site.data.keyword.dl_short}} gateway, click **Add connection +**. You can create one of the following connections:   

      * **Classic infrastructure** networks allow you to connect to {{site.data.keyword.cloud_notm}} classic resources. Only one classic infrastructure connection is allowed per {{site.data.keyword.dl_short}} gateway.
      * **VPC** networks can contain either first or second generation compute resources, allowing you to connect to your account’s VPC resources.

      You cannot request a connection to a network in another account when you create a gateway. However, you can request a connection to a network in another account after a gateway is provisioned. You also can create classic infrastructure and VPC connections after a gateway is created. To learn more, see [Adding virtual connections to a {{site.data.keyword.dl_short}} gateway](/docs/dl?topic=dl-add-virtual-connection).
      {: tip}

   * Select **Transit Gateway** to bind your direct link to transit gateways. You can bind your direct link to one or more local gateways, or one global gateway.

      If you select **Transit Gateway** as the type of network connection, you must also initiate a Direct Link connection through the [{{site.data.keyword.cloud_notm}} Transit Gateway console](https://cloud.ibm.com/interconnectivity/transit){: external} from the same {{site.data.keyword.cloud_notm}} account. For instructions, see [Adding a connection](/docs/transit-gateway?topic=transit-gateway-adding-connections){: external}.
      {: important}  

      ![Connection types](/images/dl-connections.png){: caption="Connection types" caption-side="bottom"}         

1. An order summary shows pricing estimates for your review. Read and agree to the [**{{site.data.keyword.dl_short}} prerequisites**](/docs/dl?topic=dl-ibm-cloud-dl-prerequisites) and review Cloud Services [**Terms**](https://www.ibm.com/software/sla/sladb.nsf/sla/bm-8695-01). Then, click **Create** to complete your order.  

   If you want to add GB egress data to your estimate, click **Add to estimate** to calculate the cost. You can also click the **About** tab for links to {{site.data.keyword.dl_short}} pricing tables and other helpful resources.
   {: tip}

Complete your connection, using the following instructions.

## Completing the connection
{: #complete-connection}

After you submit your {{site.data.keyword.dl_short}} order, the {{site.data.keyword.dl_short}} table indicates an **LOA creation in progress** connection status. Click the name of the connection to open its details page. Then, view the Actions section to see if you have any actions pending.

Here's how the process works:

1. IBM Cloud uploads a Letter of Authorization (LOA) containing a Connecting Facility Assignment (CFA) within 24 hours. In turn, the connection status changes to **Waiting LOA review**. At this time, you can click the corresponding buttons to preview and accept the LOA.
1. After accepting the LOA and downloading it, the connection status changes to **Waiting completion notice upload**. You must now take the LOA document to your carrier and get the completion notice. To do so, you can:

   * Supply the LOA/CFA to your colocation provider and have them order a cross connect and any required inter-campus connectivity.
   * Supply the LOA/CFA to your service provider and have them order a third-party cross connect, as well as the circuit between your on-premises and the appropriate Meet Me Room.

   IBM Cloud will not order a cross-connect on a customer's behalf.
   {: note}

1. After receiving the completion notice from your carrier, upload it. The completion notice must be in PDF format with the name **completion_notice.pdf** for the automation to process it properly. The specific connection shows an option in the {{site.data.keyword.cloud_notm}} console to upload the completion notice. Notice that the connection status changes to **Completion notice review in progress**.

1. The IBM Cloud team reviews the completion notice and accepts it. The IBM Cloud team then places an order to have the fiber installed between the patch panel/port mentioned in the LOA and the device port. This process can take 1-4 business days, depending on how quickly the site provider finishes the request. This completes the physical-layer portion of the direct link and the connection status changes to **Provisioned.**

1. You must then configure the BGP parameters on your Edge router for BGP session establishment. After this completes, the **BGP status** indicates **Established** and **Link status** indicates **Up**.  

   It can take up to 30 minutes for the link status to update.  
   {: note}

## Locations
{: #dedicated-locations}

The table gives details about the {{site.data.keyword.cloud_notm}} data centers where {{site.data.keyword.dl_short}} Dedicated (2.0) is available:

|**IBM Location Code** | **Location Type** | **Meet Me Room Operator**| **Operator Site Code** | **Operator Address** |
|-----------------|-----------------|-----------------|--------------------|--------------------|
| **Americas** |  |  |  |  |
| Chicago 1 |  PoP | Equinix  | CH4 |  350 E. Cermak |
| Dallas 3 | PoP 1 | Equinix | DA1 | 1950 N. Stemmons Freeway |
| Dallas 4 | PoP 2 | Digital Realty | DFW14 | 2323 Bryan St |
| Dallas 10 | DC(AZ1) | QTS | IRV | 6431 Longhorn Drive |
| Dallas 12 | DC(AZ2) | Digital Realty | DFW18 | 907 Security Row |
| Dallas 13 | DC(AZ3) | CyrusOne | Carrollton - Frankford | 1649 W. Frankford Rd |
| Miami 1 | PoP  | TERREMARK | MI1 | 50 NE 9th Street |
| Montreal | DC | Colo-D | MON01 | 2525 Rue Canadien |
| San Jose 2 | PoP | Equinix | SV1 | 11 Great Oaks Blvd |
| Sao Paulo 1 | DC(AZ1) | Digital Realty (Ascenty) | SAO01 | Rua Presbitero Plinio Alves de Souza, 757 J. Ermida II,Jundiai |
| Sao Paulo 2 | PoP | Equinix | SP4 | Avenida Ceci, 1900, Tambore, Barueri, SP, 06460 120 BR, Brazil |
| Sao Paulo 3 | PoP  | ODATA | SAO03 | 39,2, Estr. dos Romeiros |
| Sao Paulo 4 | DC(AZ2) | ODATA | SAO04 | 943 - Votuparim, Estr. dos Romeiros |
| Sao Paulo 5 | DC(AZ3) | ASCENTY | SAO05 | Avenida 2, n.º 50, Quadra G1 1B Parte A Gleba 1B |
| Seattle 2 | PoP | Digital Realty (The Westin Building) | WBX | 2001 6th Avenue |
| Toronto 1 | DC(AZ1)| Digital Realty | TOR01 | 371 Gough Rd Suite # 130 Markham, Ontario |
| Toronto 2 | PoP | Cologix | TOR02 | 151 Front Street, Toronto |
| Toronto 3 | PoP | Equinix| TOR03 | 45 Parliament Street, Toronto |
| Toronto 4 | DC(AZ2) | Server Farm | TOR04 | 300 Bartor Road, North York |
| Toronto 5 | DC(AZ3) | Digital Realty | TOR05 | 1 Century Place, Vaughan |
| Washington DC 2 | PoP 1 | Equinix | DC2 | 21715 Filigree Ct |
| Washington DC 4 | DC(AZ1) | Digital Realty | IAD38 | 44060 Digital Loudoun Plaza (Bldg K) |
| Washington DC 5 | PoP 2 | Coresite | DC2 | 12098 Sunrise Valley Dr |
| Washington DC 6 | DC(AZ2) | Raging Wire | VA2 | 44610 Guilford Drive |
| Washington DC 7 | DC(AZ3) | Sabey | Sabey Intergate.Ashburn | 21741 Red Rum Dr |
| **APAC** |  |  |  |  |
| Hong Kong 3 |	PoP |	Equinix |	HKG2 |	17/F Kerry Warehouse |
| Osaka 1 | PoP | Equinix | OS1 | Nishi-Shinsaibashi Bldg., 1-26-1 Shin-machi, Osaka  |
| Osaka 21  | DC(AZ1)|  IDC Frontier (SoftBank) | OSA021 | 6-1 Saitoaokita Mino-shi |
| Osaka 22  | DC(AZ2) | IDC Frontier (SoftBank) | OSA022 | 6-1 Saitoaokita Mino-shi |
| Osaka 23  | DC(AZ3) | IDC Frontier (SoftBank) | OSA023 | 6-1 Saitoaokita Mino-shi |
| Sydney 1 | DC(AZ1) | Global Switch | SYD01 | 400 Harris Street aka 273 Pyrmont St Ultimo |
| Sydney 2 | PoP 1 | Equinix | SY3 | 47 Bourke Rd |
| Sydney 3 | PoP 2 | NextDC | SYD03 | 4 Eden Park Drive, Marquarie Park |
| Sydney 4 | DC(AZ2) | Digital Realty | SYD10 | 1-11 Templar Rd, Erskine Park |
| Sydney 5 | DC(AZ3) | Equinix | SY4 | 200 Bourke Road |
| Taipei 1 | PoP | Chief Telecom | TPE01 | Chief L.Y. Building 3rd floor, No. 250 Yuang Guang St Taipei, Taiwan, R.O.C. |
| Tokyo 1 | Pop | Equinix | TY2  | 7th Floor, 3-8-21 Higashi-Shinagawa |
| Tokyo 2 | DC(AZ1) | At Toyko | TOK02 | Shin-Toyosu Cube, 6-2-12 Toyosu, Koto-ku |
| Tokyo 3 | PoP 2 | Equinix | TY4 | Chiyoda-ku |
| Tokyo 4 | DC(AZ2) | Softbank | | Saitama |
| Tokyo 5 | DC(AZ3) | NTT |  | Kawasaki Kangagawa |
| **EMEA** |  |  |  |  |
| Amsterdam 2 | PoP | Equinix | AM2 | Luttenbergweg 4, 1101 EC |
| Frankfurt 1 | PoP 1 | Digital Realty (InterXion) | FRA6 | Hanauer Landstrasse 302 |
| Frankfurt 2 | DC(AZ1) | CyrusOne (Zenium) | FRA1 | Leonhard - Heisswolf Str 4., Frankfurt am Main |
| Frankfurt 3 | PoP 2 | Equinix | FR6 | Larchenstrasse 110, Frankfurt Griesheim |
| Frankfurt 4 | DC(AZ2) | E-Shelter | Frankfurt 1 | Eschborner Landstrasse 100, Building H |
| Frankfurt 5 | DC(AZ3) | Digital Realty (InterXion) | FRA11 | Weismüllerstraße 40 |
| London 1 | PoP | Equinix (Telecity) | LD8 | 6/7 Harbour Exchange E14 9GE |
| London 2 | DC | Digital Realty | LHR13 | Fountain Court, Cox Lane, Suites 210 and 230 |
| London 3 | PoP 2 | Equinix | LD5 | 8 Buckingham Ave |
| London 4 | DC(AZ1) | ARK | A103 | A57 Cody Technology Park Old, Victor Way, Farnborough |
| London 5 | DC(AZ2) | Gyron |  | Maxted Cl, Hemel Hempstead  |
| London 6 | DC(AZ3) | CyrusOne (Zenium) | LON1 | 12 Liverpool Rd, Trading Estate |
| Milan 1 | DC | Data 4 | | Via Monzoro 101-105, 20010 Cornaredo (MI) |
| Milan 2 | PoP | Infracom Italia | Infracom 21 Via Caldera Way | Infracom Italia Spa, Building D, Caldera Business Park, Via Caldera, 21 |
| Paris 3 | PoP | Equinix | PA4 | 110 Bis avenue du Gènèral Leclerc, 93500 Pantin |
{: caption="Table 1. Direct Link Dedicated by Location" caption-side="left"}
