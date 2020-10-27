---

copyright:
  years: 2020
lastupdated: "2020-10-27"

keywords:

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

# Ordering {{site.data.keyword.dl_full_notm}} Connect
{: #how-to-order-ibm-cloud-dl-connect}
{: help}
{: support}

23 September 2020: Direct Link Connect is a limited availability offering. If you participated in the beta release, you must migrate to a standard paid plan to continue using instances that you created during the beta. Any instances that continue to use the beta plan for this service beyond the 30 days notice of general availability are subject to deletion. For more information, see [Migrating Direct Link Connect gateways](/docs/dl?topic=dl-migration).
{: preview}

## Planning considerations
{: #before-you-begin-connect}

* IBM Cloud highly recommends that a second, diverse direct link be established to prevent outages, whether unplanned, or planned due to maintenance. For more information, see [Models for diversity and redundancy](/docs/dl?topic=dl-models-for-diversity-and-redundancy-in-direct-link).

* All subnets of the VPC or classic network will be connected to the direct link. When creating VPCs, make sure to create the VPCs with non-overlapping prefixes and unique subnets. To ensure successful connectivity with the classic infrastructure, do not use IP addresses for your VPCs in the `10.0.0.0/14`, `10.200.0.0/14`, `10.198.0.0/15`, and `10.254.0.0/16` blocks.

## Partner-specific instructions
{: #instructions-partner}

[AT&T NetBond](/docs/dl?topic=dl-netbond)

## Ordering instructions
{: #instructions-connect}

To order {{site.data.keyword.dl_short}} Connect, you must determine the location that connects to IBM Cloud, complete the required configuration information, then click **Create** to submit your order for processing.
{:shortdesc}

To order {{site.data.keyword.dl_full}} Connect, follow these steps:

1. Log in to your [{{site.data.keyword.cloud_notm}}](https://{DomainName}/){:external} account.
1. Click Menu ![Menu icon](images/menu_icon.png) on the upper left of the page, then click **Interconnectivity**.
1. Scroll to locate the Connect tile, then click **Order {{site.data.keyword.dl_short}}**.

   ![Ordering options](/images/dl_options.png)   

   Alternatively, you can click **Direct Link** in the left navigation pane to view the Direct Link page, which lists existing Direct Link instances. From this page, you can click **Order Direct Link** > **Direct Link Connect**.
   {: tip}
1. Optionally, click **Open checklist** to review the ordering process (also described in [Completing the connection](/docs/dl?topic=dl-how-to-order-ibm-cloud-dl-connect#complete-connection-connect)).
1. In the Configuration section, complete the following information:
   * Type a name for your {{site.data.keyword.dl_short}} connection.
   * Choose a resource group to create the {{site.data.keyword.dl_short}} connection. Resource groups help manage and contain resources associated with an account. Select **Default** if you don't have any other groups defined in the drop-down list. For more information about resource groups, see [Best practices for organizing resources in a resource group](/docs/account?topic=account-account_setup).
   * For Billing, select **Metered** or **Unmetered**. Metered pricing is paying only for what you use. Unmetered is unlimited access, for a predicable, monthly fee. See [Pricing for {{site.data.keyword.dl_full_notm}}](/docs/dl?topic=dl-pricing-for-ibm-cloud-dl) for details.

      ![Configuration section](/images/dl-config-connect.png)   

1. In the Location section, select a geography, followed by a market, type, site, and routing option. Then, select a provider and a connection speed.

   {{site.data.keyword.dl_short}} Connect supports the following speeds: 50 Mbps, 100 Mbps, 200 Mbps, 500 Mbps, 1 Gbps, 2 Gbps, and 5 Gbps.
   {:note}  

   ![Location section](/images/dl-location-connect.png)  

   Local and global routing options are supported for {{site.data.keyword.dl_short}} Connect. The routing option that you select determines the reachability of the resources in the selected location. If you select the **Global** routing option along with your location selections, the **Region** menu list shows all the regions that are globally available in the specific account. After selecting a region, you can select any VPC from the **Available connections** menu. If you select **Local** routing, then only the region that corresponds to the selected location is available. When selected, VPCs available in the local region for your account are shown.
   {:note}          

1. In the BGP and connections section, complete the following information:

   * Select the port for the {{site.data.keyword.dl_short}} gateway.

   * Select a BGP peering subnet for the {{site.data.keyword.dl_short}} connection. There are two choices for BGP subnets:
      * Select **Auto-select IP** for IBM to assign an IP address from IP range, `169.254.0.0/16`.
      * Select **Manual-select IP** to specify two of your own IP addresses (in CIDR format) from the ranges `10.254.0.0/16`, `172.16.0.0/12`, `192.168.0.0/16`, `169.254.0.0/16`, or `Public` (a public IP address that you own). Manual-select is useful when trying to avoid conflicts with an existing subnet in use.

   * Enter your BGP ASN.

      * Make sure that any self-provided BGP addresses do not conflict with blocks that are used by IBM, or by resources external to your {{site.data.keyword.dl_short}} deployment.
      * **For Layer-3 IP VPN providers only**: You must specify the carrier's ASN, not your own. For a list of carrier interconnection types, see [Comparing Layer-2 and Layer-3 connections for {{site.data.keyword.dl_short}}](/docs/dl?topic=dl-comparing-layer-2-layer-3).
      * Excluded ASNs: 64512, 64513, 65100, 65201-65234, 65402-65433, 65500, and 4201065000-4201065999

      ![BGP and connections section](/images/dl-bgp-connect.png)            

   * Optionally, select the network connection to attach to the {{site.data.keyword.dl_short}} gateway then enter a connection name. To add multiple network connections to the {{site.data.keyword.dl_short}} gateway, click **Add connection +**. You can create one of the following connections:

      * **Classic infrastructure** networks allow you to connect to {{site.data.keyword.cloud_notm}} classic resources. Only one classic infrastructure connection is allowed per {{site.data.keyword.dl_short}} gateway.
      * **VPC** networks can contain either first or second generation compute resources, allowing you to connect to your account’s VPC resources.

      ![Add connection section](/images/dl-conn-connect.png)   

      You cannot request a connection to a network in another account when you create a gateway. However, you can request a connection to a network in another account after a gateway is provisioned. You also can create classic infrastructure and VPC connections after a gateway is created. To learn more, see [Adding virtual connections to a {{site.data.keyword.dl_short}} gateway](/docs/dl?topic=dl-add-virtual-connection).
      {:tip}

1. An order summary shows pricing estimates for your review. Read and agree to the [**{{site.data.keyword.dl_short}} prerequisites**](/docs/dl?topic=dl-ibm-cloud-dl-prerequisites) and review Cloud Services [**Terms**](https://www.ibm.com/software/sla/sladb.nsf/sla/bm-8695-01). Then, click **Create** to complete your order.  

   If you want to add GB egress data to your estimate, click **Add to estimate** to calculate the cost. You can also click the **About** tab for links to {{site.data.keyword.dl_short}} pricing tables and other helpful resources.
   {:tip}

After you create your {{site.data.keyword.dl_short}} order, the {{site.data.keyword.dl_short}} dashboard indicates a **Provisioned** connection status.

## Completing the connection
{: #complete-connection-connect}

To complete your connection, follow these steps:

1. Contact your network provider and negotiate connectivity to your on-premises or colocation.
1. Create a request on the provider portal to order a virtual circuit. Reference the case ID of the {{site.data.keyword.dl_short}} Connect request as your Request ID or Authorization ID.      
1. Configure the BGP parameters on the Customer Edge Router (CER) for BGP session establishment. After this completes, the BGP status indicates `Established`.

## Providers and locations
{: #connect-locations}

The following table lists {{site.data.keyword.dl_short}} Connect providers and locations.
{:shortdesc}

| Provider | Locations |
|----|----|
| At Tokyo | **APAC:** Osaka 1 |
| AT&T NetBond for Cloud | **Americas:** Washington DC 2 |
| British Telecom | **Americas:** Washington DC 2<br />**EU:** London 3 |  
| CenturyLink Dynamic Connections | **Americas:** Washington DC 2 |  
| Colt | **Americas:** San Jose 2, Washington DC 2 |
| Epsilon | **APAC:** Hong Kong 2<br />**EU:** London 1 |
| Equinix | **Americas:** Chicago 1, Dallas 3, San Jose 2, Washington DC 2<br />**APAC:** Osaka 1, Tokyo 3<br />**EU:** Frankfurt 3, London 3 |
| IBM BlueFringe | **Americas:** Dallas 3, Washington DC 2<br />**EU:** Frankfurt 3 |
| IBM Global Network Peering Platform (GNPP) | **EU:** London 1, London 3, London 4 |
| IBM Power Virtual Server | **Americas:** Dallas 13, Washington DC 4<br />**APAC:** Sydney 4, Sydney 5, Tokyo 4<br />**EU:** Frankfurt 4, Frankfurt 5, London 4, London 6 |
| NTT | **APAC:** Tokyo 5 |
| SoftBank | **APAC:** Tokyo 4 |
| PCCW | **Americas:** Miami 1<br />**APAC:** Osaka 1, Sydney 3, Sydney 5<br />**EU:** Frankfurt 5 |
| Telia | **Americas:** Dallas 3 |
| Tokai | **APAC:** Tokyo 3 |
{: class="simple-tab-table"}
{: caption="Table 1. Direct Link Connect by Provider" caption-side="left"}
{: #simpletabtable1}
{: tab-title="By Provider"}
{: tab-group="connect-simple"}

| Location | Providers |
|----|----|
| Chicago 1 | Equinix |
| Dallas 3 | Equinix<br />IBM BlueFringe<br />Telia |
| Dallas 13 | IBM Power Virtual Server |
| Frankfurt 3 | Equinix<br />IBM BlueFringe |
| Frankfurt 4 | IBM Power Virtual Server |
| Frankfurt 5 | IBM Power Virtual Server<br />PCCW |
| Hong Kong 2 | Epsilon |
| London 1 | Epsilon<br />IBM Global Network Peering Platform (GNPP) |
| London 3 | British Telecom<br />Equinix<br />IBM Global Network Peering Platform (GNPP)|
| London 4 | IBM Global Network Peering Platform (GNPP)<br />IBM Power Virtual Server |
| London 6 | IBM Power Virtual Server |
| Miami 1 | PCCW |
| Osaka  1 | At Tokyo<br />Equinix<br />PCCW |
| San Jose 2 | Colt<br />Equinix |
| Sydney 3 | PCCW |
| Sydney 4 | IBM Power Virtual Server |
| Sydney 5 | IBM Power Virtual Server<br />PCCW |
| Tokyo 3 | Equinix<br />Tokai |
| Tokyo 4 | IBM Power Virtual Server<br />Softbank |
| Tokyo 5 | NTT |
| Washington DC 2 | AT&T NetBond for Cloud<br />British Telecom<br />CenturyLink Dynamic Connections<br />Colt<br />Equinix<br />IBM BlueFringe |
| Washington DC 4 | IBM Power Virtual Server |
{: caption="Table 2. Direct Link Connect by Location" caption-side="left"}
{: #simpletabtable2}
{: tab-title="By Location"}
{: tab-group="connect-simple"}
{: class="simple-tab-table"}
