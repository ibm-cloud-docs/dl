---

copyright:
  years: 2024
lastupdated: "2024-03-07"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Activating, deactivating, and updating VLAN tagging
{: #activate-vlan-tagging}

You can activate Virtual Local Area Network (VLAN) tagging when you create a Direct Link Dedicated gateway, or after the gateway is provisioned. You can change the configured VLAN, or activate/deactivate VLAN tagging on a gateway at any time.
{: shortdesc}

Only IEEE 802.1q (Dot1Q) VLAN tagging is supported, therefore intermediary networks must use and support the IEEE 802.1Q (Dot1Q) standard.
{: note}

VLANs partition and isolate traffic on different networks on the same physical network. VLAN tagging associates Ethernet packets with a VLAN, thereby restricting Layer-2 network connectivity to the members in the same VLAN. This helps with limiting broadcast network traffic and securing network segments.

Activating, deactivating, or updating the VLAN interrupts established BGP sessions. The BGP session cannot be reestablished until the VLAN configuration on your BGP peer device is configured to match. Downtime and traffic loss will occur.
{: important}

## Activating VLAN tagging
{: #dl-activate-vlan-tagging}

To activate VLAN tagging after provisioning a Direct Link Dedicated gateway, follow these steps:

1. Log in to the [Direct Link console](/interconnectivity/direct-link){: external}, then click the Direct Link name in the table to show its details. The Overview tabbed view is displayed.
1. Activate the **VLAN tagging** switch. A confirmation dialog appears.
1. Specify the VLAN that is configured on your router to establish a connection to IBM. You must enter a value between `2` and `3967` and the VLAN must comply with the IEEE 802.1Q (Dot1Q) standard.
1. Click **Activate** to confirm your decision. The Details page updates with your changes.

## Deactivating VLAN tagging
{: #dl-deactivate-vlan-tagging}

To deactivate VLAN tagging after provisioning a Direct Link Dedicated gateway, follow these steps:

1. Log in to the [Direct Link console](/interconnectivity/direct-link){: external}, then click the Direct Link name in the table to show its details. The Overview tabbed view is displayed.
1. Deactivate the "VLAN tagging" switch. A confirmation dialog appears.
1. Type **Deactivate** to confirm your decision, then click **Deactivate**. The Details page updates with your changes.

## Updating VLAN tagging
{: #dl-update-vlan-tag}

To update the VLAN configured on a Direct Link Dedicated gateway, follow these steps:

1. Log in to the [Direct Link console](/interconnectivity/direct-link){: external}, then click the Direct Link name in the table to show its details. The Overview tabbed view is displayed.

1. Click **Edit** in the upper right of the page.
1. In the VLAN tagging section, update the VLAN ID. You must enter a value between `2` and `3967`.
1. Select the checkbox to acknowledge that you have read and agree to the Direct Link Dedicated prerequisities.
1. Click **Submit**.

Editing BGP ASN and BGP IPs on the IBM side after a BGP session is established causes BGP session downtime until the BGP peer device is configured for the same change.
{: remember}
