---

copyright:
  years: 2019, 2020
lastupdated: "2020-04-01"

keywords: order, provider, capabilities, Dedicated, cross-connect, locations, PoP, data center, data, center, pricing, Letter of Authorization, LOA,

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
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:term: .term}  
{:generic: data-hd-programlang="generic"}
{:download: .download}  
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Ordering {{site.data.keyword.cloud_notm}} Direct Link Dedicated
{: #how-to-order-ibm-cloud-dl-dedicated}
{: help}
{: support}

To order {{site.data.keyword.cloud}} Direct Link Dedicated, follow these steps.
{:shortdesc}

1. Log in to your [{{site.data.keyword.cloud_notm}}](https://{DomainName}/){:external} account.
1. Select the **Navigation Menu** ![Navigation Menu icon](images/menu_icon.png) on the upper left, then click **Hybrid Networking**.
1. Click **Order Direct Link +** in the upper right of the page.
1. In the Direct Link Dedicated order form, complete the following configuration information:
   * Enter a name for your Direct Link Dedicated connection.
   * Select a resource group to create the Direct Link connection and a connection speed. The speeds supported for the Direct Link Dedicated offering are 1, 2, 5, and 10 Gbps.
   * Optionally, enter a customer name, carrier name, or both.
   * Select either **Metered** or **Unmetered** for the billing option for the Dedicated connection.
   * For Location, select the **N/S America** geography and then select either the **Washington, D.C.** or **Dallas** market. Continue selecting options for type, site, and routing.

      Local and global routing options are supported for Direct Link Dedicated. When you select a routing option, the location details with reachable sites are displayed.
      {:note}

   * For BGP and Connections:
      * Select the IBM cross connect router for the Direct Link connection. The number of direct links associated with the account for each router is shown next to the router name.
      * Select a BGP peering subnet for the Direct Link connection. There are two choices for BGP subnets. If you select **Auto-select IP**, the IPs are assigned from the link local IP range, 169.254.0.0/16. If you select **Manual select IP**, you can specify IPs (in CIDR format) from the ranges `169.254.0.0/16`, `192.168.0.0/16`, `10.254.0.0/16` or `172.16.0.0/12`.
      * For BGP ASN, use either the default value of `64999`, or select an ASN from the specified allowed ranges.
      Allowed ASN ranges are:
        * For a 2-byte range, enter a value between `1-64495` or default `64999`.
        * For a 2-byte or 4-byte range, enter a value between `131072-4199999999`.
        * For a 4-byte range, enter a value between `4201000000-4201064511`.
   * Optionally, select the network connection to be attached to the Direct Link gateway, and then enter a connection name. To add multiple network connections to the Direct Link gateway, click **Add connection+**. You can create one of the following connections:

      * **Classic Infrastructure** networks allow you to connect to {{site.data.keyword.cloud_notm}} classic resources. Only one classic infrastructure connection is allowed per Direct Link gateway.
      * **VPC** networks can contain either first or second generation compute resources, allowing you to connect to your account’s VPC resources.

   You cannot request a connection to a network in another account when you create a gateway. However, you can request connection to a network in another account after a gateway is provisioned. You also can create classic infrastructure and VPC connections after a gateway is created. For more information, see [Adding virtual connections to a Direct Link gateway](/docs/dl?topic=dl-add-virtual-connection).
   {:important}

   The routing option that you selected determines the reachability of the resources in the selected location. If you selected the **Global** routing option along with your location selections, the **Regions** menu list displays all the regions that are globally available in the specific account. After selecting a region, you can select any VPC from the **Available connections** menu. If you selected **Local** routing, then only the region that corresponds to the selected location is available to select. When selected, VPCs available in the local region for your account are displayed.
   {:note}

   An order summary shows pricing estimates.

1. Agree to the [**Direct Link prerequisites**](/docs/dl?topic=dl-ibm-cloud-dl-dedicated-questionnaire) and review Cloud Services [**terms**](https://www.ibm.com/software/sla/sladb.nsf/sla/bm-8695-01). Then, click **Create** to complete your order. You can request assistance from {{site.data.keyword.cloud_notm}} Sales engineers at any time.
1. Complete the connection.

## Completing the connection
{: #complete-connection}

After you create your Direct Link order, the Direct Link table indicates an **LOA creation in progress** connection status. Click the name of the connection to open its details page. Then, view the Actions section to see if you have any actions pending.

Here's how the process works.

1. After the Letter of Authorization (LOA) is uploaded by the IBM team, the connection status changes to **Waiting LOA Review**. At this time, you can click the corresponding buttons to preview and accept the LOA. After accepting the LOA, you can download the LOA document.
2. After accepting the LOA and downloading it, the connection status changes to **Waiting completion notice upload**. At this time, you must take the LOA document to your carrier and get the completion notice.
3. After receiving the completion notice, upload it (the completion notice must be in PDF format with the name **completion_notice.pdf** in order for the automation to process it properly). The specific connection shows an option in the {{site.data.keyword.cloud_notm}} console to upload the completion notice. Notice that the connection status changes to **Completion notice review in progress**.
4. The IBM team reviews the completion notice and accepts it. The IBM team then places the cross-connect fiber in the ports mentioned in the LOA. This completes the Direct Link configuration and the connection status changes to **Provisioned**.
5. **Link status** indicates **Up**. You must then configure the BGP parameters on the Customer Edge Router (CER) for BGP session establishment. After this is completed, both the **BGP status** and **Link status** indicate **Up**.  

  It can take up to 30 minutes for the link status to update.  
  {:note}

## Locations
{: #dedicated-locations}


The table gives details about the {{site.data.keyword.cloud_notm}} data centers where Direct Link Dedicated (2.0) is available:

|**IBM Location Code** | **Location Type** | **Meet Me Room Operator**| **Operator Site Code** | **Operator Address** |
|-----------------|-----------------|-----------------|--------------------|--------------------|
| **Americas** |  |  |  |
| Dallas 3 | PoP | Equinix | DA1 | 1950 N. Stemmons Freeway |
| Dallas 4 | PoP | Digital Realty | DFW14 | 2323 Bryan St |
| Dallas 10 | DC(AZ1) | QTS | IRV | 6431 Longhorn Drive |
| Dallas 12 | DC(AZ1) | Digital Realty | DFW18 | 907 Security Row |
| Dallas 13 | DC(AZ1) | Cyrus One | Carrollton - Frankford | 1649 W. Frankford Rd |
| Washington DC 2 | PoP | Equinix | DC2 | 21715 Filigree Ct |
| Washington DC 4 | DC(AZ1) | Digital Realty | IAD38 | 44060 Digital Loudoun Plaza (Bldg K) |
| Washington DC 5 | PoP | Coresite | DC2 | 12098 Sunrise Valley Dr |
| Washington DC 6 | DC(AZ1) | Raging Wire | VA2 | 44610 Guilford Drive |
| Washington DC 7 | DC(AZ1) | Sabey | Sabey Intergate.Ashburn | 21741 Red Rum Dr |
| **APAC** |  |  |  |
| Sydney 1 | DC(AZ1) | Global Switch | SYD01 | 400 Harris Street aka 273 Pyrmont St Ultimo |
| Sydney 4 | DC(AZ2) | Digital Realty | SYD10 | 1-11 Templar Rd, Erskine Park |
| Sydney 5 | DC(AZ3) | Equinix | SY4 | 200 Bourke Road |
| Tokyo 3 | PoP 2 | Equinix | TY4 | Chiyoda-ku |
| **EMEA** |  |  |  |
| Frankfurt 1 | PoP | InterXion (DLR) | FRA01 | Hanauer Landstrasse 302 |
| Frankfurt 2 | DC(AZ1) | Zenium | FRA1 | Leonhard - Heisswolf Str 4., Frankfurt am Main |
| Frankfurt 3 | PoP | Equinix| FRA6 | Larchenstrasse 110, Frankfurt Griesheim |
| Frankfurt 4 | DC(AZ2) | E-Shelter | Frankfurt 1 | Eschborner Landstrasse 100, Building H |
| Frankfurt 5 | DC(AZ3) | InterXion | FRA05 | Weismüllerstraße 40 |
| London 2 | DC | Digital Realty | LHR13 | Fountain Court, Cox Lane, Suites 210 and 230 |
| London 3 | PoP | Equinix | LD5 | 8 Buckingham Ave |
| London 4 | DC(AZ1) | ARK | A103 | A57 Cody Technology Park Old, Victor Way, Farnborough |
| London 5 | DC(AZ2) | Gyron |  | Maxted Cl, Hemel Hempstead  |
| London 6 | DC(AZ3) | Zenium( Cyrus One) | LON1 | 12 Liverpool Rd, Trading Estate |
