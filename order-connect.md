---

copyright:
  years: 2020
lastupdated: "2020-08-05"

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

# Ordering {{site.data.keyword.dl_full_notm}} Connect (Beta)
{: #how-to-order-ibm-cloud-dl-connect}
{: help}
{: support}

The beta release of {{site.data.keyword.dl_full}} Connect is only available to allowlisted users. Contact your IBM Cloud Sales representative if you are interested in getting early access to this beta offering. After the {{site.data.keyword.dl_short}} Connect service is made generally available, you must upgrade to the standard paid plan to continue using instances that you created during the beta. Upgrade instructions will be provided to beta participants. Any instance that continues to use the beta plan for this service beyond 30 days after general availability is subject to deletion.
{: beta}

IBM Cloud highly recommends that a second, diverse direct link be established to prevent outages, whether unplanned, or planned due to maintenance. For more information, see [Models for diversity and redundancy](/docs/dl?topic=dl-models-for-diversity-and-redundancy-in-direct-link).
{: important}

Learn more

## Ordering instructions
{: #instructions-connect}

To order {{site.data.keyword.dl_short}} Connect, you must determine the location that connects to IBM Cloud, complete the required configuration information, then click **Create** to submit your order for processing.
{:shortdesc}

To order {{site.data.keyword.dl_full}} Connect, follow these steps.
{:shortdesc}

1. Log in to your [{{site.data.keyword.cloud_notm}}](https://{DomainName}/){:external} account.
1. Click Menu ![Menu icon](images/menu_icon.png) on the upper left, then click **Interconnectivity**.
1. Click **Order {{site.data.keyword.dl_short}}**.
1. Select the **{{site.data.keyword.dl_short}} Connect** option.
1. Optionally, click **Open checklist** to review the ordering process (also described in [Completing the connection](/docs/dl?topic=dl-how-to-order-ibm-cloud-dl-connect#complete-connection-connect)).
1. In the Configuration section, complete the following information:
   * Type a name for your {{site.data.keyword.dl_short}} connection.
   * Choose a resource group to create the {{site.data.keyword.dl_short}} connection. Resource groups help manage and contain resources associated with an account. Select **Default** if you don't have any other groups defined in the drop-down list. For more information about resource groups, see [Best practices for organizing resources in a resource group](/docs/resources?topic=resources-bp_resourcegroups).
   * For Billing, select **Metered** or **Unmetered**. Metered pricing is paying only for what you use. Unmetered is unlimited access, for a predicable, monthly fee. See [Pricing for {{site.data.keyword.dl_full_notm}}](/docs/dl?topic=dl-pricing-for-ibm-cloud-dl) for details.

      ![Configuration section](/images/dl-config-connect.png)   

1. In the Location section, select a geography, followed by a market, type, site, and routing option.

   Local and global routing options are supported for {{site.data.keyword.dl_short}} Connect. When you select a routing option, the location details with reachable sites are shown.  
   {:note}            

   ![Location section](/images/dl-location-connect.png)   

   * Choose a provider and then select a connection speed. The speeds supported for the {{site.data.keyword.dl_short}} Connect offering are 50 Mbps, 100 Mbps, 200 Mbps, 500 Mbps, and 1 Gbps, 2 Gbps, and 5 Gbps.

1. In the BGP and connections section, complete the following information:

      * Select the port for the {{site.data.keyword.dl_short}} gateway.
      * Select a BGP peering subnet for the {{site.data.keyword.dl_short}} connection. There are two choices for BGP subnets:
         * Select **Auto-select IP** for IBM to assign an IP address from IP range, `169.254.0.0/16`.
         * Select **Manual-select IP** to specify two of your own IP addresses (in CIDR format) from the ranges `10.254.0.0/16`, `172.16.0.0/12`, `192.168.0.0/16`, `169.254.0.0/16`, or `Public` (a public IP address that you own). Manual-select is useful when trying to avoid conflicts with an existing subnet in use.

         Make sure that any self-provided BGP addresses do not conflict with blocks that are used by IBM, or by resources external to your {{site.data.keyword.dl_short}} deployment.
         {: important}

      * For BGP ASN, use either the default value of `64999` or select an ASN from the specified allowed ranges.

         **For Layer-3 IP VPN providers only**: You must specify the carrier's ASN, not your own. For a list of carrier interconnection types, see [Comparing Layer-2 and Layer-3 connections for {{site.data.keyword.dl_short}}](/docs/dl?topic=dl-comparing-layer-2-layer-3)
         {: important}

         Allowed ASN ranges are:
         * For a 2-byte range, enter a value between `1-64495` or the default `64999`.
         * For a 2-byte or 4-byte range, enter a value between `131072-4199999999`.
         * For a 4-byte range, enter a value between `4201000000-4201064511`.

         ![BGP section](/images/dl-bgp-connect.png)            

      * Optionally, select the network connection to attach to the {{site.data.keyword.dl_short}} gateway then enter a connection name. To add multiple network connections to the {{site.data.keyword.dl_short}} gateway, click **Add connection +**. You can create one of the following connections:

         * **Classic infrastructure** networks allow you to connect to {{site.data.keyword.cloud_notm}} classic resources. Only one classic infrastructure connection is allowed per {{site.data.keyword.dl_short}} gateway.
         * **VPC** networks can contain either first or second generation compute resources, allowing you to connect to your account’s VPC resources.

         ![Add connection section](/images/dl-conn-connect.png)   

      You cannot request a connection to a network in another account when you create a gateway. However, you can request connection to a network in another account after a gateway is provisioned. You also can create classic infrastructure and VPC connections after a gateway is created. To learn more, see [Adding virtual connections to a {{site.data.keyword.dl_short}} gateway](/docs/dl?topic=dl-add-virtual-connection).
{:tip}

      The routing option that you select determines the reachability of the resources in the selected location. If you select the **Global** routing option along with your location selections, the **Region** menu list shows all the regions that are globally available in the specific account. After selecting a region, you can select any VPC from the **Available connections** menu. If you select **Local** routing, then only the region that corresponds to the selected location is available. When selected, VPCs available in the local region for your account are shown.
{:note}

1. An order summary shows pricing estimates for your review. Read and agree to the [**{{site.data.keyword.dl_short}} prerequisites**](/docs/dl?topic=dl-ibm-cloud-dl-prerequisites) and review Cloud Services [**Terms**](https://www.ibm.com/software/sla/sladb.nsf/sla/bm-8695-01). Then, click **Create** to complete your order.  

   If you want to add GB egress data to your estimate, click **Add to estimate** to calculate the cost. You can also click the **About** tab for links to {{site.data.keyword.dl_short}} pricing tables and other helpful resources.
{:tip}

Complete your connection using the following instructions.

## Completing the connection
{: #complete-connection-connect}

After you create your {{site.data.keyword.dl_short}} order, the {{site.data.keyword.dl_short}} dashboard indicates a **Provisioned** connection status. You must then configure the BGP parameters on the Customer Edge Router (CER) for BGP session establishment. After this completes, the BGP status indicates `Established`.

**Next steps**

* Contact your network provider and negotiate connectivity to your on-premises or colocation.
* Take note of the service key of the gateway, then create a request on the provider portal to order a virtual circuit. Reference the case ID of the {{site.data.keyword.dl_short}} Connect request as your Request ID or Authorization ID.

   To locate the service key, navigate to the [{{site.data.keyword.dl_short}} dashboard](https://cloud.ibm.com/interconnectivity/direct-link), then click the Direct Link name in the table to show its details.
   {: note}

## Providers and locations
{: #connect-classic-locations}

The following table lists {{site.data.keyword.dl_short}} Connect providers and locations.
{:shortdesc}

| Provider | Locations |
|----|----|
| At Tokyo | **APAC:** Osaka 1 |
| CenturyLink Dynamic Connections |  **Americas:** Washington DC 2 |  
| Colt | **Americas:** San Jose 2<br />Washington DC 2 |
| Epsilon | **APAC:** Hong Kong 2 |
| Equinix | **APAC:** Tokyo 3<br />**EU:** Frankfurt 3, London 3 <br />**Americas:** Chicago 1, Dallas 3, San Jose 2, Washington DC 2|
| IBM BlueFringe | **EU:** Frankfurt 3 |
| IBM Power Virtual Server | **Americas:** Washington DC 4<br />**EU:** Frankfurt 4, Frankfurt 5, London 6 |
| Megaport | **Americas:**  Dallas 4<br />**APAC:** Osaka 1<br />**EU:** Amsterdam 2<br />London 3 (no diversity) |
{: class="simple-tab-table"}
{: caption="Table 1. Direct Link Connect by Provider" caption-side="left"}
{: #simpletabtable1}
{: tab-title="By Provider"}
{: tab-group="connect-simple"}

| Location | Providers |
|----|----|
| Amsterdam 2 | Megaport |
| Chicago 1 | Equinix |
| Dallas 3 | Equinix |
| Dallas 4 | Megaport |
| Frankfort 3 | Equinix<br />IBM BlueFringe |
| Frankfort 4 | IBM Power Virtual Server |
| Frankfort 5 | IBM Power Virtual Server |
| Hong Kong 2 | Epsilon |
| London 3 | Equinix<br />Megaport (no diversity)|
| London 3 (no diversity) | Megaport |
| London 6 | IBM Power Virtual Server |
| Osaka  1 | At Tokyo<br />Megaport |
| San Jose 2 | Colt<br />Equinix |
| Tokyo 3 | Equinix |
| Washington DC 2 | CenturyLink Dynamic Connections<br />Colt<br />Equinix |
| Washington DC 4 | IBM Power Virtual Server |
{: caption="Table 2. Direct Link Connect by Location" caption-side="left"}
{: #simpletabtable2}
{: tab-title="By Location"}
{: tab-group="connect-simple"}
{: class="simple-tab-table"}
