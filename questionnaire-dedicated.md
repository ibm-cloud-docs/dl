---

copyright:
  years: 2018, 2019
lastupdated: "2019-12-15"

keywords: dedicated, finalize, questionnaire, special network services, billing, fees, VRF, BGP, case, cross-connect, link speed, VPN, data center, PoP, ECMP

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

# Direct Link prerequisites
{: #ibm-cloud-dl-dedicated-questionnaire}

When you are ready to finalize your Direct Link order, you are asked to read and agree to the following prerequisites. You can speak with an {{site.data.keyword.cloud}} Sales engineer at any time about these terms.
{:shortdesc}

1. Each Direct Link connection requires a unique order. If you require multiple connections, order a Direct Link for each connection.

2. The {{site.data.keyword.cloud_notm}} fees for Direct Link cover the cost of service termination on the {{site.data.keyword.cloud_notm}} infrastructure. You will be responsible for any fees associated with reaching the PoP from your remote network and any cross-connects needed within the PoP facility to reach your exchange provider. You (or your provider) will also be responsible for buying the virtual circuit to {{site.data.keyword.cloud_notm}}. If your provider requires that a router or other device physically sit in the PoP, you will be responsible for the costs associated with collocating that equipment as well. Confirm that your Network or PoP provider can reach the Direct Link and price out the associated costs.

3. {{site.data.keyword.cloud_notm}} will not colocate any customer equipment in our network PoPs.

4. Direct Link service is an unprotected path into the {{site.data.keyword.cloud_notm}} environment. If redundancy is required through the Direct Link service, you must purchase two separate Direct link connections in a single {{site.data.keyword.cloud_notm}} network PoP on two separate routers or order 2 single connections into 2 geographically diverse Direct Link PoP locations. It is the client’s responsibility to configure the routing protocols to ensure resiliency between the two links.

5. {{site.data.keyword.cloud_notm}} will not allow customers to back haul traffic between their remote sites across the {{site.data.keyword.cloud_notm}} backbone. The Direct Link product is meant for your remote networks to be able to privately communicate with your {{site.data.keyword.cloud_notm}} infrastructure.

6. After you've confirmed your circuit has reached the Direct Link PoP, you will need to place an order with the Service Provider to extend service to the Direct Link Demarcation point. IBM will supply a LOA/CFA with port information to order the cross connect.  

7. Please be aware that if you use the `10.x.x.x` network, you still cannot overlap with your hosts within {{site.data.keyword.cloud_notm}} nor with the {{site.data.keyword.cloud_notm}} services network (`10.0.0.0/14`, `10.198.0.0/15`, and `10.200.0.0/14`).

8. VRF is not compatible with {{site.data.keyword.cloud_notm}} SSL and IPsec VPN services. An alternative is to use the direct link itself for management of your servers or run your own VPN solution (such as a Vyatta) that can be configured with different types of VPN. After migrating to a VRF, SSL VPN typically works when a VPN connection is made to the same DC location as the compute that's being accessed, but does not allow access globally.

9. Direct Link Cloud requires BGP in order to implement routes to a customer's remote network.

10.  If you choose to use Auto assign IP addressing, IBM will assign 2 IP addresses from this network, `169.254.0.0/16` for the BGP point-to-point addresses. IBM will use the first IP address in the `/30` subnet. Customer can use the second IP address from this subnet.
