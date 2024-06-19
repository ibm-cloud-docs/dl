---

copyright:
  years: 2020, 2024
lastupdated: "2024-06-19"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Activating and deactivating Bidirectional Forwarding Detection (BFD)
{: #activate-deactivate-bfd}

You can activate bidirectional forwarding detection (BFD) when you create a {{site.data.keyword.dl_short}} gateway, or after the gateway is provisioned. You can deactivate BFD at any time.
{: shortdesc}

   **WARNING**: Activating and deactivating BFD after the BGP session is established causes BGP session downtime and network disruption until the BGP peer device is configured for the same change.

## Activating BFD
{: #dl-activate-bfd}

To activate BFD on a provisioned gateway, follow these steps:
1. Log in to the [Direct Link console](/interconnectivity/direct-link){: external}, then click the Direct Link name in the table to show its details.
1. Click the BGP tab, then click the bidirectional forwarding detection (BFD) **Deactivated** switch to open the Activate BGP window.
1. Complete the following information:
   * **Interval** – The interval is the minimum time (in milliseconds) expected to occur between when the local routing device sends BFD hello packets and the reply from its neighbor. This value can range from 300 to 255,000 milliseconds.
   * **Multiplier** – The multiplier is the number of times that a hello packet is missed before BFD declares the neighbor down. This value can range from 1 to 255. The default multiplier value is 3.
1. Click **Activate**. The information is added to the details page and the switch shows **Activated**.

If you later want to edit BGP values, click **Edit** in the upper right of the BGP tabbed view. Keep in mind that editing BGP ASN and BGP IPs on the IBM side after BGP session is established, also causes BGP session downtime until the BGP peer device is configured for the same change.
{: note}

## Deactivating BFD
{: #dl-deactivate-bfd}

To deactivate BGP BFD follow these steps:

1. Log in to the [Direct Link console](/interconnectivity/direct-link){: external}, then click the Direct Link name in the table to show its details.
1. Click the BGP tab, then click the bidirectional forwarding detection (BFD) **Activated** switch to show the Deactivate BFD window.
1. Type **Deactivate** to confirm your decision, then click **Deactivate**. The Details page is updated with your change.
