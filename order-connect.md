---

copyright:
  years: 2020
lastupdated: "2020-05-26"

keywords: order, provider, capabilities, Connect, cross-connect, locations, PoP, data center, pricing

subcollection: dl

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:preview: .preview}
{:note: .note}
{:beta: .beta}
{:important: .important}
{:deprecated: .deprecated}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:term: .term}  
{:generic: data-hd-programlang="generic"}
{:download: .download}  
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Ordering IBM Cloud Direct Link Connect (Beta)
{: #how-to-order-ibm-cloud-dl-connect}
{: help}
{: support}

Direct Link Connect is a Beta release and only available to whitelisted users.

The beta release of {{site.data.keyword.dl_full}} Connect is only available to whitelisted users. Contact your IBM Cloud Sales representative if you are interested in getting early access to this beta offering. After the Direct Link Connect service is made generally available, you must upgrade to the standard paid plan to continue using instances that you created during the beta. Upgrade instructions will be provided to beta participants. Any instances that continue to use the beta plan for this service beyond 30 days after general availability are subject to deletion.
{: beta}

## Ordering instructions
{: #instructions-connect}

To order Direct Link Connect, you must determine the location that connects to IBM Cloud, complete the required configuration information, then click **Create** to submit your order for processing.
{:shortdesc}

To order {{site.data.keyword.dl_full}} Connect, follow these steps.
{:shortdesc}

1. Log in to your [{{site.data.keyword.cloud_notm}}](https://{DomainName}/){:external} account.
1. Click Menu ![Menu icon](images/menu_icon.png) on the upper left, then click **Interconnectivity**.
1. Click **Order Direct Link**.
1. Select the **Direct Link Connect** option.
1. Optionally, click **Open checklist** to review the ordering process (also described in [Completing the connection](/docs/dl?topic=dl-how-to-order-ibm-cloud-dl-connect#complete-connection-connect)).
1. In the Configuration section, complete the following information:
   * Type a name for your Direct Link connection.
   * Choose a resource group to create the Direct Link connection. Resource groups help manage and contain resources associated with an account. Select **Default** if you don't have any other groups defined in the drop-down list. For more information about resource groups, see [Best practices for organizing resources in a resource group](/docs/resources?topic=resources-bp_resourcegroups).
   * For Billing, select **Metered** or **Unmetered**. Metered pricing is paying only for what you use. Unmetered is unlimited access, for a predicable, monthly fee. See [Pricing for {{site.data.keyword.dl_full_notm}}](/docs/dl?topic=dl-pricing-for-ibm-cloud-dl) for details.

      ![Configuration section](/images/dl-config-connect.png)   

1. In the Location section, select a geography, followed by a market, type, site, and routing option.

      Local and global routing options are supported for Direct Link Connect. When you select a routing option, the location details with reachable sites are shown.  
      {:note}            

      ![Location section](/images/dl-location-connect.png)   

   * Choose a provider and then select a connection speed. The speeds supported for the Direct Link Connect offering are 50 Mbps, 100 Mbps, 200 Mbps, 500 Mbps, and 1 Gbps, 2 Gbps, and 5 Gbps.

1. In the BGP and connections section, complete the following information:

      * Select the port for the Direct Link gateway.
      * Select a BGP peering subnet for the Direct Link connection. There are two choices for BGP subnets:
         * Select **Auto-select IP** for IBM to assign an IP address from IP range, `169.254.0.0/16`.
         * Select **Manual-select IP** to specify two of your own IP addresses (in CIDR format) from the ranges `10.254.0.0/16`, `172.16.0.0/12`, `192.168.0.0/16`, `169.254.0.0/16`, or `Public` (a public IP address that you own). Manual-select is useful when trying to avoid conflicts with an existing subnet in use.

         Make sure that any self-provided BGP addresses do not conflict with blocks that are used by IBM, or by resources external to your Direct Link deployment.
         {: important}

      * For BGP ASN, use either the default value of `64999` or select an ASN from the specified allowed ranges.

      Allowed ASN ranges are:
         * For a 2-byte range, enter a value between `1-64495` or the default `64999`.
         * For a 2-byte or 4-byte range, enter a value between `131072-4199999999`.
         * For a 4-byte range, enter a value between `4201000000-4201064511`.

      ![BGP section](/images/dl-bgp-connect.png)            

      * Optionally, select the network connection to attach to the Direct Link gateway then enter a connection name. To add multiple network connections to the Direct Link gateway, click **Add connection +**. You can create one of the following connections:

         * **Classic infrastructure** networks allow you to connect to {{site.data.keyword.cloud_notm}} classic resources. Only one classic infrastructure connection is allowed per Direct Link gateway.
         * **VPC** networks can contain either first or second generation compute resources, allowing you to connect to your account’s VPC resources.

         ![Add connection section](/images/dl-conn-connect.png)   

      You cannot request a connection to a network in another account when you create a gateway. However, you can request connection to a network in another account after a gateway is provisioned. You also can create classic infrastructure and VPC connections after a gateway is created. To learn more, see [Adding virtual connections to a Direct Link gateway](/docs/dl?topic=dl-add-virtual-connection).
{:tip}

      The routing option that you select determines the reachability of the resources in the selected location. If you select the **Global** routing option along with your location selections, the **Region** menu list shows all the regions that are globally available in the specific account. After selecting a region, you can select any VPC from the **Available connections** menu. If you select **Local** routing, then only the region that corresponds to the selected location is available. When selected, VPCs available in the local region for your account are shown.
{:note}

1. An order summary shows pricing estimates for your review. Read and agree to the [**Direct Link prerequisites**](/docs/dl?topic=dl-ibm-cloud-dl-prerequisites) and review Cloud Services [**Terms**](https://www.ibm.com/software/sla/sladb.nsf/sla/bm-8695-01). Then, click **Create** to complete your order.  

   If you want to add GB egress data to your estimate, click **Add to estimate** to calculate the cost. You can also click the **About** tab for links to Direct Link pricing tables and other helpful resources.
{:tip}

Complete your connection using the following instructions.

## Completing the connection
{: #complete-connection-connect}

After you create your Direct Link order, the Direct Link table indicates a **Provisioned** connection status. You must then configure the BGP parameters on the Customer Edge Router (CER) for BGP session establishment. After this completes, the BGP status indicates `Established`.

**Next steps**

* Contact your Connect provider and negotiate connectivity to your on-premises or colocation.
* Order a virtual circuit through your Connect provider and reference the case ID of the Direct Link Connect request as your Request ID or Authorization ID.

## Locations
{: #connect-locations}


The table gives details about the {{site.data.keyword.cloud_notm}} data centers where Direct Link Connect is available:

|**IBM Location Code** | **Location Type** | **Meet Me Room Operator**| **Operator Site Code** | **Operator Address** |
|-----------------|-----------------|-----------------|--------------------|--------------------|
| **Americas** |  |  |  |  |
| Chicago 1 |  PoP | Equinix  | CH4 |  350 E. Cermak |
| Dallas 3 | PoP 1 | Equinix | DA1 | 1950 N. Stemmons Freeway |
| Dallas 4 | PoP 2 | Digital Realty | DFW14 | 2323 Bryan St |
| Dallas 10 | DC(AZ1) | QTS | IRV | 6431 Longhorn Drive |
| Dallas 12 | DC(AZ2) | Digital Realty | DFW18 | 907 Security Row |
| Dallas 13 | DC(AZ3) | Cyrus One | Carrollton - Frankford | 1649 W. Frankford Rd |
| San Jose 2 | PoP | Equinix | SV111 | Great Oaks Blvd |
| Washington DC 2 | PoP 1 | Equinix | DC2 | 21715 Filigree Ct |
| Washington DC 4 | DC(AZ1) | Digital Realty | IAD38 | 44060 Digital Loudoun Plaza (Bldg K) |
| Washington DC 5 | PoP 2 | Coresite | DC2 | 12098 Sunrise Valley Dr |
| Washington DC 6 | DC(AZ2) | Raging Wire | VA2 | 44610 Guilford Drive |
| Washington DC 7 | DC(AZ3) | Sabey | Sabey Intergate.Ashburn | 21741 Red Rum Dr |
| **APAC** |  |  |  |  |
| Sydney 1 | DC(AZ1) | Global Switch | SYD01 | 400 Harris Street aka 273 Pyrmont St Ultimo |
| Sydney 2 | PoP 1 | Equinix | SY3 | 47 Bourke Rd |
| Sydney 3 | PoP 2 | NextDC | SYD03 | 4 Eden Park Drive, Marquarie Park |
| Sydney 4 | DC(AZ2) | Digital Realty | SYD10 | 1-11 Templar Rd, Erskine Park |
| Sydney 5 | DC(AZ3) | Equinix | SY4 | 200 Bourke Road |
| Tokyo 1 | Pop | Equinix | TY2  |  |
| Tokyo 3 | PoP 2 | Equinix | TY4 | Chiyoda-ku |
| Tokyo 4 | DC(AZ2) | Softbank | | Saitama |
| Tokyo 5 | DC(AZ3) | NTT |  | Kawasaki Kangagawa |
| **EMEA** |  |  |  |  |
| Frankfurt 1 | PoP 1 | Digital Realty (fInterXion) | FRA01 | Hanauer Landstrasse 302 |
| Frankfurt 2 | DC(AZ1) | Cyrus One (fZenium) | FRA1 | Leonhard - Heisswolf Str 4., Frankfurt am Main |
| Frankfurt 3 | PoP 2 | Equinix| FRA6 | Larchenstrasse 110, Frankfurt Griesheim |
| Frankfurt 4 | DC(AZ2) | E-Shelter | Frankfurt 1 | Eschborner Landstrasse 100, Building H |
| Frankfurt 5 | DC(AZ3) | Digital Realty (fInterXion) | FRA05 | Weismüllerstraße 40 |
| London 2 | DC | Digital Realty | LHR13 | Fountain Court, Cox Lane, Suites 210 and 230 |
| London 3 | PoP 2 | Equinix | LD5 | 8 Buckingham Ave |
| London 4 | DC(AZ1) | ARK | A103 | A57 Cody Technology Park Old, Victor Way, Farnborough |
| London 5 | DC(AZ2) | Gyron |  | Maxted Cl, Hemel Hempstead  |
| London 6 | DC(AZ3) | Cyrus One (fZenium) | LON1 | 12 Liverpool Rd, Trading Estate |
| Paris 2 | PoP | Equinix | PA2 | 114 Rue Ambroise Croizat, St Denis |
