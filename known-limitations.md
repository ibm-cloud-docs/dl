---

copyright:
  years: 2020, 2024
lastupdated: "2024-09-18"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Known limitations
{: #known-limitations}

Known limitations are as follows:

* VPC networking doesn't consider the AS path length when selecting the best route for network traffic. Therefore, AS prepends configured on direct links have no effect when VPCs are directly connected. However, you can use a transit gateway between the direct link and VPC in some topologies to achieve the wanted effect. For planning considerations, see [Using AS prepends with VPC connections](/docs/dl?topic=dl-dl-planning-considerations&interface=ui#as-prepends-routes).
* Each {{site.data.keyword.dl_full_notm}} connection requires a unique order. If you require multiple connections, open an {{site.data.keyword.dl_full_notm}} order for each connection.
* {{site.data.keyword.dl_full_notm}} requires BGP to establish the routes to a customer's remote network.
* Each {{site.data.keyword.dl_full_notm}} service is not redundant. Diversity can be supplied by IBM for multiple direct links. However, customers must build redundancy in their own BGP schemes.
* If you want to connect to the classic infrastructure, keep in mind that IP subnet overlaps might exist and require exception approval. For more information, see [Configuring BGP](/docs/direct-link?topic=direct-link-configure-ibm-cloud-direct-link#configuring-bgp).
* The {{site.data.keyword.cloud_notm}} services network isn't accessible directly from your remote networks.
* {{site.data.keyword.cloud_notm}} doesn't permit customers to back haul traffic between their remote sites across the {{site.data.keyword.cloud_notm}} backbone. Use {{site.data.keyword.dl_full_notm}} to let your remote networks communicate privately with your {{site.data.keyword.cloud_notm}} infrastructure.
* {{site.data.keyword.dl_full_notm}} requires you to use a VRF (Virtual Routing and Forwarding) instance.
* VRF isn't fully compatible with the {{site.data.keyword.cloud_notm}} SSL and IPsec VPN services.
* The {{site.data.keyword.cloud_notm}} fees for {{site.data.keyword.dl_short}} Dedicated cover the cost of port termination on the {{site.data.keyword.cloud_notm}} infrastructure. Customers are responsible for any fees that are associated with reaching the PoP from a remote network and any cross-connects needed within the PoP facility. {{site.data.keyword.cloud_notm}} does not order a cross-connect on any customer's behalf.
* {{site.data.keyword.cloud_notm}} does not colocate any customer equipment in our network PoPs. Customers must work with their provider to determine whether they need to colocate any equipment in the facility where the {{site.data.keyword.cloud_notm}} network PoP exists.
