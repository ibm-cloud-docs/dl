---

copyright:
  years: 2024
lastupdated: "2024-05-01"
keywords:

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Preparing for Direct Link changes to advertised service network routes
{: #notification-dl-tgw}

## What changed?
{: #what-changed}

Starting 1 May 2024, IBM Cloud Direct Link Connect and Dedicated offerings enabled a new feature. `10.0.0.0/14`, `10.198.0.0/15`, and `10.200.0.0/14` routes are now announced from a direct link over IBM Cloud Transit Gateway. Additionally, Transit Gateway prevents these routes from making it into classic connections. Only non-classic connections on a transit gateway can use these routes from an on-prem network.

## Why did we make this change?
{: #why-make-this-change}

A direct link must be in transit mode so that it can only connect to transit gateways. When in transit mode, a direct link will not advertise these routes to protect classic networks that might be on a transit gateway that it is connected to. These changes are being made to allow other non-classic connections (for example, VPC or Power Edge Router) on the transit gateway to access these on-prem routes.

## What are the effects of this change?
{: #affected-by-this-change}

All transit gateways with either a classic or Direct Link connection can be affected by this change to `10.0.0.0/14`, `10.198.0.0/15`, and `10.200.0.0/14` routes.

* Classic connections will no longer see these routes, even if they previously did from other non-Direct Link connections.
* Other non-classic connections will see these routes from Direct Link connections.

Keep in mind that:

* If a VM in a classic connection relied on access to these routes from a VPC, it will now be blocked.
* If a virtual server instance in a PER-enabled Power Virtual Server workspace wants to access one of these routes from on-prem, it will now be able to.

## What actions can you take to avoid a failure?
{: #actions-to-take}

If you are relying on a virtual server instance, bare metal server, and/or firewall from classic to access one of these routes from another connection on a transit gateway, you must address any potential issues before this feature is enabled.

No customer action is required to enable these routing changes on Transit Gateway. However, for any existing direct links to start advertising service network routes, follow these steps:

1. Remove the direct link as a connection from all transit gateways. For more information, see [Deleting a connection](/docs/transit-gateway?topic=transit-gateway-deleting-connections&interface=ui).
1. Open the [Direct Link console](/interconnectivity/direct-link){: external} and click the Direct Link name to display its Details page.
1. Click the Edit icon ![Edit icon](/images/edit.png). The Edit configuration side panel displays.
1. Scroll down to the Connections section and change **Transit Gateway** to **Direct resources**.
1. Read and agree to the Direct Link prerequisites, then click **Submit**.
1. Edit the Details page again and change the Connections setting back to **Transit Gateway.**
1. Add the direct link back as a connection on your transit gateways. For more information, see [Adding a connection](/docs/transit-gateway?topic=transit-gateway-adding-connections&interface=ui).
