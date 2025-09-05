---

copyright:
  years: 2020, 2025
lastupdated: "2025-09-05"

keywords: direct link release notes

subcollection: dl

content-type: release-note

---

{{site.data.keyword.attribute-definition-list}}
{:release-note: data-hd-content-type='release-note'}

# Release notes for Direct Link
{: #direct-link-release-notes}

Check back regularly to see what's new with {{site.data.keyword.cloud}} Direct Link.
{: shortdesc}

## 02 September 2025
{: #dl-sept0225}
{: release-note}

Manage BGP route selection in VPC
:    Previously, VPC didn't honor AS path length when choosing the best route, and this required using a Transit Gateway between Direct Link and VPC in certain topologies to achieve specific routing behavior and high availability. With this enhancement, you can now influence routing decisions by using AS Path length to choose specific paths—ideal for managing primary and backup Direct Link connections, or configuring failover in hybrid and multicloud environments. For more information, see [Using AS Prepends with VPC connections](/docs/dl?topic=dl-dl-planning-considerations#as-prepends-routes). 

## 17 June 2025
{: #dl-june1725}

Media Access Control Security (MACsec) support for Direct Link Dedicated
:    MACsec, a security protocol that provides encryption for data over Ethernet, is now available in select locations equipped with cross-connect switches (XCS) that support MACsec functionality. Supported markets include Chicago, Madrid, Montreal, Toronto, and Washington D.C. For more information, see [Planning for the Direct Link Dedicated MACsec feature](/docs/dl?topic=dl-dl-planning-considerations#macsec-feature-dedicated).

## 13 March 2025
{: #dl-march1325}

Montreal region now available
:    Montreal is now a supported region for the Direct Link service. For more information, see [IBM Cloud region and data center locations for resource deployment](/docs/overview?topic=overview-locations).

## 12 December 2024
{: #dl-december1224}

Metrics routing support
:    You can now monitor and track metrics for Direct Link physical connections and virtual interfaces, allowing you to analyze traffic flow and set up alerts. This way, you can be notified and take appropriate action if any anomalies or unusual traffic patterns are detected. For more information, see [Monitoring Direct Link](/docs/dl?topic=dl-monitoring).

## 01 May 2024
{: #dl-may0124}

Enable service network routes from Direct Link to non-Classic connections (Behavior Change)
:    When a direct link is connected to a transit gateway, the direct link advertises all service network routes. Before this change, when a direct link was connected to a transit gateway, the direct link did not advertise any service network routes. For more information, see [Preparing for Direct Link changes to advertised service network routes](/docs/dl?topic=dl-notification-dl-tgw).

## 07 March 2024
{: #dl-march0724}
{: release-note}

VLAN tagging support for Direct Link Dedicated
:   A VLAN keeps traffic from different networks separated when traversing shared links and devices within a topology. This process, also known as _VLAN tagging_, limits broadcast network traffic and secures network segments. Previously, dedicated gateway traffic could not be tagged with a VLAN. Now, a customer can optionally specify their own VLAN value either at the time of gateway creation, or update or remove it later. For more information, see [Activating, deactivating, and updating VLAN tagging](/docs/dl?topic=dl-activate-vlan-tagging#dl-update-vlan-tag).

## 06 July 2023
{: #dl-july0623}
{: release-note}

Route report enhancements
:   Added advertised routes to verify route filters and AS prepends applied to the Direct Link gateway.

:   Added “AS path” information to on-prem routes to verify AS prepends.

    For more information, see [Generating a direct link route report](/docs/dl?topic=dl-generate-route-reports&interface=ui).
    {: note}

Support for Madrid multi-zone region (MZR)

## 20 March 2023
{: #dl-march2023}
{: release-note}

BGP route filtering support
:   Configure route filters to control the inbound routes that are learned by your direct link and outbound routes that are advertised by your direct link. BGP route filtering can help reduce resource usage, influence network traffic, and add security. For more information, see [About route filtering](/docs/dl?topic=dl-filter-routes).

## 21 September 2022
{: #dl-september2122}
{: release-note}

Generate a route report for a specific direct link
:   Request a route report to verify expected routes and figure out which routes are associated with attached virtual connections. This feature helps diagnose and troubleshoot routing and connectivity issues. For more information, see [Generating a direct link route report](/docs/dl?topic=dl-generate-route-reports&interface=ui).

BGP AS prepending support
:   Prepend one or more autonomous system numbers (ASNs) at the beginning of an AS path. Prepending an AS path makes a shorter AS path look longer and therefore less preferable to BGP. For more information, see [Using AS prepends to influence route preference](/docs/dl?topic=dl-dl-about#use-case-1).
